---
title: Системы координат в Unity
description: Сведения о создании за кресло репутацию комнаты и масштабирования смешении и мир и масштабирования интерфейсов реальности в Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: системы координат, пространственные системы координат, только для ориентации, установки и масштабирования, положение и масштабирования, места и масштабирования, всему миру и масштабирования, сидели 360 градусов, положение, номере, всему миру, масштаб, позиции, ориентации, Unity, привязки, пространственных привязки, привязки к всему миру, заблокированы в мире, Блокировка в мире, заблокирован для текста, текст блокировки, отслеживания потери, locatability, границы, центровку
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605053"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="2abaa-104">Системы координат в Unity</span><span class="sxs-lookup"><span data-stu-id="2abaa-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="2abaa-105">Смешанная реальность Windows поддерживает приложения для широкого диапазона из [возникнуть шкал](coordinate-systems.md), из приложений только для ориентации и сидели масштабирования вверх через комнаты масштабируемых приложений.</span><span class="sxs-lookup"><span data-stu-id="2abaa-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="2abaa-106">На HoloLens можно пойти дальше и создавать world масштабируемых приложений, позволяющих пользователям пройти за 5 м изучение всей этаж здания и за ее пределами.</span><span class="sxs-lookup"><span data-stu-id="2abaa-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="2abaa-107">Является первым шагом в создании более возможности смешанной реальности в Unity, чтобы определить, какие [возможности масштабирования](coordinate-systems.md) будет работать ваше приложение.</span><span class="sxs-lookup"><span data-stu-id="2abaa-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="2abaa-108">Построение интерфейс только для ориентации или установки и масштабирования</span><span class="sxs-lookup"><span data-stu-id="2abaa-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="2abaa-109">**Пространство имен:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="2abaa-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="2abaa-110">**Тип:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="2abaa-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="2abaa-111">Для создания **только для ориентации** или **сидели высококлассные возможности**, необходимо задать Unity бланк отслеживания тип пространства.</span><span class="sxs-lookup"><span data-stu-id="2abaa-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="2abaa-112">Этот параметр задает Unity мировая система координат для отслеживания [стационарной системой отсчета координат](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="2abaa-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="2abaa-113">В режиме отслеживания неподвижным, содержимое помещено в редакторе перед камерой расположение по умолчанию (вперед -Z) будет отображаться перед пользователем, при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="2abaa-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="2abaa-114">**Пространство имен:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="2abaa-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="2abaa-115">**Тип:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="2abaa-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="2abaa-116">Для чистого **только для ориентации интерфейс** например характеристиках видео средства просмотра, (где позиционные обновления головного бы разрушить иллюзию), затем можно задать [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) значение true:</span><span class="sxs-lookup"><span data-stu-id="2abaa-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="2abaa-117">Для **сидели высококлассные возможности**, чтобы пользователи могли позже центровку за кресло источника, можно вызвать [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) метод:</span><span class="sxs-lookup"><span data-stu-id="2abaa-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="2abaa-118">Фиксированный масштаб или масштаб комнаты качества построения</span><span class="sxs-lookup"><span data-stu-id="2abaa-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="2abaa-119">**Пространство имен:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="2abaa-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="2abaa-120">**Тип:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="2abaa-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="2abaa-121">Для **положение шкалы** или **комнаты высококлассные возможности**, вам потребуется разместить содержимое относительно ближайшее снизу целое.</span><span class="sxs-lookup"><span data-stu-id="2abaa-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="2abaa-122">Обсуждения пользователя floor с помощью  **[пространственных этап](coordinate-systems.md#spatial-coordinate-systems)**, который представляет пользователя определенные полу источника и границ необязательно комнаты, заданный во время первого запуска.</span><span class="sxs-lookup"><span data-stu-id="2abaa-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="2abaa-123">Чтобы убедиться, что Unity работает с мировая система координат на уровне floor, можно присвоить Unity RoomScale, отслеживание типа пространство и убедитесь, что набор выполняется успешно:</span><span class="sxs-lookup"><span data-stu-id="2abaa-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* <span data-ttu-id="2abaa-124">Если SetTrackingSpaceType возвращает значение true, мировая система координат для отслеживания успешно переключился Unity [этап подразумевает](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="2abaa-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="2abaa-125">Если SetTrackingSpaceType возвращает false, Unity не удалось переключиться на этапе отсчета, скорее всего, поскольку пользователь не установил даже этаж в своей среде.</span><span class="sxs-lookup"><span data-stu-id="2abaa-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="2abaa-126">Это не часто, но также может произойти, если в рабочей области были настроены в другой комнате и устройства был перемещен в текущего места без пользователь, настраивающий новый этап.</span><span class="sxs-lookup"><span data-stu-id="2abaa-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="2abaa-127">После приложения успешно задает RoomScale, отслеживания тип пространства, содержимого уделено y = 0, плоскость появятся в ближайшее снизу целое.</span><span class="sxs-lookup"><span data-stu-id="2abaa-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="2abaa-128">Исходный объект на (0, 0, 0) будет определенное место в процессе установки, где пользователь стояли во время установки комнате с -Z, представляющая вперед, которые они были с выходом во время установки.</span><span class="sxs-lookup"><span data-stu-id="2abaa-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="2abaa-129">**Пространство имен:** *UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="2abaa-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="2abaa-130">**Тип:** *Границ*</span><span class="sxs-lookup"><span data-stu-id="2abaa-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="2abaa-131">В коде скрипта можно вызов метода TryGetGeometry на вы будете типа UnityEngine.Experimental.XR.Boundary многоугольника границ, задание типа TrackedArea границ.</span><span class="sxs-lookup"><span data-stu-id="2abaa-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="2abaa-132">Если определяемый пользователем границе (можно вернуть список вершин), вы знаете, безопасно доставлять **комнаты высококлассные возможности** для пользователя, где они могут помочь вокруг сцены создать.</span><span class="sxs-lookup"><span data-stu-id="2abaa-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="2abaa-133">Обратите внимание на то, система автоматически будет отображать границу пользователя приближается к его.</span><span class="sxs-lookup"><span data-stu-id="2abaa-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="2abaa-134">Приложения не нужно использовать для подготовки к просмотру самой границе этого многоугольника.</span><span class="sxs-lookup"><span data-stu-id="2abaa-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="2abaa-135">Тем не менее вы можете разместить объекты сцены с помощью этого многоугольника границ, чтобы убедиться, что пользователь физически имеет доступ к этим объектам без teleporting:</span><span class="sxs-lookup"><span data-stu-id="2abaa-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="2abaa-136">Создание более world высококлассные возможности</span><span class="sxs-lookup"><span data-stu-id="2abaa-136">Building a world-scale experience</span></span>

<span data-ttu-id="2abaa-137">**Пространство имен:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="2abaa-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="2abaa-138">**Тип:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="2abaa-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="2abaa-139">Для значения верно **world высококлассные возможности** на HoloLens, с помощью которых пользователи перемещаются за пределы 5 м, вам потребуется новые методики, помимо тех, которые используются для работы в комнате и масштабирования.</span><span class="sxs-lookup"><span data-stu-id="2abaa-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="2abaa-140">Один ключевой метод, вы будете использовать, — для создания [пространственных привязки](coordinate-systems.md#spatial-anchors) заблокировать кластера голограммы точно на месте в физическом мире, независимо от того, насколько далеко перемещаемого пользователя, а затем [найти эти голограммы попытку в более поздней версии сеансы](coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="2abaa-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="2abaa-141">В Unity, вы создадите пространственных привязки, добавив **WorldAnchor** компонент Unity в объект GameObject.</span><span class="sxs-lookup"><span data-stu-id="2abaa-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="2abaa-142">Добавление привязки к всему миру</span><span class="sxs-lookup"><span data-stu-id="2abaa-142">Adding a World Anchor</span></span>

<span data-ttu-id="2abaa-143">Чтобы добавить привязку мира, вызовите AddComponent<WorldAnchor>() в объекте игры с преобразованием, нужно закрепить в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="2abaa-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="2abaa-144">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="2abaa-144">That's it!</span></span> <span data-ttu-id="2abaa-145">Теперь этот объект игр будет привязана к текущего места в физическом мире — немного изменить со временем, чтобы обеспечить выравнивание физических мировых координатах его Unity система может появиться.</span><span class="sxs-lookup"><span data-stu-id="2abaa-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="2abaa-146">Используйте [сохраняемости](persistence-in-unity.md) найти этот прикрепленных расположение еще раз в сеансе приложению в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="2abaa-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="2abaa-147">Удаление привязки World</span><span class="sxs-lookup"><span data-stu-id="2abaa-147">Removing a World Anchor</span></span>

<span data-ttu-id="2abaa-148">Если вы больше не нужны GameObject будут находиться в физическом мире расположение и не планируете его перемещения этого кадра, затем можно просто вызвать Destroy World привязки компонента.</span><span class="sxs-lookup"><span data-stu-id="2abaa-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="2abaa-149">Если вы хотите переместить объект GameObject данного кадра, необходимо вместо этого вызвать DestroyImmediate.</span><span class="sxs-lookup"><span data-stu-id="2abaa-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="2abaa-150">Перемещение мир привязанный объект GameObject</span><span class="sxs-lookup"><span data-stu-id="2abaa-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="2abaa-151">Невозможно переместить объект GameObject во время привязки к всему миру на нем.</span><span class="sxs-lookup"><span data-stu-id="2abaa-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="2abaa-152">Если вам нужно переместить объект GameObject данного кадра, необходимо:</span><span class="sxs-lookup"><span data-stu-id="2abaa-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="2abaa-153">DestroyImmediate World привязки компонента</span><span class="sxs-lookup"><span data-stu-id="2abaa-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="2abaa-154">Переместить GameObject</span><span class="sxs-lookup"><span data-stu-id="2abaa-154">Move the GameObject</span></span>
3. <span data-ttu-id="2abaa-155">Добавьте новый компонент привязки World GameObject.</span><span class="sxs-lookup"><span data-stu-id="2abaa-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="2abaa-156">Обработка изменений Locatability</span><span class="sxs-lookup"><span data-stu-id="2abaa-156">Handling Locatability Changes</span></span>

<span data-ttu-id="2abaa-157">WorldAnchor может оказаться может быть найдена в физическом мире общую точку во времени.</span><span class="sxs-lookup"><span data-stu-id="2abaa-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="2abaa-158">Если это происходит, Unity не обновлять преобразование привязанного объекта.</span><span class="sxs-lookup"><span data-stu-id="2abaa-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="2abaa-159">Это также можно изменить во время работы приложения.</span><span class="sxs-lookup"><span data-stu-id="2abaa-159">This also can change while an app is running.</span></span> <span data-ttu-id="2abaa-160">Ошибка для обработки изменений в locatability вызовет элемент, который отображается в в нужное место в мире.</span><span class="sxs-lookup"><span data-stu-id="2abaa-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="2abaa-161">Чтобы получать уведомления об изменениях locatability:</span><span class="sxs-lookup"><span data-stu-id="2abaa-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="2abaa-162">Подписаться на событие OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="2abaa-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="2abaa-163">Обработка события</span><span class="sxs-lookup"><span data-stu-id="2abaa-163">Handle the event</span></span>

<span data-ttu-id="2abaa-164">**OnTrackingChanged** событие будет вызываться при каждом изменении базовых пространственных привязки между состоянием, может быть найдена, и не может быть найдена.</span><span class="sxs-lookup"><span data-stu-id="2abaa-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="2abaa-165">Затем можно обработать событие:</span><span class="sxs-lookup"><span data-stu-id="2abaa-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="2abaa-166">Иногда привязки, расположены немедленно.</span><span class="sxs-lookup"><span data-stu-id="2abaa-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="2abaa-167">В этом случае это свойство isLocated привязки будет присвоено значение true, если AddComponent<WorldAnchor>() возвращает.</span><span class="sxs-lookup"><span data-stu-id="2abaa-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="2abaa-168">В результате OnTrackingChanged событие не будет применяться.</span><span class="sxs-lookup"><span data-stu-id="2abaa-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="2abaa-169">Очистить шаблон будет вызывать обработчик OnTrackingChanged с начальное состояние IsLocated после присоединения привязки.</span><span class="sxs-lookup"><span data-stu-id="2abaa-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="2abaa-170">Совместное использование привязки на устройствах</span><span class="sxs-lookup"><span data-stu-id="2abaa-170">Sharing anchors across devices</span></span>

<span data-ttu-id="2abaa-171">Можно использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a> для создания привязки надежные облачные из локального WorldAnchor, который приложения можно найти в нескольких HoloLens, iOS и устройств Android.</span><span class="sxs-lookup"><span data-stu-id="2abaa-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="2abaa-172">Совместное использование общих пространственных привязки на нескольких устройствах, каждый пользователь может видеть содержимое отображается относительно эту привязку, в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="2abaa-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="2abaa-173">Это позволяет выполнять публикацию в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="2abaa-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="2abaa-174">Чтобы приступить к работе, создания общих возможностей в Unity, изучите 5-минутные <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">краткие руководства по Azure пространственных привязки Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="2abaa-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="2abaa-175">После того, как приступить к работе с пространственными привязки Azure, вы можете затем <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создать и найдите привязки в Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="2abaa-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="2abaa-176">См. также</span><span class="sxs-lookup"><span data-stu-id="2abaa-176">See Also</span></span>
* [<span data-ttu-id="2abaa-177">Возможности масштабирования</span><span class="sxs-lookup"><span data-stu-id="2abaa-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="2abaa-178">Пространственные рабочей области</span><span class="sxs-lookup"><span data-stu-id="2abaa-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="2abaa-179">Отслеживание потери в Unity</span><span class="sxs-lookup"><span data-stu-id="2abaa-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="2abaa-180">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="2abaa-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="2abaa-181">Сохраняемость в Unity</span><span class="sxs-lookup"><span data-stu-id="2abaa-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="2abaa-182">Публикацию в Unity</span><span class="sxs-lookup"><span data-stu-id="2abaa-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="2abaa-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure пространственных привязки</a></span><span class="sxs-lookup"><span data-stu-id="2abaa-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="2abaa-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure пространственных привязки пакета SDK для Unity</a></span><span class="sxs-lookup"><span data-stu-id="2abaa-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>