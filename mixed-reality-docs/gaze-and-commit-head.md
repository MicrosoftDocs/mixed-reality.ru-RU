---
title: Направление головы и фиксация
description: Общие сведения о модели направления головы и фиксации
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Смешанная реальность, взгляд, нацеливание взглядом, взаимодействие, проектирование
ms.openlocfilehash: 5fef778dde6852222e098aeb1cbb41fe04e0b744
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441095"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="6ab7b-104">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="6ab7b-104">Head-gaze and commit</span></span>
<span data-ttu-id="6ab7b-105">_Head-взгляд и фиксация_ — это особый случай входной модели « [взгляд» и «фиксация](gaze-and-commit.md) », включающей в себя объект с направлением заголовка «вперед» (головное), а затем использующий его с дополнительным входом, например с помощью жеста руки. Коснитесь или выберите команду "выбрать".</span><span class="sxs-lookup"><span data-stu-id="6ab7b-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with the direction of your head pointing forward (head-direction), and then acting on it with a secondary input, such as the hand gesture air tap or the voice command "Select".</span></span> 

## <a name="device-support"></a><span data-ttu-id="6ab7b-106">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="6ab7b-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6ab7b-107"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="6ab7b-107"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="6ab7b-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6ab7b-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6ab7b-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6ab7b-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6ab7b-110"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="6ab7b-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6ab7b-111">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="6ab7b-111">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="6ab7b-112">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="6ab7b-112">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="6ab7b-113">✔ Рекомендуется (третий вариант <a href="interaction-fundamentals.md">см. в разделе других возможностей</a>)</span><span class="sxs-lookup"><span data-stu-id="6ab7b-113">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="6ab7b-114">➕ Альтернативный вариант</span><span class="sxs-lookup"><span data-stu-id="6ab7b-114">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="6ab7b-115">Изменение размера цели и обратная связь</span><span class="sxs-lookup"><span data-stu-id="6ab7b-115">Target sizing and feedback</span></span>
<span data-ttu-id="6ab7b-116">Вектор взгляда Head повторяется, чтобы его можно было использовать для тонкого нацеливания, но он, как правило, лучше всего подходит для валовой нацеливания, предустанавливая несколько более крупные целевые объекты.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-116">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring somewhat larger targets.</span></span> <span data-ttu-id="6ab7b-117">Минимальный размер целевого объекта от 1 до 1,5 градусов позволяет успешно выполнять действия пользователя в большинстве сценариев, хотя целевые объекты в 3 градусах часто обеспечивают более высокую скорость.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-117">Minimum target sizes of 1 to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="6ab7b-118">Обратите внимание, что пользовательские цели — это фактически двумерная область, даже если это трехмерный элемент: проекция, которая обращена к пользователю, будет областью, на которую можно нацелиться.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-118">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="6ab7b-119">Очень полезно указать ключевые, что элемент является "активным" (то есть он предназначен для пользователя).</span><span class="sxs-lookup"><span data-stu-id="6ab7b-119">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful.</span></span> <span data-ttu-id="6ab7b-120">Это может включать использование, такие как видимые эффекты наведения указателя, звуковые элементы или щелчки, а также четкое выравнивание курсора с помощью элемента.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-120">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="6ab7b-121">![Оптимальный размер целевого объекта на расстоянии 2 метра](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6ab7b-121">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="6ab7b-122">*Оптимальный размер целевого объекта на расстоянии 2 метра*</span><span class="sxs-lookup"><span data-stu-id="6ab7b-122">*Optimal target size at 2 meter distance*</span></span>

<br>

<span data-ttu-id="6ab7b-123">![Пример выделения выбранного взглядом целевого объекта](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6ab7b-123">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="6ab7b-124">*Пример выделения выбранного взглядом целевого объекта*</span><span class="sxs-lookup"><span data-stu-id="6ab7b-124">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="6ab7b-125">Размещение цели</span><span class="sxs-lookup"><span data-stu-id="6ab7b-125">Target placement</span></span>
<span data-ttu-id="6ab7b-126">Пользователям часто не удается найти элементы пользовательского интерфейса, которые находятся очень высоко или очень низкы в своем поле зрения. основное внимание уделяется вопросам, связанным с областями вокруг основного фокусирования.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-126">Users often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="6ab7b-127">Размещение большинства целей в приемлемом диапазоне примерно на уровне глаз может исправить ситуацию.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-127">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="6ab7b-128">Учитывая склонность пользователей в любой момент фокусироваться на относительно небольшой визуальной области (область фокусировки внимания в поле зрения составляет приблизительно 10 градусов), группирование элементов интерфейса в такой мере, чтобы они были концептуально связаны, может задействовать поведение, связанное с перемещением внимания с объекта на объект, по мере перемещения взгляда пользователя по области.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-128">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="6ab7b-129">При разработке интерфейса учитывайте возможные значительные отклонения в поле зрения HoloLens и иммерсивной гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-129">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="6ab7b-130">![Пример сгруппированных элементов интерфейса для упрощения нацеливания взглядом в Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6ab7b-130">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="6ab7b-131">*Пример сгруппированных элементов интерфейса для упрощения нацеливания взглядом в Galaxy Explorer*</span><span class="sxs-lookup"><span data-stu-id="6ab7b-131">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="6ab7b-132">Улучшение поведения выбора цели</span><span class="sxs-lookup"><span data-stu-id="6ab7b-132">Improving targeting behaviors</span></span>
<span data-ttu-id="6ab7b-133">Если цель пользователя может быть определена (или приблизительно точнее), может оказаться полезной возможность принятия практических попыток взаимодействия, как если бы они были нацелены правильно.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-133">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept near miss attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="6ab7b-134">Вот несколько успешных методов, которые могут быть включены в возможности смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="6ab7b-134">Here are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="6ab7b-135">Стабилизация направления головы ("колодцы гравитации")</span><span class="sxs-lookup"><span data-stu-id="6ab7b-135">Head-gaze stabilization ("gravity wells")</span></span>
<span data-ttu-id="6ab7b-136">Этот параметр должен быть включен в большую часть времени или полностью.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-136">This should be turned on most or all of the time.</span></span> <span data-ttu-id="6ab7b-137">Эта методика позволяет устранить естественные колебания и колебании горловины, которые пользователи могут иметь в качестве хорошей передвижения из-за поведения при оформлении и распознавании речи.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-137">This technique removes the natural head and neck jitters that users might have as well movement due to looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="6ab7b-138">Алгоритмы ближайшего звена</span><span class="sxs-lookup"><span data-stu-id="6ab7b-138">Closest link algorithms</span></span>
<span data-ttu-id="6ab7b-139">Они лучше всего работают в областях с разреженным интерактивным содержимым.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-139">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="6ab7b-140">Если есть высокая вероятность того, что вы можете определить, с чем пользователь пытался взаимодействовать, можно дополнить его возможностями нацеливания, предполагая определенный уровень намерения.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-140">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="6ab7b-141">Действия баккдатинг и постдатинг</span><span class="sxs-lookup"><span data-stu-id="6ab7b-141">Backdating and postdating actions</span></span>
<span data-ttu-id="6ab7b-142">Этот механизм полезен для задач, требующих скорости.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-142">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="6ab7b-143">Когда пользователь перемещается по ряду нацеливания и манеуверс на скорости, целесообразно предположить, что он имеет некоторую намерение, и позволить пропущенным действиям работать с целевыми объектами, на которые пользователь находился в фокусе немного раньше или немного после 50 того, как в EA Тестирование РЛИ).</span><span class="sxs-lookup"><span data-stu-id="6ab7b-143">When a user is moving through a series of targeting and activation maneuvers at speed, it is useful to assume some intent, and allow missed steps to act upon targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="6ab7b-144">Сглаживание</span><span class="sxs-lookup"><span data-stu-id="6ab7b-144">Smoothing</span></span>
<span data-ttu-id="6ab7b-145">Этот механизм полезен при перемещении путем перемещения, уменьшая незначительные колебания и качающуюся из-за особенностей естественных головных перемещений.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-145">This mechanism is useful for pathing movements, reducing the slight jitter and wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="6ab7b-146">При смягчении по контуру движения, плавное изменение размера и расстояния движений, а не со временем.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-146">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="6ab7b-147">Магнитность</span><span class="sxs-lookup"><span data-stu-id="6ab7b-147">Magnetism</span></span>
<span data-ttu-id="6ab7b-148">Этот механизм можно рассматривать как более общую версию ближайших алгоритмов связи — Рисование курсора на целевую платформу или простое увеличение хитбоксес, как видимых, так и незаметного, так как пользователи, вероятнее всего, используют знания интерактивного макета, чтобы лучше подход к намерениям пользователя.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-148">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="6ab7b-149">Это может быть особенно эффективно для небольших целей.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-149">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="6ab7b-150">Закрепление фокуса</span><span class="sxs-lookup"><span data-stu-id="6ab7b-150">Focus stickiness</span></span>
<span data-ttu-id="6ab7b-151">При определении соседних интерактивных элементов, на которые передаются фокус, фокус прикрепления обеспечивает сдвиг к элементу, который в настоящий момент находится в фокусе.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-151">When determining which nearby interactive elements to give focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="6ab7b-152">Это помогает сократить число неустойчивых переключений фокуса при плавающей точке между двумя элементами с естественным шум.</span><span class="sxs-lookup"><span data-stu-id="6ab7b-152">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>


## <a name="see-also"></a><span data-ttu-id="6ab7b-153">См. также</span><span class="sxs-lookup"><span data-stu-id="6ab7b-153">See also</span></span>
* [<span data-ttu-id="6ab7b-154">Взаимодействие на основе глаз</span><span class="sxs-lookup"><span data-stu-id="6ab7b-154">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="6ab7b-155">Взгляд и остановка</span><span class="sxs-lookup"><span data-stu-id="6ab7b-155">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="6ab7b-156">Руки — прямое управление</span><span class="sxs-lookup"><span data-stu-id="6ab7b-156">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6ab7b-157">Жесты руки</span><span class="sxs-lookup"><span data-stu-id="6ab7b-157">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="6ab7b-158">Практические указания и фиксация</span><span class="sxs-lookup"><span data-stu-id="6ab7b-158">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="6ab7b-159">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="6ab7b-159">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="6ab7b-160">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="6ab7b-160">Voice input</span></span>](voice-input.md)



