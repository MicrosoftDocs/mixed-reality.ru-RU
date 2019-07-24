---
title: Пространственный звук в DirectX
description: Добавьте Пространственный звук в приложения Windows Mixed Reality на основе DirectX, используя библиотеки аудио XAudio2 и Ксапо Audio.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Пространственный звук, приложения, XAudio2, низкий уровень, Ксапо, аудио Библиотека, пошаговое руководство, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550432"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="71191-104">Пространственный звук в DirectX</span><span class="sxs-lookup"><span data-stu-id="71191-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="71191-105">Добавьте Пространственный звук в приложения Windows Mixed Reality на основе DirectX, используя библиотеки аудио [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) и [ксапо](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) Audio.</span><span class="sxs-lookup"><span data-stu-id="71191-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="71191-106">В этом разделе используется пример кода из Холографичртфаудиосампле.</span><span class="sxs-lookup"><span data-stu-id="71191-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="71191-107">Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="71191-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="71191-108">Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="71191-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="71191-109">Общие сведения о геоотносительном пространственном звуке Head</span><span class="sxs-lookup"><span data-stu-id="71191-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="71191-110">Пространственный звук реализуется как **объект обработки звука (API)** , использующий фильтр **связанной функции передачи (хртф) Head** для *спатиализе* обычного звукового потока.</span><span class="sxs-lookup"><span data-stu-id="71191-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="71191-111">Включите эти файлы заголовков в PCH. h для доступа к API аудио:</span><span class="sxs-lookup"><span data-stu-id="71191-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="71191-112">XAudio2. h</span><span class="sxs-lookup"><span data-stu-id="71191-112">XAudio2.h</span></span>
* <span data-ttu-id="71191-113">ксапо. h</span><span class="sxs-lookup"><span data-stu-id="71191-113">xapo.h</span></span>
* <span data-ttu-id="71191-114">хртфапоапи. h</span><span class="sxs-lookup"><span data-stu-id="71191-114">hrtfapoapi.h</span></span>

<span data-ttu-id="71191-115">Настройка пространственного звука:</span><span class="sxs-lookup"><span data-stu-id="71191-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="71191-116">Вызовите [креатехртфапо](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) , чтобы инициализировать новый API для хртф Audio.</span><span class="sxs-lookup"><span data-stu-id="71191-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="71191-117">Назначьте [Параметры хртф](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) и [среду хртф](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) , чтобы определить акустические характеристики пространственного звукового API.</span><span class="sxs-lookup"><span data-stu-id="71191-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="71191-118">Настройте подсистему XAudio2 для обработки ХРТФ.</span><span class="sxs-lookup"><span data-stu-id="71191-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="71191-119">Создайте объект [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) и вызовите [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span><span class="sxs-lookup"><span data-stu-id="71191-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="71191-120">Реализация ХРТФ и пространственного звука в приложении DirectX</span><span class="sxs-lookup"><span data-stu-id="71191-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="71191-121">Вы можете добиться разнообразных эффектов, настроив API ХРТФ с различными параметрами и средами.</span><span class="sxs-lookup"><span data-stu-id="71191-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="71191-122">Используйте следующий код для изучения возможностей.</span><span class="sxs-lookup"><span data-stu-id="71191-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="71191-123">Скачайте пример кода универсальная платформа Windows отсюда: [Пример пространственного звука](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="71191-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="71191-124">Вспомогательные типы доступны в следующих файлах:</span><span class="sxs-lookup"><span data-stu-id="71191-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="71191-125">[Аудиофилереадер. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Загружает звуковые файлы с помощью Media Foundation и [интерфейса имфсаурцереадер](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span><span class="sxs-lookup"><span data-stu-id="71191-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="71191-126">[XAudio2Helpers. h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Реализует функцию **SetupXAudio2** для инициализации XAudio2 для обработки хртф.</span><span class="sxs-lookup"><span data-stu-id="71191-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="71191-127">Добавление пространственного звука для источника всенаправленные</span><span class="sxs-lookup"><span data-stu-id="71191-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="71191-128">Некоторые голограммы в выпуске окружающей среды пользователя порождаются поровну во всех направлениях.</span><span class="sxs-lookup"><span data-stu-id="71191-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="71191-129">В следующем коде показано, как инициализировать API для выдачи всенаправленныеного звука.</span><span class="sxs-lookup"><span data-stu-id="71191-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="71191-130">В этом примере мы применяем эту концепцию к вращающимся кубам из шаблона приложения Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="71191-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="71191-131">Полный листинг кода см. в разделе [омнидиректионалсаунд. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span><span class="sxs-lookup"><span data-stu-id="71191-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="71191-132">**Пространственный обработчик звуков окна поддерживает только 48 тысяч samplerate для воспроизведения. Большинство программ промежуточного слоя, таких как Unity, автоматически преобразуют звуковые файлы в нужный формат, но если вы начинаете полюсами на более низких уровнях звуковой системы или сделаете свои собственные, это очень важно помнить, чтобы предотвратить сбои или нежелательные поведения, например ХРТФ сбой системы.**</span><span class="sxs-lookup"><span data-stu-id="71191-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="71191-133">Сначала необходимо инициализировать API.</span><span class="sxs-lookup"><span data-stu-id="71191-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="71191-134">В нашем примере приложения мы решили сделать это, когда у нас будет **холографикспаце**.</span><span class="sxs-lookup"><span data-stu-id="71191-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="71191-135">Из *холографичртфаудиосамплемаин:: сесолографикспаце ()* :</span><span class="sxs-lookup"><span data-stu-id="71191-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="71191-136">Реализация Initialize из *омнидиректионалсаунд. cpp*:</span><span class="sxs-lookup"><span data-stu-id="71191-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

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

<span data-ttu-id="71191-137">После настройки API для ХРТФ вызовите [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) на исходном голоса, чтобы воспроизвести звук.</span><span class="sxs-lookup"><span data-stu-id="71191-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="71191-138">В нашем примере приложения мы решили разместить его в цикле, чтобы вы могли услышать звук, поступающий из куба.</span><span class="sxs-lookup"><span data-stu-id="71191-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="71191-139">Из *холографичртфаудиосамплемаин:: сесолографикспаце ()* :</span><span class="sxs-lookup"><span data-stu-id="71191-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="71191-140">Из *омнидиректионалсаунд. cpp*:</span><span class="sxs-lookup"><span data-stu-id="71191-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="71191-141">Теперь, когда мы обновляем кадр, необходимо обновить расположение голограммы относительно самого устройства.</span><span class="sxs-lookup"><span data-stu-id="71191-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="71191-142">Это обусловлено тем, что положения ХРТФ всегда выражаются относительно заголовка пользователя, включая положение и ориентацию головного элемента.</span><span class="sxs-lookup"><span data-stu-id="71191-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="71191-143">Чтобы сделать это в Холографикспаце, нам нужно создать матрицу преобразования из нашей системы координат Спатиалстатионарифрамеофреференце в системе координат, которая исправлена на самом устройстве.</span><span class="sxs-lookup"><span data-stu-id="71191-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="71191-144">Из *холографичртфаудиосамплемаин:: Update ()* :</span><span class="sxs-lookup"><span data-stu-id="71191-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

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

<span data-ttu-id="71191-145">Расположение ХРТФ применяется непосредственно к звуковому APIу вспомогательного класса Омнидиректионалсаунд.</span><span class="sxs-lookup"><span data-stu-id="71191-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="71191-146">Из *омнидиректионалсаунд:: OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="71191-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="71191-147">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="71191-147">That's it!</span></span> <span data-ttu-id="71191-148">Продолжайте чтение для получения дополнительных сведений о том, что можно делать с ХРТФ Audio и Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="71191-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="71191-149">Инициализировать Пространственный звук для направленного источника</span><span class="sxs-lookup"><span data-stu-id="71191-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="71191-150">Некоторые голограммы в выпуске окружающей среды пользователя порождаются в основном в одном направлении.</span><span class="sxs-lookup"><span data-stu-id="71191-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="71191-151">Этот шаблон звука называется *кардиоид* , так как выглядит как мультипликационное сердце.</span><span class="sxs-lookup"><span data-stu-id="71191-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="71191-152">В следующем коде показано, как инициализировать API, чтобы выдать направленный звук.</span><span class="sxs-lookup"><span data-stu-id="71191-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="71191-153">Полный листинг кода см. в разделе [кардиоидсаунд. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span><span class="sxs-lookup"><span data-stu-id="71191-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="71191-154">После настройки API для ХРТФ вызовите [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) на исходном голоса, чтобы воспроизвести звук.</span><span class="sxs-lookup"><span data-stu-id="71191-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

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

### <a name="implement-custom-decay"></a><span data-ttu-id="71191-155">Реализация пользовательского Decay</span><span class="sxs-lookup"><span data-stu-id="71191-155">Implement custom decay</span></span>

<span data-ttu-id="71191-156">Можно переопределить скорость, с которой пространственный звук будет отключаться с расстояния и (или) расстояния, на котором она полностью обрезается.</span><span class="sxs-lookup"><span data-stu-id="71191-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="71191-157">Чтобы реализовать пользовательское поведение Decay для пространственного звука, заполните [структуру хртфдистанцедекай](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) и присвойте ее полю **Дистанцедекай** в [структуре хртфапоинит](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) , прежде чем передать его в функцию [креатехртфапо](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) .</span><span class="sxs-lookup"><span data-stu-id="71191-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="71191-158">Добавьте следующий код в метод **Initialize** , показанный ранее, чтобы указать пользовательское поведение Decay.</span><span class="sxs-lookup"><span data-stu-id="71191-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="71191-159">Полный листинг кода см. в разделе [кустомдекай. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span><span class="sxs-lookup"><span data-stu-id="71191-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

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
