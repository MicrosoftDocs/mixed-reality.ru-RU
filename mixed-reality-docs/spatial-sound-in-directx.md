---
title: Пространственные звук в DirectX
description: Добавьте Пространственные звук в Windows Mixed Reality приложения, основанные на DirectX с помощью библиотек XAudio2 и xAPO аудио.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows смешанный реальность, пространственных звук, приложения, XAudio2, низкого уровня, xAPO, аудио библиотеки, пошаговое руководство, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605143"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="6c05e-104">Пространственные звук в DirectX</span><span class="sxs-lookup"><span data-stu-id="6c05e-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="6c05e-105">Добавить Пространственные звук в Windows Mixed Reality приложения, основанные на DirectX с помощью [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) и [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) аудио библиотеки.</span><span class="sxs-lookup"><span data-stu-id="6c05e-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="6c05e-106">В этом разделе использует образец кода из HolographicHRTFAudioSample.</span><span class="sxs-lookup"><span data-stu-id="6c05e-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="6c05e-107">Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="6c05e-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="6c05e-108">Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.</span><span class="sxs-lookup"><span data-stu-id="6c05e-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="6c05e-109">Общие сведения о Head относительный пространственных звука</span><span class="sxs-lookup"><span data-stu-id="6c05e-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="6c05e-110">Пространственные звук реализуется как **объект обработки звука (APO)** , использующий **head связанные функции передачи (HRTF)** фильтр для *spatialize* обычные аудиопоток.</span><span class="sxs-lookup"><span data-stu-id="6c05e-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="6c05e-111">Включить эти файлы заголовка в pch.h для доступа к API-интерфейсы аудио:</span><span class="sxs-lookup"><span data-stu-id="6c05e-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="6c05e-112">XAudio2.h</span><span class="sxs-lookup"><span data-stu-id="6c05e-112">XAudio2.h</span></span>
* <span data-ttu-id="6c05e-113">xapo.h</span><span class="sxs-lookup"><span data-stu-id="6c05e-113">xapo.h</span></span>
* <span data-ttu-id="6c05e-114">hrtfapoapi.h</span><span class="sxs-lookup"><span data-stu-id="6c05e-114">hrtfapoapi.h</span></span>

<span data-ttu-id="6c05e-115">Чтобы настроить пространственных звука:</span><span class="sxs-lookup"><span data-stu-id="6c05e-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="6c05e-116">Вызовите [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) для инициализации нового APO HRTF аудио.</span><span class="sxs-lookup"><span data-stu-id="6c05e-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="6c05e-117">Назначить [параметры HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) и [HRTF среды](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) акустические характеристики пространственных APO звука.</span><span class="sxs-lookup"><span data-stu-id="6c05e-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="6c05e-118">Настройте ядро XAudio2 для обработки HRTF.</span><span class="sxs-lookup"><span data-stu-id="6c05e-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="6c05e-119">Создание [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) и вызовите [запустить](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span><span class="sxs-lookup"><span data-stu-id="6c05e-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="6c05e-120">Реализация HRTF и пространственных звука в приложении DirectX</span><span class="sxs-lookup"><span data-stu-id="6c05e-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="6c05e-121">Можно реализовать множество эффектов, настроив HRTF APO с различными параметрами и сред.</span><span class="sxs-lookup"><span data-stu-id="6c05e-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="6c05e-122">Используйте следующий код для исследования возможностей.</span><span class="sxs-lookup"><span data-stu-id="6c05e-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="6c05e-123">Загрузите пример кода для универсальной платформы Windows здесь: [Образец Spatial звука](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="6c05e-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="6c05e-124">Вспомогательные типы доступны в этих файлах:</span><span class="sxs-lookup"><span data-stu-id="6c05e-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="6c05e-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Загружает звуковые файлы, используя Media Foundation и [IMFSourceReader интерфейс](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span><span class="sxs-lookup"><span data-stu-id="6c05e-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="6c05e-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Реализует **SetupXAudio2** функцию для инициализации XAudio2 для обработки HRTF.</span><span class="sxs-lookup"><span data-stu-id="6c05e-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="6c05e-127">Добавить Пространственные звук для всенаправленные источника</span><span class="sxs-lookup"><span data-stu-id="6c05e-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="6c05e-128">Некоторые голограммы в окружения пользователя выдавать звук одинаково во всех направлениях.</span><span class="sxs-lookup"><span data-stu-id="6c05e-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="6c05e-129">Приведенный ниже показано, как инициализировать APO для порождения всенаправленные звук.</span><span class="sxs-lookup"><span data-stu-id="6c05e-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="6c05e-130">В этом примере мы применяем эту концепцию для вращающегося куба на основе Windows Holographic шаблона приложения.</span><span class="sxs-lookup"><span data-stu-id="6c05e-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="6c05e-131">Полный пример кода, см. в разделе [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span><span class="sxs-lookup"><span data-stu-id="6c05e-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="6c05e-132">**Окна пространственных звуковой ядра поддерживает только 48 k samplerate для воспроизведения. Большинство программ по промежуточного слоя, например Unity, автоматически преобразует звуковые файлы в нужный формат, но при запуске переделки на более низких уровнях аудио система или внесении свои собственные, это очень важно помнить предотвратить сбои или нежелательным поведением, как Сбой системы HRTF.**</span><span class="sxs-lookup"><span data-stu-id="6c05e-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="6c05e-133">Во-первых нам нужно инициализировать APO.</span><span class="sxs-lookup"><span data-stu-id="6c05e-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="6c05e-134">В нашем примере holographic, мы решили сделать это, когда у нас **HolographicSpace**.</span><span class="sxs-lookup"><span data-stu-id="6c05e-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="6c05e-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="6c05e-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="6c05e-136">Реализация Initialize, из *OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="6c05e-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

```
// Initializes an APO that emits sound equally in all directions.
HRESULT OmnidirectionalSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        // Passing in nullptr as the first arg for HrtfApoInit initializes the APO with defaults of
        // omnidirectional sound with natural distance decay behavior.
        // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( nullptr, &xapo );
    }

    if ( SUCCEEDED( hr ) )
    {
        // _hrtfParams is of type ComPtr<IXAPOHrtfParameters>.
        hr = xapo.As( &_hrtfParams );
    }

    // Set the default environment.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice.
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;

        // _sourceVoice is of type IXAudio2SourceVoice*.
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

<span data-ttu-id="6c05e-137">После настройки APO для HRTF вызове [запустить](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) на источник голоса для воспроизведения звукового файла.</span><span class="sxs-lookup"><span data-stu-id="6c05e-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="6c05e-138">В нашем примере мы решили поместить его в цикле обработки, таким образом, чтобы продолжить слышать, поступающих из куба.</span><span class="sxs-lookup"><span data-stu-id="6c05e-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="6c05e-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="6c05e-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="6c05e-140">Из *OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="6c05e-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="6c05e-141">Теперь всякий раз, когда мы обновите рамку, нам нужно обновить голограмма положения относительно самого устройства.</span><span class="sxs-lookup"><span data-stu-id="6c05e-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="6c05e-142">Это обусловлено позиций HRTF всегда указываются относительно head пользователя, включая головной положение и ориентацию.</span><span class="sxs-lookup"><span data-stu-id="6c05e-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="6c05e-143">Чтобы сделать это в HolographicSpace, нам нужно создать матрицу преобразования из нашей системы координат SpatialStationaryFrameOfReference для системы координат, которая фиксируется в самом устройстве.</span><span class="sxs-lookup"><span data-stu-id="6c05e-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="6c05e-144">From *HolographicHrtfAudioSampleMain::Update()*:</span><span class="sxs-lookup"><span data-stu-id="6c05e-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

```
m_spinningCubeRenderer->Update(m_timer);

SpatialPointerPose^ currentPose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
if (currentPose != nullptr)
{
    // Use a coordinate system built from a pointer pose.
    SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
    if (pose != nullptr)
    {
        float3 headPosition = pose->Head->Position;
        float3 headUp = pose->Head->UpDirection;
        float3 headDirection = pose->Head->ForwardDirection;

        // To construct a rotation matrix, we need three vectors that are mutually orthogonal.
        // The first vector is the gaze vector.
        float3 negativeZAxis = normalize(headDirection);

        // The second vector should end up pointing away from the horizontal plane of the device.
        // We first guess by using the head "up" direction.
        float3 positiveYAxisGuess = normalize(headUp);

        // The third vector completes the set by being orthogonal to the other two.
        float3 positiveXAxis = normalize(cross(negativeZAxis, positiveYAxisGuess));

        // Now, we can correct our "up" vector guess by redetermining orthogonality.
        float3 positiveYAxis = normalize(cross(negativeZAxis, positiveXAxis));

        // The rotation matrix is formed as a standard basis rotation.
        float4x4 rotationTransform =
            {
            positiveXAxis.x, positiveYAxis.x, negativeZAxis.x, 0.f,
            positiveXAxis.y, positiveYAxis.y, negativeZAxis.y, 0.f,
            positiveXAxis.z, positiveYAxis.z, negativeZAxis.z, 0.f,
            0.f, 0.f, 0.f, 1.f,
            };

        // The translate transform can be constructed using the Windows::Foundation::Numerics API.
        float4x4 translationTransform = make_float4x4_translation(-headPosition);

        // Now, we have a basis transform from our spatial coordinate system to a device-relative
        // coordinate system.
        float4x4 coordinateSystemTransform = translationTransform * rotationTransform;

        // Reinterpret the cube position in the device's coordinate system.
        float3 cubeRelativeToHead = transform(m_spinningCubeRenderer->GetPosition(), coordinateSystemTransform);

        // Note that at (0, 0, 0) exactly, the HRTF audio will simply pass through audio. We can use a minimal offset
        // to simulate a zero distance when the hologram position vector is exactly at the device origin in order to
        // allow HRTF to continue functioning in this edge case.
        float distanceFromHologramToHead = length(cubeRelativeToHead);
        static const float distanceMin = 0.00001f;
        if (distanceFromHologramToHead < distanceMin)
        {
            cubeRelativeToHead = float3(0.f, distanceMin, 0.f);
        }

        // Position the spatial sound source on the hologram.
        m_omnidirectionalSound.OnUpdate(cubeRelativeToHead);

        // For debugging, it can be interesting to observe the distance in the debugger.
        /*
        std::wstring distanceString = L"Distance from hologram to head: ";
        distanceString += std::to_wstring(distanceFromHologramToHead);
        distanceString += L"\n";
        OutputDebugStringW(distanceString.c_str());
        */
    }
}
```

<span data-ttu-id="6c05e-145">Положение HRTF применяется непосредственно к звуковой APO с вспомогательный класс OmnidirectionalSound.</span><span class="sxs-lookup"><span data-stu-id="6c05e-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="6c05e-146">Из *OmnidirectionalSound::OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="6c05e-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="6c05e-147">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="6c05e-147">That's it!</span></span> <span data-ttu-id="6c05e-148">Продолжите чтение, чтобы узнать больше о возможностях со HRTF аудио- и Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="6c05e-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="6c05e-149">Инициализировать пространственных звук для направления источника</span><span class="sxs-lookup"><span data-stu-id="6c05e-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="6c05e-150">Некоторые голограммы в окружения пользователя выдавать звук главным образом в одном направлении.</span><span class="sxs-lookup"><span data-stu-id="6c05e-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="6c05e-151">Он называется звуковой *cardioid* так, как он выглядит как основа Мультипликационный.</span><span class="sxs-lookup"><span data-stu-id="6c05e-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="6c05e-152">Приведенный ниже показано, как инициализировать APO для отправки направленных звука.</span><span class="sxs-lookup"><span data-stu-id="6c05e-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="6c05e-153">Полный пример кода, см. в разделе [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span><span class="sxs-lookup"><span data-stu-id="6c05e-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="6c05e-154">После настройки APO для HRTF вызвать [запустить](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) на источник голоса для воспроизведения звукового файла.</span><span class="sxs-lookup"><span data-stu-id="6c05e-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

```
// Initializes an APO that emits directional sound.
HRESULT CardioidSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );
    if ( SUCCEEDED( hr ) )
    {
        // Initialize with "Scaling" fully directional and "Order" with broad radiation pattern.
        // As the order goes higher, the cardioid directivity region becomes narrower.
        // Any direct path signal outside of the directivity region will be attenuated based on the scaling factor.
        // For example, if scaling is set to 1 (fully directional) the direct path signal outside of the directivity
        // region will be fully attenuated and only the reflections from the environment will be audible.
        hr = ConfigureApo( 1.0f, 4.0f );
    }
    return hr;
}

HRESULT CardioidSound::ConfigureApo( float scaling, float order )
{
    // Cardioid directivity configuration:
    // Directivity is specified at xAPO instance initialization and can't be changed per frame.
    // To change directivity, stop audio processing and reinitialize another APO instance with the new directivity.
    HrtfDirectivityCardioid cardioid;
    cardioid.directivity.type = HrtfDirectivityType::Cardioid;
    cardioid.directivity.scaling = scaling;
    cardioid.order = order;

    // APO intialization
    HrtfApoInit apoInit;
    apoInit.directivity = &cardioid.directivity;
    apoInit.distanceDecay = nullptr; // nullptr specifies natural distance decay behavior (simulates real world)

    // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
    ComPtr<IXAPO> xapo;
    auto hr = CreateHrtfApo( &apoInit, &xapo );

    if ( SUCCEEDED( hr ) )
    {
        hr = xapo.As( &_hrtfParams );
    }

    // Set the initial environment.
    // Environment settings configure the "distance cues" used to compute the early and late reverberations.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( _HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

### <a name="implement-custom-decay"></a><span data-ttu-id="6c05e-155">Реализация пользовательского decay</span><span class="sxs-lookup"><span data-stu-id="6c05e-155">Implement custom decay</span></span>

<span data-ttu-id="6c05e-156">Вы можете переопределить скорость, по которому пространственных звука уменьшается с расстоянием и/или на какие расстоянии она обрезает полностью.</span><span class="sxs-lookup"><span data-stu-id="6c05e-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="6c05e-157">Чтобы реализовать поведение пользовательского отхода пространственных звук, заполнить [структуры HrtfDistanceDecay](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) и назначьте его **distanceDecay** в [HrtfApoInit структуры](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) Перед передачей в [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) функции.</span><span class="sxs-lookup"><span data-stu-id="6c05e-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="6c05e-158">Добавьте следующий код, чтобы **инициализировать** метод для задания поведения пользовательского отхода было показано ранее.</span><span class="sxs-lookup"><span data-stu-id="6c05e-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="6c05e-159">Полный пример кода, см. в разделе [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span><span class="sxs-lookup"><span data-stu-id="6c05e-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

```
HRESULT CustomDecaySound::Initialize( LPCWSTR filename )
{
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        HrtfDistanceDecay customDecay;
        customDecay.type = HrtfDistanceDecayType::CustomDecay;               // Custom decay behavior, we'll pass in the gain value on every frame.
        customDecay.maxGain = 0;                                             // 0dB max gain
        customDecay.minGain = -96.0f;                                        // -96dB min gain
        customDecay.unityGainDistance = HRTF_DEFAULT_UNITY_GAIN_DISTANCE;    // Default unity gain distance
        customDecay.cutoffDistance = HRTF_DEFAULT_CUTOFF_DISTANCE;           // Default cutoff distance

        // Setting the directivity to nullptr specifies omnidirectional sound.
        HrtfApoInit init;
        init.directivity = nullptr;
        init.distanceDecay = &customDecay;

        // CreateHrtfApo will fail with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( &init, &xapo );
    }
...
}
```
