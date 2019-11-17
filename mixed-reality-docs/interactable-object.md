---
title: Взаимодействующий объект
description: Кнопка длиннее метафоры, используемой для активации события в 2D-абстрактном мире. В мире объемной смешанной реальности мы больше не должны беспокоиться об этом мире абстракции.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, Пользовательский интерфейс, UX
ms.openlocfilehash: 73c8a3ce9e01f580ecbae23f2178871642c4540e
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143256"
---
# <a name="interactable-object"></a><span data-ttu-id="f1c0b-105">Взаимодействующий объект</span><span class="sxs-lookup"><span data-stu-id="f1c0b-105">Interactable object</span></span>

![Объекты интерактибле](images/UX/UX_Hero_Interactable.jpg)

<span data-ttu-id="f1c0b-107">Кнопка длиннее метафоры, используемой для активации события в 2D-абстрактном мире.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="f1c0b-108">В мире объемной смешанной реальности мы больше не должны беспокоиться об этом мире абстракции.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="f1c0b-109">Любой может быть **взаимодействующим объектом** , запускающим событие.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="f1c0b-110">Взаимодействующий объект может быть представлен любым из чашк кофе в таблице в виде всплывающей подсказки, плавающей в воздухе.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="f1c0b-111">Мы по-прежнему используем традиционные кнопки в определенных ситуациях, например в пользовательском интерфейсе диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="f1c0b-112">Визуальное представление кнопки зависит от контекста.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="f1c0b-113">Важные свойства взаимодействующего объекта</span><span class="sxs-lookup"><span data-stu-id="f1c0b-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="f1c0b-114">Визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="f1c0b-114">Visual cues</span></span>

<span data-ttu-id="f1c0b-115">Визуальные подсказки — это подсистемы датчиков, получаемые глазом в виде освещения и обрабатываемые визуальной системой во время визуального восприятия.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="f1c0b-116">Так как визуальная система находится во многих виды цветов, особенно для людей, визуальные подсказки представляют собой большой источник информации о том, как воспринимается мир.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="f1c0b-117">Поскольку holographic объектов смешиваются с реальной средой в смешанной реальности, может быть трудно понять, с какими объектами можно взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="f1c0b-118">Для любых взаимодействующих объектов важно предоставить дифференцированные визуальные подсказки для каждого входного состояния.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="f1c0b-119">Это помогает пользователю понять, какая часть вашего интерфейса является взаимодействующей, и делает пользователя уверенным, используя согласованный метод взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="f1c0b-120">Дальнее взаимодействие</span><span class="sxs-lookup"><span data-stu-id="f1c0b-120">Far interactions</span></span>

<span data-ttu-id="f1c0b-121">Для любых объектов, с которыми пользователь может взаимодействовать с помощью элемента управления "взгляд, рука и луч контроллера движения", рекомендуется иметь разные визуальные подсказки для этих трех состояний входа:</span><span class="sxs-lookup"><span data-stu-id="f1c0b-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f1c0b-122">![интерактиблеобжект — состояния — по умолчанию](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="f1c0b-123">**Состояние по умолчанию (наблюдение)**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="f1c0b-124">Состояние простоя объекта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-124">Default idle state of the object.</span></span>
    <span data-ttu-id="f1c0b-125">Курсор не находится на объекте.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-125">The cursor is not on the object.</span></span> <span data-ttu-id="f1c0b-126">Рука не обнаружена.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f1c0b-127">![интерактиблеобжект состояния — Целевая](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="f1c0b-128">**Целевое состояние (наведение указателя)**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="f1c0b-129">Когда объект ориентирован на курсор «взгляд», указатель мыши на палец или контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="f1c0b-130">Курсор находится на объекте.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-130">The cursor is on the object.</span></span> <span data-ttu-id="f1c0b-131">Обнаружена, готова.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f1c0b-132">![интерактиблеобжект-States](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="f1c0b-133">**Нажатое состояние**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-133">**Pressed state**</span></span><br>
        <span data-ttu-id="f1c0b-134">Когда объект нажимается с помощью жеста касания, нажмите кнопку "выбрать" для сенсорного экрана.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="f1c0b-135">Курсор находится на объекте.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-135">The cursor is on the object.</span></span> <span data-ttu-id="f1c0b-136">Обнаружена рука, касание воздуха.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="f1c0b-137">Вы можете использовать такие методы, как выделение или масштабирование, чтобы обеспечить визуальные подсказки для состояния ввода пользователя.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="f1c0b-138">В смешанной реальности можно найти примеры визуализации различных состояний ввода в меню "Пуск" и с кнопками панели приложений.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="f1c0b-139">Вот как эти состояния выглядят на **кнопке holographic**:</span><span class="sxs-lookup"><span data-stu-id="f1c0b-139">Here is what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f1c0b-140">![интерактиблеобжект — состояния — по умолчанию](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="f1c0b-141">**Состояние по умолчанию (наблюдение)**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f1c0b-142">![интерактиблеобжект состояния — Целевая](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="f1c0b-143">**Целевое состояние (наведение указателя)**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f1c0b-144">![интерактиблеобжект-States](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="f1c0b-145">**Нажатое состояние**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="f1c0b-146">Близкое взаимодействие (Direct)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-146">Near interactions (direct)</span></span> 

<span data-ttu-id="f1c0b-147">HoloLens 2 поддерживает вводные данные отслеживания, которые позволяют взаимодействовать с объектами.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="f1c0b-148">Без хаптик отзывов и более глубокого восприятия иногда может быть трудно определить, насколько далеко от руки покидает объект, или же вы его намерены касаться.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="f1c0b-149">Важно предоставить достаточно визуальных подсказок для передачи состояния объекта и, в частности, состояния ваших связей с этим объектом.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="f1c0b-150">Используйте визуальную обратную связь, чтобы сообщить следующее:</span><span class="sxs-lookup"><span data-stu-id="f1c0b-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="f1c0b-151">**По умолчанию (наблюдение)** : состояние простоя объекта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="f1c0b-152">**Наведение указателя мыши**: когда руку приближается к голограмме, измените визуальные элементы так, чтобы они могли взаимодействовать с голограммами.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="f1c0b-153">**Расстояние и точка взаимодействия**: как рука приближается к голограмме, вы отдаете отзыв о проектировании, чтобы сообщить о предполагаемой точке взаимодействия, а также о том, насколько далеко от объекта палец</span><span class="sxs-lookup"><span data-stu-id="f1c0b-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="f1c0b-154">**Начало контакта**: измените визуальные элементы (светло, Color), чтобы сообщить о том, что произошло касание.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="f1c0b-155">Повышено **: изменение**визуальных элементов (светлое, цветное) при проходе на объект</span><span class="sxs-lookup"><span data-stu-id="f1c0b-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="f1c0b-156">**Окончание связи**: изменение визуальных элементов (светлое, цветное) при завершении сенсорного ввода</span><span class="sxs-lookup"><span data-stu-id="f1c0b-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="f1c0b-157">![наведение (далеко)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="f1c0b-158">**Наведение (далеко)**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="f1c0b-159">Выделение на основе сходства руки.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f1c0b-160">![наведение указателя мыши (вблизи)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="f1c0b-161">**Наведение указателя мыши (вблизи)**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="f1c0b-162">Выделяйте изменения размера в зависимости от расстояния от руки.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="f1c0b-163">![касание или нажатие клавиши](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="f1c0b-164">**Сенсорный ввод/нажатие**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-164">**Touch / press**</span></span><br>
        <span data-ttu-id="f1c0b-165">Визуальная и обратная связь.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f1c0b-166">![](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="f1c0b-167">**Осознавать**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-167">**Grasp**</span></span><br>
        <span data-ttu-id="f1c0b-168">Визуальная и обратная связь.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="f1c0b-169">[Кнопка в HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) представляет собой пример визуализации различных состояний взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f1c0b-170">![по умолчанию](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="f1c0b-171">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f1c0b-172">![](images/640px-interactibleobject-pressablebutton-hover.jpg) с наведением</span><span class="sxs-lookup"><span data-stu-id="f1c0b-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="f1c0b-173">**Помещении**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-173">**Hover**</span></span><br>
        <span data-ttu-id="f1c0b-174">Показать эффекты освещения на основе близости.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="f1c0b-175">![Сенсорный ввод](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="f1c0b-176">**Сенсорный ввод**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-176">**Touch**</span></span><br>
        <span data-ttu-id="f1c0b-177">Отображать эффекты Ripple.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f1c0b-178">![нажмите](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="f1c0b-179">**Нажать**</span><span class="sxs-lookup"><span data-stu-id="f1c0b-179">**Press**</span></span><br>
        <span data-ttu-id="f1c0b-180">Переместите переднюю форму.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="f1c0b-181">Визуальная подсказка кольца в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f1c0b-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="f1c0b-182">В HoloLens 2 есть дополнительная визуальная подсказка, которая может помочь пользователю в восприятии глубины.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="f1c0b-183">Кольцо рядом с ним отображается и масштабируется по мере того, как прокрутка будет ближе к объекту.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="f1c0b-184">В конечном итоге, если достигнуто нажатое состояние, кольцо будет находиться в точке.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="f1c0b-185">Этот визуальный подход позволяет пользователю понять, насколько далеко они от объекта.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="f1c0b-186">*Цикл видео. пример визуальной обратной связи на основе сходства с ограничивающим прямоугольником*</span><span class="sxs-lookup"><span data-stu-id="f1c0b-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="f1c0b-187">![пространство](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="f1c0b-188">![визуальной обратной связи](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="f1c0b-189">Звуковые подсказки</span><span class="sxs-lookup"><span data-stu-id="f1c0b-189">Audio cues</span></span>

<span data-ttu-id="f1c0b-190">При прямом взаимодействии руки правильная обратная связь может значительно улучшить взаимодействие с пользователем.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="f1c0b-191">Используйте отзыв о звуке, чтобы сообщить следующее:</span><span class="sxs-lookup"><span data-stu-id="f1c0b-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="f1c0b-192">**Начало контакта**: воспроизведение звука при начале сенсорного ввода</span><span class="sxs-lookup"><span data-stu-id="f1c0b-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="f1c0b-193">**Окончание контакта**: воспроизведение звука в сенсорном конце</span><span class="sxs-lookup"><span data-stu-id="f1c0b-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="f1c0b-194">**Начало захвата**: воспроизведение звука при начале</span><span class="sxs-lookup"><span data-stu-id="f1c0b-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="f1c0b-195">**Конец захвата**: воспроизведение звука при завершении захвата</span><span class="sxs-lookup"><span data-stu-id="f1c0b-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="f1c0b-196">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="f1c0b-196">Voice commanding</span></span><br>
        <span data-ttu-id="f1c0b-197">Для любых взаимодействующих объектов важно поддерживать альтернативные варианты взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="f1c0b-198">По умолчанию рекомендуется поддерживать [командную команду Voice](voice-design.md) для всех объектов, которые являются взаимодействующими.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-198">By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="f1c0b-199">Чтобы улучшить возможность обнаружения, можно также предоставить подсказку во время наведения указателя мыши.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="f1c0b-200">*Изображение: подсказка для команды Voice*</span><span class="sxs-lookup"><span data-stu-id="f1c0b-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![голосовое командое](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="f1c0b-202">Рекомендации по выбору размера</span><span class="sxs-lookup"><span data-stu-id="f1c0b-202">Sizing recommendations</span></span> 

<span data-ttu-id="f1c0b-203">Чтобы пользователи могли легко затронуть все взаимодействующие объекты, рекомендуется убедиться, что они соответствуют минимальному размеру (визуальный угол, часто измеряемый в градусах визуальной дуги) в зависимости от расстояния, которое он помещает от пользователя.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="f1c0b-204">Визуальный угол основан на расстоянии между глазами пользователя и объектом и остается постоянным, а физический размер целевого объекта может измениться по мере изменения расстояния от пользователя.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="f1c0b-205">Чтобы определить необходимый физический размер объекта на основе расстояния от пользователя, попробуйте использовать визуальный калькулятор [угла, такой как.](https://elvers.us/perception/visualAngle/)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="f1c0b-206">Ниже приведены рекомендации для минимального размера взаимодействующего содержимого.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="f1c0b-207">Целевой размер для взаимодействия непосредственно с рукой</span><span class="sxs-lookup"><span data-stu-id="f1c0b-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="f1c0b-208">Друг</span><span class="sxs-lookup"><span data-stu-id="f1c0b-208">Distance</span></span> | <span data-ttu-id="f1c0b-209">Угол просмотра</span><span class="sxs-lookup"><span data-stu-id="f1c0b-209">Viewing angle</span></span> | <span data-ttu-id="f1c0b-210">Size (Размер)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="f1c0b-211">45cm</span><span class="sxs-lookup"><span data-stu-id="f1c0b-211">45cm</span></span>  | <span data-ttu-id="f1c0b-212">не меньше 2 °</span><span class="sxs-lookup"><span data-stu-id="f1c0b-212">no smaller than 2°</span></span> | <span data-ttu-id="f1c0b-213">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="f1c0b-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="f1c0b-214">![целевого размера для взаимодействия с прямыми подключениями](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="f1c0b-215">*Целевой размер для взаимодействия непосредственно с рукой*</span><span class="sxs-lookup"><span data-stu-id="f1c0b-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="f1c0b-216">Целевой размер для кнопок</span><span class="sxs-lookup"><span data-stu-id="f1c0b-216">Target size for buttons</span></span>

<span data-ttu-id="f1c0b-217">При создании кнопок для прямого взаимодействия рекомендуется увеличить минимальный размер 3,2 x 3,2 cm, чтобы убедиться в наличии достаточного пространства для размещения значка и потенциального текста.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="f1c0b-218">Друг</span><span class="sxs-lookup"><span data-stu-id="f1c0b-218">Distance</span></span> | <span data-ttu-id="f1c0b-219">Минимальный размер</span><span class="sxs-lookup"><span data-stu-id="f1c0b-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="f1c0b-220">45cm</span><span class="sxs-lookup"><span data-stu-id="f1c0b-220">45cm</span></span>  | <span data-ttu-id="f1c0b-221">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="f1c0b-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="f1c0b-222">![размер целевого объекта для кнопок](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="f1c0b-223">*Целевой размер для кнопок*</span><span class="sxs-lookup"><span data-stu-id="f1c0b-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="f1c0b-224">Целевой размер для взаимодействия "рука" или "взгляд"</span><span class="sxs-lookup"><span data-stu-id="f1c0b-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="f1c0b-225">Друг</span><span class="sxs-lookup"><span data-stu-id="f1c0b-225">Distance</span></span> | <span data-ttu-id="f1c0b-226">Угол просмотра</span><span class="sxs-lookup"><span data-stu-id="f1c0b-226">Viewing angle</span></span> | <span data-ttu-id="f1c0b-227">Size (Размер)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="f1c0b-228">2</span><span class="sxs-lookup"><span data-stu-id="f1c0b-228">2m</span></span>  | <span data-ttu-id="f1c0b-229">не меньше 1 °</span><span class="sxs-lookup"><span data-stu-id="f1c0b-229">no smaller than 1°</span></span> | <span data-ttu-id="f1c0b-230">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="f1c0b-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="f1c0b-231">![ный целевой размер для взаимодействия "рука" или "взгляд"](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="f1c0b-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="f1c0b-232">*Целевой размер для взаимодействия "рука" или "взгляд"*</span><span class="sxs-lookup"><span data-stu-id="f1c0b-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a><span data-ttu-id="f1c0b-233">Взаимодействующий объект в МРТК (набор средств для смешанной реальности) для Unit</span><span class="sxs-lookup"><span data-stu-id="f1c0b-233">Interactable object in MRTK(Mixed Reality Toolkit) for Unit</span></span>

<span data-ttu-id="f1c0b-234">В **[мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** можно использовать [**взаимодействие**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) с скриптом, чтобы объекты отвечали на различные типы состояний взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="f1c0b-235">Он поддерживает различные типы тем, которые позволяют определять визуальные состояния, управляя свойствами объектов, такими как цвет, размер, материал и шейдер.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-235">It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="f1c0b-236">Элементом</span><span class="sxs-lookup"><span data-stu-id="f1c0b-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="f1c0b-237">Button</span><span class="sxs-lookup"><span data-stu-id="f1c0b-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="f1c0b-238">Сцены с примерами взаимодействия руки</span><span class="sxs-lookup"><span data-stu-id="f1c0b-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="f1c0b-239">Стандартный шейдер Микседреалититулкит предоставляет различные параметры, такие как **освещение** , позволяющее создавать визуальные и звуковые подсказки.</span><span class="sxs-lookup"><span data-stu-id="f1c0b-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="f1c0b-240">Стандартный шейдер МРТК</span><span class="sxs-lookup"><span data-stu-id="f1c0b-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="f1c0b-241">См. также</span><span class="sxs-lookup"><span data-stu-id="f1c0b-241">See also</span></span>

* [<span data-ttu-id="f1c0b-242">Курсоры</span><span class="sxs-lookup"><span data-stu-id="f1c0b-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f1c0b-243">Рука</span><span class="sxs-lookup"><span data-stu-id="f1c0b-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f1c0b-244">Button</span><span class="sxs-lookup"><span data-stu-id="f1c0b-244">Button</span></span>](button.md)
* [<span data-ttu-id="f1c0b-245">Активный объект</span><span class="sxs-lookup"><span data-stu-id="f1c0b-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f1c0b-246">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="f1c0b-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f1c0b-247">Управлять</span><span class="sxs-lookup"><span data-stu-id="f1c0b-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f1c0b-248">Меню руки</span><span class="sxs-lookup"><span data-stu-id="f1c0b-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f1c0b-249">Ближайшее меню</span><span class="sxs-lookup"><span data-stu-id="f1c0b-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f1c0b-250">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="f1c0b-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f1c0b-251">Voice, команда</span><span class="sxs-lookup"><span data-stu-id="f1c0b-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f1c0b-252">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="f1c0b-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f1c0b-253">Сказок</span><span class="sxs-lookup"><span data-stu-id="f1c0b-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f1c0b-254">Рекламы</span><span class="sxs-lookup"><span data-stu-id="f1c0b-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="f1c0b-255">Slider</span><span class="sxs-lookup"><span data-stu-id="f1c0b-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="f1c0b-256">Шейдера</span><span class="sxs-lookup"><span data-stu-id="f1c0b-256">Shader</span></span>](shader.md)
* [<span data-ttu-id="f1c0b-257">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="f1c0b-257">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f1c0b-258">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="f1c0b-258">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f1c0b-259">Магнит поверхности</span><span class="sxs-lookup"><span data-stu-id="f1c0b-259">Surface magnetism</span></span>](surface-magnetism.md)
