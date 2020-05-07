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
# <a name="hand-tracking"></a><span data-ttu-id="3baac-104">Отслеживание вручную</span><span class="sxs-lookup"><span data-stu-id="3baac-104">Hand Tracking</span></span>

<span data-ttu-id="3baac-105">Система отслеживания вручную использует Палмс и пальцы человека в качестве входных данных для нереального.</span><span class="sxs-lookup"><span data-stu-id="3baac-105">The hand tracking system uses a person’s palms and fingers as input to Unreal.</span></span> <span data-ttu-id="3baac-106">Разработчик может получить все координаты и поворот пальца, все карманные ПК и даже руки, чтобы использовать их в своем собственном коде.</span><span class="sxs-lookup"><span data-stu-id="3baac-106">A developer can get every finger’s position and rotation, the entire palm, and even hand gestures to use in their own code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="3baac-107">Рука</span><span class="sxs-lookup"><span data-stu-id="3baac-107">Hand Pose</span></span>

<span data-ttu-id="3baac-108">С помощью руки разработчики могут отвести от руки и пальцы активного пользователя в качестве входных данных.</span><span class="sxs-lookup"><span data-stu-id="3baac-108">Using the hand pose, developers can track the hands and fingers of the active user as input.</span></span> <span data-ttu-id="3baac-109">Эта система предоставляется в виде схем и C++.</span><span class="sxs-lookup"><span data-stu-id="3baac-109">This system is exposed through both Blueprints and C++.</span></span> <span data-ttu-id="3baac-110">Технические сведения находятся в соответствующем классе WinRT [Windows. восприятие. People. хандпосе](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) . Этот нереалй API предоставляет данные в формате системы координат нереального времени, а такты — синхронизированы с нереальным механизмом.</span><span class="sxs-lookup"><span data-stu-id="3baac-110">Technical details are in the corresponding WinRT class [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) This Unreal API provides the data in the format of Unreal’s coordinate system and ticks are synchronised with the Unreal Engine.</span></span>

### <a name="enum"></a><span data-ttu-id="3baac-111">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="3baac-111">Enum</span></span>

<span data-ttu-id="3baac-112">Евмрхандкэйпоинт описывает иерархию костей руки.</span><span class="sxs-lookup"><span data-stu-id="3baac-112">EWMRHandKeypoint describes the Hand’s bone hierarchy.</span></span> 

<span data-ttu-id="3baac-113">Схем</span><span class="sxs-lookup"><span data-stu-id="3baac-113">Blueprint:</span></span>

![Кэйпоинт BP](images/unreal/hand-keypoint-bp.png)
 
<span data-ttu-id="3baac-115">C++:</span><span class="sxs-lookup"><span data-stu-id="3baac-115">C++:</span></span>
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

<span data-ttu-id="3baac-117">Числовые значения можно найти в таблице [Windows. восприятие. People. ханджоинткинд](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span><span class="sxs-lookup"><span data-stu-id="3baac-117">The numerical values can be found in the table [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span></span>
 
### <a name="functions"></a><span data-ttu-id="3baac-118">Функции</span><span class="sxs-lookup"><span data-stu-id="3baac-118">Functions</span></span>

<span data-ttu-id="3baac-119">Чтобы использовать функции отслеживания в схемах, откройте "отслеживание вручную/Windows Mixed Reality".</span><span class="sxs-lookup"><span data-stu-id="3baac-119">To use hand tracking functions in Blueprints, open "Hand Tracking/Windows Mixed Reality"</span></span>

![BP для отслеживания](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="3baac-121">Для функций C++ включите "Виндовсмикседреалитихандтраккингфунктионлибрари. h"</span><span class="sxs-lookup"><span data-stu-id="3baac-121">For C++ functions, include "WindowsMixedRealityHandTrackingFunctionLibrary.h"</span></span>

<span data-ttu-id="3baac-122">ВР</span><span class="sxs-lookup"><span data-stu-id="3baac-122">BP:</span></span>

![Поддерживает отправную очередь для отслеживания](images/unreal/supports-hand-tracking-bp.png)
 
<span data-ttu-id="3baac-124">C++:</span><span class="sxs-lookup"><span data-stu-id="3baac-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

<span data-ttu-id="3baac-125">Возвращает значение true, если на устройстве поддерживается отслеживание, значение false, если отслеживание недоступно.</span><span class="sxs-lookup"><span data-stu-id="3baac-125">Returns true if hand tracking is supported on the device, false if hand tracking is not available.</span></span>

<span data-ttu-id="3baac-126">ВР</span><span class="sxs-lookup"><span data-stu-id="3baac-126">BP:</span></span>

![Преобразование «получение соединения с рукой»](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="3baac-128">C++:</span><span class="sxs-lookup"><span data-stu-id="3baac-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="3baac-129">Эта функция возвращает пространственные данные руки.</span><span class="sxs-lookup"><span data-stu-id="3baac-129">This function returns spatial data of the hand.</span></span> <span data-ttu-id="3baac-130">Данные обновляются каждым кадром, внутри фрейма кэшируются возвращаемые значения.</span><span class="sxs-lookup"><span data-stu-id="3baac-130">The data updates every frame, inside a frame the returned values are cached.</span></span> <span data-ttu-id="3baac-131">Не рекомендуется включать в эту функцию интенсивную логику по соображениям производительности.</span><span class="sxs-lookup"><span data-stu-id="3baac-131">It is not recommended to have heavy logic on this function for performance reasons.</span></span> 

* <span data-ttu-id="3baac-132">**Рука** , рука пользователя, стрелка влево или вправо</span><span class="sxs-lookup"><span data-stu-id="3baac-132">**Hand** – hand of the user, may be left or right</span></span>
* <span data-ttu-id="3baac-133">**Кэйпоинт** — кость руки.</span><span class="sxs-lookup"><span data-stu-id="3baac-133">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="3baac-134">**Transform** — координаты и ориентация базы данных-основания кости.</span><span class="sxs-lookup"><span data-stu-id="3baac-134">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="3baac-135">Чтобы получить данные преобразования для конца кости, необходимо запросить базу следующей кости.</span><span class="sxs-lookup"><span data-stu-id="3baac-135">To get the transform data for the end of a bone, the base of the next bone should be requested.</span></span> <span data-ttu-id="3baac-136">Специальная кость TIP дает окончание дистал.</span><span class="sxs-lookup"><span data-stu-id="3baac-136">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="3baac-137">**Радиус** — радиус базовой части кости.</span><span class="sxs-lookup"><span data-stu-id="3baac-137">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="3baac-138">**Возвращаемое значение** — true, если кость отслеживанием этого кадра, значение false, если кость не будет отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="3baac-138">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="3baac-139">Анимация прямой связи</span><span class="sxs-lookup"><span data-stu-id="3baac-139">Hand Live Link Animation</span></span>
<span data-ttu-id="3baac-140">Руки, доступные для анимации, используют подключаемый модуль динамической компоновки.</span><span class="sxs-lookup"><span data-stu-id="3baac-140">Hand poses are exposed to Animation using the Live Link plugin.</span></span> <span data-ttu-id="3baac-141">Документация по подключаемому модулю находится [здесь](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span><span class="sxs-lookup"><span data-stu-id="3baac-141">The plugin documentation is [here](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span></span>

<span data-ttu-id="3baac-142">Если включены подключаемые модули Windows Mixed Reality и Live Links, перейдите в **окно > динамическая ссылка** , чтобы открыть окно редактора динамической связи.</span><span class="sxs-lookup"><span data-stu-id="3baac-142">If the Windows Mixed Reality and Live Link plugins are enabled, go to **Window > Live Link** to open the Live Link editor window.</span></span> <span data-ttu-id="3baac-143">Нажмите кнопку **+ Source (+ источник** ) и включите источник отслеживания Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3baac-143">Click the **+ Source button** and enable Windows Mixed Reality Hand Tracking Source</span></span>

![Источник прямой связи](images/unreal/live-link-source.png)
 
<span data-ttu-id="3baac-145">После включения источника и открытия любого ресурса анимации на вкладке сцена сцены будут доступны следующие дополнительные параметры (подробности приведены в документации по нереальному каналу. так как подключаемый модуль находится в бета-версии, процесс может измениться позже).</span><span class="sxs-lookup"><span data-stu-id="3baac-145">After you enable the source and open any animation asset, the Preview Scene tab of Animation will have the following additional options (the details are in Unreal’s Live Link documentation- as the plugin is in beta, the process may change later)</span></span>

![Динамическая анимация ссылки](images/unreal/live-link-animation.png)
 
<span data-ttu-id="3baac-147">Иерархия анимации руки такая же, как и в Евмрхандкэйпоинт.</span><span class="sxs-lookup"><span data-stu-id="3baac-147">The hand animation hierarchy is the same as in EWMRHandKeypoint.</span></span> <span data-ttu-id="3baac-148">Анимацию можно перенацелить с помощью Виндовсмикседреалитихандтраккингливелинкремапассет.</span><span class="sxs-lookup"><span data-stu-id="3baac-148">Animation can be retargeted using WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span></span> 

![Анимация прямой связи 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="3baac-150">Его можно подклассировать в редакторе</span><span class="sxs-lookup"><span data-stu-id="3baac-150">It can be subclassed in the editor</span></span>

![Сопоставление активных ссылок](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a><span data-ttu-id="3baac-152">Сетка руки</span><span class="sxs-lookup"><span data-stu-id="3baac-152">Hand Mesh</span></span>
<span data-ttu-id="3baac-153">Сетка, представляющая пользователя.</span><span class="sxs-lookup"><span data-stu-id="3baac-153">Mesh representing the user hands.</span></span> 

![Сетка руки](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a><span data-ttu-id="3baac-155">Включение и настройка</span><span class="sxs-lookup"><span data-stu-id="3baac-155">How to enable and configure</span></span>

<span data-ttu-id="3baac-156">Разработчики могут получить прямой доступ к сетке вручную для собственных целей.</span><span class="sxs-lookup"><span data-stu-id="3baac-156">Developers can get direct access to hand meshes for their own purposes.</span></span> <span data-ttu-id="3baac-157">Этот доступ должен быть включен в Арсессионконфиг: AR Settings-> мировое сопоставление — > создавать данные сетки из отслеживающей геометрии.</span><span class="sxs-lookup"><span data-stu-id="3baac-157">This access must be enabled in ARSessionConfig: AR Settings -> World Mapping -> Generate Mesh Data from Tracked Geometry.</span></span> 

<span data-ttu-id="3baac-158">Ниже приведены параметры по умолчанию для сеток.</span><span class="sxs-lookup"><span data-stu-id="3baac-158">Here are the default parameters for meshes:</span></span>

1.  <span data-ttu-id="3baac-159">Использование данных сетки для перекрытия</span><span class="sxs-lookup"><span data-stu-id="3baac-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="3baac-160">Создать конфликт для данных сетки</span><span class="sxs-lookup"><span data-stu-id="3baac-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="3baac-161">Создать сетку навигации для данных сетки</span><span class="sxs-lookup"><span data-stu-id="3baac-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="3baac-162">Отображение данных сетки в каркасе — параметр отладки, показывающий созданную сетку</span><span class="sxs-lookup"><span data-stu-id="3baac-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="3baac-163">Для проектов смешанной реальности эти значения параметров будут использоваться в качестве сетки пространственного сопоставления и значений по умолчанию для сетки.</span><span class="sxs-lookup"><span data-stu-id="3baac-163">For mixed reality projects, these parameter values will be used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="3baac-164">Разработчики могут изменять их в BP или коде для любой конкретной сетки.</span><span class="sxs-lookup"><span data-stu-id="3baac-164">Developers can change them in BP or code for any particular mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="3baac-165">Справочник по API C++</span><span class="sxs-lookup"><span data-stu-id="3baac-165">C++ API Reference</span></span> 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

<span data-ttu-id="3baac-166">Это значение представляет собой сетчатую сетку для всех объектов, доступных для наблюдения.</span><span class="sxs-lookup"><span data-stu-id="3baac-166">This value is the hand mesh among all trackable objects.</span></span>

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

<span data-ttu-id="3baac-167">Эти делегаты вызываются, когда система обнаруживает любой отслеживающий объект, включая сетку данных.</span><span class="sxs-lookup"><span data-stu-id="3baac-167">These delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
<span data-ttu-id="3baac-168">Обработчики делегатов должны иметь следующую сигнатуру:</span><span class="sxs-lookup"><span data-stu-id="3baac-168">Handlers to the delegates should have the following signature:</span></span>
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

<span data-ttu-id="3baac-169">Доступ к данным сетки можно получить с помощью`UARTrackedGeometry::GetUnderlyingMesh`</span><span class="sxs-lookup"><span data-stu-id="3baac-169">Mesh data can be accessed by `UARTrackedGeometry::GetUnderlyingMesh`</span></span>

### <a name="blueprint-api-reference"></a><span data-ttu-id="3baac-170">Справочник по API-интерфейсам схем</span><span class="sxs-lookup"><span data-stu-id="3baac-170">Blueprint API Reference</span></span>

<span data-ttu-id="3baac-171">Разработчикам следует добавить к субъекту-схеме компонент для уведомления AR с контролем</span><span class="sxs-lookup"><span data-stu-id="3baac-171">Developers should add an AR Trackable Notify Component to a Blueprint actor</span></span>

![Уведомление Артраккабле](images/unreal/ar-trackable-notify.png)
 
<span data-ttu-id="3baac-173">Затем перейдите к сведениям о компоненте.</span><span class="sxs-lookup"><span data-stu-id="3baac-173">Then go to the component’s details</span></span> 

![Артраккабле уведомление 2](images/unreal/ar-trackable-notify2.png)
 
<span data-ttu-id="3baac-175">И перезаписать для добавления, обновления или удаления отслеживающей геометрии с помощью кода, подобного приведенному ниже:</span><span class="sxs-lookup"><span data-stu-id="3baac-175">And overwrite On Add/Update/Remove Tracked Geometry with code like the below:</span></span>

![Уведомление Артраккабле](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="3baac-177">Лучи с рукой</span><span class="sxs-lookup"><span data-stu-id="3baac-177">Hand Rays</span></span>

<span data-ttu-id="3baac-178">Разработчики могут использовать в качестве указывающего устройства луч.</span><span class="sxs-lookup"><span data-stu-id="3baac-178">Developers can use a hand ray as a pointing device.</span></span> <span data-ttu-id="3baac-179">Система доступна в C++ и в проекте.</span><span class="sxs-lookup"><span data-stu-id="3baac-179">The system is available in C++ and Blueprint.</span></span> <span data-ttu-id="3baac-180">Технически он предоставляет [Windows. UI. input. spatial. спатиалпоинтеринтерактионсаурцепосе](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span><span class="sxs-lookup"><span data-stu-id="3baac-180">Technically it exposes [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span></span>

<span data-ttu-id="3baac-181">Важно отметить, что поскольку результаты всех функций изменяют каждый кадр, все они становятся вызываемыми.</span><span class="sxs-lookup"><span data-stu-id="3baac-181">It’s important to mention that since the results of all the functions changes every frame, they are all made callable.</span></span> <span data-ttu-id="3baac-182">Дополнительные сведения об чистом и нечистом или вызываемых функциях см. [в разделе](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span><span class="sxs-lookup"><span data-stu-id="3baac-182">For more information about pure vs impure or callable functions, see [that](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="3baac-183">Для чертежа откройте "Windows Mixed Reality ХМД"</span><span class="sxs-lookup"><span data-stu-id="3baac-183">For Blueprint open “Windows Mixed Reality HMD”</span></span>

![BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="3baac-185">Для C++ включите "Виндовсмикседреалитифунктионлибрари. h"</span><span class="sxs-lookup"><span data-stu-id="3baac-185">For C++ include "WindowsMixedRealityFunctionLibrary.h"</span></span>

### <a name="enum"></a><span data-ttu-id="3baac-186">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="3baac-186">Enum</span></span>

![Кнопки контроллера ввода](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* <span data-ttu-id="3baac-188">**SELECT** -– активируемое пользователем событие SELECT, которое может быть активировано в HoloLens 2 с помощью аиртап или взгляда и фиксации.</span><span class="sxs-lookup"><span data-stu-id="3baac-188">**Select** -– User triggered Select event, which can be triggered in HoloLens 2 by airtap or gaze and commit.</span></span> <span data-ttu-id="3baac-189">Другим способом активации этого события является "Select".</span><span class="sxs-lookup"><span data-stu-id="3baac-189">Another way to trigger this event is to say “Select”.</span></span> 
* <span data-ttu-id="3baac-190">Это событие **, активируемое** пользователем, которое активируется в HoloLens 2 путем закрытия пальцев пользователя на голограмме.</span><span class="sxs-lookup"><span data-stu-id="3baac-190">**Grasp** -– User triggered Grasp event, which is triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* <span data-ttu-id="3baac-191">**Ноттраккед** — рука не отображается</span><span class="sxs-lookup"><span data-stu-id="3baac-191">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="3baac-192">С **отслеживанием** — рука полностью отслеживание</span><span class="sxs-lookup"><span data-stu-id="3baac-192">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="3baac-193">Структура</span><span class="sxs-lookup"><span data-stu-id="3baac-193">Struct</span></span>

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
* <span data-ttu-id="3baac-195">**Источник** — источник руки</span><span class="sxs-lookup"><span data-stu-id="3baac-195">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="3baac-196">**Направление** — направление руки</span><span class="sxs-lookup"><span data-stu-id="3baac-196">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="3baac-197">**Вверх** — вверх в виде вектора руки</span><span class="sxs-lookup"><span data-stu-id="3baac-197">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="3baac-198">**Orientation** — ориентация кватерниона</span><span class="sxs-lookup"><span data-stu-id="3baac-198">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="3baac-199">**Состояние отслеживания** — текущее состояние отслеживания</span><span class="sxs-lookup"><span data-stu-id="3baac-199">**Tracking Status** – current tracking status</span></span>

### <a name="functions"></a><span data-ttu-id="3baac-200">Функции</span><span class="sxs-lookup"><span data-stu-id="3baac-200">Functions</span></span>

<span data-ttu-id="3baac-201">Все функции должны вызываться для каждого кадра для непрерывного мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3baac-201">All the functions should be callable on every frame for continuous monitoring.</span></span> 

![Получить сведения о указателе](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
<span data-ttu-id="3baac-203">Функция возвращает полные сведения о направлении руки в этом кадре.</span><span class="sxs-lookup"><span data-stu-id="3baac-203">The function returns the full information about the hand ray direction in this frame.</span></span> 

![Есть BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
<span data-ttu-id="3baac-205">Возвращает значение true, если рука проблюдается в этом кадре.</span><span class="sxs-lookup"><span data-stu-id="3baac-205">Returns true if the hand is grasped in this frame.</span></span> 

![Выбрана нажатая нажимаемая BP](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
<span data-ttu-id="3baac-207">Возвращает значение true, если пользователь активировал выбор в этом кадре.</span><span class="sxs-lookup"><span data-stu-id="3baac-207">Returns true if the user triggered Select in this frame.</span></span>

![Нажата кнопка BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
<span data-ttu-id="3baac-209">Возвращает значение true, если событие или кнопка активированы в этом кадре.</span><span class="sxs-lookup"><span data-stu-id="3baac-209">Returns true if the event/button is triggered in this frame.</span></span>

![Получить состояние отслежения контроллера](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
<span data-ttu-id="3baac-211">Возвращает состояние отслеживания в этом кадре.</span><span class="sxs-lookup"><span data-stu-id="3baac-211">Returns the tracking status in this frame.</span></span>

## <a name="gestures"></a><span data-ttu-id="3baac-212">Жесты</span><span class="sxs-lookup"><span data-stu-id="3baac-212">Gestures</span></span>

<span data-ttu-id="3baac-213">Hololens 2 может контролировать пространственные жесты.</span><span class="sxs-lookup"><span data-stu-id="3baac-213">The Hololens 2 can track spatial gestures.</span></span> <span data-ttu-id="3baac-214">Сведения об этих жестах приведены [здесь](https://docs.microsoft.com/hololens/hololens2-basic-usage) разработчик может записать их в качестве входных данных в свое приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="3baac-214">Details about these gestures are [here](https://docs.microsoft.com/hololens/hololens2-basic-usage) A developer can capture them as input to their mixed reality application.</span></span> 

<span data-ttu-id="3baac-215">Функция C++ находится в "Виндовсмикседреалитиспатиалинпутфунктионлибрари. h"</span><span class="sxs-lookup"><span data-stu-id="3baac-215">The C++ function is in "WindowsMixedRealitySpatialInputFunctionLibrary.h"</span></span>

<span data-ttu-id="3baac-216">Функция схемы находится в пространственном вводе Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3baac-216">The Blueprint function is in Windows Mixed Reality Spatial Input</span></span>

![Жесты записи](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="3baac-218">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="3baac-218">Enum</span></span>

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
<span data-ttu-id="3baac-220">Это перечисление описывает жесты для пространственных осей.</span><span class="sxs-lookup"><span data-stu-id="3baac-220">This enum describes spatial axis gestures.</span></span> <span data-ttu-id="3baac-221">Сведения о них можно прочитать [здесь](holograms-211.md) .</span><span class="sxs-lookup"><span data-stu-id="3baac-221">You can read about them [here](holograms-211.md)</span></span>

### <a name="function"></a><span data-ttu-id="3baac-222">Функция</span><span class="sxs-lookup"><span data-stu-id="3baac-222">Function</span></span>

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
<span data-ttu-id="3baac-224">Функция включает и отключает захват жестов.</span><span class="sxs-lookup"><span data-stu-id="3baac-224">The function enables and disables capturing of gestures.</span></span> <span data-ttu-id="3baac-225">Включенные жесты запускают события ввода.</span><span class="sxs-lookup"><span data-stu-id="3baac-225">The enabled gestures fire input events.</span></span> <span data-ttu-id="3baac-226">Он возвращает значение true, если запись жеста была включена, и значение false в случае ошибки.</span><span class="sxs-lookup"><span data-stu-id="3baac-226">It returns true if enabling gesture capture succeeded and false if there's an error.</span></span>
<span data-ttu-id="3baac-227">Ключевые события</span><span class="sxs-lookup"><span data-stu-id="3baac-227">Key Events</span></span>

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
<span data-ttu-id="3baac-230">Если жест включен, события начинают срабатывание.</span><span class="sxs-lookup"><span data-stu-id="3baac-230">If the gesture is enabled, the events begin firing.</span></span> 

