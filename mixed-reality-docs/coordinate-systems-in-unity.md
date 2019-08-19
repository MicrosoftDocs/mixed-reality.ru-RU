---
title: Системы координат в Unity
description: Узнайте, как создавать посторонние, ориентированные, масштабируемые и крупномасштабные возможности смешанной реальности в Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: система координат, пространственный система координат, только ориентация, установленный масштаб, фиксированное масштабирование, свободное пространство, масштаб, мир, 360 градусов, установленный, зафиксированный, комната, мир, масштаб, положение, ориентация, Unity, привязка, пространственный якорь, прикрепление, универсальная блокировка Блокировка мира, Блокировка текста, блокировка тела, отслеживание потерь, локатабилити, границы, перецентрирование
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525961"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="e3451-104">Системы координат в Unity</span><span class="sxs-lookup"><span data-stu-id="e3451-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="e3451-105">Windows Mixed Reality поддерживает приложения в [различных масштабах](coordinate-systems.md), начиная с приложений с ориентацией на страницы и до крупномасштабных приложений.</span><span class="sxs-lookup"><span data-stu-id="e3451-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="e3451-106">В HoloLens вы можете создавать приложения для мирового уровня, которые позволяют пользователям проходить более чем за 5 метров, изучая целый ряд здания и выходят за рамки.</span><span class="sxs-lookup"><span data-stu-id="e3451-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="e3451-107">Первым шагом в создании смешанной реальности в Unity является определение того, для чего будет работать [масштабирование](coordinate-systems.md) приложения.</span><span class="sxs-lookup"><span data-stu-id="e3451-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="e3451-108">Создание интерфейса, поддерживающего только ориентацию, или с возможностями масштабирования</span><span class="sxs-lookup"><span data-stu-id="e3451-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="e3451-109">**Имен** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="e3451-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="e3451-110">**Тип** *ксрдевице*</span><span class="sxs-lookup"><span data-stu-id="e3451-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="e3451-111">Чтобы создать интерфейс с **поддержкой ориентации** или **режима**, необходимо задать для Unity стационарный тип пространства отслеживания.</span><span class="sxs-lookup"><span data-stu-id="e3451-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="e3451-112">Этот параметр задает мировую систему координат Unity для отслеживания [стационарной рамки ссылки](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="e3451-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="e3451-113">В режиме нестационарного отслеживания содержимое, помещенное в редактор непосредственно перед расположением по умолчанию камеры (переадресация — Z), будет отображаться перед пользователем при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="e3451-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="e3451-114">**Имен** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="e3451-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="e3451-115">**Тип** *инпуттраккинг*</span><span class="sxs-lookup"><span data-stu-id="e3451-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="e3451-116">Для чистой **ориентации** , такой как видео-средство просмотра 360 (если позиционированные головные обновления насмарку иллюзию), можно установить [XR. Инпуттраккинг. Дисаблепоситионалтраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) имеет значение true:</span><span class="sxs-lookup"><span data-stu-id="e3451-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="e3451-117">Для **работы с возможностями масштабирования**, чтобы пользователь мог позже изменить центр исходного места, можно вызвать [XR. Метод Инпуттраккинг. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :</span><span class="sxs-lookup"><span data-stu-id="e3451-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="e3451-118">Создание фиксированного масштаба или возможностей для масштабирования комнаты</span><span class="sxs-lookup"><span data-stu-id="e3451-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="e3451-119">**Имен** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="e3451-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="e3451-120">**Тип** *ксрдевице*</span><span class="sxs-lookup"><span data-stu-id="e3451-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="e3451-121">Для работы с фиксированным масштабированием или **комнатным масштабированием**необходимо разместить содержимое относительно основания.</span><span class="sxs-lookup"><span data-stu-id="e3451-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="e3451-122">Вы указываете на этаж пользователя с помощью **[пространственного этапа](coordinate-systems.md#spatial-coordinate-systems)** , который представляет определенное пользователем происхождение на уровне пола и дополнительную границу комнаты, настраивается во время первого запуска.</span><span class="sxs-lookup"><span data-stu-id="e3451-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="e3451-123">Чтобы убедиться, что Unity работает со своей мировой системой координат на уровне пола, можно задать для Unity тип пространства отслеживания Румскале и убедиться, что набор выполнен правильно:</span><span class="sxs-lookup"><span data-stu-id="e3451-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

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
* <span data-ttu-id="e3451-124">Если Сеттраккингспацетипе возвращает значение true, Unity успешно переключил свою систему координат мира для мониторинга промежуточного [кадра ссылки](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="e3451-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="e3451-125">Если Сеттраккингспацетипе возвращает значение false, Unity не смог переключиться на промежуточный кадр ссылки, скорее всего потому, что пользователь не настроил даже этаж в своей среде.</span><span class="sxs-lookup"><span data-stu-id="e3451-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="e3451-126">Это не является распространенным, но может произойти, если этап был настроен в другой комнате и устройство было перемещено в текущую комнату без настройки нового этапа пользователем.</span><span class="sxs-lookup"><span data-stu-id="e3451-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="e3451-127">После того как приложение успешно установит тип пространства отслеживания Румскале, на этаж будут отображаться содержимое, помещенное на плоскости y = 0.</span><span class="sxs-lookup"><span data-stu-id="e3451-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="e3451-128">Источник в точке (0, 0, 0) будет определять конкретное место в этаже, где пользователь стояли во время настройки комнаты, с параметром-Z, представляющим Направление переадресации во время установки.</span><span class="sxs-lookup"><span data-stu-id="e3451-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="e3451-129">**Имен** *UnityEngine. экспериментальный. XR*</span><span class="sxs-lookup"><span data-stu-id="e3451-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="e3451-130">**Тип** *Границ*</span><span class="sxs-lookup"><span data-stu-id="e3451-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="e3451-131">В коде скрипта можно вызвать метод Трижетжеометри, так как тип UnityEngine. экспериментальный. XR. граничное используется для получения граничного многоугольника, указывая тип границы Траккедареа.</span><span class="sxs-lookup"><span data-stu-id="e3451-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="e3451-132">Если пользователь определил границу (вы получаете список вершин), вы узнаете, как можно обеспечить пользователю **возможности масштабирования комнаты** , где он может пройти по создаваемой сцене.</span><span class="sxs-lookup"><span data-stu-id="e3451-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="e3451-133">Обратите внимание, что система автоматически визуализирует границу, когда пользователь его приближает.</span><span class="sxs-lookup"><span data-stu-id="e3451-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="e3451-134">Приложению не нужно использовать этот многоугольник для отрисовки самой границы.</span><span class="sxs-lookup"><span data-stu-id="e3451-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="e3451-135">Тем не менее можно выбрать размещение объектов сцены с помощью этого многоугольника, чтобы гарантировать, что пользователь сможет физически достичь этих объектов без переноса.</span><span class="sxs-lookup"><span data-stu-id="e3451-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="e3451-136">Создание возможностей для мирового масштабирования</span><span class="sxs-lookup"><span data-stu-id="e3451-136">Building a world-scale experience</span></span>

<span data-ttu-id="e3451-137">**Имен** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="e3451-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="e3451-138">**Тип** *ворлданчор*</span><span class="sxs-lookup"><span data-stu-id="e3451-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="e3451-139">Для полноценного **крупномасштабного взаимодействия** в HoloLens, который позволяет пользователям рыскающего более 5 метров, вам потребуются новые методы, кроме тех, которые используются для работы с масштабом комнаты.</span><span class="sxs-lookup"><span data-stu-id="e3451-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="e3451-140">Одной из ключевых методик, которую вы будете использовать, является создание [пространственной привязки](coordinate-systems.md#spatial-anchors) для блокировки кластера голограмм, точно на месте физического мира, независимо от того, на каком расстояние перемещен пользователь, а затем [снова находит эти голограммы в последующих сеансах](coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="e3451-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="e3451-141">В Unity вы создаете пространственное привязку, добавив компонент Unity **ворлданчор** в GameObject.</span><span class="sxs-lookup"><span data-stu-id="e3451-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="e3451-142">Добавление универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="e3451-142">Adding a World Anchor</span></span>

<span data-ttu-id="e3451-143">Чтобы добавить привязку к мировому объекту<WorldAnchor>, вызовите метод AddComponent () для игрового объекта с преобразованием, которое необходимо привязать в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="e3451-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="e3451-144">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="e3451-144">That's it!</span></span> <span data-ttu-id="e3451-145">Этот объект игры теперь будет привязан к его текущему расположению в физическом мире. Вы можете увидеть, что его координаты Unity могут немного измениться с течением времени, чтобы обеспечить физическое выравнивание.</span><span class="sxs-lookup"><span data-stu-id="e3451-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="e3451-146">Используйте [сохраняемость](persistence-in-unity.md) для повторного нахождения этого привязанного расположения в следующем сеансе приложения.</span><span class="sxs-lookup"><span data-stu-id="e3451-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="e3451-147">Удаление универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="e3451-147">Removing a World Anchor</span></span>

<span data-ttu-id="e3451-148">Если вы больше не хотите, чтобы GameObject заблокировались в физическом расположении и не планировали перемещать его, то можно просто вызвать Destroy в компоненте «Универсальная привязка».</span><span class="sxs-lookup"><span data-stu-id="e3451-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="e3451-149">Если вы хотите переместить GameObject этот кадр, необходимо вызвать Дестройиммедиате.</span><span class="sxs-lookup"><span data-stu-id="e3451-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="e3451-150">Перемещение привязанного GameObject по всему миру</span><span class="sxs-lookup"><span data-stu-id="e3451-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="e3451-151">GameObject нельзя переместить, пока на нем есть универсальная привязка.</span><span class="sxs-lookup"><span data-stu-id="e3451-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="e3451-152">Если вам нужно переместить GameObject этот кадр, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="e3451-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="e3451-153">Дестройиммедиате компонент «мировая привязка»</span><span class="sxs-lookup"><span data-stu-id="e3451-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="e3451-154">Перемещение GameObject</span><span class="sxs-lookup"><span data-stu-id="e3451-154">Move the GameObject</span></span>
3. <span data-ttu-id="e3451-155">Добавьте новый компонент универсальной привязки к GameObject.</span><span class="sxs-lookup"><span data-stu-id="e3451-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="e3451-156">Обработка изменений Локатабилити</span><span class="sxs-lookup"><span data-stu-id="e3451-156">Handling Locatability Changes</span></span>

<span data-ttu-id="e3451-157">Ворлданчор не может быть размещаемые в физическом мире на момент времени.</span><span class="sxs-lookup"><span data-stu-id="e3451-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="e3451-158">В таком случае Unity не будет обновлять преобразование привязанного объекта.</span><span class="sxs-lookup"><span data-stu-id="e3451-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="e3451-159">Это также можно изменить во время работы приложения.</span><span class="sxs-lookup"><span data-stu-id="e3451-159">This also can change while an app is running.</span></span> <span data-ttu-id="e3451-160">Сбой при обработке изменения в локатабилити приведет к тому, что объект не будет отображаться в правильном физическом расположении в мире.</span><span class="sxs-lookup"><span data-stu-id="e3451-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="e3451-161">Чтобы получать уведомления об изменениях локатабилити:</span><span class="sxs-lookup"><span data-stu-id="e3451-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="e3451-162">Подпишитесь на событие Онтраккингчанжед</span><span class="sxs-lookup"><span data-stu-id="e3451-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="e3451-163">Обработайте событие</span><span class="sxs-lookup"><span data-stu-id="e3451-163">Handle the event</span></span>

<span data-ttu-id="e3451-164">Событие **онтраккингчанжед** будет вызываться при каждом изменении базовой пространственной привязки между состояниями размещаемые и not размещаемые.</span><span class="sxs-lookup"><span data-stu-id="e3451-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="e3451-165">Затем обработайте событие:</span><span class="sxs-lookup"><span data-stu-id="e3451-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="e3451-166">Иногда привязки размещаются немедленно.</span><span class="sxs-lookup"><span data-stu-id="e3451-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="e3451-167">В этом случае для этого свойства объекта привязки будет задано значение true, если функция AddComponent<WorldAnchor>() возвращает.</span><span class="sxs-lookup"><span data-stu-id="e3451-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="e3451-168">В результате событие Онтраккингчанжед не будет активировано.</span><span class="sxs-lookup"><span data-stu-id="e3451-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="e3451-169">Чистый шаблон будет вызывать обработчик Онтраккингчанжед с начальным состоянием после присоединения привязки.</span><span class="sxs-lookup"><span data-stu-id="e3451-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="e3451-170">Совместное использование привязок на разных устройствах</span><span class="sxs-lookup"><span data-stu-id="e3451-170">Sharing anchors across devices</span></span>

<span data-ttu-id="e3451-171"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания надежной облачной привязки на основе локальной ворлданчор, которую приложение может разместить на нескольких устройствах HoloLens, iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="e3451-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="e3451-172">При совместном использовании общей пространственной привязки на нескольких устройствах каждый пользователь может видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="e3451-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="e3451-173">Это позволяет обмениваться опытом в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="e3451-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="e3451-174">Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.</span><span class="sxs-lookup"><span data-stu-id="e3451-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="e3451-175">После завершения работы с пространственными привязками Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="e3451-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3451-176">См. также</span><span class="sxs-lookup"><span data-stu-id="e3451-176">See Also</span></span>
* [<span data-ttu-id="e3451-177">Масштабирование работы</span><span class="sxs-lookup"><span data-stu-id="e3451-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="e3451-178">Пространственный этап</span><span class="sxs-lookup"><span data-stu-id="e3451-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="e3451-179">Потеря слежения в Unity</span><span class="sxs-lookup"><span data-stu-id="e3451-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="e3451-180">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="e3451-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="e3451-181">Сохраняемость в Unity</span><span class="sxs-lookup"><span data-stu-id="e3451-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="e3451-182">Общий доступ в Unity</span><span class="sxs-lookup"><span data-stu-id="e3451-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="e3451-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a></span><span class="sxs-lookup"><span data-stu-id="e3451-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="e3451-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Пакет SDK для пространственных привязок Azure для Unity</a></span><span class="sxs-lookup"><span data-stu-id="e3451-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>