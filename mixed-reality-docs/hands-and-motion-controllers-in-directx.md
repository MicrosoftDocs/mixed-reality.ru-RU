---
title: Руки и контроллеры движения в DirectX
description: Рекомендации для разработчиков по использованию контроллеров отслеживания и движения в собственных приложениях DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: руки, контроллеры движения, DirectX, ввод, голограммы
ms.openlocfilehash: 7b8222e5e539eb95b07cc24d6b49106bd174b490
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435194"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Руки и контроллеры движения в DirectX

В Windows Mixed Reality входные данные и [контроллера движения](motion-controllers.md) выполняются через API-интерфейсы пространственного ввода, находящиеся в пространстве имен [Windows. UI. input. spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) . Это позволяет легко выполнять типичные действия, такие как **Выбор** между обоими контроллерами и движениями.

## <a name="getting-started"></a>Начало работы

Чтобы получить доступ к пространственному входу в Windows Mixed Reality, начните с интерфейса Спатиалинтерактионманажер.  Доступ к этому интерфейсу можно получить, вызвав [спатиалинтерактионманажер:: жетфоркуррентвиев](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), как правило, во время запуска приложения.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

Задача Спатиалинтерактионманажер — предоставить доступ к [спатиалинтерактионсаурцес](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource), который представляет источник входных данных.  В системе доступно три типа Спатиалинтерактионсаурцес.
* **Рука** — это обнаруженная пользователем рука. Источники руки предлагают различные функции, основанные на устройстве, от базовых жестов на HoloLens до полностью четкого отслеживания в HoloLens 2. 
* **Контроллер** представляет сопряженный контроллер движения. Контроллеры движения могут предоставлять разнообразные возможности.  Например, выберите триггеры, кнопки меню, кнопки, сенсорные панели и сумбстиккс.
* **Voice** представляет голосовые сообщения пользователя, обнаруженные системой. Например, этот источник будет включать выбор и освобождение при каждом нажатии пользователем кнопки "Select".

Данные каждого кадра для источника представлены интерфейсом [спатиалинтерактионсаурцестате](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) . Существует два разных способа доступа к этим данным в зависимости от того, требуется ли использовать основанную на событиях или опросную модель в приложении.

### <a name="event-driven-input"></a>Входные данные, управляемые событиями
Спатиалинтерактионманажер предоставляет ряд событий, которые может прослушивать приложение.  Вот несколько примеров: [саурцепрессед](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [саурцерелеасед](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) и [SourceUpdated](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Например, следующий код подключает обработчик событий с именем MyApp:: Онсаурцепрессед к событию Саурцепрессед.  Это позволяет приложению обнаруживать нажатия для любого типа источника взаимодействия.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Это нажатое событие будет отправлено в приложение асинхронно, вместе с соответствующим Спатиалинтерактионсаурцестате на момент нажатия. Вашему приложению или игровому модулю может потребоваться выполнить определенную обработку сразу или поочередно поместить данные о событиях в подсистему обработки входных данных. Ниже приведена функция обработчика событий для события Саурцепрессед, которая показывает, как проверить, была ли нажата кнопка выбора.

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

Приведенный выше код проверяет только нажатие клавиши "Select", которое соответствует основному действию на устройстве. Примеры включают в себя выполнение Аиртап в HoloLens или извлечение триггера в контроллере движения.  Нажатия клавиши "Select" представляют намерение пользователя активировать голограмму, для которой они предназначены.  Событие Саурцепрессед будет срабатывать на несколько различных кнопок и жестов, и вы можете проверить другие свойства в Спатиалинтерактионсаурце, чтобы проверить их в этих случаях.

### <a name="polling-based-input"></a>Входные данные на основе опроса
Можно также использовать Спатиалинтерактионманажер для опроса текущего состояния входных данных каждого кадра.  Для этого просто вызовите [жетдетектедсаурцесаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) для каждого кадра.  Эта функция возвращает массив, содержащий один [спатиалинтерактионсаурцестате](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) для каждого активного [спатиалинтерактионсаурце](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource). Это означает, что по одному для каждого активного контроллера движения, по одному для каждой контрольной руки, и один для речи, если команда "Select" недавно распространенная. Затем можно проверить свойства каждого Спатиалинтерактионсаурцестате, чтобы ввести входные данные в приложение. 

Ниже приведен пример того, как проверить действие "Select" с помощью метода опроса. Обратите внимание, что переменная *прогноза* представляет объект [холографикфрамепредиктион](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , который можно получить из [холографикфраме](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).

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

Каждый Спатиалинтерактионсаурце имеет идентификатор, который можно использовать для идентификации новых источников и корреляции существующих источников от Frame к кадру.  Каждый раз, когда они оставляют и вводят фов, им назначается новый идентификатор, но идентификаторы контроллеров остаются статическими в течение сеанса.  События в Спатиалинтерактионманажер, такие как [саурцедетектед](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) и [саурцелост](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), можно использовать для реагирования на ввод или выход из представления устройства, а также при включении или отключении контроллеров движения, а также при установке парных или непарных.

### <a name="predicted-vs-historical-poses"></a>Прогнозируемые и исторические
Обратите внимание, что Жетдетектедсаурцесаттиместамп имеет параметр timestamp. Это позволяет запрашивать прогнозируемые или исторические данные о состоянии и представлении, позволяя сопоставлять пространственные взаимодействия с другими источниками входных данных. Например, при визуализации расположения руки в текущем кадре можно передать прогнозируемую метку времени, предоставляемую [холографикфраме](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe). Это позволяет системе пересылать прогнозы по положению руки, чтобы точно согласовать их с визуализированным выходным кадром, минимизируя наблюдаемую задержку.

Однако такая прогнозируемая версия не создает идеальный указывающий луч для нацеливания на источник взаимодействия. Например, при нажатии кнопки "контроллер движения" может потребоваться до 20 мс для этого события, чтобы это событие было переработано через Bluetooth к операционной системе. Аналогично, после того, как пользователь выполняет жест руки, может пройти некоторое время, прежде чем система обнаружит жест, а приложение запрашивает его. К моменту, когда приложение опрашивается об изменении состояния, головной элемент и рука, используемые для этого, в действительности происходили в прошлом. Если вы намерены передать метку времени текущей Холографикфраме в Жетдетектедсаурцесаттиместамп, то она будет перенаправлена на целевой луч во время отображения кадра, что может быть более 20 мс в будущем. Эта будущая версия является хорошей для *подготовки к просмотру* источника взаимодействия, но создает задачу по *времени для взаимодействия* , так как нацеливание пользователя происходило в прошлом.

К счастью, события [саурцепрессед](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [саурцерелеасед](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) и [SourceUpdated](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) предоставляют исторические [состояния](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) , связанные с каждым входным событием.  Это напрямую включает в себя главную и руки с предысторией, доступные через [трижетпоинтерпосе](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), а также историческую [метку времени](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) , которую можно передать другим API-интерфейсам для сопоставления с этим событием.

Это приводит к следующим рекомендациям при визуализации и нацеливании на руки и контроллеры каждого кадра:
* Для **отрисовки вручную или контроллера** каждого кадра приложение должно **опрашиваться** за **однонаправленную прогнозную** часть каждого источника взаимодействия на время Photon текущего кадра.  Можно опросить все источники взаимодействия, вызвав [жетдетектедсаурцесаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) каждый кадр, передав прогнозируемую отметку времени, предоставленную [Холографикфраме:: куррентпредиктион](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* Для **целей или контроллеров, предназначенных** для пресс-релизов, приложение должно обрабатывать **события**, вызванные нажатием или выпуском, райкастинг на основе **исторической** головки или руки для этого события. Этот целевой объект можно получить, обрабатывая событие [саурцепрессед](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) или [саурцерелеасед](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) , получая свойство [State](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) из аргументов события, а затем вызывая его метод [трижетпоинтерпосе](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .

## <a name="cross-device-input-properties"></a>Свойства ввода для разных устройств
API Спатиалинтерактионсаурце поддерживает контроллеры и системы отслеживания вручную с широким спектром возможностей. Некоторые из этих возможностей являются общими для разных типов устройств. Например, для отслеживания и контроллеров движения вручную предоставляется действие "Select" и трехмерное расположение. Везде, где это возможно, API сопоставляет эти общие возможности тем же свойствам в Спатиалинтерактионсаурце.  Это позволяет приложениям более легко поддерживать широкий спектр входных типов. В следующей таблице описаны поддерживаемые свойства и их сравнение во входных типах.

| Свойство | Описание | Жесты HoloLens | Контроллеры движения | Руки с формулировкой|
|--- |--- |--- |--- |--- |
| [Спатиалинтерактионсаурце::**правой или левой**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Правый или левый рукой или Controller. | Не поддерживается | Поддерживается | Поддерживается |
| [Спатиалинтерактионсаурцестате::**исселектпрессед**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Текущее состояние основной кнопки. | Касание Air | Необходимость | Небольшое воздушное касание (вертикальное сжатие) |
| [Спатиалинтерактионсаурцестате **::** ](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Текущее состояние кнопки захвата. | Не поддерживается | Кнопка "захватить" | Сжатие или закрываемая рука |
| [Спатиалинтерактионсаурцестате::**исменупрессед**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Текущее состояние кнопки меню.    | Не поддерживается | Кнопка меню | Не поддерживается |
| [Спатиалинтерактионсаурцелокатион::**Расположение**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | XYZ положение руки или захвата на контроллере. | Расположение Palm | Заменяющая позицией захвата | Расположение Palm |
| [Спатиалинтерактионсаурцелокатион::**Orientation**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Кватернион, представляющий ориентацию руки или захвата на контроллере. | Не поддерживается | Ориентация на подзахват | Ориентация Palm |
| [Спатиалпоинтеринтерактионсаурцепосе::**Расположение**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Источник указывающего луча. | Не поддерживается | Поддерживается | Поддерживается |
| [Спатиалпоинтеринтерактионсаурцепосе::**форварддиректион**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Направление указывающего луча. | Не поддерживается | Поддерживается | Поддерживается |

Некоторые из перечисленных выше свойств доступны не на всех устройствах, и API предоставляет средства для проверки. Например, можно проверить свойство [спатиалинтерактионсаурце:: исграспсуппортед](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) , чтобы определить, предоставляет ли источник действие "оценить".

### <a name="grip-pose-vs-pointing-pose"></a>Захват захвата и указание объекта a

Windows Mixed Reality поддерживает контроллеры движения различными конструктивными факторами.  Он также поддерживает системы отслеживания с формулировками.  Все эти системы имеют разные связи между положением руки и естественным направлением "вперед", которое приложения должны использовать для указания или отрисовки объектов в руки пользователя.  Для поддержки всего этого существует два типа трехмерных объектов, предоставляемых для контроллеров отслеживания и перемещения.  Первый — захват, представляющий собой точку руки пользователя.  Второй объект указывает на объект, который представляет указывающий луч, исходящий от руки или контроллера пользователя. Таким образом, если требуется визуализировать **руку пользователя** или **объект, хранящийся в руки пользователя**, например технологий или обойма, используйте захват a. Если вы хотите райкаст от контроллера или вручную, например, когда пользователь **указывает на пользовательский интерфейс** , используйте указывающее объект.

Доступ к **захвату** можно получить с помощью [спатиалинтерактионсаурцестате::P списке:: трижетлокатион (...)](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  Он определяется следующим образом:
* **Позиция захвата**: Карманный центроид при удержании контроллера естественным образом настраивается влево или вправо для центрирования места внутри захвата.
* **Правая ось ориентации захвата**: когда вы полностью открываете руку для формирования плоской задачи с 5-пальцем, луч, обычный для вашего кармана (вперед от левого кармана, назад от правого Palm)
* **Прямая ось ориентации захвата**: когда вы частично закрываете руку (как при удержании контроллера), луч, который указывает на "Forward" через лампу, сформированную небегункными пальцами.
* **Ось Up (вверх) для ориентации захвата**: ось Up, подразумеваемая правым и прямым определением.

Доступ к **указателю** a можно получить через [спатиалинтерактионсаурцестате::P списке:: трижетлокатион (...):: саурцепоинтерпосе](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) или [спатиалинтерактионсаурцестате:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_) .

## <a name="controller-specific-input-properties"></a>Входные свойства, зависящие от контроллера
Для контроллеров Спатиалинтерактионсаурце имеет свойство Controller с дополнительными возможностями.
* **Хассумбстикк:** Если значение — true, контроллер имеет аналоговый стик. Проверьте свойство [контроллерпропертиес](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) объекта спатиалинтерактионсаурцестате, чтобы получить значения x и y аналогового стика (Сумбстикккс и сумбстикки), а также состояние нажатия (иссумбстиккпрессед).
* **Хастаучпад:** Если значение — true, контроллер имеет сенсорную панель. Изучите свойство Контроллерпропертиес объекта Спатиалинтерактионсаурцестате, чтобы получить значения x и y сенсорной панели (Таучпадкс и сенсорную панель), а также узнать, касается ли пользователь сенсорной панели (Истаучпадтаучед) и если они нажаты на сенсорную панель ( Истаучпадпрессед).
* **Симплехаптиксконтроллер:** API Симплехаптиксконтроллер для контроллера позволяет проверять возможности контроллера хаптикс, а также управлять обратной связью хаптик.

Обратите внимание, что диапазон для сенсорной панели и аналоговый стик имеет значение от-1 до 1 для обеих осей (снизу вверх и слева направо). Диапазон для аналогового триггера, доступ к которому осуществляется с помощью свойства Спатиалинтерактионсаурцестате:: Селектпресседвалуе, имеет диапазон от 0 до 1. Значение 1 соответствует значению Исселектпрессед, равному true; любое другое значение корреляции с Исселектпрессед равно false.

## <a name="articulated-hand-tracking"></a>Отслеживание с формулировками
API Windows Mixed Reality обеспечивает полную поддержку для наследных отслеживания, например в HoloLens 2. Отслеживание с клавиатуры можно использовать для реализации прямой манипуляции и входных моделей с точки зрения и фиксации в приложениях. Его также можно использовать для создания полностью настраиваемых взаимодействий.

### <a name="hand-skeleton"></a>Схема руки
Отслеживание с выдвижностью предоставляет 25-общий каркас, обеспечивающий множество различных типов взаимодействий.  Скелет предоставляет 5 соединений для индексов, средних и кольцевых и маленьких пальцев, 4 соединений для бегунка и 1-я сочленения.  Сочленение выступает в качестве основы иерархии. На следующем рисунке показана структура каркаса.

![Схема руки](images/hand-skeleton.png)

В большинстве случаев имя каждого соединения определяется на основе кости, которую он представляет.  Поскольку существует две кости на каждой объединенной версии, мы используем соглашение об именовании каждого соединения на основе дочерней кости в этом расположении.  Дочерняя кость определяется как кость дальше от себя.  Например, соединение "index Проксимал" содержит начальную точку проксимал индекса и ориентацию этой кости.  Он не содержит конечную точку кости.  Если это необходимо, вы получите его из следующего совместного соединения в иерархии — «промежуточное соединение с индексом».

Помимо 25 иерархических соединений, система обеспечивает соединение Palm.  Карманный ПК обычно не считается частью структуры скелетообразных.  Он предоставляется только в качестве удобного способа для получения общего положения и ориентации от руки.

Для каждого соединения предоставляются следующие сведения:

| Имя | Описание |
|--- |--- |
|Положение | Трехмерное положение соединения, доступное в любой запрошенной системе координат. |
|Orientation | Трехмерная ориентация кости, доступная в любой запрошенной системе координат. |
|Радиус | Расстояние до поверхности обложки в связной позиции. Полезно для настройки прямых взаимодействий или визуализаций, использующих ширину пальца. |
|Точность | Предоставляет указание о том, насколько надежна система относительно данных этого соединения. |

Вы можете получить доступ к данным схемы руки с помощью функции в [спатиалинтерактионсаурцестате](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  Функция называется [трижесандпосе](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)и возвращает объект с именем [хандпосе](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose).  Если источник не поддерживает сочлененные руки, эта функция возвратит значение null.  После создания Хандпосе можно получить текущие соединения, вызвав [трижетжоинт](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), указав имя интересующего вас соединения.  Данные возвращаются в виде структуры [жоинтпосе](https://docs.microsoft.com//uwp/api/windows.perception.people.jointpose) .  Следующий код возвращает расположение Совета по индексу. Переменная *currentState* представляет экземпляр [спатиалинтерактионсаурцестате](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

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

### <a name="hand-mesh"></a>Сетка руки

API отслеживания с обобразованиями позволяет полностью деформировать сетку с треугольником.  Эта сеть может Deform в режиме реального времени вместе с каркасом руки и полезна для визуализации, а также для создания сложных физических методов.  Для доступа к сетке типа "рука" необходимо сначала создать объект [хандмешобсервер](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver) , вызвав [трикреатехандмешобсерверасинк](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) в [спатиалинтерактионсаурце](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Это необходимо сделать один раз для каждого источника, как правило, при первом его отображении.  Это означает, что вы назовем эту функцию для создания объекта Хандмешобсервер каждый раз, когда руки попадает в фов.  Обратите внимание, что это асинхронная функция, поэтому вам придется поработать с рядом параллелизма.  После получения доступа можно запросить объект Хандмешобсервер для буфера индекса треугольника, вызвав [жеттрианглеиндицес](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Индексы не изменяют кадр над кадром, поэтому их можно получить и кэшировать в течение времени существования источника.  Индексы задаются в порядке поворота по часовой стрелке.

Следующий код ускоряет отсоединенный std:: Thread для создания наблюдателя сетки и извлекает буфер индекса после того, как наблюдатель сетки становится доступным.  Он начинается с переменной с именем *currentState*, которая является экземпляром [спатиалинтерактионсаурцестате](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) , представляющим отслеживающую руку.

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
Запуск отсоединенного потока — это только один вариант для обработки асинхронных вызовов.  Кроме того, можно использовать новые функции [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) , поддерживаемые C++/винрт.

Когда у вас есть объект Хандмешобсервер, необходимо удерживать его на время активности соответствующего Спатиалинтерактионсаурце.  Затем каждый кадр можно запросить о последнем буфере вершин, который представляет руку, вызвав [жетвертексстатефорпосе](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) и передав экземпляр [хандпосе](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose) , представляющий объект, для которого требуются вершины.  Каждая вершина в буфере имеет расположение и нормаль.  Ниже приведен пример того, как получить текущий набор вершин для сетки типа «рука».  Как и ранее, переменная *currentState* представляет экземпляр [спатиалинтерактионсаурцестате](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

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

В отличие от схемы соединений, интерфейс API сетки руки не позволяет указать систему координат для вершин.  Вместо этого [хандмешвертексстате](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshvertexstate) указывает систему координат, в которой предоставляются вершины.  Затем можно получить преобразование сетки, вызвав [трижеттрансформто](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) и указав нужную систему координат.  Это преобразование сетки необходимо использовать при работе с вершинами.  Такой подход сокращает нагрузку на ЦП, особенно если вы используете только сетку для целей визуализации.

## <a name="gaze-and-commit-composite-gestures"></a>Составные жесты взгляда и фиксации
Для приложений, использующих входную модель "взгляд-and-Commit", особенно в HoloLens (First Gen), пространственный входной API предоставляет необязательный [спатиалжестуререкогнизер](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) , который можно использовать для включения составных жестов, построенных на основе события SELECT.  Выполняя маршрутизацию взаимодействия от Спатиалинтерактионманажер к Спатиалжестуререкогнизеру голограммы, приложения могут равномерно обнаруживать события касания, удержания, манипуляции и навигации по голосовым и сенсорным устройствам ввода, а также не обрабатывать нажатия. и выпуски вручную.

Спатиалжестуререкогнизер выполняет только минимальную неоднозначность между набором запрашиваемых жестов. Например, если вы запрашиваете просто касание, пользователь может удерживать палец вниз, если бы они были, и касание все равно будет выполняться. Если вы запрашиваете касание и удержание, то спустя некоторое время, удерживая палец, жест будет преобразован в удержание, и касание больше не будет выполняться.

Чтобы использовать Спатиалжестуререкогнизер, обработайте событие [Интерактиондетектед](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) спатиалинтерактионманажер и захватите в нем спатиалпоинтерпосе. Чтобы определить, с каким действием пользователь может взаимодействовать, используйте заголовку из этого объекта, чтобы выполнить пересечение с голограммами и сетками поверхностей в окружающей области пользователя. Затем направьте Спатиалинтерактион в аргументах события в Спатиалжестуререкогнизер целевой голограммы с помощью метода [каптуреинтерактион](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) . Это начнет интерпретировать взаимодействие в соответствии с [спатиалжестуресеттингс](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) , установленным для этого распознавателя во время создания или [трисетжестуресеттингс](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

В HoloLens (первое поколение) взаимодействия и жесты обычно должны наследовать нацеливание от заголовков пользователя, а не пытаться напрямую отрисовываться или взаимодействовать в расположении руки. После запуска взаимодействия можно использовать относительные движения руки для управления жестом, как в случае манипуляции или жеста навигации.

## <a name="see-also"></a>См. также
* [Направление головы и взгляда в DirectX](gaze-in-directx.md)
* [Входная модель прямого управления](direct-manipulation.md)
* [Входная модель "точка-and-фиксация"](point-and-commit.md)
* [Входная модель "взгляд" и "фиксация"](gaze-and-commit.md)
* [Контроллеры движения](motion-controllers.md)
