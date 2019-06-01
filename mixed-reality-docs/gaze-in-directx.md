---
title: HEAD и глаз взглядом в DirectX
description: Руководство разработчика по использованию головной взглядом и отслеживания в собственных приложениях DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: взглядом, головного взглядом, head отслеживания, отслеживания, directx, входные данные и голограммы
ms.openlocfilehash: ac72c5305527ed2d68945aeb32051cf2246a736e
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453740"
---
# <a name="head-and-eye-gaze-input-in-directx"></a>HEAD и глаз помощи входных данных в DirectX

В Windows Mixed Reality, глаз и головной взглядом входных данных используется для определения того, что пользователь просматривает. Это может использоваться для диска основных моделей ввода, такие как [головного взглядом и фиксации](gaze-and-commit.md)и Кроме того, чтобы предоставить контекст для типов взаимодействия. Существует два вида взглядом векторы, которые доступны через API: head взглядом и взглядом глаз.  Оба языка поставляются как 3 измерений Рэй с начала координат и направление. Приложения могут затем raycast в их сцены или реальном мире и определить, что он предназначен.

**HEAD помощи** представляет направление, в указанном head пользователя. Это можно рассматривать как положения и направления переадресации самого устройства, с позиции, представляющий центре точек между двух мониторов.  HEAD взглядом доступна на всех устройствах смешанной реальности.

**Взглядом глаз** представляет направление, в котором глаза пользователя нужны сторону. Начало координат находится между глаза пользователя.  Она доступна на устройствах смешанной реальности, включающие за системой отслеживания.

Head и глаз взглядом лучей, доступны через [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API. Просто вызовите [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) для получения объекта SpatialPointerPose в указанной отметке времени и [системы координат](coordinate-systems-in-directx.md). Этот SpatialPointerPose содержит origin головной взглядом и направление. Он также содержит начала координат глаз взглядом и направление при наличии отслеживания.

## <a name="using-head-gaze"></a>С помощью головного взглядом

Чтобы получить доступ к головному взглядом, запустите путем вызова [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) для получения объекта SpatialPointerPose. Необходимо передать следующие параметры.
 - Объект [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , представляющий требуемой системы координат для головного взглядом. Это ограничение задается *система coordinateSystem* переменных в следующем коде. Дополнительные сведения см. в статье наших [системы координат](coordinate-systems-in-directx.md) руководство разработчика.
 - Объект [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , представляющий точное время Головной позу запрошено.  Обычно вы будете использовать метку времени, соответствующее времени, когда будет отображаться текущего кадра. Вы можете получить эту метку времени отображения прогнозируемых из [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) объект, который можно получить с помощью текущего [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).  Этот объект HolographicFramePrediction представлен *прогноза* переменной в следующем коде.

 При наличии допустимых SpatialPointerPose головного положения и направления переадресации доступны как свойства.  Ниже показано, как получить к ним доступ.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a>С помощью взглядом глаз

API взглядом глаз очень похожа на головной взглядом.  Она использует тот же [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, предоставляющая луча, начало координат и направление, вы можете raycast от сцены.  Единственная разница в, необходимо явно включить отслеживание глаз перед его использованием. Для этого вам необходимо выполнить два действия:
1. Запрашивать разрешение пользователя для использования отслеживания в приложении.
2. Включите функцию «Помощи Input» в манифесте пакета.

### <a name="requesting-access-to-gaze-input"></a>Запросить доступ к помощи входных данных
При запуске приложения вызовите [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) запрашивать доступ к глаз отслеживания. Система будет запрашивать пользователя, при необходимости и возвращают [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) после предоставления доступа. Это асинхронный вызов, поэтому она требует некоторого дополнительного управления. Следующий пример запускает отсоединенных std::thread ожидания результата, который сохраняется в переменную-член вызывается *m_isEyeTrackingEnabled*.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
Запуск отсоединенных поток является только один из вариантов для обработки асинхронных вызовов.  Кроме того, можно использовать новый [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) функциональные возможности, поддерживаемые C++/WinRT.
Вот еще один пример для запросом разрешения пользователя:
-   EyesPose::IsSupported() позволяет приложению для запуска диалогового окна разрешение только в том случае, если имеется tracker глаз.
-   GazeInputAccessStatus m_gazeInputAccessStatus; Это необходимо для предотвращения многократного всплывающее окно с запросом разрешения.

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a>Объявление *помощи ввода* возможностей

Дважды щелкните файл appxmanifest в *обозревателе решений*.  Затем перейдите к *возможности* и установите *помощи ввода* возможностей. 

![Возможность ввода взглядом](images/gaze-input-capability.png)

Это добавляет следующие строки, чтобы *пакета* раздела appxmanifest-файла:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Начало Рэй взглядом глаз
После получения доступа к ET, вы можете свободно скопировать Рэй взглядом глаз каждого кадра.  Как и в головном взглядом получить [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) путем вызова [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) требуемой отметкой времени и системы координат. Содержит SpatialPointerPose [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) объекта через [глаза](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) свойство. Это отличное от null, только при включении отслеживания. Оттуда можно проверить, есть ли у пользователя на устройстве за отслеживание калибровки, вызвав [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  Затем используйте [помощи](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) свойство для получения [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing глаза помощи положения и направления. Свойства взглядом могут иногда иметь значение null, поэтому не забудьте проверить это. Это может произойти является, если калиброванных пользователь временно закрывает их глаза.

Приведенный ниже показано, как получить доступ к Рэй взглядом глаз.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a>Сопоставление взглядом с других входных данных

Иногда может оказаться необходимым [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) , соответствующий с событием в прошлом. Например если пользователь выполняет Air коснитесь кнопки, приложение может потребоваться знать, что они бы все видели. Для этой цели, используя [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) с кадром прогнозируемое время могут быть неточными из-за задержки между системы обработки ввода и отображения времени. Кроме того при использовании взглядом глаза для нацеливания на этот момент, как правило, для перемещения еще до завершения действие фиксации. Это меньше всего важна для простой Air, коснитесь, но становится более критичной, при объединении долго голосовые команды с быстрой глаз перемещений. Один из способов обработки этого сценария — чтобы сделать дополнительный вызов [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), с помощью исторических метку времени, соответствующее событию ввода.  

Однако для входных данных, которая направляет через SpatialInteractionManager, есть более простой метод. [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) имеет свои собственные [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) функции. Вызова метода, предоставляющий вполне коррелированные [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) без догадки. Дополнительные сведения о работе с SpatialInteractionSourceStates взгляните на [руки и контроллеры движения в DirectX](hands-and-motion-controllers-in-directx.md) документации.

## <a name="see-also"></a>См. также
* [Головной модель ввода, взглядом и фиксации](gaze-and-commit.md)
* [Отслеживания на HoloLens 2](eye-tracking.md)
* [Системы координат в DirectX](coordinate-systems-in-directx.md)
* [Голосовой ввод в DirectX](voice-input-in-directx.md)
* [Контроллеры движения и жестов в DirectX](hands-and-motion-controllers-in-directx.md)
