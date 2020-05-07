---
title: Отслеживание вручную в нереальном времени
description: Объясняется, как использовать отслеживание вручную в нереальных
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, отслеживание вручную
ms.openlocfilehash: 3f7f4dd1eb62cb707eaaf8632a2ba3c280a4ac31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835447"
---
# <a name="hand-tracking"></a>Отслеживание вручную

Система отслеживания вручную использует Палмс и пальцы человека в качестве входных данных для нереального. Разработчик может получить все координаты и поворот пальца, все карманные ПК и даже руки, чтобы использовать их в своем собственном коде. 

## <a name="hand-pose"></a>Рука

С помощью руки разработчики могут отвести от руки и пальцы активного пользователя в качестве входных данных. Эта система предоставляется в виде схем и C++. Технические сведения находятся в соответствующем классе WinRT [Windows. восприятие. People. хандпосе](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) . Этот нереалй API предоставляет данные в формате системы координат нереального времени, а такты — синхронизированы с нереальным механизмом.

### <a name="enum"></a>Перечисление.

Евмрхандкэйпоинт описывает иерархию костей руки. 

Схем

![Кэйпоинт BP](images/unreal/hand-keypoint-bp.png)
 
C++:
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

![Схема руки](images/hand-skeleton.png)

Числовые значения можно найти в таблице [Windows. восприятие. People. ханджоинткинд](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)
 
### <a name="functions"></a>Функции

Чтобы использовать функции отслеживания в схемах, откройте "отслеживание вручную/Windows Mixed Reality".

![BP для отслеживания](images/unreal/hand-tracking-bp.png)

Для функций C++ включите "Виндовсмикседреалитихандтраккингфунктионлибрари. h"

ВР

![Поддерживает отправную очередь для отслеживания](images/unreal/supports-hand-tracking-bp.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

Возвращает значение true, если на устройстве поддерживается отслеживание, значение false, если отслеживание недоступно.

ВР

![Преобразование «получение соединения с рукой»](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Эта функция возвращает пространственные данные руки. Данные обновляются каждым кадром, внутри фрейма кэшируются возвращаемые значения. Не рекомендуется включать в эту функцию интенсивную логику по соображениям производительности. 

* **Рука** , рука пользователя, стрелка влево или вправо
* **Кэйпоинт** — кость руки. 
* **Transform** — координаты и ориентация базы данных-основания кости. Чтобы получить данные преобразования для конца кости, необходимо запросить базу следующей кости. Специальная кость TIP дает окончание дистал. 
* **Радиус** — радиус базовой части кости.
* **Возвращаемое значение** — true, если кость отслеживанием этого кадра, значение false, если кость не будет отслеживанием.

## <a name="hand-live-link-animation"></a>Анимация прямой связи
Руки, доступные для анимации, используют подключаемый модуль динамической компоновки. Документация по подключаемому модулю находится [здесь](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)

Если включены подключаемые модули Windows Mixed Reality и Live Links, перейдите в **окно > динамическая ссылка** , чтобы открыть окно редактора динамической связи. Нажмите кнопку **+ Source (+ источник** ) и включите источник отслеживания Windows Mixed Reality

![Источник прямой связи](images/unreal/live-link-source.png)
 
После включения источника и открытия любого ресурса анимации на вкладке сцена сцены будут доступны следующие дополнительные параметры (подробности приведены в документации по нереальному каналу. так как подключаемый модуль находится в бета-версии, процесс может измениться позже).

![Динамическая анимация ссылки](images/unreal/live-link-animation.png)
 
Иерархия анимации руки такая же, как и в Евмрхандкэйпоинт. Анимацию можно перенацелить с помощью Виндовсмикседреалитихандтраккингливелинкремапассет. 

![Анимация прямой связи 2](images/unreal/live-link-animation2.png)
 
Его можно подклассировать в редакторе

![Сопоставление активных ссылок](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a>Сетка руки
Сетка, представляющая пользователя. 

![Сетка руки](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a>Включение и настройка

Разработчики могут получить прямой доступ к сетке вручную для собственных целей. Этот доступ должен быть включен в Арсессионконфиг: AR Settings-> мировое сопоставление — > создавать данные сетки из отслеживающей геометрии. 

Ниже приведены параметры по умолчанию для сеток.

1.  Использование данных сетки для перекрытия
2.  Создать конфликт для данных сетки
3.  Создать сетку навигации для данных сетки
4.  Отображение данных сетки в каркасе — параметр отладки, показывающий созданную сетку

Для проектов смешанной реальности эти значения параметров будут использоваться в качестве сетки пространственного сопоставления и значений по умолчанию для сетки. Разработчики могут изменять их в BP или коде для любой конкретной сетки.

### <a name="c-api-reference"></a>Справочник по API C++ 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

Это значение представляет собой сетчатую сетку для всех объектов, доступных для наблюдения.

```cpp
class FARSupportInterface 
{
public:
// other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Эти делегаты вызываются, когда система обнаруживает любой отслеживающий объект, включая сетку данных. 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
Обработчики делегатов должны иметь следующую сигнатуру:
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

Доступ к данным сетки можно получить с помощью`UARTrackedGeometry::GetUnderlyingMesh`

### <a name="blueprint-api-reference"></a>Справочник по API-интерфейсам схем

Разработчикам следует добавить к субъекту-схеме компонент для уведомления AR с контролем

![Уведомление Артраккабле](images/unreal/ar-trackable-notify.png)
 
Затем перейдите к сведениям о компоненте. 

![Артраккабле уведомление 2](images/unreal/ar-trackable-notify2.png)
 
И перезаписать для добавления, обновления или удаления отслеживающей геометрии с помощью кода, подобного приведенному ниже:

![Уведомление Артраккабле](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>Лучи с рукой

Разработчики могут использовать в качестве указывающего устройства луч. Система доступна в C++ и в проекте. Технически он предоставляет [Windows. UI. input. spatial. спатиалпоинтеринтерактионсаурцепосе](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)

Важно отметить, что поскольку результаты всех функций изменяют каждый кадр, все они становятся вызываемыми. Дополнительные сведения об чистом и нечистом или вызываемых функциях см. [в разделе](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

Для чертежа откройте "Windows Mixed Reality ХМД"

![BP](images/unreal/hand-rays-bp.png)
 
Для C++ включите "Виндовсмикседреалитифунктионлибрари. h"

### <a name="enum"></a>Перечисление.

![Кнопки контроллера ввода](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* **SELECT** -– активируемое пользователем событие SELECT, которое может быть активировано в HoloLens 2 с помощью аиртап или взгляда и фиксации. Другим способом активации этого события является "Select". 
* Это событие **, активируемое** пользователем, которое активируется в HoloLens 2 путем закрытия пальцев пользователя на голограмме. 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* **Ноттраккед** — рука не отображается
* С **отслеживанием** — рука полностью отслеживание

### <a name="struct"></a>Структура

![BP, сведения о указателе](images/unreal/pointer-pose-info-bp.png)
```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```
* **Источник** — источник руки
* **Направление** — направление руки
* **Вверх** — вверх в виде вектора руки
* **Orientation** — ориентация кватерниона 
* **Состояние отслеживания** — текущее состояние отслеживания

### <a name="functions"></a>Функции

Все функции должны вызываться для каждого кадра для непрерывного мониторинга. 

![Получить сведения о указателе](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
Функция возвращает полные сведения о направлении руки в этом кадре. 

![Есть BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
Возвращает значение true, если рука проблюдается в этом кадре. 

![Выбрана нажатая нажимаемая BP](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
Возвращает значение true, если пользователь активировал выбор в этом кадре.

![Нажата кнопка BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
Возвращает значение true, если событие или кнопка активированы в этом кадре.

![Получить состояние отслежения контроллера](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
Возвращает состояние отслеживания в этом кадре.

## <a name="gestures"></a>Жесты

Hololens 2 может контролировать пространственные жесты. Сведения об этих жестах приведены [здесь](https://docs.microsoft.com/hololens/hololens2-basic-usage) разработчик может записать их в качестве входных данных в свое приложение смешанной реальности. 

Функция C++ находится в "Виндовсмикседреалитиспатиалинпутфунктионлибрари. h"

Функция схемы находится в пространственном вводе Windows Mixed Reality

![Жесты записи](images/unreal/capture-gestures.png)

### <a name="enum"></a>Перечисление.

![Тип жеста](images/unreal/gesture-type.png)
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```
Это перечисление описывает жесты для пространственных осей. Сведения о них можно прочитать [здесь](holograms-211.md) .

### <a name="function"></a>Функция

![Точка применения жестов захвата](images/unreal/capture-gestures-bp.png)
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```
Функция включает и отключает захват жестов. Включенные жесты запускают события ввода. Он возвращает значение true, если запись жеста была включена, и значение false в случае ошибки.
Ключевые события

![Ключевые события](images/unreal/key-events.png)

![Ключевые события 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```
Если жест включен, события начинают срабатывание. 

