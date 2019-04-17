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
# <a name="spatial-sound-in-directx"></a>Пространственные звук в DirectX

Добавить Пространственные звук в Windows Mixed Reality приложения, основанные на DirectX с помощью [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) и [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) аудио библиотеки.

В этом разделе использует образец кода из HolographicHRTFAudioSample.

>[!NOTE]
>Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).  Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.

## <a name="overview-of-head-relative-spatial-sound"></a>Общие сведения о Head относительный пространственных звука

Пространственные звук реализуется как **объект обработки звука (APO)** , использующий **head связанные функции передачи (HRTF)** фильтр для *spatialize* обычные аудиопоток.

Включить эти файлы заголовка в pch.h для доступа к API-интерфейсы аудио:
* XAudio2.h
* xapo.h
* hrtfapoapi.h

Чтобы настроить пространственных звука:
1. Вызовите [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) для инициализации нового APO HRTF аудио.
2. Назначить [параметры HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) и [HRTF среды](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) акустические характеристики пространственных APO звука.
3. Настройте ядро XAudio2 для обработки HRTF.
4. Создание [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) и вызовите [запустить](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>Реализация HRTF и пространственных звука в приложении DirectX

Можно реализовать множество эффектов, настроив HRTF APO с различными параметрами и сред. Используйте следующий код для исследования возможностей. Загрузите пример кода для универсальной платформы Windows здесь: [Образец Spatial звука](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

Вспомогательные типы доступны в этих файлах:
* [AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Загружает звуковые файлы, используя Media Foundation и [IMFSourceReader интерфейс](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).
* [XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Реализует **SetupXAudio2** функцию для инициализации XAudio2 для обработки HRTF.

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>Добавить Пространственные звук для всенаправленные источника

Некоторые голограммы в окружения пользователя выдавать звук одинаково во всех направлениях. Приведенный ниже показано, как инициализировать APO для порождения всенаправленные звук. В этом примере мы применяем эту концепцию для вращающегося куба на основе Windows Holographic шаблона приложения. Полный пример кода, см. в разделе [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).

**Окна пространственных звуковой ядра поддерживает только 48 k samplerate для воспроизведения. Большинство программ по промежуточного слоя, например Unity, автоматически преобразует звуковые файлы в нужный формат, но при запуске переделки на более низких уровнях аудио система или внесении свои собственные, это очень важно помнить предотвратить сбои или нежелательным поведением, как Сбой системы HRTF.**

Во-первых нам нужно инициализировать APO. В нашем примере holographic, мы решили сделать это, когда у нас **HolographicSpace**.

From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

Реализация Initialize, из *OmnidirectionalSound.cpp*:

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

После настройки APO для HRTF вызове [запустить](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) на источник голоса для воспроизведения звукового файла. В нашем примере мы решили поместить его в цикле обработки, таким образом, чтобы продолжить слышать, поступающих из куба.

From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

Из *OmnidirectionalSound.cpp*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

Теперь всякий раз, когда мы обновите рамку, нам нужно обновить голограмма положения относительно самого устройства. Это обусловлено позиций HRTF всегда указываются относительно head пользователя, включая головной положение и ориентацию.

Чтобы сделать это в HolographicSpace, нам нужно создать матрицу преобразования из нашей системы координат SpatialStationaryFrameOfReference для системы координат, которая фиксируется в самом устройстве.

From *HolographicHrtfAudioSampleMain::Update()*:

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

Положение HRTF применяется непосредственно к звуковой APO с вспомогательный класс OmnidirectionalSound.

Из *OmnidirectionalSound::OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

Вот и все! Продолжите чтение, чтобы узнать больше о возможностях со HRTF аудио- и Windows Holographic.

### <a name="initialize-spatial-sound-for-a-directional-source"></a>Инициализировать пространственных звук для направления источника

Некоторые голограммы в окружения пользователя выдавать звук главным образом в одном направлении. Он называется звуковой *cardioid* так, как он выглядит как основа Мультипликационный. Приведенный ниже показано, как инициализировать APO для отправки направленных звука. Полный пример кода, см. в разделе [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .

После настройки APO для HRTF вызвать [запустить](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) на источник голоса для воспроизведения звукового файла.

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

### <a name="implement-custom-decay"></a>Реализация пользовательского decay

Вы можете переопределить скорость, по которому пространственных звука уменьшается с расстоянием и/или на какие расстоянии она обрезает полностью. Чтобы реализовать поведение пользовательского отхода пространственных звук, заполнить [структуры HrtfDistanceDecay](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) и назначьте его **distanceDecay** в [HrtfApoInit структуры](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) Перед передачей в [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) функции.

Добавьте следующий код, чтобы **инициализировать** метод для задания поведения пользовательского отхода было показано ранее. Полный пример кода, см. в разделе [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).

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
