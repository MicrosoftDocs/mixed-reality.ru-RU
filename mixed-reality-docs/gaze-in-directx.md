---
title: Взгляд на головной взгляд и глаз в DirectX
description: Рекомендации для разработчиков по использованию головного взгляда и отслеживания взгляда в собственных приложениях DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: глаз-взгляд, руководитель-взгляд, отслеживание головок, отслеживание глаз, DirectX, ввод, голограммы
ms.openlocfilehash: 664657b9ab01530a608e31091823e828cc99d0cd
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926558"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>Ввод с взгляда на глаза в DirectX

В Windows Mixed Reality для определения того, что просматривает пользователь, используется ввод с глазом и взглядом на головной взгляд. Это можно использовать для создания первичных входных моделей, таких как [head-взгляд и Commit](gaze-and-commit.md), а также для предоставления контекста для типов взаимодействий. Есть два типа векторов взгляда, доступных через API: «Head-взгляд» и «глаз-взгляд».  Оба значения предоставляются в виде трехмерного луча с исходным и направленным координатами. Приложения могут райкаст в фоновом режиме или в реальном мире, а также определить назначение пользователя.

**Заголовок-взгляд** представляет направление, на которое указывает заголовок пользователя. Это следует рассматривать как расположение и направление вперед самого устройства, а также позицию, представляющую центральную точку между двумя дисплеями. Головной взгляд доступен на всех устройствах смешанной реальности.

**Глаз** . Наблюдатель представляет направление, в котором просматриваются глаза пользователя. Источник располагается между глазами пользователя.  Она доступна на устройствах смешанной реальности, включающих систему отслеживания взгляда.

И те, и другие лучи доступны через API [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) . Просто вызовите [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) , чтобы получить новый объект спатиалпоинтерпосе в указанной метке времени и [системе координат](coordinate-systems-in-directx.md). Этот Спатиалпоинтерпосе содержит источник и направление головного взгляда. Он также содержит источник глаза и направление взгляда, если отслеживание взгляда доступно.

### <a name="device-support"></a>Поддержка устройств
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Функциями</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></td>
</tr>
<tr>
     <td>Направление головы</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>Взгляд — взгляд</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>Использование Head-взгляда

Чтобы получить доступ к Head, начните с вызова [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) , чтобы получить новый объект спатиалпоинтерпосе. Необходимо передать следующие параметры.
 - Объект [спатиалкурдинатесистем](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) , представляющий нужную систему координат для головного взгляда. Он представлен переменной *курдинатесистем* в следующем коде. Дополнительные сведения см. в нашем разделе, посвященном разработчику [систем координат](coordinate-systems-in-directx.md) .
 - [Отметка времени](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , представляющая точное время запроса Head.  Обычно используется метка времени, соответствующая времени, когда будет отображаться текущий кадр. Эту прогнозируемую отметку экрана можно получить из объекта [холографикфрамепредиктион](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , доступного через текущий [холографикфраме](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).  Этот объект Холографикфрамепредиктион представляется переменной *прогноза* в следующем коде.

 После получения допустимого Спатиалпоинтерпосе расположение головного и прямого направления можно получить в виде свойств.  В следующем коде показано, как получить доступ к ним.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>Использование глаза-взгляд

Обратите внимание, что для пользователей, использующих входные данные взгляда глаз, каждый пользователь должен пройти по [калибровке пользователя с отслеживанием взгляда](calibration.md) при первом использовании устройства. API взгляда на глаза очень похож на голову.
Он использует тот же API [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , который предоставляет происхождение и направление луча, которые можно райкаст на сцене.  Единственное отличие заключается в том, что необходимо явно включить отслеживание взгляда перед его использованием. Для этого необходимо выполнить два действия:
1. Запрос разрешения пользователя на использование отслеживания взгляда в приложении.
2. Включите функцию "Ввод взгляда" в манифесте пакета.

### <a name="requesting-access-to-eye-gaze-input"></a>Запрос доступа к входным данным взгляда
При запуске приложения вызовите [эйеспосе:: рекуестакцессасинк](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) , чтобы запросить доступ к отслеживанию глаз. Система запросит пользователя при необходимости и возвратит [газеинпутакцессстатус:: Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) после предоставления доступа. Это асинхронный вызов, поэтому для него требуется некоторое дополнительное управление. В следующем примере показано, как отсоединить отсоединенный std:: Thread для ожидания результата, который он сохраняет в переменную-член с именем *m_isEyeTrackingEnabled*.

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
Запуск отсоединенного потока — это только один вариант для обработки асинхронных вызовов. Кроме того, можно использовать новые функции [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) , поддерживаемые C++/винрт.
Вот еще один пример для запроса разрешения пользователя:
-   Эйеспосе:: An () позволяет приложению активировать диалоговое окно разрешения только в том случае, если имеется средство регистрации взгляда.
-   Газеинпутакцессстатус m_gazeInputAccessStatus; Это позволяет предотвратить повторное извлечение запроса на разрешение.

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

### <a name="declaring-the-gaze-input-capability"></a>Объявление возможности ввода с помощью *взгляда*

Дважды щелкните файл AppxManifest в *Обозреватель решений*.  Затем перейдите к разделу возможностей и проверьте возможность *ввода* с помощью *средства* выбора. 

![Возможность ввода с клавиатуры](images/gaze-input-capability.png)

В раздел *пакета* в файле appxmanifest добавляются следующие строки:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Получение луча с глазом взгляда
После получения доступа к ET вы можете бесплатно захватить каждый кадр.
Как и в случае с Head-взглядом, получите [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , вызвав [Спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) с нужной меткой времени и системой координат. Спатиалпоинтерпосе содержит объект [эйеспосе](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) через свойство [глаза](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) . Это значение не равно null, только если включено отслеживание глаз. Здесь можно проверить, имеет ли пользователь устройства калибровку отслеживания взгляда, вызвав [эйеспосе:: искалибратионвалид](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  Затем используйте свойство [взгляда](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) , чтобы получить [спатиалрай](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) , содержащий расположение и направление взгляда. Свойство "взгляд" иногда может иметь значение null, поэтому обязательно проверьте это. Это может произойти, если калибровка пользователя временно закрывает свои глаза.

В следующем коде показано, как получить доступ к лучау глаза.

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
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-is-not-available"></a>Откат при недоступности отслеживания взгляда
Как упоминалось в [документах по проектированию отслеживания взгляда](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), разработчики должны иметь в виду, что могут существовать экземпляры, в которых данные отслеживания взгляда могут быть недоступны для вашего приложения.
Существуют различные причины для этого, если пользователь не откалиброван, пользователь запретил приложению доступ к данным отслеживания взгляда или просто временные помехи (например, палецы на делители HoloLens или волосы, окклудинг глаз пользователя). Хотя некоторые API-интерфейсы уже упоминались в этом документе, в следующей статье мы предоставляем сводку о том, как определить, что отслеживание взгляда доступно в качестве краткого справочника: 

* Убедитесь, что система поддерживает отслеживание глаз. Вызовите следующий *метод*: [Windows. восприятие. People. эйеспосе. Поддержка ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* Убедитесь, что пользователь откалиброван. Вызовите следующее *свойство*: [Windows. восприятие. People. эйеспосе. искалибратионвалид](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid) 

* Убедитесь, что пользователь предоставил приложению разрешение на использование данных отслеживания взгляда: получение текущего _"газеинпутакцессстатус"_ . Пример того, как это сделать, объясняется в [запросе доступа к вводу с помощью взгляда](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).   

Кроме того, может потребоваться проверить, что данные отслеживания взгляда не устарели, добавив время ожидания между полученными обновлениями данных отслеживания взгляда и иным способом откатом к заголовку, как описано ниже.  
Дополнительные сведения см. в разделе [рекомендации по проектированию резервного проекта](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) .

<br>

## <a name="correlating-gaze-with-other-inputs"></a>Сопоставление взгляда с другими входными данными
Иногда может оказаться, что требуется [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) , соответствующий событию в прошлом. Например, если пользователь выполняет касание Air, приложение может захотеть узнать, что именно оно искало. Для этой цели простое использование [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) с прогнозируемым временем кадров будет неточным из-за задержки между системной обработкой входных данных и временем вывода. Кроме того, если для нацеливания используется глаз, наши глаза, как правило, переходят даже перед завершением действия фиксации. Это не является проблемой для простого касания воздуха, но становится более важным при объединении длинных голосовых команд с помощью передвижений с быстрым глазом. Одним из способов решения этого сценария является создание дополнительного вызова [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)с использованием метки времени с предысторией, соответствующей входному событию.  

Однако для входных данных, перенаправляющихся через Спатиалинтерактионманажер, существует более простой метод. [Спатиалинтерактионсаурцестате](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) имеет собственную функцию [трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) . Вызов, который предоставит вполне коррелированный [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) без предоставляя. Дополнительные сведения о работе с Спатиалинтерактионсаурцестатес см. в документации по [DirectX](hands-and-motion-controllers-in-directx.md) .

<br>

## <a name="calibration"></a>Монитора
Чтобы отслеживание отслеживания проработало правильно, каждый пользователь должен пройти по [калибровке пользователя с отслеживанием взгляда](calibration.md). Это позволяет устройству настроить систему для более удобного и качественного просмотра для пользователя, а также для обеспечения точного отслеживания в то же время. Разработчикам не нужно ничего делать на своих концах для управления калибровкой пользователей. Система обеспечит пользователю запрос на калибровку устройства в следующих случаях:
* Пользователь использует устройство в первый раз
* Пользователь ранее отказался от процесса калибровки
* Процесс калибровки не был выполнен в последний раз, когда пользователь использовал устройство.

Разработчикам следует обеспечить необходимую поддержку для пользователей, для которых данные отслеживания взгляда могут быть недоступны. Дополнительные сведения см. в статье рекомендации по [отслеживанию решений на сайте Hololens 2](eye-tracking.md).

<br>

## <a name="see-also"></a>См. также
* [Калибровка](calibration.md)
* [Системы координат в DirectX](coordinate-systems-in-directx.md)
* [Глаз — Взгляните на HoloLens 2](eye-tracking.md)
* [Входная модель "взгляд" и "фиксация"](gaze-and-commit.md)
* [Контроллеры движения и жестов в DirectX](hands-and-motion-controllers-in-directx.md)
* [Ввод голоса в DirectX](voice-input-in-directx.md)
