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
# <a name="spatial-sound-in-directx"></a>Пространственный звук в DirectX

Добавьте Пространственный звук в приложения Windows Mixed Reality на основе DirectX, используя библиотеки аудио [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) и [ксапо](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) Audio.

В этом разделе используется пример кода из Холографичртфаудиосампле.

>[!NOTE]
>Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

## <a name="overview-of-head-relative-spatial-sound"></a>Общие сведения о геоотносительном пространственном звуке Head

Пространственный звук реализуется как **объект обработки звука (API)** , использующий фильтр **связанной функции передачи (хртф) Head** для *спатиализе* обычного звукового потока.

Включите эти файлы заголовков в PCH. h для доступа к API аудио:
* XAudio2. h
* ксапо. h
* хртфапоапи. h

Настройка пространственного звука:
1. Вызовите [креатехртфапо](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) , чтобы инициализировать новый API для хртф Audio.
2. Назначьте [Параметры хртф](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) и [среду хртф](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) , чтобы определить акустические характеристики пространственного звукового API.
3. Настройте подсистему XAudio2 для обработки ХРТФ.
4. Создайте объект [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) и вызовите [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>Реализация ХРТФ и пространственного звука в приложении DirectX

Вы можете добиться разнообразных эффектов, настроив API ХРТФ с различными параметрами и средами. Используйте следующий код для изучения возможностей. Скачайте пример кода универсальная платформа Windows отсюда: [Пример пространственного звука](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

Вспомогательные типы доступны в следующих файлах:
* [Аудиофилереадер. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Загружает звуковые файлы с помощью Media Foundation и [интерфейса имфсаурцереадер](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).
* [XAudio2Helpers. h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Реализует функцию **SetupXAudio2** для инициализации XAudio2 для обработки хртф.

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>Добавление пространственного звука для источника всенаправленные

Некоторые голограммы в выпуске окружающей среды пользователя порождаются поровну во всех направлениях. В следующем коде показано, как инициализировать API для выдачи всенаправленныеного звука. В этом примере мы применяем эту концепцию к вращающимся кубам из шаблона приложения Windows Holographic. Полный листинг кода см. в разделе [омнидиректионалсаунд. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).

**Пространственный обработчик звуков окна поддерживает только 48 тысяч samplerate для воспроизведения. Большинство программ промежуточного слоя, таких как Unity, автоматически преобразуют звуковые файлы в нужный формат, но если вы начинаете полюсами на более низких уровнях звуковой системы или сделаете свои собственные, это очень важно помнить, чтобы предотвратить сбои или нежелательные поведения, например ХРТФ сбой системы.**

Сначала необходимо инициализировать API. В нашем примере приложения мы решили сделать это, когда у нас будет **холографикспаце**.

Из *холографичртфаудиосамплемаин:: сесолографикспаце ()* :

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

Реализация Initialize из *омнидиректионалсаунд. cpp*:

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

После настройки API для ХРТФ вызовите [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) на исходном голоса, чтобы воспроизвести звук. В нашем примере приложения мы решили разместить его в цикле, чтобы вы могли услышать звук, поступающий из куба.

Из *холографичртфаудиосамплемаин:: сесолографикспаце ()* :

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

Из *омнидиректионалсаунд. cpp*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

Теперь, когда мы обновляем кадр, необходимо обновить расположение голограммы относительно самого устройства. Это обусловлено тем, что положения ХРТФ всегда выражаются относительно заголовка пользователя, включая положение и ориентацию головного элемента.

Чтобы сделать это в Холографикспаце, нам нужно создать матрицу преобразования из нашей системы координат Спатиалстатионарифрамеофреференце в системе координат, которая исправлена на самом устройстве.

Из *холографичртфаудиосамплемаин:: Update ()* :

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

Расположение ХРТФ применяется непосредственно к звуковому APIу вспомогательного класса Омнидиректионалсаунд.

Из *омнидиректионалсаунд:: OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

Вот и все! Продолжайте чтение для получения дополнительных сведений о том, что можно делать с ХРТФ Audio и Windows Holographic.

### <a name="initialize-spatial-sound-for-a-directional-source"></a>Инициализировать Пространственный звук для направленного источника

Некоторые голограммы в выпуске окружающей среды пользователя порождаются в основном в одном направлении. Этот шаблон звука называется *кардиоид* , так как выглядит как мультипликационное сердце. В следующем коде показано, как инициализировать API, чтобы выдать направленный звук. Полный листинг кода см. в разделе [кардиоидсаунд. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .

После настройки API для ХРТФ вызовите [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) на исходном голоса, чтобы воспроизвести звук.

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

### <a name="implement-custom-decay"></a>Реализация пользовательского Decay

Можно переопределить скорость, с которой пространственный звук будет отключаться с расстояния и (или) расстояния, на котором она полностью обрезается. Чтобы реализовать пользовательское поведение Decay для пространственного звука, заполните [структуру хртфдистанцедекай](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) и присвойте ее полю **Дистанцедекай** в [структуре хртфапоинит](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) , прежде чем передать его в функцию [креатехртфапо](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) .

Добавьте следующий код в метод **Initialize** , показанный ранее, чтобы указать пользовательское поведение Decay. Полный листинг кода см. в разделе [кустомдекай. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).

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
