---
title: Руки и контроллеры движения в DirectX
description: Руководство разработчика по использованию отслеживания вручную и контроллеры движения в собственных приложениях DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: руки, контроллеры движения, directx, входные данные, голограммы
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629647"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Руки и контроллеры движения в DirectX

В Windows Mixed Reality, обе стороны и [контроллера движения](motion-controllers.md) входных данных осуществляется через пространственных входные данные API, в [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) пространства имен. Это позволяет с легкостью выполнить общие действия, такие как **выберите** нажимает так же, как в руки и контроллеры движения.

## <a name="getting-started"></a>Начало работы

Пространственные доступ ввода в Windows Mixed Reality начните с SpatialInteractionManager интерфейс.  Этот интерфейс может быть открыт, вызвав [SpatialInteractionManager::GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), обычно иногда во время запуска приложения.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

Задание SpatialInteractionManager заключается в предоставлении доступа к [SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource), который представляет источник входных данных.  Существует три вида SpatialInteractionSources, доступных в системе.
* **Рука** представляет обнаруженных руку пользователя. Рука источников, предлагают различные функции, на основе устройства, от простейших жестов на HoloLens полные руки, отслеживания на HoloLens 2. 
* **Контроллер** представляет контроллер парных движения. Контроллеры движения могут предлагать широкий набор возможностей.  Пример: Выберите триггеры, кнопки меню, кнопки коммерческих тайн, сенсорные панели и thumbsticks.
* **Голосовые** представляет голос пользователя, говоря система обнаружила ключевые слова. Например этот источник будет внедрить выберите press и выпуска всякий раз, когда пользователь скажет: «Выбрать».

Кадров данных для представленного источника [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) интерфейс. Доступ к этим данным, в зависимости от того, требуется ли использовать модель управляемых событиями или на основе опроса в приложении двумя способами.

### <a name="event-driven-input"></a>Входные данные на основе событий
SpatialInteractionManager предоставляет ряд событий, которые приложение может прослушивать.  Некоторые включают [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) и [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Например следующий код подключает обработчик событий вызывается MyApp::OnSourcePressed SourcePressed событие.  Благодаря этому приложение для обнаружения нажатий на любой тип источника взаимодействия.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Это событие нажатия асинхронно, отправляется в приложение вместе с соответствующей SpatialInteractionSourceState во время произошло прессе. Ваше приложение или игровое ядро может потребоваться выполнить некоторые задачи обработки прямо сейчас или требуется поставить данные событий в подпрограмму обработки входных данных. Вот функцию обработчика событий для события SourcePressed, которое показывает, как проверить, была ли нажата кнопка "выбрать".

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

Приведенный выше код проверяет только «Select» press, который соответствует основное действие на устройстве. Примеры выполнения AirTap на HoloLens или извлечение триггер на контроллере движения.  При нажатии «Select» представляют намерение пользователя активировать голограмма, который их используете.  SourcePressed событие будет срабатывать по ряду кнопок и жестов, и вы можете проверить другие свойства SpatialInteractionSource для тестирования в тех случаях.

### <a name="polling-based-input"></a>Ввод на основе опроса
Также можно SpatialInteractionManager для опроса текущее состояние ввода каждого кадра.  Чтобы сделать это, просто вызовите [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) каждого кадра.  Эта функция возвращает массив, содержащий один [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) для каждого активного [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource). Это означает одна для каждого контроллера active движения, для каждой отслеживаемой стрелки и один для распознавания речи, если был недавно распространенная команду «select». Это позволяет проверить свойства каждого SpatialInteractionSourceState для входных данных с диска в приложение. 

Вот пример того, как для проверки для действия «выберите» использование метода опроса. Обратите внимание, что *прогноза* переменная представляет [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) объект, который может быть получен из [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

Каждый SpatialInteractionSource имеет идентификатор, который можно использовать для определения новых источников и сопоставить существующие источники из фрейма.  Руки присваивается новый идентификатор каждый раз, они оставьте и введите FOV, но идентификаторов оставаться статическим в течение сеанса.  Можно использовать события на SpatialInteractionManager например [SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) и [SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), представления реагировать руки введите или устройство, или при контроллеры движения включить и выключить или, в паре/непарный.

### <a name="predicted-vs-historical-poses"></a>Прогнозируемые и ведением журнала создает
Обратите внимание, что GetDetectedSourcesAtTimestamp параметра метки времени. Это позволяет состояние запроса и представлять данные, либо прогнозируемое или журнала, что вы сопоставлять пространственных взаимодействия с другими источниками входных данных. Например, при подготовке к просмотру наличии позицию в текущем кадре, можно передать прогнозируемое timestamp, предоставляемые [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe). Это позволяет системе прогнозировать вперед положение руки для приведения их с выходными данными Отрисованный кадр, сводя к минимуму наблюдаемой задержки.

Тем не менее прогнозируемое поза не создает идеальный указывающего Рэй для нацеливания с источником взаимодействия. Например при нажатии кнопки контроллера движения, может занять до 20 мс для этого события всплывать через Bluetooth в операционную систему. Аналогичным образом после выполнении пользователем жеста руки, некоторое время может понадобиться система обнаруживает жест и приложения, а затем выполняет опрос для него. Когда приложение выполняет опрос для изменения состояния создает head и наличии используется для целевой объект, который взаимодействия фактически произошло в прошлом. Если вы устанавливаете путем передачи timestamp вашей текущей HolographicFrame GetDetectedSourcesAtTimestamp, позу вместо вперед прогнозируемой для нацеливания луч во время кадра отображается, в которой может быть более чем 20 мс, в будущем. Этот будущих поза хорошо подходит для *отрисовки* источника взаимодействия, но приводит к увеличению наша проблема времени для *нацеливания* взаимодействия, как пользователь предназначенных для произошло в прошлом.

К счастью [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) и [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) события предоставляют исторических [состояние](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) связанные с Каждое событие ввода.  Это напрямую включает в себя исторические head и наличии создает, доступных через [TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), вместе с ведением журнала [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) , можно передать в другие API-интерфейсы для корреляции с этим событием.

Это ведет к следующие рекомендации при визуализации и определение целевых объектов с руки и контроллеры каждого кадра:
* Для **наличии/контроллер отрисовки** каждого кадра, приложение должно **опроса** для **прогнозируемые вперед** представлять каждого источника взаимодействия во время photon текущего кадра.  Можно выполнить опрос для всех источников взаимодействия, вызвав [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) каждого кадра, передавая прогнозируемые метки времени, предоставляемые [HolographicFrame::CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* Для **нацеливание стороны/контроллер** по press или выпуска, приложения должны обрабатывать нажата и отпущена **события**, точные точки для отслеживания на основе **исторических** поза head или вручную для Это событие. Вы получаете этот нацеливания Рэй путем обработки [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) или [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) событий, начало [состояние](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) свойства из аргументов события и последующего вызова его [ TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) метод.

## <a name="cross-device-input-properties"></a>Входные свойства между устройствами
Этот API SpatialInteractionSource поддерживает контроллеры и наличии отслеживания системах с широким диапазоном возможностей. Несколько эти возможности, общие для различных типов устройств. К примеру вручную отслеживания движения контроллеры и оба предоставляют действием «select», а также трехмерного положения. По возможности API сопоставляется те же свойства на SpatialInteractionSource эти общие возможности.  Это позволяет приложениям более просто поддерживать широкий спектр типов входных данных. В следующей таблице описаны свойства, которые поддерживаются, и об отличиях между типов входных данных.

| Свойство | Описание | Жесты HoloLens | Контроллеры движения | Ясно сформулированные руки|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**рабочей руки пользователя**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Справа или слева / контроллера. | Не поддерживается | Поддерживается | Поддерживается |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Текущее состояние основную кнопку. | Жест касания | триггер | Нестрогой Air коснитесь (вертикальное сжатие) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Текущее состояние кнопки захвата. | Не поддерживается | Кнопки захвата | Жест сжатия или закрытое вручную |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Текущее состояние кнопки меню.    | Не поддерживается | Кнопки меню | Не поддерживается |
| [SpatialInteractionSourceLocation::**позиции**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | Местоположение XYZ вручную или захвата для изменения позиции на контроллере. | Расположение Palm | Позиция поза захвата для изменения | Расположение Palm |
| [SpatialInteractionSourceLocation::**ориентации**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Кватернион, представляющий ориентацию позу вручную или захвата для изменения на контроллере. | Не поддерживается | Ориентация поза захвата для изменения | Ориентация Palm |
| [SpatialPointerInteractionSourcePose::**позиции**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Начало координат луча, указывающего. | Не поддерживается | Поддерживается | Поддерживается |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Направление луча, указывающего. | Не поддерживается | Поддерживается | Поддерживается |

Некоторые из указанных выше свойств доступны не на всех устройствах, и API-Интерфейс позволяет проверить это. Например, вы можете проверить [SpatialInteractionSource::IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) свойства, чтобы определить, предоставляет ли источник действия может воспользоваться.

### <a name="grip-pose-vs-pointing-pose"></a>Поза захвата для изменения и указывающего поза

Смешанная реальность Windows поддерживает движения контроллеров в различных форм-факторов.  Она также поддерживает ясно сформулированные наличии системы по отслеживанию.  Все эти системы обладают разным связям между положением руки и естественным «вперед», приложения должны использовать для команды или rendreing объектов в руки пользователя.  Для поддержки все это, существует два вида 3D создает для обоих контроллеров отслеживания и перемещения вручную.  Во-первых, поза захвата для изменения, который представляет положение руки пользователя.  Вторая указывает поза, который представляет указывающего луча, исходящие от руки пользователя или контроллера. Таким образом, если нужно отобразить **руку пользователя** или **объект содержится в руки пользователя**, такие как помехой или оружия, используйте поза захвата для изменения. Если вы хотите raycast от контроллера или вручную, например, если пользователь является **обращены пользовательского интерфейса** , указывающего поза использовать.

Вы можете получить доступ к **поза захвата для изменения** через [SpatialInteractionSourceState::Properties::TryGetLocation(...) ](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  Определяется следующим образом:
* **Возьмитесь за позиции**: Palm центроида при удержании контроллер, естественно, корректируется, влево или вправо, чтобы центрировать позиция в пределах захвата.
* **Возьмитесь за правой оси в ориентации**: При открытии полностью свои силы для формирования позу плоских 5 палец, луч, является нормальным для вашей palm (вперед от левой palm назад от правой palm)
* **Возьмитесь за ориентации на ось, направленная вперед**: При закрытии вашей руке частично (как будто держа контроллеру), луч, указывающий «forward» трубку, образованное пальцы отличных от бегунка.
* **Возьмитесь за ориентации элемента вверх оси**: Ось вверх, право и прямого определения содержится в разрешении.

Вы можете получить доступ к **поза указатель** через [SpatialInteractionSourceState::Properties::TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) или [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Входные свойства конкретного контроллера
Для контроллеров SpatialInteractionSource имеет свойство контроллера с помощью дополнительных возможностей.
* **HasThumbstick:** Если значение равно true, контроллер может джойстик. Проверьте [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) свойство SpatialInteractionSourceState получения джойстик x и y значения (ThumbstickX и ThumbstickY), а также его нажаты (IsThumbstickPressed).
* **HasTouchpad:** Если значение равно true, контроллер может сенсорной панели. Проверьте свойство ControllerProperties SpatialInteractionSourceState получения сенсорной панели x и y значений (TouchpadX и TouchpadY) и знать, если пользователь касается планшета (IsTouchpadTouched) и если они нажав сенсорной вниз () IsTouchpadPressed).
* **SimpleHapticsController:** Интерфейс API SimpleHapticsController для контроллера, позволяет исследовать возможности haptics контроллера, а также позволяет управлять обратной связи haptic.

Обратите внимание, что диапазон для сенсорной панели и джойстик -1 до 1 для обеих осей (снизу вверх и слева направо). Диапазон для аналоговой триггера, к которому можно получить с помощью свойства SpatialInteractionSourceState::SelectPressedValue, имеет диапазон от 0 до 1. Значение 1 соответствует с IsSelectPressed равен true; любое другое значение связано с IsSelectPressed равен false.

## <a name="articulated-hand-tracking"></a>Ясно сформулированные вручную отслеживания
API смешанной реальностью Windows обеспечивает полную поддержку для ясно сформулированные руки, отслеживания, к примеру HoloLens 2. Ясно сформулированные вручную отслеживания можно использовать для реализации прямой манипуляцией и моделями входных данных для точки и фиксации в ваших приложениях. Его также можно создавать полностью настраиваемые взаимодействий.

### <a name="hand-skeleton"></a>Каркас вручную
Ясно сформулированные вручную отслеживания предоставляет 25 совместные каркас, позволяющий множество различных типов взаимодействия.  Скелет предоставляет 5 соединений для индекса или среднего/кольцо/мало пальцы, 4 соединений для бегунка и 1 запястья соединения.  Совместные запястья служит основой иерархии. На следующем рисунке показана Макет схемы.

![Каркас вручную](images/hand-skeleton.png)

В большинстве случаев каждый соединение называется основании костей, который он представляет.  Так как существуют две кости на каждого соединения, мы используем соглашению именования каждого соединения, исходя кости дочерний в этом расположении.  Дочерние кости определяется как кости максимально далеко от кисти.  Например «индекс Proximal» совместные содержит начальное положение proximal кости индекса и ориентацию, кости.  Он не содержит конечную позицию костей.  Если требуется, получится его от следующего соединения в иерархии «индекса средний уровень» соединения.

В дополнение к 25 иерархических соединений система предоставляет palm соединением.  Palm обычно не считается частью базовой структуры.  Он предоставляется только в качестве удобного способа получить общую положение и ориентацию вручную.

Для каждого соединения, предоставляется следующая информация:

| Имя | Описание |
|--- |--- |
|Положение | Трехмерного положения соединения, доступен в любом запросе системы координат. |
|Orientation | 3D ориентацию кости, доступен в любом запросе системы координат. |
|Радиус | Расстояние область обложки совместные позиции. Это удобно для настройки непосредственного взаимодействия или визуализаций, которые зависят от ширина палец. |
|Точность | Содержит указание на уверены, как система, в том числе о программе этого соединения. |

Доступ к данным скелет вручную с помощью функции на [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  Эта функция вызывается [TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose), и возвращает объект с именем [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose).  Если источник не поддерживает ясно сформулированные руки, эта функция вернет значение null.  Получив HandPose, можно получить текущие данные соединения, вызвав [TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), с именем соединения, которые вас интересуют.  Данные возвращаются в виде [JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose) структуры.  Следующий код получает положение подсказки вытянутым указательным пальцем. Переменная *currentState* представляет экземпляр [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>Стороны сетки

Ясно сформулированные Рука отслеживания API позволяет полностью deformable сетку вручную.  Этой сетчатой структурой можно deform в режиме реального времени наряду с ее вручную и используется для визуализации, а также методы расширенной физики.  Чтобы получить доступ к сети вручную, необходимо сначала создать [HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver) путем вызова метода [TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) на [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Это действие необходимо выполнить один раз для одного источника, обычно в первый раз, он отображается.  Это означает, что Вы вызовите эту функцию для создания объекта HandMeshObserver всякий раз, когда FOV переходит в руки.  Обратите внимание на то, что это функцию с модификатором async, поэтому вам придется иметь дело с немного здесь параллелизма.  Когда она станет доступна, вы можете запросить объект HandMeshObserver буфера индекса треугольника путем вызова [GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Индексы не изменяйте кадра на рамку, чтобы можно было получить их один раз и кэшировать их в течение времени существования источника.  Индексы, указанные в порядке, поворота по часовой стрелке.

Следующий код запускает отсоединенных std::thread, чтобы создать Наблюдатель сети и извлекает буфера индекса, когда доступен сетке наблюдатель.  Он запускается из переменной с именем *currentState*, который является экземпляром [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) представляющий отслеживаемые руки.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
Запуск отсоединенных поток является только один из вариантов для обработки асинхронных вызовов.  Кроме того, можно использовать новый [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) функциональные возможности, поддерживаемые C++/WinRT.

Получив объект HandMeshObserver, должен удерживать в течение его соответствующий SpatialInteractionSource активен.  Затем каждый кадр, вы можете запросить ее последней буфера вершин, представляющий Рука путем вызова [GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) и передавая [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose) экземпляр, представляющий поза, возникает необходимость вершины для.  Каждая вершина в буфере, имеющую положение и обычной.  Ниже приведен пример, иллюстрирующий получение текущего набора вершин сетки вручную.  Как и раньше *currentState* переменная представляет экземпляр [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

В отличие от соединений, которая скелет сетки в наличии API не позволяют укажите систему координат для вершины.  Вместо этого [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate) задает систему координат, вершин, предусмотренных в.  Преобразование сетки можно получить, вызвав [TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) и указав требуемый координат.  Необходимо использовать это преобразование сетки при работе с вершины.  Этот подход уменьшает нагрузку на ЦП, особенно в том случае, если вы используете только сетки для отрисовки.

## <a name="gaze-and-commit-composite-gestures"></a>Помощи и зафиксируйте составные жесты
Для приложений, использующих модель ввода взглядом и фиксации, особенно на HoloLens (первого поколения), пространственных входной API поддерживает необязательный [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) , может использоваться для включить составные жесты, создаются на основе «Выберите» событие.  Маршрутизации взаимодействий из SpatialInteractionManager для SpatialGestureRecognizer голограмма приложений может обнаруживать события касания, удержание, манипуляции и навигации равномерно в руки, голоса и пространственных устройств ввода, без необходимости обрабатывать нажатия и освобождает вручную.

SpatialGestureRecognizer выполняет только минимальный устранения неоднозначности между набор жестов, которые можно запросить. К примеру Если вы запрашивали только Tap, пользователь может удерживать пальцев, пока они любят и отвод по-прежнему будет выполняться. При запросе коснитесь и хранения, после того как об одной секунды удерживая пальцев, жест переведет в удержание и Tap не будет происходить.

Чтобы использовать SpatialGestureRecognizer, обрабатывать SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) событий и захвата SpatialPointerPose предоставляются существует. Используйте Рэй головной взглядом пользователя из этого поза для пересечения с голограммы и поверхности сетки в окружения пользователя, чтобы определить, что пользователь собирается для взаимодействия с. Затем направлять SpatialInteraction в аргументах событий для целевой голограмма SpatialGestureRecognizer, с помощью его [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) метод. Запустится интерпретации, реализуемый в соответствии с [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) задать на этот распознаватель, во время создания - или с [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

На HoloLens (сначала gen), взаимодействия и жесты следует обычно являются их выбора целевой платформы из головного взглядом пользователя, а не при визуализации или напрямую взаимодействовать в расположении вручную. После запуска взаимодействия относительный движения вручную может использоваться для управления жест, как и в случае с жестом манипуляции или навигации.

## <a name="see-also"></a>См. также
* [HEAD и глаз взглядом в DirectX](gaze-in-directx.md)
* [Модель ввода непосредственной работы со](direct-manipulation.md)
* [Модель ввода точки и фиксации](point-and-commit.md)
* [Модель ввода взглядом и фиксации](gaze-and-commit.md)
* [Контроллеры движения](motion-controllers.md)
