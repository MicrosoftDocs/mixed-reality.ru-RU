---
title: Жесты и контроллеры движения в Unity
description: Существует два основных способа выполнения действий с вашим взглядом в Unity, жестами и контроллерами движения.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: жесты, контроллеры движения, Unity, взгляд, входные данные
ms.openlocfilehash: a85797bfb443f33147c116e90a02c88abda63c67
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375651"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="7e5d5-104">Жесты и контроллеры движения в Unity</span><span class="sxs-lookup"><span data-stu-id="7e5d5-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="7e5d5-105">Существует два основных способа выполнения действий с вашим [взглядом в Unity](gaze-in-unity.md), [жестами](gaze-and-commit.md#composite-gestures) и [контроллерами движения](motion-controllers.md) в HoloLens и иммерсивное ХМД.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gaze-and-commit.md#composite-gestures) and [motion controllers](motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="7e5d5-106">Доступ к данным для обоих источников пространственных данных осуществляется через одни и те же API в Unity.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="7e5d5-107">Unity предоставляет два основных способа доступа к пространственным входным данным для Windows Mixed Reality, общих *входных и входных API-интерфейсов input.* XR, работающих в нескольких пакетах SDK для Unity, и API *интерактионманажер/GestureRecognizer* , относящийся к Windows Mixed Reality, который предоставляет полный набор пространственных входных данных.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="7e5d5-108">Таблица сопоставления кнопок и осей Unity</span><span class="sxs-lookup"><span data-stu-id="7e5d5-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="7e5d5-109">Идентификаторы кнопок и осей, приведенные в таблице ниже, поддерживаются диспетчером ввода Unity для контроллеров движения Windows Mixed Reality с помощью *входных API-интерфейсов input. OnButton и AXIS* , а столбец "Windows MR" относится к свойствам, доступным для типа *интерактионсаурцестате* .</span><span class="sxs-lookup"><span data-stu-id="7e5d5-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="7e5d5-110">Каждый из этих API подробно описан в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="7e5d5-111">Сопоставление ИДЕНТИФИКАТОРов кнопок и осей для Windows Mixed Reality обычно соответствует идентификаторам кнопок и осей Окулус.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="7e5d5-112">Сопоставление ИДЕНТИФИКАТОРов кнопок и осей для Windows Mixed Reality отличается от сопоставлений Опенвр двумя способами:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="7e5d5-113">Сопоставление использует идентификаторы сенсорной панели, отличающиеся от аналоговый, для поддержки контроллеров с сумбстиккс и сенсорными устройствами.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="7e5d5-114">Сопоставление позволяет избежать перегрузки идентификаторов кнопок A и X для кнопок меню, чтобы оставить их доступными для физических кнопок АБКСИ.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="7e5d5-115">Ввод</span><span class="sxs-lookup"><span data-stu-id="7e5d5-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="7e5d5-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Общие интерфейсы API Unity</a></span><span class="sxs-lookup"><span data-stu-id="7e5d5-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="7e5d5-117">(Входные данные. Кнопка/ось)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="7e5d5-118"><a href="gestures-and-motion-controllers-in-unity.md#">Входной API Windows MR</a></span><span class="sxs-lookup"><span data-stu-id="7e5d5-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="7e5d5-119">XR. Головк. Входной</span><span class="sxs-lookup"><span data-stu-id="7e5d5-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="7e5d5-120">Левая рука</span><span class="sxs-lookup"><span data-stu-id="7e5d5-120">Left hand</span></span> </th><th> <span data-ttu-id="7e5d5-121">Правая рука</span><span class="sxs-lookup"><span data-stu-id="7e5d5-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7e5d5-122">Выбрать триггер нажат</span><span class="sxs-lookup"><span data-stu-id="7e5d5-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="7e5d5-123">Ось 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="7e5d5-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="7e5d5-124">Ось 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="7e5d5-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="7e5d5-125">селектпрессед</span><span class="sxs-lookup"><span data-stu-id="7e5d5-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-126">Выбор триггера аналогового значения</span><span class="sxs-lookup"><span data-stu-id="7e5d5-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="7e5d5-127">Ось 9</span><span class="sxs-lookup"><span data-stu-id="7e5d5-127">Axis 9</span></span> </td><td> <span data-ttu-id="7e5d5-128">Ось 10</span><span class="sxs-lookup"><span data-stu-id="7e5d5-128">Axis 10</span></span> </td><td> <span data-ttu-id="7e5d5-129">селектпресседамаунт</span><span class="sxs-lookup"><span data-stu-id="7e5d5-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-130">Выделение триггера частично нажато</span><span class="sxs-lookup"><span data-stu-id="7e5d5-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="7e5d5-131">Кнопка 14 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7e5d5-132">Кнопка 15 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7e5d5-133">Селектпресседамаунт &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="7e5d5-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-134">Нажата кнопка меню</span><span class="sxs-lookup"><span data-stu-id="7e5d5-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="7e5d5-135">Кнопка 6 \*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-135">Button 6\*</span></span> </td><td> <span data-ttu-id="7e5d5-136">Кнопка 7 \*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-136">Button 7\*</span></span> </td><td> <span data-ttu-id="7e5d5-137">менупрессед</span><span class="sxs-lookup"><span data-stu-id="7e5d5-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-138">Нажата кнопка захвата</span><span class="sxs-lookup"><span data-stu-id="7e5d5-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="7e5d5-139">Ось 11 = 1,0 (нет аналоговых значений)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="7e5d5-140">Кнопка 4 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7e5d5-141">Ось 12 = 1,0 (нет аналоговых значений)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="7e5d5-142">Кнопка 5 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7e5d5-143">Новы</span><span class="sxs-lookup"><span data-stu-id="7e5d5-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-144">Аналоговый стик X <i>(слева:-1,0, Right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="7e5d5-145">Ось 1</span><span class="sxs-lookup"><span data-stu-id="7e5d5-145">Axis 1</span></span> </td><td> <span data-ttu-id="7e5d5-146">Ось 4</span><span class="sxs-lookup"><span data-stu-id="7e5d5-146">Axis 4</span></span> </td><td> <span data-ttu-id="7e5d5-147">Сумбстиккпоситион. x</span><span class="sxs-lookup"><span data-stu-id="7e5d5-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-148">Аналоговый стик <i>по оси Y (Top:-1,0, Нижняя: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="7e5d5-149">Ось 2</span><span class="sxs-lookup"><span data-stu-id="7e5d5-149">Axis 2</span></span> </td><td> <span data-ttu-id="7e5d5-150">Ось 5</span><span class="sxs-lookup"><span data-stu-id="7e5d5-150">Axis 5</span></span> </td><td> <span data-ttu-id="7e5d5-151">Сумбстиккпоситион. y</span><span class="sxs-lookup"><span data-stu-id="7e5d5-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-152">Нажатый аналоговый стик</span><span class="sxs-lookup"><span data-stu-id="7e5d5-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="7e5d5-153">Кнопка 8</span><span class="sxs-lookup"><span data-stu-id="7e5d5-153">Button 8</span></span> </td><td> <span data-ttu-id="7e5d5-154">Кнопка 9</span><span class="sxs-lookup"><span data-stu-id="7e5d5-154">Button 9</span></span> </td><td> <span data-ttu-id="7e5d5-155">сумбстиккпрессед</span><span class="sxs-lookup"><span data-stu-id="7e5d5-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-156">Сенсорная панель X <i>(левая:-1,0, Right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="7e5d5-157">Ось 17 \*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="7e5d5-158">Ось 19 \*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="7e5d5-159">Таучпадпоситион. x</span><span class="sxs-lookup"><span data-stu-id="7e5d5-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-160">Сенсорная панель Y <i>(начало:-1,0, Нижняя: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="7e5d5-161">Ось 18 \*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="7e5d5-162">Ось 20 \*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="7e5d5-163">Таучпадпоситион. y</span><span class="sxs-lookup"><span data-stu-id="7e5d5-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-164">Сенсорная панель затронута</span><span class="sxs-lookup"><span data-stu-id="7e5d5-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="7e5d5-165">Кнопка 18 \*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-165">Button 18\*</span></span> </td><td> <span data-ttu-id="7e5d5-166">Кнопка 19 \*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-166">Button 19\*</span></span> </td><td> <span data-ttu-id="7e5d5-167">таучпадтаучед</span><span class="sxs-lookup"><span data-stu-id="7e5d5-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-168">Сенсорная панель нажата</span><span class="sxs-lookup"><span data-stu-id="7e5d5-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="7e5d5-169">Кнопка 16 \*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-169">Button 16\*</span></span> </td><td> <span data-ttu-id="7e5d5-170">Кнопка 17 \*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-170">Button 17\*</span></span> </td><td> <span data-ttu-id="7e5d5-171">таучпадпрессед</span><span class="sxs-lookup"><span data-stu-id="7e5d5-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-172">6DoF захват захвата или указатель</span><span class="sxs-lookup"><span data-stu-id="7e5d5-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="7e5d5-173">Только <i>захват</i> : <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Инпуттраккинг. Жетлокалпоситион</a></span><span class="sxs-lookup"><span data-stu-id="7e5d5-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="7e5d5-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Инпуттраккинг. Жетлокалротатион</a></span><span class="sxs-lookup"><span data-stu-id="7e5d5-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="7e5d5-175">Передается <i>захват</i> или <i>указатель</i> в качестве аргумента: Саурцестате. саурцепосе. трижетпоситион</span><span class="sxs-lookup"><span data-stu-id="7e5d5-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="7e5d5-176">Саурцестате. Саурцепосе. Трижетротатион</span><span class="sxs-lookup"><span data-stu-id="7e5d5-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-177">Состояние отслеживания</span><span class="sxs-lookup"><span data-stu-id="7e5d5-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="7e5d5-178"><i>Точность расположения и потери исходного кода доступны только через API-интерфейс MR</i> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="7e5d5-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">Саурцестате. Саурцепосе. Поситионаккураци</a></span><span class="sxs-lookup"><span data-stu-id="7e5d5-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="7e5d5-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">Саурцестате. Properties. Саурцелоссриск</a></span><span class="sxs-lookup"><span data-stu-id="7e5d5-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="7e5d5-181">Эти идентификаторы кнопок и осей отличаются от идентификаторов, используемых Unity для Опенвр из-за конфликтов в сопоставлениях, используемых в игровых элементах управления, Окулус Touch и Опенвр.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="7e5d5-182">Захват захвата и указание объекта a</span><span class="sxs-lookup"><span data-stu-id="7e5d5-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="7e5d5-183">Windows Mixed Reality поддерживает контроллеры Motion в различных конструктивных факторах, при этом структура каждого контроллера различается в связи между положением пользователя и естественным направлением "вперед", которое приложения должны использовать для указания при визуализации контроллера.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="7e5d5-184">Для лучшего представления этих контроллеров существует два вида экземпляров, которые можно исследовать для каждого источника взаимодействия, **захвата** и **указателя**.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="7e5d5-185">Координаты захвата и указателя "указатель" выражаются всеми API Unity в глобальных координатах мира Unity.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="7e5d5-186">Подзахват</span><span class="sxs-lookup"><span data-stu-id="7e5d5-186">Grip pose</span></span>

<span data-ttu-id="7e5d5-187">Подсистема **захвата** представляет собой расположение кармана от руки, обнаруженного HoloLens, или карманного компьютера, удерживающий контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="7e5d5-188">На современных головных телефонах подзахваты лучше использовать для отрисовки **руки пользователя** или объекта, **хранящегося в руки пользователя**, например технологий или обоймы.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="7e5d5-189">Элемент захвата также используется при визуализации контроллера движения, так как **модель подготовки к просмотру** , предоставляемая Windows для контроллера движения, использует захват в качестве источника и центра вращения.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="7e5d5-190">Захват захвата определяется в частности следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="7e5d5-191">**Позиция захвата**: Карманный центроид при удержании контроллера естественным образом настраивается влево или вправо для центрирования места внутри захвата.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="7e5d5-192">В контроллере движения Windows Mixed Reality эта отправка обычно соответствует кнопке "расположить".</span><span class="sxs-lookup"><span data-stu-id="7e5d5-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="7e5d5-193">**Правая ось ориентации захвата**: когда вы полностью открываете руку для формирования плоской задачи с 5-пальцем, луч, обычный для вашего кармана (вперед от левого кармана, назад от правого Palm)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="7e5d5-194">**Прямая ось ориентации захвата**: когда вы частично закрываете руку (как при удержании контроллера), луч, который указывает на "Forward" через лампу, сформированную небегункными пальцами.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="7e5d5-195">**Ось Up (вверх) для ориентации захвата**: ось Up, подразумеваемая правым и прямым определением.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="7e5d5-196">Доступ к захвату можно получить через API-интерфейс ввода кросс-поставщика Unity ( *[XR). Инпуттраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Жетлокалпоситион/вращение*) или через API-интерфейс Windows MR (*Саурцестате. Саурцепосе. Трижетпоситион/вращение*, запрашивающий данные для узла **захвата** ).</span><span class="sxs-lookup"><span data-stu-id="7e5d5-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="7e5d5-197">Указатель a</span><span class="sxs-lookup"><span data-stu-id="7e5d5-197">Pointer pose</span></span>

<span data-ttu-id="7e5d5-198">**Указатель** a представляет кончик контроллера, указывающий на пересылку.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="7e5d5-199">Предоставляемый системой указатель, который лучше использовать для райкаст при **отрисовке самой модели контроллера**.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="7e5d5-200">При визуализации какого-либо другого виртуального объекта вместо контроллера, например виртуального, следует указывать на луч, который наиболее естественным для этого виртуального объекта, например луч, который перемещается на объект модели обойм, определяемой приложением.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="7e5d5-201">Так как пользователи могут видеть виртуальный объект, а не физический контроллер, указание виртуального объекта, скорее всего, будет более естественным для тех, кто использует ваше приложение.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="7e5d5-202">В настоящее время указатель a доступен в Unity только через API-интерфейс Windows MR, *саурцестате. саурцепосе. трижетпоситион/вращение*, передавая *интерактионсаурценоде. Pointer* в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="7e5d5-203">Состояние отслеживания контроллера</span><span class="sxs-lookup"><span data-stu-id="7e5d5-203">Controller tracking state</span></span>

<span data-ttu-id="7e5d5-204">Как и гарнитуры, для контроллера движения Windows Mixed Reality не требуется настраивать внешние датчики отслеживания.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="7e5d5-205">Вместо этого контроллеры прописываются датчиками в самой гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="7e5d5-206">Если пользователь перемещает контроллеры из поля зрения гарнитуры, в большинстве случаев Windows будет по прежнему вычислять позиции контроллера и предоставлять их приложению.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="7e5d5-207">Когда контроллер потеряет Визуальное отслеживание на достаточно длинном уровне, позиции контроллера будут отбрасываться на позиции приблизительной точности.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="7e5d5-208">На этом этапе система будет блокировать контроллер для пользователя, отслеживая положение пользователя по мере его перемещения, сохраняя при этом ориентацию на уровне true, используя внутренние датчики ориентации.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="7e5d5-209">Многие приложения, использующие контроллеры для указания и активации элементов пользовательского интерфейса, могут нормально работать при приближенной точности, не закрывая пользователю.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="7e5d5-210">Лучший способ сделать это — попробовать.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="7e5d5-211">Просмотрите это видео с примерами впечатляющих материалов, которые работают с контроллерами движения в различных состояниях отслеживания:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="7e5d5-212">Явное объяснение состояния отслеживания</span><span class="sxs-lookup"><span data-stu-id="7e5d5-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="7e5d5-213">Приложения, которые хотят обрабатывать позиции по-разному в зависимости от состояния отслеживания, могут дополнительно проанализировать свойства в состоянии контроллера, такие как *саурцелоссриск* и *поситионаккураци*:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="7e5d5-214">Состояние отслеживания</span><span class="sxs-lookup"><span data-stu-id="7e5d5-214">Tracking state</span></span> </th><th> <span data-ttu-id="7e5d5-215">саурцелоссриск</span><span class="sxs-lookup"><span data-stu-id="7e5d5-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="7e5d5-216">поситионаккураци</span><span class="sxs-lookup"><span data-stu-id="7e5d5-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="7e5d5-217">трижетпоситион</span><span class="sxs-lookup"><span data-stu-id="7e5d5-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7e5d5-218"><b>Высокая точность</b> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="7e5d5-219">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="7e5d5-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7e5d5-220">Высокий</span><span class="sxs-lookup"><span data-stu-id="7e5d5-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7e5d5-221">true</span><span class="sxs-lookup"><span data-stu-id="7e5d5-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-222"><b>Высокая точность (при потере риска)</b> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="7e5d5-223">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="7e5d5-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7e5d5-224">Высокий</span><span class="sxs-lookup"><span data-stu-id="7e5d5-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7e5d5-225">true</span><span class="sxs-lookup"><span data-stu-id="7e5d5-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-226"><b>Приблизительная точность</b> </span><span class="sxs-lookup"><span data-stu-id="7e5d5-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="7e5d5-227">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="7e5d5-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="7e5d5-228">Приблизительна</span><span class="sxs-lookup"><span data-stu-id="7e5d5-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7e5d5-229">true</span><span class="sxs-lookup"><span data-stu-id="7e5d5-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e5d5-230">Нет а по <b>положению</b></span><span class="sxs-lookup"><span data-stu-id="7e5d5-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="7e5d5-231">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="7e5d5-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="7e5d5-232">Приблизительна</span><span class="sxs-lookup"><span data-stu-id="7e5d5-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="7e5d5-233">false</span><span class="sxs-lookup"><span data-stu-id="7e5d5-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="7e5d5-234">Эти состояния отслеживания контроллера движения определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="7e5d5-235">**Высокая точность:** Хотя контроллер движения находится внутри поля зрения гарнитуры, он обычно предоставляет высокую точность на основе визуального отслеживания.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="7e5d5-236">Обратите внимание, что перемещаемый контроллер, проходящий через некоторое время, покидает поле зрения или мгновенно закрывается от датчиков гарнитуры (например, с другой стороны пользователя), будет по-прежнему возвращать высокую точность в течение короткого времени, исходя из инерции отслеживания контроллера. загрузить.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="7e5d5-237">**Высокая точность (при потере риска):** Когда пользователь перемещает контроллер движения за пределы поля "гарнитура", головной телефон вскоре не сможет визуально отвести мониторинг позиции контроллера.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="7e5d5-238">Приложение знает, когда контроллер достиг этой фов границы, просматривая **саурцелоссриск** REACH 1,0.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="7e5d5-239">На этом этапе приложение может приостановить жесты контроллера, для которых требуется устойчивый поток с очень высоким качеством.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="7e5d5-240">**Приблизительная точность:** Когда контроллер потеряет Визуальное отслеживание на достаточно длинном уровне, позиции контроллера будут отбрасываться на позиции приблизительной точности.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="7e5d5-241">На этом этапе система будет блокировать контроллер для пользователя, отслеживая положение пользователя по мере его перемещения, сохраняя при этом ориентацию на уровне true, используя внутренние датчики ориентации.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="7e5d5-242">Многие приложения, использующие контроллеры для указания и активации элементов пользовательского интерфейса, могут нормально работать в режиме обычной точности, не закрывая пользователю.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="7e5d5-243">Приложения с более **высокими** требованиями к входным данным могут отказаться от высокой точности для **приблизительной** точности, проверив свойство **поситионаккураци** , например, чтобы предоставить пользователю более масштабная хитбокс на экранных целевых объектах в течение этого времени.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="7e5d5-244">**Без расположения:** Несмотря на то, что контроллер может нормально обрабатываться в течение длительного времени, иногда система знает, что даже в данный момент не имеет смысла в положении блокировки текста.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="7e5d5-245">Например, контроллер, который был только что включен, может никогда не наблюдать визуально, или же пользователь может установить контроллер, который затем забирается другим пользователем.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="7e5d5-246">В это время система не будет предоставлять никакой позиции приложению, а *трижетпоситион* вернет значение false.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="7e5d5-247">Общие API-интерфейсы Unity (входные или кнопки и ось)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="7e5d5-248">**Пространство имен:** *UnityEngine*, *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="7e5d5-249">**Types**: *input*, *XR. Инпуттраккинг*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="7e5d5-250">В настоящее время Unity использует общие *входные API-интерфейсы input. Окулус и input. Axis* для предоставления входных данных для [пакета SDK для](https://docs.unity3d.com/Manual/OculusControllers.html), [пакета SDK опенвр](https://docs.unity3d.com/Manual/OpenVRControllers.html) и Windows Mixed Reality, включая руки и контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="7e5d5-251">Если приложение использует эти API для ввода данных, оно может легко поддерживать контроллеры движения в нескольких пакетах SDK XR, включая Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="7e5d5-252">Получение состояния нажатия логической кнопки</span><span class="sxs-lookup"><span data-stu-id="7e5d5-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="7e5d5-253">Чтобы использовать общие интерфейсы API ввода Unity, обычно начнем с привязки кнопок и осей к логическим именам в [диспетчере ввода Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), привязывая идентификаторы кнопок или осей к каждому имени.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="7e5d5-254">Затем можно написать код, ссылающийся на эту логическую кнопку или имя оси.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="7e5d5-255">Например, чтобы связать кнопку триггера левого контроллера движения с действием Отправить, перейдите в меню **правка > параметры проекта > входные данные** в Unity и разверните свойства раздела отправить в разделе оси.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="7e5d5-256">Измените **положительную кнопку** или свойство **положительной кнопки Alt** , чтобы прочесть **игровую кнопку 14**, например:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-256">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="7e5d5-257">![](images/unity-input-manager.png) InputManager Unity</span><span class="sxs-lookup"><span data-stu-id="7e5d5-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="7e5d5-258">*InputManager Unity*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-258">*Unity InputManager*</span></span>

<span data-ttu-id="7e5d5-259">Затем скрипт может проверить действие отправки с помощью *input. OnButton*:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="7e5d5-260">Можно добавить дополнительные логические кнопки, изменив свойство **size** в разделе **оси**.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="7e5d5-261">Непосредственное получение состояния нажатия физической кнопки</span><span class="sxs-lookup"><span data-stu-id="7e5d5-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="7e5d5-262">Можно также получить доступ к кнопкам вручную по полному имени с помощью *input. GetKey*:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="7e5d5-263">Получение объекта руки или контроллера движения</span><span class="sxs-lookup"><span data-stu-id="7e5d5-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="7e5d5-264">Вы можете получить доступ к положению и повороту контроллера с помощью *XR. Инпуттраккинг*:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="7e5d5-265">Обратите внимание, что это представляет собой захват контроллера (где пользователь удерживает контроллер), который полезен для отрисовки технологий или оружия в руки пользователя или модели самого контроллера.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="7e5d5-266">Обратите внимание, что связь между этим захватом и указателем (где накладывается кончик контроллера) может отличаться в разных контроллерах.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="7e5d5-267">На данный момент доступ к элементу указателя контроллера может осуществляться только через API ввода, характерный для MR, описанный в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="7e5d5-268">Интерфейсы API для Windows (XR. Головк. Входной</span><span class="sxs-lookup"><span data-stu-id="7e5d5-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="7e5d5-269">**Пространство имен:** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="7e5d5-270">**Типы**: *интерактионманажер*, *интерактионсаурцестате*, *интерактионсаурце*, *интерактионсаурцепропертиес*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="7e5d5-271">Чтобы получить более подробные сведения о вводе-выделе Windows Mixed Reality (для HoloLens) и контроллеров движения, можно выбрать использование пространственных входных API Windows в пространстве имен *UnityEngine. XR. WSA. Input* .</span><span class="sxs-lookup"><span data-stu-id="7e5d5-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="7e5d5-272">Это позволяет получить доступ к дополнительным сведениям, таким как точность расположения или тип источника, что позволяет сообщать о руки и контроллерах.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="7e5d5-273">Опрос состояния движений и контроллеров движения</span><span class="sxs-lookup"><span data-stu-id="7e5d5-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="7e5d5-274">Вы можете опросить состояние этого кадра для каждого источника взаимодействия (вручную или контроллера движения) с помощью метода *жеткуррентреадинг* .</span><span class="sxs-lookup"><span data-stu-id="7e5d5-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="7e5d5-275">Каждый *интерактионсаурцестате* , который вы получаете назад, представляет источник взаимодействия на текущий момент времени.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="7e5d5-276">*Интерактионсаурцестате* предоставляет такие сведения:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="7e5d5-277">Какие [виды нажатия](motion-controllers.md) происходят (выбор/меню, распечатка, Сенсорная панель или аналоговый стик)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="7e5d5-278">Другие данные, относящиеся к контроллерам движения, таким как координаты и/или ТОЧЕЧный стик, а также затронутое состояние</span><span class="sxs-lookup"><span data-stu-id="7e5d5-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="7e5d5-279">Интерактионсаурцекинд, чтобы выяснить, является ли источник рукой или контроллером движения</span><span class="sxs-lookup"><span data-stu-id="7e5d5-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="7e5d5-280">Опрос для перенаправляемых прогнозов отрисовки</span><span class="sxs-lookup"><span data-stu-id="7e5d5-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="7e5d5-281">При опросе данных об источнике взаимодействия от рук и контроллеров, получаемые вами данные будут перенаправлены на момент времени, когда фотоны этого кадра будет достигнуть глаз пользователя.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="7e5d5-282">Эти перенаправленные объекты лучше использовать для **подготовки к просмотру** контроллера или удерживаемого объекта в каждом кадре.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="7e5d5-283">Если вы нажимаете на контроллере любую нажатие или выпуск, это будет наиболее точным, если вы используете API событий предыстории, описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="7e5d5-284">Вы также можете получить в этом текущем фрейме объект с прямым прогнозированием.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="7e5d5-285">Как и в случае с исходной версией, это полезно для **отрисовки** курсора, хотя нацеливание на заданную клавишу или выпуск будет наиболее точным, если вы используете интерфейсы API событий с предысторией, описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="7e5d5-286">Обработка событий источника взаимодействия</span><span class="sxs-lookup"><span data-stu-id="7e5d5-286">Handling interaction source events</span></span>

<span data-ttu-id="7e5d5-287">Чтобы обрабатывались входные события, происходящие с точными данными предыстории, вместо опроса можно использовать события источника взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="7e5d5-288">Для управления событиями источника взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-288">To handle interaction source events:</span></span>
* <span data-ttu-id="7e5d5-289">Регистрация для события ввода *интерактионманажер* .</span><span class="sxs-lookup"><span data-stu-id="7e5d5-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="7e5d5-290">Для каждого интересующего вас типа события взаимодействия необходимо подписываться на него.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="7e5d5-291">Обработайте событие.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-291">Handle the event.</span></span> <span data-ttu-id="7e5d5-292">После подписки на событие взаимодействия вы получите обратный вызов при необходимости.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="7e5d5-293">В примере *саурцепрессед* это произойдет после обнаружения источника и до его освобождения или потери.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="7e5d5-294">Как прерывать обработку события</span><span class="sxs-lookup"><span data-stu-id="7e5d5-294">How to stop handling an event</span></span>

<span data-ttu-id="7e5d5-295">Если вы больше не заинтересованы в событии или удаляете объект, подписанный на событие, необходимо отменить обработку события.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="7e5d5-296">Чтобы прерывать обработку события, отказаться от подписки на событие.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="7e5d5-297">Список событий источника взаимодействия</span><span class="sxs-lookup"><span data-stu-id="7e5d5-297">List of interaction source events</span></span>

<span data-ttu-id="7e5d5-298">Доступные события источника взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-298">The available interaction source events are:</span></span>
* <span data-ttu-id="7e5d5-299">*Интерактионсаурцедетектед* (источник стал активным)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="7e5d5-300">*Интерактионсаурцелост* (неактивен)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="7e5d5-301">*Интерактионсаурцепрессед* (TAP, нажатие кнопки или "Select" распространенная)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="7e5d5-302">*Интерактионсаурцерелеасед* (окончание касания, кнопка отжата или конец "Select" распространенная)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="7e5d5-303">*Интерактионсаурцеупдатед* (перемещение или иным образом изменяет некоторое состояние)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="7e5d5-304">События для исторических целей, которые наиболее точно соответствуют нажатию или выпуску</span><span class="sxs-lookup"><span data-stu-id="7e5d5-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="7e5d5-305">API-интерфейсы опроса, описанные выше, предоставляют приложению перенаправление прогнозов.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="7e5d5-306">Хотя эти прогнозируемые объекты лучше всего подходят для подготовки к просмотру контроллера или виртуального карманного объекта, будущие элементы не оптимальны для нацеливания, по двум основным причинам:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="7e5d5-307">Когда пользователь нажимает кнопку на контроллере, может быть около 20 мс задержки беспроводной сети через Bluetooth, прежде чем система получит нажатие.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="7e5d5-308">Затем, если вы используете прямую прогнозную единицу, будет использоваться еще 10-20 мс прямого прогноза, который будет применяться к моменту, когда фотоны текущего кадра достигнет глаза пользователя.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="7e5d5-309">Это означает, что опрос дает вам исходную позицию или головной элемент, который составляет 30 – 40ms вперед от того места, где головка пользователя и руки в действительности были возвращены при нажатии или выпуске.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="7e5d5-310">Для входных данных HoloLens, в то время как нет задержки беспроводной передачи, существует аналогичная задержка обработки для обнаружения нажатия.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="7e5d5-311">Чтобы правильно ориентироваться в зависимости от первоначальной цели пользователя или нажатия контроллера, следует использовать источник с предысторией или головной элемент из этого события ввода *интерактионсаурцепрессед* или *интерактионсаурцерелеасед* .</span><span class="sxs-lookup"><span data-stu-id="7e5d5-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="7e5d5-312">Вы можете выбрать пресс или Release с предысторией данных из заголовка пользователя или контроллера:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="7e5d5-313">В момент, когда произошло нажатие жеста или контроллера, эта головная программа может быть **использована для определения** того, что именно [облаками](gaze-and-commit.md) пользователь:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="7e5d5-314">Исходная ошибка в момент, когда произошло нажатие кнопки контроллера движения, которое можно использовать для определения **нацеливания** пользователя на контроллер.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="7e5d5-315">Это будет состояние контроллера, на котором нажимается клавиша.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="7e5d5-316">Если вы создаете сам контроллер, то можете запросить объект a, а не захват, чтобы прокрутить целевой луч от того, что пользователь будет рассматривать как естественный Совет этого отображаемого контроллера:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="7e5d5-317">Пример обработчиков событий</span><span class="sxs-lookup"><span data-stu-id="7e5d5-317">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="7e5d5-318">Интерфейсы API составных жестов высокого уровня (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="7e5d5-319">**Пространство имен:** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="7e5d5-320">**Типы**: *GestureRecognizer*, *жестуресеттингс*, *интерактионсаурцекинд*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="7e5d5-321">Приложение может также распознать составные жесты более высокого уровня для пространственных источников входных данных, коснуться, удерживать, манипуляции и жесты навигации.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="7e5d5-322">Эти составные жесты можно распознавать как в движении, [так и в](gaze-and-commit.md#composite-gestures) [контроллерах движения](motion-controllers.md) с помощью GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-322">You can recognize these composite gestures across both [hands](gaze-and-commit.md#composite-gestures) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="7e5d5-323">Каждое событие жеста в GestureRecognizer предоставляет Саурцекинд для входных данных, а также целевой заголовочный элемент на момент события.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="7e5d5-324">Некоторые события предоставляют дополнительные сведения, относящиеся к контексту.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="7e5d5-325">Для записи жестов с помощью распознавателя жестов требуется всего несколько действий:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="7e5d5-326">Создание нового распознавателя жестов</span><span class="sxs-lookup"><span data-stu-id="7e5d5-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="7e5d5-327">Укажите, какие жесты следует отслеживать</span><span class="sxs-lookup"><span data-stu-id="7e5d5-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="7e5d5-328">Подписываться на события для этих жестов</span><span class="sxs-lookup"><span data-stu-id="7e5d5-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="7e5d5-329">Начать запись жестов</span><span class="sxs-lookup"><span data-stu-id="7e5d5-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="7e5d5-330">Создание нового распознавателя жестов</span><span class="sxs-lookup"><span data-stu-id="7e5d5-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="7e5d5-331">Чтобы использовать *GestureRecognizer*, необходимо создать *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="7e5d5-332">Укажите, какие жесты следует отслеживать</span><span class="sxs-lookup"><span data-stu-id="7e5d5-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="7e5d5-333">Укажите, какие жесты вы хотите использовать с помощью *сетрекогнизаблежестурес ()* :</span><span class="sxs-lookup"><span data-stu-id="7e5d5-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="7e5d5-334">Подписываться на события для этих жестов</span><span class="sxs-lookup"><span data-stu-id="7e5d5-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="7e5d5-335">Подпишитесь на события для интересующих вас жестов.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-335">Subscribe to events for the gestures you are interested in.</span></span>

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
><span data-ttu-id="7e5d5-336">Жесты навигации и манипуляции являются взаимоисключающими в экземпляре *GestureRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="7e5d5-337">Начать запись жестов</span><span class="sxs-lookup"><span data-stu-id="7e5d5-337">Start capturing gestures</span></span>

<span data-ttu-id="7e5d5-338">По умолчанию *GestureRecognizer* не отслеживает входные данные до тех пор, пока не будет вызван *старткаптурингжестурес ()* .</span><span class="sxs-lookup"><span data-stu-id="7e5d5-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="7e5d5-339">Возможно, что событие жеста может быть создано после вызова *стопкаптурингжестурес ()* , если входные данные были выполнены до того, как был обработан *стопкаптурингжестурес ()* .</span><span class="sxs-lookup"><span data-stu-id="7e5d5-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="7e5d5-340">*GestureRecognizer* будет запоминать, была ли она включена или отключена во время предыдущего кадра, в котором он действительно выполнялся, и таким образом, чтобы обеспечить возможность запуска и остановки мониторинга жестов на основе целевых объектов взгляда.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-340">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="7e5d5-341">Завершение записи жестов</span><span class="sxs-lookup"><span data-stu-id="7e5d5-341">Stop capturing gestures</span></span>

<span data-ttu-id="7e5d5-342">Чтобы отключить распознавание жестов, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="7e5d5-343">Удаление распознавателя жестов</span><span class="sxs-lookup"><span data-stu-id="7e5d5-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="7e5d5-344">Не забудьте отказаться от подписки на подписанные события перед уничтожением объекта *GestureRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="7e5d5-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="7e5d5-345">Подготовка модели контроллера движения к просмотру в Unity</span><span class="sxs-lookup"><span data-stu-id="7e5d5-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="7e5d5-346">![модель контроллера движения и](images/motioncontrollertest-teleport-1000px.png) телепереноса</span><span class="sxs-lookup"><span data-stu-id="7e5d5-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="7e5d5-347">*Модель контроллера движения и телеперенос*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="7e5d5-348">Для подготовки к просмотру в приложении контроллеров движения, соответствующих физическим контроллерам, которые хранятся и обрабатываются при нажатии различных кнопок, можно использовать **prefab мотионконтроллер** в [наборе средств Mixed Reality](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="7e5d5-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="7e5d5-349">Этот prefab динамически загружает правильную модель Глтф во время выполнения из установленного в системе драйвера контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="7e5d5-350">Важно динамически загружать эти модели, а не импортировать их вручную в редакторе, чтобы приложение показывало физически точную трехмерную модель для всех существующих и будущих контроллеров, которые могут иметь пользователи.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="7e5d5-351">Следуйте инструкциям по [Начало работы](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) , чтобы скачать набор средств для смешанной реальности и добавить его в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="7e5d5-352">Если вы заменили камеру на *микседреалитикамерапарент* prefab в рамках начало работы действий, то можете продолжить!</span><span class="sxs-lookup"><span data-stu-id="7e5d5-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="7e5d5-353">Этот prefab включает визуализацию контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="7e5d5-354">В противном случае добавьте *Assets/холотулкит/input/Prefabs/мотионконтроллерс. prefab* в сцену из области проекта.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="7e5d5-355">Вам потребуется добавить prefab в качестве дочернего объекта для того, чтобы перемещать камеру, когда у пользователя есть телепередачи в пределах сцены, чтобы контроллеры поступали вместе с пользователем.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="7e5d5-356">Если ваше приложение не предусматривает телеперенос, просто добавьте prefab в корень сцены.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="7e5d5-357">Создание вызывающих объектов</span><span class="sxs-lookup"><span data-stu-id="7e5d5-357">Throwing objects</span></span>

<span data-ttu-id="7e5d5-358">Создание объектов в Virtual Reality усложняется, и это может показаться на первый взгляд.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="7e5d5-359">Как и в случае с наиболее частыми взаимодействиями, когда вызов в игре происходит непредвиденным образом, он немедленно становится очевидным и нарушается.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="7e5d5-360">Мы тратили некоторое время на обдумывание того, как представить физически правильное поведение при вызове и получили несколько рекомендаций, включенных через обновления нашей платформы, которые мы хотели бы поделиться с вами.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="7e5d5-361">Вы можете найти пример того, как мы рекомендуем реализовать [это](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)создание.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="7e5d5-362">Этот пример соответствует следующим четырем рекомендациям:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="7e5d5-363">**Используйте *скорость* контроллера вместо расположения**.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="7e5d5-364">В ноябре-обновлении Windows мы предоставили изменение в поведении, когда в [позиционированном состоянии отслеживания "приближено](motion-controllers.md#controller-tracking-state)".</span><span class="sxs-lookup"><span data-stu-id="7e5d5-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="7e5d5-365">В этом состоянии информация о скорости контроллера будет по-прежнему отображаться до тех пор, пока мы считаем, что он имеет высокую точность, что часто бывает дольше, чем в положении.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="7e5d5-366">**Внедрение *угловой скорости* контроллера**.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="7e5d5-367">Эта логика содержится в файле `throwing.cs` в статическом методе `GetThrownObjectVelAngVel` в связанном выше пакете:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="7e5d5-368">По мере того, как угловая скорость сохраняется, создаваемый объект должен поддерживать ту же угловую скорость, что и в момент создания: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="7e5d5-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="7e5d5-369">Поскольку центр массы создаваемого объекта, скорее всего, не находится на происхождении захвата, он, вероятно, имеет другую скорость, а контроллер в кадре ссылки пользователя.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="7e5d5-370">Часть скорости объекта, созданная таким образом, является мгновенно отношения скоростью центра массы создаваемого объекта по отношению к источнику контроллера.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="7e5d5-371">Отношения скорость — это перекрестное произведение угловой скорости контроллера с вектором, представляющим расстояние между источником контроллера и центром массы создаваемого объекта.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="7e5d5-372">Общая скорость создаваемого объекта, таким образом, является суммой скорости контроллера и этой отношения скорости: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="7e5d5-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="7e5d5-373">**Обратите особое внимание на *время* , когда мы применяем скорость**.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="7e5d5-374">При нажатии кнопки может потребоваться до 20 мс для этого события, чтобы это событие было переработано с помощью Bluetooth к операционной системе.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="7e5d5-375">Это означает, что если вы опрашиваете изменение состояния контроллера с нажатия на не нажато или наоборот, сведения об этом контроллере, которые вы получаете вместе с ним, на самом деле будут находиться впереди этого изменения в состоянии.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="7e5d5-376">Кроме того, контроллер, представленный нашим API-интерфейсом опроса, передается в прогноз, чтобы отразить, что в момент отображения кадра может быть больше 20 мс в будущем.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="7e5d5-377">Это хорошо подходит для *визуализации* удерживаемых объектов, но создает *задачу по времени для объекта* , так как мы вычисляем траекторию на момент, когда пользователь выпустил свое исключение.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="7e5d5-378">К счастью, при обновлении за Ноябрьское событие при отправке события Unity, такого как *интерактионсаурцепрессед* или *интерактионсаурцерелеасед* , состояние включает данные предыстории с обратной стороны, когда кнопка была на самом деле нажата или освобождена.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="7e5d5-379">Чтобы получить наиболее точную визуализацию контроллера и нацеливание контроллера во время возникновения исключения, необходимо правильно использовать опрос и события, если это уместно:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="7e5d5-380">Для **отрисовки** каждого кадра на контроллере приложение должно располагать *GameObject* контроллера на переphotonном контроллере в течение текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="7e5d5-381">Эти данные можно получить из API опроса Unity, например *[XR. Инпуттраккинг. Жетлокалпоситион](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* или *[XR. Головк. Входные данные. Интерактионманажер. Жеткуррентреадинг](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .</span><span class="sxs-lookup"><span data-stu-id="7e5d5-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="7e5d5-382">Для **нацеливания контроллера** на нажатие или выпуск ваше приложение должно райкаст и вычислять траекторий на основе данных о том, что такое событие выпусков.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="7e5d5-383">Эти данные можно получить из API-интерфейсов Unity, таких как *[интерактионманажер. интерактионсаурцепрессед](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .</span><span class="sxs-lookup"><span data-stu-id="7e5d5-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="7e5d5-384">**Использование захвата**.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-384">**Use the grip pose**.</span></span> <span data-ttu-id="7e5d5-385">Угловая скорость и скорость отмечаются относительно захвата, а не указателя.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="7e5d5-386">Порождение продолжит совершенствоваться с будущими обновлениями Windows, и вы сможете найти дополнительные сведения здесь.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="7e5d5-387">Жесты и контроллеры движения в МРТК v2</span><span class="sxs-lookup"><span data-stu-id="7e5d5-387">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="7e5d5-388">Вы можете получить доступ к жестам и контроллеру движения из диспетчера ввода.</span><span class="sxs-lookup"><span data-stu-id="7e5d5-388">You can access gesture and motion controller from the input Manager.</span></span> 
* [<span data-ttu-id="7e5d5-389">Жест в МРТК v2</span><span class="sxs-lookup"><span data-stu-id="7e5d5-389">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="7e5d5-390">Контроллер движения в МРТК v2</span><span class="sxs-lookup"><span data-stu-id="7e5d5-390">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="7e5d5-391">Пройдите вместе с учебниками</span><span class="sxs-lookup"><span data-stu-id="7e5d5-391">Follow along with tutorials</span></span>

<span data-ttu-id="7e5d5-392">Пошаговые учебники с более подробными примерами настройки доступны в Academyе Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-392">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="7e5d5-393">Ввод MR 211: жест</span><span class="sxs-lookup"><span data-stu-id="7e5d5-393">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="7e5d5-394">Ввод с MR 213: контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="7e5d5-394">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="7e5d5-395">[![MR input 213 — контроллер движения](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="7e5d5-395">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="7e5d5-396">*MR-вход 213 — контроллер движения*</span><span class="sxs-lookup"><span data-stu-id="7e5d5-396">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="7e5d5-397">См. также:</span><span class="sxs-lookup"><span data-stu-id="7e5d5-397">See also</span></span>

* [<span data-ttu-id="7e5d5-398">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="7e5d5-398">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="7e5d5-399">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="7e5d5-399">Motion controllers</span></span>](motion-controllers.md)


