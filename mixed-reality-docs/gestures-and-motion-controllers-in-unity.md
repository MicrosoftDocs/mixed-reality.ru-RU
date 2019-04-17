---
title: Жестов и контроллеры движения в Unity
description: Существует два основных способа действия с вашей взглядом в Unity, жестами руками и контроллеры движения.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: жесты, контроллеры движения, unity, взглядом, входные данные
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597656"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="354ff-104">Жестов и контроллеры движения в Unity</span><span class="sxs-lookup"><span data-stu-id="354ff-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="354ff-105">Существует два способа ключа для выполнения действий на вашей [помощи в Unity](gaze-in-unity.md), [передать жесты](gestures.md) и [движения контроллеров](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="354ff-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="354ff-106">Данные для обоих источников пространственных данных, доступный через те же интерфейсы API в Unity.</span><span class="sxs-lookup"><span data-stu-id="354ff-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="354ff-107">Среда Unity предоставляет два основных способа для доступа к пространственных входных данных для Windows Mixed Reality, распространенные *Input.GetButton/Input.GetAxis* API, которые работают на нескольких пакетов SDK Unity XR и *InteractionManager / GestureRecognizer* API, относящиеся к Windows Mixed Reality, который предоставляет полный набор доступных пространственных входных данных.</span><span class="sxs-lookup"><span data-stu-id="354ff-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="354ff-108">Таблица сопоставления кнопки/оси Unity</span><span class="sxs-lookup"><span data-stu-id="354ff-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="354ff-109">Идентификаторы в таблице ниже кнопку и оси, поддерживаются в Unity входных данных Manager для контроллеров движения Windows Mixed Reality через *Input.GetButton/GetAxis* API-интерфейсов, пока в столбце «Windows MR» определяемые ссылается на свойства Доступные за пределами класса *InteractionSourceState* типа.</span><span class="sxs-lookup"><span data-stu-id="354ff-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="354ff-110">Каждый из этих API подробно описаны в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="354ff-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="354ff-111">Идентификатор сопоставления кнопки/оси для смешанной реальности Windows обычно соответствует Oculus кнопку/оси идентификаторы.</span><span class="sxs-lookup"><span data-stu-id="354ff-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="354ff-112">Идентификатор сопоставления кнопки/оси для смешанной реальности Windows отличаются от сопоставлений в OpenVR двумя способами:</span><span class="sxs-lookup"><span data-stu-id="354ff-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="354ff-113">Сопоставление использует идентификаторы сенсорной панели, которые отличаются от джойстик, для поддержки контроллеров с thumbsticks и сенсорные панели.</span><span class="sxs-lookup"><span data-stu-id="354ff-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="354ff-114">Сопоставление позволяет избежать перегрузки кнопку A и X идентификаторов кнопок меню для оставлю их для физических кнопок ABXY.</span><span class="sxs-lookup"><span data-stu-id="354ff-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="354ff-115">Ввод</span><span class="sxs-lookup"><span data-stu-id="354ff-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="354ff-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Общие интерфейсы API Unity</a></span><span class="sxs-lookup"><span data-stu-id="354ff-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="354ff-117">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="354ff-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="354ff-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Входной API конкретных Windows MR</a></span><span class="sxs-lookup"><span data-stu-id="354ff-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="354ff-119">(XR. WSA. Входные данные)</span><span class="sxs-lookup"><span data-stu-id="354ff-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="354ff-120">Слева</span><span class="sxs-lookup"><span data-stu-id="354ff-120">Left hand</span></span> </th><th> <span data-ttu-id="354ff-121">Справа</span><span class="sxs-lookup"><span data-stu-id="354ff-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="354ff-122">Выбор триггера нажата</span><span class="sxs-lookup"><span data-stu-id="354ff-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="354ff-123">9 = 1.0 оси</span><span class="sxs-lookup"><span data-stu-id="354ff-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="354ff-124">10 = 1.0 оси</span><span class="sxs-lookup"><span data-stu-id="354ff-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="354ff-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="354ff-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-126">Выберите значение аналогового триггера</span><span class="sxs-lookup"><span data-stu-id="354ff-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="354ff-127">Оси 9</span><span class="sxs-lookup"><span data-stu-id="354ff-127">Axis 9</span></span> </td><td> <span data-ttu-id="354ff-128">Оси 10</span><span class="sxs-lookup"><span data-stu-id="354ff-128">Axis 10</span></span> </td><td> <span data-ttu-id="354ff-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="354ff-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-130">Выбор триггера частично нажата</span><span class="sxs-lookup"><span data-stu-id="354ff-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="354ff-131">Кнопка 14 <i>(игровой совместимости)</i> </span><span class="sxs-lookup"><span data-stu-id="354ff-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="354ff-132">Кнопка 15 <i>(игровой совместимости)</i> </span><span class="sxs-lookup"><span data-stu-id="354ff-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="354ff-133">selectPressedAmount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="354ff-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-134">Была нажата кнопка меню</span><span class="sxs-lookup"><span data-stu-id="354ff-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="354ff-135">Кнопка 6 \*</span><span class="sxs-lookup"><span data-stu-id="354ff-135">Button 6\*</span></span> </td><td> <span data-ttu-id="354ff-136">Кнопка 7 \*</span><span class="sxs-lookup"><span data-stu-id="354ff-136">Button 7\*</span></span> </td><td> <span data-ttu-id="354ff-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="354ff-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-138">Была нажата кнопка захвата для изменения</span><span class="sxs-lookup"><span data-stu-id="354ff-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="354ff-139">Оси 11 = 1.0 (не аналоговый значения)</span><span class="sxs-lookup"><span data-stu-id="354ff-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="354ff-140">Кнопка 4 <i>(игровой совместимости)</i> </span><span class="sxs-lookup"><span data-stu-id="354ff-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="354ff-141">Оси 12 = 1.0 (не аналоговый значения)</span><span class="sxs-lookup"><span data-stu-id="354ff-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="354ff-142">Кнопка 5 <i>(игровой совместимости)</i> </span><span class="sxs-lookup"><span data-stu-id="354ff-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="354ff-143">Поняв значимость комбинирования</span><span class="sxs-lookup"><span data-stu-id="354ff-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-144">Джойстик X <i>(слева: от -1.0, справа: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="354ff-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="354ff-145">Оси 1</span><span class="sxs-lookup"><span data-stu-id="354ff-145">Axis 1</span></span> </td><td> <span data-ttu-id="354ff-146">Оси 4</span><span class="sxs-lookup"><span data-stu-id="354ff-146">Axis 4</span></span> </td><td> <span data-ttu-id="354ff-147">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="354ff-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-148">Джойстик Y <i>(top: от -1.0, нижней: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="354ff-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="354ff-149">Оси 2</span><span class="sxs-lookup"><span data-stu-id="354ff-149">Axis 2</span></span> </td><td> <span data-ttu-id="354ff-150">Оси 5</span><span class="sxs-lookup"><span data-stu-id="354ff-150">Axis 5</span></span> </td><td> <span data-ttu-id="354ff-151">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="354ff-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-152">Джойстик нажата</span><span class="sxs-lookup"><span data-stu-id="354ff-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="354ff-153">Кнопка 8</span><span class="sxs-lookup"><span data-stu-id="354ff-153">Button 8</span></span> </td><td> <span data-ttu-id="354ff-154">Кнопка 9</span><span class="sxs-lookup"><span data-stu-id="354ff-154">Button 9</span></span> </td><td> <span data-ttu-id="354ff-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="354ff-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-156">X сенсорной панели <i>(слева: от -1.0, справа: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="354ff-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="354ff-157">Оси 17 \*</span><span class="sxs-lookup"><span data-stu-id="354ff-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="354ff-158">Оси 19 \*</span><span class="sxs-lookup"><span data-stu-id="354ff-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="354ff-159">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="354ff-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-160">Y сенсорной панели <i>(top: от -1.0, нижней: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="354ff-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="354ff-161">Оси 18 \*</span><span class="sxs-lookup"><span data-stu-id="354ff-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="354ff-162">Оси 20 \*</span><span class="sxs-lookup"><span data-stu-id="354ff-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="354ff-163">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="354ff-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-164">Затронутых сенсорной панели</span><span class="sxs-lookup"><span data-stu-id="354ff-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="354ff-165">Кнопка 18 \*</span><span class="sxs-lookup"><span data-stu-id="354ff-165">Button 18\*</span></span> </td><td> <span data-ttu-id="354ff-166">Кнопка 19 \*</span><span class="sxs-lookup"><span data-stu-id="354ff-166">Button 19\*</span></span> </td><td> <span data-ttu-id="354ff-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="354ff-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-168">Нажата сенсорной панели</span><span class="sxs-lookup"><span data-stu-id="354ff-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="354ff-169">Кнопка 16 \*</span><span class="sxs-lookup"><span data-stu-id="354ff-169">Button 16\*</span></span> </td><td> <span data-ttu-id="354ff-170">Кнопка 17 \*</span><span class="sxs-lookup"><span data-stu-id="354ff-170">Button 17\*</span></span> </td><td> <span data-ttu-id="354ff-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="354ff-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-172">Поза 6DoF захвата для изменения или поза указатель</span><span class="sxs-lookup"><span data-stu-id="354ff-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="354ff-173"><i>Захват</i> представляют только: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="354ff-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="354ff-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="354ff-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="354ff-175">Передайте <i>захвата для изменения</i> или <i>указатель</i> как аргумент: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="354ff-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="354ff-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="354ff-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="354ff-177">Отслеживание состояния</span><span class="sxs-lookup"><span data-stu-id="354ff-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="354ff-178"><i>Позиция точность источника потери риска и доступно только через интерфейс API, специально MR</i> </span><span class="sxs-lookup"><span data-stu-id="354ff-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="354ff-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="354ff-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="354ff-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="354ff-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="354ff-181">Эти кнопки/оси идентификаторы отличаются от используемых Unity для OpenVR из-за конфликтов в сопоставления, используемые игровые планшеты, сенсорное управление Oculus и OpenVR идентификаторы.</span><span class="sxs-lookup"><span data-stu-id="354ff-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="354ff-182">Поза захвата для изменения и указывающего поза</span><span class="sxs-lookup"><span data-stu-id="354ff-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="354ff-183">Windows Mixed Reality поддерживает движения контроллеров в различных форм-факторов, дизайна каждый контроллер, отличающихся по отношению между положение руки пользователя и натуральный «переслать» направление этого приложения следует использовать для команды при подготовке к просмотру контроллер.</span><span class="sxs-lookup"><span data-stu-id="354ff-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="354ff-184">Чтобы лучше представить эти контроллеры, существует два вида можно выяснить, для каждого источника взаимодействия создает **поза захвата для изменения** и **поза указатель**.</span><span class="sxs-lookup"><span data-stu-id="354ff-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="354ff-185">Оба захвата для изменения поза и указатель поза координаты заданы все API-интерфейсами Unity в мировых координатах глобального Unity.</span><span class="sxs-lookup"><span data-stu-id="354ff-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="354ff-186">Поза захвата для изменения</span><span class="sxs-lookup"><span data-stu-id="354ff-186">Grip pose</span></span>

<span data-ttu-id="354ff-187">**Поза захвата для изменения** представляет расположение руку, обнаруживаемые HoloLens или palm, удерживая контроллером движения.</span><span class="sxs-lookup"><span data-stu-id="354ff-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="354ff-188">На иммерсивную, поза захвата для изменения лучше всего подходит для подготовки к просмотру **руку пользователя** или **объект содержится в руки пользователя**, например помехой или оружия.</span><span class="sxs-lookup"><span data-stu-id="354ff-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="354ff-189">Захват поза также используется, когда визуализация контроллером движения, как **отрисовываемые модели** предоставляемых по Windows для перемещения контроллер использует поза захвата для изменения в качестве его источника и центр вращения.</span><span class="sxs-lookup"><span data-stu-id="354ff-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="354ff-190">Захват поза определяется специально следующим образом:</span><span class="sxs-lookup"><span data-stu-id="354ff-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="354ff-191">**Возьмитесь за позиции**: Palm центроида при удержании контроллер, естественно, корректируется, влево или вправо, чтобы центрировать позиция в пределах захвата.</span><span class="sxs-lookup"><span data-stu-id="354ff-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="354ff-192">На контроллере Windows Mixed Reality движения этой позиции обычно выравнивает может воспользоваться кнопкой.</span><span class="sxs-lookup"><span data-stu-id="354ff-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="354ff-193">**Возьмитесь за правой оси в ориентации**: При открытии полностью свои силы для формирования позу плоских 5 палец, луч, является нормальным для вашей palm (вперед от левой palm назад от правой palm)</span><span class="sxs-lookup"><span data-stu-id="354ff-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="354ff-194">**Возьмитесь за ориентации на ось, направленная вперед**: При закрытии вашей руке частично (как будто держа контроллеру), луч, указывающий «forward» трубку, образованное пальцы отличных от бегунка.</span><span class="sxs-lookup"><span data-stu-id="354ff-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="354ff-195">**Возьмитесь за ориентации элемента вверх оси**: Ось вверх, право и прямого определения содержится в разрешении.</span><span class="sxs-lookup"><span data-stu-id="354ff-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="354ff-196">Для доступа к поза захвата для изменения входных данных между поставщиками либо Unity API (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) или через интерфейс API, специально Windows MR (*sourceState.sourcePose.TryGetPosition/Rotation*, запрос представлять данные для **захвата для изменения** узла).</span><span class="sxs-lookup"><span data-stu-id="354ff-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="354ff-197">Указатель поза</span><span class="sxs-lookup"><span data-stu-id="354ff-197">Pointer pose</span></span>

<span data-ttu-id="354ff-198">**Поза указатель** представляет собой кончик контроллера, указывающего вперед.</span><span class="sxs-lookup"><span data-stu-id="354ff-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="354ff-199">Поза системных указатель лучше использовать для raycast, когда вы будете **Подготовка к просмотру самой модели контроллера**.</span><span class="sxs-lookup"><span data-stu-id="354ff-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="354ff-200">При отрисовке другого виртуального объекта вместо контроллера, такие как виртуальные оружия, должна указывать с луч, наиболее удобный для этого виртуального объекта, например луч, проходит по barrel дулом заданное приложением модели.</span><span class="sxs-lookup"><span data-stu-id="354ff-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="354ff-201">Так как пользователи смогут просматривать виртуальным объектом и не физический контроллер, указывает с виртуальный объект будет более естественным для тех, с помощью приложения.</span><span class="sxs-lookup"><span data-stu-id="354ff-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="354ff-202">В настоящее время доступна в Unity только через интерфейс API, специально Windows MR, поза указатель *sourceState.sourcePose.TryGetPosition/Rotation*, передавая *InteractionSourceNode.Pointer* как аргумент.</span><span class="sxs-lookup"><span data-stu-id="354ff-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="354ff-203">Состояние отслеживания контроллера</span><span class="sxs-lookup"><span data-stu-id="354ff-203">Controller tracking state</span></span>

<span data-ttu-id="354ff-204">Например наушники контроллер движения Windows Mixed Reality не требует настройки внешних отслеживания датчиков.</span><span class="sxs-lookup"><span data-stu-id="354ff-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="354ff-205">Вместо этого контроллеры отслеживаются датчики в гарнитуры, сам.</span><span class="sxs-lookup"><span data-stu-id="354ff-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="354ff-206">Если пользователь перемещает контроллеров из поля зрения гарнитуры, в большинстве случаев Windows будет продолжать infer позиций контроллера и предоставлять их в приложение.</span><span class="sxs-lookup"><span data-stu-id="354ff-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="354ff-207">Когда контроллер потерял visual отслеживание достаточно, долго позиций контроллера приведет к удалению в положения приблизительное точность.</span><span class="sxs-lookup"><span data-stu-id="354ff-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="354ff-208">На этом этапе система будет текст с блокировкой на контроллере, чтобы пользователь, отслеживания положение пользователя по мере перемещения, во время по-прежнему предоставляя true ориентации контроллера с помощью датчиков его внутренней ориентации.</span><span class="sxs-lookup"><span data-stu-id="354ff-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="354ff-209">Многие приложения, использующие контроллеры указывали на и активировать элементы пользовательского интерфейса можно работать в обычном режиме в точности приблизительных без каких-пользователя.</span><span class="sxs-lookup"><span data-stu-id="354ff-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="354ff-210">Чтобы понять, для этого рекомендуется испытать их самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="354ff-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="354ff-211">Просмотрите этот видеоролик с примерами иммерсивных содержимого, которое работает с контроллерами движения для различных состояний для отслеживания:</span><span class="sxs-lookup"><span data-stu-id="354ff-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="354ff-212">Рассуждения о явно отслеживания состояния</span><span class="sxs-lookup"><span data-stu-id="354ff-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="354ff-213">Приложения, которые желают обрабатывать позиций, иначе, основываясь на отслеживание состояния может пойти дальше и проверять состояние контроллера на свойства, например *SourceLossRisk* и *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="354ff-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="354ff-214">Отслеживание состояния</span><span class="sxs-lookup"><span data-stu-id="354ff-214">Tracking state</span></span> </th><th> <span data-ttu-id="354ff-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="354ff-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="354ff-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="354ff-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="354ff-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="354ff-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="354ff-218"><b>Высокая точность</b> </span><span class="sxs-lookup"><span data-stu-id="354ff-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="354ff-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="354ff-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="354ff-220">Высокий</span><span class="sxs-lookup"><span data-stu-id="354ff-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="354ff-221">true</span><span class="sxs-lookup"><span data-stu-id="354ff-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-222"><b>Высокая точность (риску потери)</b> </span><span class="sxs-lookup"><span data-stu-id="354ff-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="354ff-223">== 1.0</span><span class="sxs-lookup"><span data-stu-id="354ff-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="354ff-224">Высокий</span><span class="sxs-lookup"><span data-stu-id="354ff-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="354ff-225">true</span><span class="sxs-lookup"><span data-stu-id="354ff-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-226"><b>Точность приблизительных</b> </span><span class="sxs-lookup"><span data-stu-id="354ff-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="354ff-227">== 1.0</span><span class="sxs-lookup"><span data-stu-id="354ff-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="354ff-228">Приблизительна</span><span class="sxs-lookup"><span data-stu-id="354ff-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="354ff-229">true</span><span class="sxs-lookup"><span data-stu-id="354ff-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="354ff-230"><b>Позиция не</b> </span><span class="sxs-lookup"><span data-stu-id="354ff-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="354ff-231">== 1.0</span><span class="sxs-lookup"><span data-stu-id="354ff-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="354ff-232">Приблизительна</span><span class="sxs-lookup"><span data-stu-id="354ff-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="354ff-233">false</span><span class="sxs-lookup"><span data-stu-id="354ff-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="354ff-234">Эти состояния отслеживания контроллера движения, определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="354ff-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="354ff-235">**Высокая точность:** Когда движения контроллер находится в пределах гарнитура поле зрения, он предоставит обычно позиций, высокой точности, основываясь на visual отслеживания.</span><span class="sxs-lookup"><span data-stu-id="354ff-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="354ff-236">Обратите внимание, что перемещение контроллера, сразу же оставляет поле зрения или закрывается сразу же датчиков Гарнитура (например, пользователей с другой стороны) продолжит возвращать создает высокой точности на короткое время, в зависимости от инерционного отслеживания контроллера сам.</span><span class="sxs-lookup"><span data-stu-id="354ff-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="354ff-237">**Высокая точность (риску потери):** При перемещении контроллера движения за край поле зрения гарнитуры, гарнитура скоро будет может визуально отслеживать положение контроллера.</span><span class="sxs-lookup"><span data-stu-id="354ff-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="354ff-238">Приложение знает, когда контроллер достиг эту FOV границу, достаточно **SourceLossRisk** достичь 1.0.</span><span class="sxs-lookup"><span data-stu-id="354ff-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="354ff-239">На этом этапе приложение можно приостановить контроллера жесты, требующих устойчивый поток создает очень высокого качества.</span><span class="sxs-lookup"><span data-stu-id="354ff-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="354ff-240">**Точность приблизительных:** Когда контроллер потерял visual отслеживание достаточно, долго позиций контроллера приведет к удалению в положения приблизительное точность.</span><span class="sxs-lookup"><span data-stu-id="354ff-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="354ff-241">На этом этапе система будет текст с блокировкой на контроллере, чтобы пользователь, отслеживания положение пользователя по мере перемещения, во время по-прежнему предоставляя true ориентации контроллера с помощью датчиков его внутренней ориентации.</span><span class="sxs-lookup"><span data-stu-id="354ff-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="354ff-242">Многие приложения, использующие контроллеры указывали на и активировать элементы пользовательского интерфейса может работать как обычный while в точности приблизительных без каких-пользователя.</span><span class="sxs-lookup"><span data-stu-id="354ff-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="354ff-243">Приложений с помощью более дешевые требования к входным данным, можно находить спад из **высокой** точность до одной **приблизительно** точности, проверяя **PositionAccuracy** свойство, для Пример для предоставления пользователю более масштабны hitbox на целевые объекты вне экрана в течение этого времени.</span><span class="sxs-lookup"><span data-stu-id="354ff-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="354ff-244">**Позиция не:** Пока контроллер может работать в точности приблизительных в течение длительного времени, иногда система знает, что даже позицию заблокирован для текста не имеет смысла в данный момент.</span><span class="sxs-lookup"><span data-stu-id="354ff-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="354ff-245">Например контроллер, который просто был включен может никогда не наблюдались визуально или пользователь может поместить работу контроллера, который затем передается другим пользователем.</span><span class="sxs-lookup"><span data-stu-id="354ff-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="354ff-246">В эти моменты времени, система не будет предоставлять любой позиции в приложение и *TryGetPosition* возвратит значение false.</span><span class="sxs-lookup"><span data-stu-id="354ff-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="354ff-247">Общие интерфейсы API Unity (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="354ff-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="354ff-248">**Пространство имен:** *UnityEngine*, *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="354ff-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="354ff-249">**Типы**: *Входные данные*, *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="354ff-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="354ff-250">Unity в настоящее время использует общего *Input.GetButton/Input.GetAxis* API-интерфейсы для предоставления входных данных для [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) и смешанной реальности Windows, включая руки и контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="354ff-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="354ff-251">Если ваше приложение использует эти API-интерфейсы для входных данных, его можно легко поддерживать контроллеры движения нескольких пакетов SDK XR, в том числе Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="354ff-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="354ff-252">Получение логического кнопка нажата</span><span class="sxs-lookup"><span data-stu-id="354ff-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="354ff-253">Чтобы использовать общие интерфейсам API ввода Unity, вы обычно начнем с подключения кнопки и осей для логические имена в [диспетчер ввода Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), привязка к имени каждой кнопки или оси идентификаторы.</span><span class="sxs-lookup"><span data-stu-id="354ff-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="354ff-254">Затем можно написать код, который ссылается на это имя логического кнопку/оси.</span><span class="sxs-lookup"><span data-stu-id="354ff-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="354ff-255">Например, чтобы сопоставить кнопка слева движения контроллера триггера действие отправки, перейдите к **изменить > Параметры проекта > ввода** в Unity и разверните свойства разделе отправить осей.</span><span class="sxs-lookup"><span data-stu-id="354ff-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="354ff-256">Изменение **положительным кнопку** или **положительное кнопку Alt** свойство для чтения **кнопку джойстика 14**, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="354ff-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="354ff-257">![Unity InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="354ff-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="354ff-258">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="354ff-258">*Unity InputManager*</span></span>

<span data-ttu-id="354ff-259">Скрипт затем можно установить флажок для действия отправки с помощью *Input.GetButton*:</span><span class="sxs-lookup"><span data-stu-id="354ff-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="354ff-260">Можно добавить более логичным кнопки, изменив **размер** свойства в разделе **осей**.</span><span class="sxs-lookup"><span data-stu-id="354ff-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="354ff-261">Начало физической кнопки нажаты напрямую</span><span class="sxs-lookup"><span data-stu-id="354ff-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="354ff-262">Можно также открыть кнопки вручную, их полное доменное имя, используя *Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="354ff-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="354ff-263">Получение руки или поза движения контроллера</span><span class="sxs-lookup"><span data-stu-id="354ff-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="354ff-264">Можно получить доступ к положения и поворота контроллера, с помощью *XR. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="354ff-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="354ff-265">Обратите внимание, что это относится к поза захвата для изменения контроллера (когда пользователь удерживает контроллеру), что полезно для подготовки к просмотру помехой или дулом в пользователя вручную, или модель сам контроллер.</span><span class="sxs-lookup"><span data-stu-id="354ff-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="354ff-266">Обратите внимание на то, что связь между этой поза захвата для изменения и позу указатель (куда указывает кончика контроллеру), могут отличаться между контроллерами.</span><span class="sxs-lookup"><span data-stu-id="354ff-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="354ff-267">В данный момент доступ к поза указателя контроллера можно только посредством ввода MR конкретных API, описанные в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="354ff-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="354ff-268">Windows API-интерфейсам конкретной (XR. WSA. Входные данные)</span><span class="sxs-lookup"><span data-stu-id="354ff-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="354ff-269">**Пространство имен:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="354ff-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="354ff-270">**Типы**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*,  *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="354ff-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="354ff-271">Чтобы получить более подробные сведения о наличии входных данных в Windows Mixed Reality (для HoloLens) и контроллеры движения, вы можете использовать Windows пространственных входной API-интерфейсам конкретной в разделе *UnityEngine.XR.WSA.Input* пространства имен.</span><span class="sxs-lookup"><span data-stu-id="354ff-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="354ff-272">Это позволяет получить доступ к Дополнительные сведения, например положение точности или вид источника, позволяя определить руки и контроллеры друг от друга.</span><span class="sxs-lookup"><span data-stu-id="354ff-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="354ff-273">Опрос состояния руки и контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="354ff-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="354ff-274">Можно выполнить опрос для этого кадра состояния для каждого источника (вручную или движения контроллер) взаимодействия с помощью *GetCurrentReading* метод.</span><span class="sxs-lookup"><span data-stu-id="354ff-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="354ff-275">Каждый *InteractionSourceState* вы получаете назад представляет источник взаимодействия в текущий момент времени.</span><span class="sxs-lookup"><span data-stu-id="354ff-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="354ff-276">*InteractionSourceState* предоставляет сведения, такие как:</span><span class="sxs-lookup"><span data-stu-id="354ff-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="354ff-277">Который [виды нажатия](motion-controllers.md) происходят (Select/меню/коммерческих тайн/сенсорной панели/джойстик)</span><span class="sxs-lookup"><span data-stu-id="354ff-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="354ff-278">Другие данные, относящиеся к движения контроллеров, такие сенсорной панели и/или джойстик координатами x и y и изменять состояние</span><span class="sxs-lookup"><span data-stu-id="354ff-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="354ff-279">InteractionSourceKind знать, если источником является руки или контроллер движения</span><span class="sxs-lookup"><span data-stu-id="354ff-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="354ff-280">Запрос создает прогноз вперед отрисовки</span><span class="sxs-lookup"><span data-stu-id="354ff-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="354ff-281">При опросе с целью взаимодействия исходных данных от руки и контроллеры, создает, которые можно получить, создает прогноз вперед в данный момент времени, когда этого кадра photons достигнет глаза пользователя.</span><span class="sxs-lookup"><span data-stu-id="354ff-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="354ff-282">Создает эти прогнозируемые вперед лучше всего подходят для **отрисовки** контроллера или принудительное объекта каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="354ff-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="354ff-283">Предназначенные для заданного press или выпуска с контроллером, которые будут наиболее точным, если вы используете событие журнала API, описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="354ff-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="354ff-284">Также можно получить головной поза, прогнозируемые вперед для этого текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="354ff-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="354ff-285">Как с помощью источника поза, это полезно для **отрисовки** a курсора, несмотря на то, что приложение предназначено для заданного press или выпуска будет наиболее точным, если вы используете событие журнала API, описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="354ff-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="354ff-286">Обработка событий источника взаимодействия</span><span class="sxs-lookup"><span data-stu-id="354ff-286">Handling interaction source events</span></span>

<span data-ttu-id="354ff-287">Для обработки входных событий, происходящих с их точным поза исторических данных, можно обрабатывать события источника взаимодействия вместо опроса.</span><span class="sxs-lookup"><span data-stu-id="354ff-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="354ff-288">Для обработки взаимодействия источника событий:</span><span class="sxs-lookup"><span data-stu-id="354ff-288">To handle interaction source events:</span></span>
* <span data-ttu-id="354ff-289">Зарегистрируйтесь для *InteractionManager* входного события.</span><span class="sxs-lookup"><span data-stu-id="354ff-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="354ff-290">Для каждого типа событий взаимодействия, которые вас интересуют необходимо подписаться на него.</span><span class="sxs-lookup"><span data-stu-id="354ff-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="354ff-291">Обработайте событие.</span><span class="sxs-lookup"><span data-stu-id="354ff-291">Handle the event.</span></span> <span data-ttu-id="354ff-292">Как только вы подписаны на события взаимодействия, вы получите обратного вызова, когда это необходимо.</span><span class="sxs-lookup"><span data-stu-id="354ff-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="354ff-293">В *SourcePressed* примере это будет после был обнаружен источник, и до выпуска или потеряно.</span><span class="sxs-lookup"><span data-stu-id="354ff-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="354ff-294">Остановка обработки события</span><span class="sxs-lookup"><span data-stu-id="354ff-294">How to stop handling an event</span></span>

<span data-ttu-id="354ff-295">Необходимо остановить обработку событие, когда вы больше не интересует события или уничтожается объект, который подписался на событие.</span><span class="sxs-lookup"><span data-stu-id="354ff-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="354ff-296">Для остановки обработки события, можно отменить подписку на событие.</span><span class="sxs-lookup"><span data-stu-id="354ff-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="354ff-297">Список событий источника взаимодействия</span><span class="sxs-lookup"><span data-stu-id="354ff-297">List of interaction source events</span></span>

<span data-ttu-id="354ff-298">Возможное взаимодействие источника события включают:</span><span class="sxs-lookup"><span data-stu-id="354ff-298">The available interaction source events are:</span></span>
* <span data-ttu-id="354ff-299">*InteractionSourceDetected* (источник становится активным)</span><span class="sxs-lookup"><span data-stu-id="354ff-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="354ff-300">*InteractionSourceLost* (становится неактивным)</span><span class="sxs-lookup"><span data-stu-id="354ff-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="354ff-301">*InteractionSourcePressed* (tap, нажатие кнопки или «Выберите» распространенная)</span><span class="sxs-lookup"><span data-stu-id="354ff-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="354ff-302">*InteractionSourceReleased* (конец tap, кнопка или конец «Выбрать» распространенная)</span><span class="sxs-lookup"><span data-stu-id="354ff-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="354ff-303">*InteractionSourceUpdated* (перемещение или в противном случае изменения определенного состояния)</span><span class="sxs-lookup"><span data-stu-id="354ff-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="354ff-304">События для исторических создает выбора целевой платформы, которые наиболее точно соответствуют press или выпуска</span><span class="sxs-lookup"><span data-stu-id="354ff-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="354ff-305">Опрос API, описанные ранее Присвойте приложению создает прогноз вперед.</span><span class="sxs-lookup"><span data-stu-id="354ff-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="354ff-306">Хотя эти прогнозируемое создает лучше всего подходят для подготовки к просмотру контроллера или виртуальный объект handheld, будущих создает не являются оптимальными для нацеливания, по двум основным причинам:</span><span class="sxs-lookup"><span data-stu-id="354ff-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="354ff-307">Когда пользователь нажимает кнопку на контроллере, может быть около 20 мс задержки беспроводной через Bluetooth прежде, чем система получает клавишу.</span><span class="sxs-lookup"><span data-stu-id="354ff-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="354ff-308">Затем, если вы используете позу прогнозируемые вперед, существует другой 10-20 мс прямой прогноза применялся к целевое время, когда текущий кадр photons достигнет глаза пользователя.</span><span class="sxs-lookup"><span data-stu-id="354ff-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="354ff-309">Это означает, что опроса дает позу источника или head представляют то есть 30-40 мс вперед от head и руки пользователя фактически зависимостью обратно в том случае, когда произошло press или выпуска.</span><span class="sxs-lookup"><span data-stu-id="354ff-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="354ff-310">HoloLens входных данных вручную хотя без задержки беспроводной передачи есть аналогичные задержки для обнаружения нажатия.</span><span class="sxs-lookup"><span data-stu-id="354ff-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="354ff-311">Чтобы точно целевой объект на основании исходное намерение пользователя для нажатие вручную или контроллера, следует использовать поза исторических источника или головного поза, *InteractionSourcePressed* или *InteractionSourceReleased* входного события.</span><span class="sxs-lookup"><span data-stu-id="354ff-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="354ff-312">Вы можете целевой пресс или выпуска с поза исторические данные из головы пользователя или свой контроллер:</span><span class="sxs-lookup"><span data-stu-id="354ff-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="354ff-313">Произошла головной поза на данный момент времени, когда жест или контроллера нажмите клавишу, который может использоваться для **нацеливания** для определения того, что пользователь выполнял [gazing](gaze.md) в:</span><span class="sxs-lookup"><span data-stu-id="354ff-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="354ff-314">Произошла поза источника на момент времени, при контроллером движения клавиши, который может использоваться для **нацеливания** для определения того, что пользователь указывал на контроллер.</span><span class="sxs-lookup"><span data-stu-id="354ff-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="354ff-315">Это будет состояние контроллера, в которых прессе.</span><span class="sxs-lookup"><span data-stu-id="354ff-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="354ff-316">При отрисовке сам контроллер, вы можете запросить поза указатель, а не поза захвата для изменения, прострелить нацеливания лучом, проведенным из что пользователь сочтет естественным кончика, подготовке к просмотру контроллера:</span><span class="sxs-lookup"><span data-stu-id="354ff-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="354ff-317">Пример обработчики событий</span><span class="sxs-lookup"><span data-stu-id="354ff-317">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="354ff-318">Высокоуровневые составного жест API-интерфейсы (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="354ff-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="354ff-319">**Пространство имен:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="354ff-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="354ff-320">**Типы**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="354ff-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="354ff-321">Приложение также может распознавать более высокого уровня составные жесты для пространственных источников входных данных, касание, удержание, управления и навигации жестов.</span><span class="sxs-lookup"><span data-stu-id="354ff-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="354ff-322">В обоих сценариях можно распознать эти составные жесты [руки](gestures.md) и [движения контроллеров](motion-controllers.md) с помощью GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="354ff-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="354ff-323">Каждое событие жестов на GestureRecognizer предоставляет SourceKind для входных данных, а также определения луч головного во время события.</span><span class="sxs-lookup"><span data-stu-id="354ff-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="354ff-324">Некоторые события предоставляют дополнительные определенные сведения о контексте.</span><span class="sxs-lookup"><span data-stu-id="354ff-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="354ff-325">Существует лишь несколько действий, необходимых для записи с помощью распознавателя жестов:</span><span class="sxs-lookup"><span data-stu-id="354ff-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="354ff-326">Создать новый распознаватель жестов</span><span class="sxs-lookup"><span data-stu-id="354ff-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="354ff-327">Укажите, какие "действия" для отслеживания</span><span class="sxs-lookup"><span data-stu-id="354ff-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="354ff-328">Подписаться на события для этих жестов</span><span class="sxs-lookup"><span data-stu-id="354ff-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="354ff-329">Начать захват жесты</span><span class="sxs-lookup"><span data-stu-id="354ff-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="354ff-330">Создать новый распознаватель жестов</span><span class="sxs-lookup"><span data-stu-id="354ff-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="354ff-331">Чтобы использовать *GestureRecognizer*, необходимо создать *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="354ff-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="354ff-332">Укажите, какие "действия" для отслеживания</span><span class="sxs-lookup"><span data-stu-id="354ff-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="354ff-333">Укажите, какие "действия" вы заинтересованы в через *SetRecognizableGestures()*:</span><span class="sxs-lookup"><span data-stu-id="354ff-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="354ff-334">Подписаться на события для этих жестов</span><span class="sxs-lookup"><span data-stu-id="354ff-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="354ff-335">Подписаться на события для жестов, которые вас интересуют.</span><span class="sxs-lookup"><span data-stu-id="354ff-335">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="354ff-336">Жесты перехода и обработки являются взаимоисключающими для экземпляра *GestureRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="354ff-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="354ff-337">Начать захват жесты</span><span class="sxs-lookup"><span data-stu-id="354ff-337">Start capturing gestures</span></span>

<span data-ttu-id="354ff-338">По умолчанию *GestureRecognizer* не отслеживает входных данных до *StartCapturingGestures()* вызывается.</span><span class="sxs-lookup"><span data-stu-id="354ff-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="354ff-339">Возможно, что событие жест может быть сформировано после *StopCapturingGestures()* вызывается, если входные данные была создана до кадра где *StopCapturingGestures()* был обработан.</span><span class="sxs-lookup"><span data-stu-id="354ff-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="354ff-340">*GestureRecognizer* запоминают ли было включить или отключить во время previou кадра, в котором жест действительно выполнены и таким образом надежен, для запуска и остановки мониторинга жест с использованием нацеливания взглядом этого кадра.</span><span class="sxs-lookup"><span data-stu-id="354ff-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="354ff-341">Остановка отслеживания жесты</span><span class="sxs-lookup"><span data-stu-id="354ff-341">Stop capturing gestures</span></span>

<span data-ttu-id="354ff-342">Чтобы остановить распознавания жестов:</span><span class="sxs-lookup"><span data-stu-id="354ff-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="354ff-343">Удаление распознаватель жестов</span><span class="sxs-lookup"><span data-stu-id="354ff-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="354ff-344">Не забудьте отменить подписку на события подписки перед удалением *GestureRecognizer* объекта.</span><span class="sxs-lookup"><span data-stu-id="354ff-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="354ff-345">Подготовка к просмотру модели контроллера движения в Unity</span><span class="sxs-lookup"><span data-stu-id="354ff-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="354ff-346">![Модель контроллера движения и teleportation](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="354ff-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="354ff-347">*Модель контроллера движения и teleportation*</span><span class="sxs-lookup"><span data-stu-id="354ff-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="354ff-348">Для подготовки к просмотру движения контроллеров в приложении, которые соответствуют физических контроллеров пользователей удерживают и сформулировать, как различные кнопки, можно использовать **MotionController prefab** в [смешанной реальности Toolkit ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="354ff-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="354ff-349">Этого готового блока динамически загружает правильные glTF модели во время выполнения из драйвера контроллера установленных движения системы.</span><span class="sxs-lookup"><span data-stu-id="354ff-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="354ff-350">Очень важно для динамической загрузки этих моделей, а не импортируя их вручную в редакторе, что приложение будет отображать физически точные трехмерные модели какие-либо контроллеры, текущие и будущие пользователи могут иметь.</span><span class="sxs-lookup"><span data-stu-id="354ff-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="354ff-351">Выполните [Приступая к работе](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) инструкции по загрузке смешанной реальности Toolkit и добавьте его в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="354ff-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="354ff-352">Если Вы заменили камеры с *MixedRealityCameraParent* prefab как часть действия Приступая к работе, вы готовы к работе!</span><span class="sxs-lookup"><span data-stu-id="354ff-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="354ff-353">Этого готового блока включает отрисовки контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="354ff-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="354ff-354">В противном случае добавьте *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* сцены из области проекта.</span><span class="sxs-lookup"><span data-stu-id="354ff-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="354ff-355">Необходимо добавить как дочерний независимо от родительского объекта prefab использовать для перемещения камеры вокруг при teleports пользователя внутри сцены, таким образом, чтобы контроллеры поставляются вместе с пользователем.</span><span class="sxs-lookup"><span data-stu-id="354ff-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="354ff-356">Если приложение не включает teleporting, просто добавьте готового блока в корне сцены.</span><span class="sxs-lookup"><span data-stu-id="354ff-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="354ff-357">Создание объектов</span><span class="sxs-lookup"><span data-stu-id="354ff-357">Throwing objects</span></span>

<span data-ttu-id="354ff-358">Создание объектов в виртуальной реальности проблема сложнее, а затем может поначалу показаться.</span><span class="sxs-lookup"><span data-stu-id="354ff-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="354ff-359">Как и в случае с наиболее физически на основе взаимодействия, при генерации в игры действует непредвиденным образом, он совершенно очевидно и разбивает погружения.</span><span class="sxs-lookup"><span data-stu-id="354ff-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="354ff-360">Мы потратили некоторое времени на размышления глубоко о том, как для представления физически правильное поведение создает исключение и получили рекомендации, с помощью обновления нашей платформы, который мы хотели бы поделиться с вами.</span><span class="sxs-lookup"><span data-stu-id="354ff-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="354ff-361">Вы найдете пример как корпорация Майкрософт рекомендует реализовать генерации [здесь](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="354ff-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="354ff-362">Этот пример эти четыре рекомендации:</span><span class="sxs-lookup"><span data-stu-id="354ff-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="354ff-363">**Использование контроллера *скорости* вместо позиции**.</span><span class="sxs-lookup"><span data-stu-id="354ff-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="354ff-364">В ноябрьском обновлении для Windows, мы представили изменение в поведении при работе в ['' приблизительное '' позиционные отслеживания состояния](motion-controllers.md#controller-tracking-state).</span><span class="sxs-lookup"><span data-stu-id="354ff-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="354ff-365">В этом состоянии скорости сведения о контроллере продолжит возвращаются до тех пор, пока мы считаем, что он является высокая точность, это часто бывает больше времени, чем позиция остается высокой точности.</span><span class="sxs-lookup"><span data-stu-id="354ff-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="354ff-366">**Включить *угловую скорость* контроллера**.</span><span class="sxs-lookup"><span data-stu-id="354ff-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="354ff-367">Эта логика находится в `throwing.cs` файл `GetThrownObjectVelAngVel` статический метод, в пакете ссылки выше:</span><span class="sxs-lookup"><span data-stu-id="354ff-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="354ff-368">Как угловую скорость сэкономленная, созданный объект должен поддерживать же угловую скорость, как оно было в момент, когда исключение: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="354ff-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="354ff-369">Как центру массы вызванного объекта, вероятно, не в начале координат поза захвата для изменения, Да, скорее всего различные скорости то контроллера в отсчета пользователя.</span><span class="sxs-lookup"><span data-stu-id="354ff-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="354ff-370">Часть объекта скорости, использованных в этом случае является мгновенно тоже скорость центру массы вызванного объекта вокруг начала координат контроллера.</span><span class="sxs-lookup"><span data-stu-id="354ff-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="354ff-371">Это тоже скорость составляет перекрестное произведение угловую скорость контроллера с помощью вектора, представляющего расстояние между контроллера-источником и центру массы созданный объект.</span><span class="sxs-lookup"><span data-stu-id="354ff-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="354ff-372">Общая скорость вызванного объекта, таким образом, сумма скорости контроллера и это тоже скорость: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="354ff-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="354ff-373">**Обратите внимание на *время* по которому мы применяем скорость**.</span><span class="sxs-lookup"><span data-stu-id="354ff-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="354ff-374">При нажатии кнопки, может занять до 20 мс для этого события всплывать через Bluetooth в операционную систему.</span><span class="sxs-lookup"><span data-stu-id="354ff-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="354ff-375">Это означает, что если опрос для изменения состояния контроллера из клавиш для не нажата или наоборот, сведения о контроллере поза, получаемых с ним будет заранее это изменение в состоянии.</span><span class="sxs-lookup"><span data-stu-id="354ff-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="354ff-376">Кроме того поза контроллера, представленный наших опроса API вперед вычисляется в соответствии с вероятностью поза во время отображения кадр, что в будущем может быть более 20 мс, затем.</span><span class="sxs-lookup"><span data-stu-id="354ff-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="354ff-377">Это хороший вариант для *отрисовки* сохраняться объекты, но приводит к увеличению наша проблема времени для *нацеливания* объект как мы вычисляем траектория в данный момент пользователь отпустил их throw.</span><span class="sxs-lookup"><span data-stu-id="354ff-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="354ff-378">К счастью, с ноябрьского обновления, когда события Unity, например *InteractionSourcePressed* или *InteractionSourceReleased* отправляется, в том числе поза исторические данные от обратно, когда кнопки был фактически нажатом или выпущенные.</span><span class="sxs-lookup"><span data-stu-id="354ff-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="354ff-379">Чтобы получить наиболее точные визуализации контроллера и предназначенных для контроллера во время создает исключение, необходимо правильно использовать опроса и обработки событий, соответствующим образом:</span><span class="sxs-lookup"><span data-stu-id="354ff-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="354ff-380">Для **отрисовки контроллера** каждого кадра, приложения следует располагать контроллера *GameObject* на контроллере прогнозируемые вперед представлять время photon текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="354ff-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="354ff-381">Получить данные из Unity опроса API, такими как *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* или  *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="354ff-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="354ff-382">Для **нацеливания контроллера** по press или выпуска, ваше приложение должно raycast и вычислить траекторий, в зависимости от поза исторических контроллера для данного события, нажмите клавишу "или" выпуск.</span><span class="sxs-lookup"><span data-stu-id="354ff-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="354ff-383">Получить данные из событий Unity API-интерфейсы, такие как  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span><span class="sxs-lookup"><span data-stu-id="354ff-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="354ff-384">**Использовать поза захвата для изменения**.</span><span class="sxs-lookup"><span data-stu-id="354ff-384">**Use the grip pose**.</span></span> <span data-ttu-id="354ff-385">Относительно поза захвата для изменения, а не указатель поза выводятся угловую скорость и скорости.</span><span class="sxs-lookup"><span data-stu-id="354ff-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="354ff-386">Генерация будет продолжать улучшать в последующих обновлениях Windows, и вы сможете найти дополнительную информацию о них здесь.</span><span class="sxs-lookup"><span data-stu-id="354ff-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="accelerate-development-with-mixed-reality-toolkit"></a><span data-ttu-id="354ff-387">Ускорение разработки с помощью смешанной реальности Toolkit</span><span class="sxs-lookup"><span data-stu-id="354ff-387">Accelerate development with Mixed Reality Toolkit</span></span>

<span data-ttu-id="354ff-388">Существуют две сцены пример о InputManager и MotionController в Unity.</span><span class="sxs-lookup"><span data-stu-id="354ff-388">There are two example scenes about InputManager and MotionController in Unity.</span></span> <span data-ttu-id="354ff-389">Через эти сцен рассказывается, как InputManager MRTK доступ к данных обработки событий с помощью кнопок перемещения контроллера.</span><span class="sxs-lookup"><span data-stu-id="354ff-389">Through these scenes, you can learn how to use MRTK's InputManager and access data handle events from the motion controller buttons.</span></span>

- [<span data-ttu-id="354ff-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="354ff-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [<span data-ttu-id="354ff-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span><span class="sxs-lookup"><span data-stu-id="354ff-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [<span data-ttu-id="354ff-392">Технические сведения в файле README</span><span class="sxs-lookup"><span data-stu-id="354ff-392">Technical details README File</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

<span data-ttu-id="354ff-393">![Пример входных данных сцен в MRTK](images/MRTK_ExampleScene_Input.png)</span><span class="sxs-lookup"><span data-stu-id="354ff-393">![Input example scenes in MRTK](images/MRTK_ExampleScene_Input.png)</span></span><br>
<span data-ttu-id="354ff-394">*Пример входных данных сцен в MRTK*</span><span class="sxs-lookup"><span data-stu-id="354ff-394">*Input example scenes in MRTK*</span></span>

### <a name="automatic-scene-setup"></a><span data-ttu-id="354ff-395">Настройка автоматического сцены</span><span class="sxs-lookup"><span data-stu-id="354ff-395">Automatic scene setup</span></span>

<span data-ttu-id="354ff-396">При импорте [Unity пакеты выпуска MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) или клонируйте проект со страницы [репозиторий GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), нужно найти новое меню «Смешанной реальности Toolkit» в Unity.</span><span class="sxs-lookup"><span data-stu-id="354ff-396">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="354ff-397">В меню «Настройка» вы увидите меню «Применить смешанной реальности сцены параметры».</span><span class="sxs-lookup"><span data-stu-id="354ff-397">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="354ff-398">Если щелкнуть его, он удаляет камеры по умолчанию и добавляет основных компонентов — [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), и [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span><span class="sxs-lookup"><span data-stu-id="354ff-398">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="354ff-399">![Меню MRTK для установки сцены](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="354ff-399">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="354ff-400">*Меню MRTK для установки сцены*</span><span class="sxs-lookup"><span data-stu-id="354ff-400">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="354ff-401">![Настройка автоматического сцены в MRTK](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="354ff-401">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="354ff-402">*Настройка автоматического сцены в MRTK*</span><span class="sxs-lookup"><span data-stu-id="354ff-402">*Automatic scene setup in MRTK*</span></span>

### <a name="mixedrealitycamera-prefab"></a><span data-ttu-id="354ff-403">MixedRealityCamera prefab</span><span class="sxs-lookup"><span data-stu-id="354ff-403">MixedRealityCamera prefab</span></span>

<span data-ttu-id="354ff-404">Их можно также вручную добавить из панели «проект».</span><span class="sxs-lookup"><span data-stu-id="354ff-404">You can also manually add these from the project panel.</span></span> <span data-ttu-id="354ff-405">Эти компоненты можно найти как prefabs.</span><span class="sxs-lookup"><span data-stu-id="354ff-405">You can find these components as prefabs.</span></span> <span data-ttu-id="354ff-406">При поиске **MixedRealityCamera**, можно увидеть два различных камеры prefabs.</span><span class="sxs-lookup"><span data-stu-id="354ff-406">When you search **MixedRealityCamera**, you will be able to see two different camera prefabs.</span></span> <span data-ttu-id="354ff-407">Разница в том, **MixedRealityCamera** только в том случае камеры prefab в то время как **MixedRealityCameraParent** включает дополнительные компоненты для иммерсивную, например Teleportation движения Контроллер и границ.</span><span class="sxs-lookup"><span data-stu-id="354ff-407">The difference is, **MixedRealityCamera** is the camera only prefab whereas, **MixedRealityCameraParent** includes additional components for the immersive headsets such as Teleportation, Motion Controller and, Boundary.</span></span>

<span data-ttu-id="354ff-408">![Плоскости камеры MRTK](images/MRTK_HowTo_Input2.png)</span><span class="sxs-lookup"><span data-stu-id="354ff-408">![Camera prefabs in MRTK](images/MRTK_HowTo_Input2.png)</span></span><br>
<span data-ttu-id="354ff-409">*Плоскости камеры MRTK*</span><span class="sxs-lookup"><span data-stu-id="354ff-409">*Camera prefabs in MRTK*</span></span>

<span data-ttu-id="354ff-410">**MixedRealtyCamera** поддерживает HoloLens и иммерсивных гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="354ff-410">**MixedRealtyCamera** supports both HoloLens and immersive headset.</span></span> <span data-ttu-id="354ff-411">Он определяет тип устройства и оптимизирует такие свойства как очистить флаги и Skybox.</span><span class="sxs-lookup"><span data-stu-id="354ff-411">It detects the device type and optimizes the properties such as clear flags and Skybox.</span></span> <span data-ttu-id="354ff-412">Далее представлены некоторые полезные свойства можно настроить, например пользовательский курсор, контроллер движения модели и Floor.</span><span class="sxs-lookup"><span data-stu-id="354ff-412">Below you can find some of the useful properties you can customize such as custom Cursor, Motion Controller models, and Floor.</span></span>

<span data-ttu-id="354ff-413">![Свойства для контроллера движения курсора и Floor](images/MRTK_HowTo_Input3.png)</span><span class="sxs-lookup"><span data-stu-id="354ff-413">![Properties for the Motion controller, Cursor and Floor](images/MRTK_HowTo_Input3.png)</span></span><br>
<span data-ttu-id="354ff-414">*Свойства для контроллера движения курсора и Floor*</span><span class="sxs-lookup"><span data-stu-id="354ff-414">*Properties for the Motion controller, Cursor and Floor*</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="354ff-415">Следуйте указаниям, разрабатывая учебники</span><span class="sxs-lookup"><span data-stu-id="354ff-415">Follow along with tutorials</span></span>

<span data-ttu-id="354ff-416">Пошаговые руководства с более подробные Примеры настроек, доступны в академии реальности Mixed:</span><span class="sxs-lookup"><span data-stu-id="354ff-416">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="354ff-417">Входные данные MR 211: Жест</span><span class="sxs-lookup"><span data-stu-id="354ff-417">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="354ff-418">Входные данные MR 213: Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="354ff-418">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="354ff-419">[![Г-н ввода 213 - контроллера движения](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="354ff-419">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="354ff-420">*Г-н ввода 213 - контроллера движения*</span><span class="sxs-lookup"><span data-stu-id="354ff-420">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="354ff-421">См. также</span><span class="sxs-lookup"><span data-stu-id="354ff-421">See also</span></span>

* [<span data-ttu-id="354ff-422">Жесты</span><span class="sxs-lookup"><span data-stu-id="354ff-422">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="354ff-423">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="354ff-423">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="354ff-424">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="354ff-424">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="354ff-425">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="354ff-425">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="354ff-426">InteractionInputSource.cs в MixedRealityToolkit Unity</span><span class="sxs-lookup"><span data-stu-id="354ff-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
