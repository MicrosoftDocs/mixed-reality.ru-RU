---
title: Нацеливание на целевой объект
description: Все взаимодействия построены на базе возможности пользователя нацеливаться на элемент, с которым они хотят взаимодействовать, независимо от модальности ввода.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Смешанная реальность, Взгляните, выбор целевой платформы, взаимодействие, проектирование
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829837"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="a60fa-104">Взгляните и вдаваясь</span><span class="sxs-lookup"><span data-stu-id="a60fa-104">Gaze and dwell</span></span>
<span data-ttu-id="a60fa-105">Существует множество различных способов подтвердить фиксацию, например  объединение взгляда с голосовыми  жестами или _руки_.</span><span class="sxs-lookup"><span data-stu-id="a60fa-105">There are lots of different ways to confirm a _commit_ such as combining gaze with _voice_ or _hand gestures_.</span></span>
<span data-ttu-id="a60fa-106">Существует несколько пользовательских сценариев, в которых потоки пользователей могут быть заняты или не могут быть отслеживанием (например, работники фабрики с чрезмерным размером высокой пошлины перчатки).</span><span class="sxs-lookup"><span data-stu-id="a60fa-106">There are several user scenarios though, in which users' hands may either be busy or cannot be tracked (e.g., factory workers with oversized heavy duty gloves).</span></span> <span data-ttu-id="a60fa-107">Речевой ввод также может быть недоступен из-за настроек пользователя, в социальных сетях или в громком окружении.</span><span class="sxs-lookup"><span data-stu-id="a60fa-107">Voice input may also not be available due to user preferences, social context or loud environments.</span></span>
<span data-ttu-id="a60fa-108">В качестве резервного решения другим вариантом выполнения _фиксации_ является просто сохранение звездочки в элементе пользовательского интерфейса, который мы будем называть _вдаваясь_.</span><span class="sxs-lookup"><span data-stu-id="a60fa-108">As a fallback solution another option to perform a _commit_ is simply to keep staring at a UI element which we refer to as _dwell_.</span></span>
<span data-ttu-id="a60fa-109">_Вдаваясь_ можно выполнить с помощью взгляда на головной взгляд или глаз.</span><span class="sxs-lookup"><span data-stu-id="a60fa-109">A _dwell_ can be performed with either head or eye gaze.</span></span> <span data-ttu-id="a60fa-110">Идея проста, и ее можно разделить на следующие этапы:</span><span class="sxs-lookup"><span data-stu-id="a60fa-110">The idea is simple and can be broken down in the following phases:</span></span> 
1. <span data-ttu-id="a60fa-111">Пользователь запускает облаками с помощью кнопки с holographic</span><span class="sxs-lookup"><span data-stu-id="a60fa-111">User starts gazing at a holographic button</span></span>

2. <span data-ttu-id="a60fa-112">После краткой задержки SES (например, 150 мс) запускается анимация визуальной обратной связи.</span><span class="sxs-lookup"><span data-stu-id="a60fa-112">After a brief onset delay (e.g., 150 ms) some visual feedback animation is started.</span></span> <span data-ttu-id="a60fa-113">Задержка SES используется, чтобы избежать перегрузки пользователя за счет немедленного получения обратной связи.</span><span class="sxs-lookup"><span data-stu-id="a60fa-113">The onset delay is used to avoid overwhelming the user by immediately popping up feedback all the time.</span></span>
    - <span data-ttu-id="a60fa-114">Для _глазного взгляда_мы рекомендуем использовать следующие элементы для разработки отзыва визуального вдаваясь:</span><span class="sxs-lookup"><span data-stu-id="a60fa-114">For _eye gaze_, we recommend the following for the design of the visual dwell feedback:</span></span>
      - <span data-ttu-id="a60fa-115">**Смешивание**: Плавное смешивание в обратной связи от незаметного видимого при первом, полностью непрозрачном.</span><span class="sxs-lookup"><span data-stu-id="a60fa-115">**Blend it**: Smoothly blend in the feedback from barely visible at first to fully opaque.</span></span> <span data-ttu-id="a60fa-116">Это делает отзыв менее нежелательным, а овервхлеминг и хорошо соответствует уверенности в том, что пользователь действительно хочет привлечься к этой кнопке.</span><span class="sxs-lookup"><span data-stu-id="a60fa-116">This makes the feedback less distracting and overwhleming and nicely aligns with the confidence that the system has that the user really wants to engage with this button.</span></span>
      - <span data-ttu-id="a60fa-117">**Извлечь в**: Создание визуальной обратной связи по сравнению с уменьшением размера и переходом к центру целевого объекта с привлечением визуального внимания пользователя.</span><span class="sxs-lookup"><span data-stu-id="a60fa-117">**Pull it in**: Create a visual feedback than decreases in size and moves towards the center of the target, pulling in the user's visual attention.</span></span> 

3. <span data-ttu-id="a60fa-118">После заранее определенной длительности вдаваясь (например, 800 мс) вдаваясь завершается и запускается связанное событие.</span><span class="sxs-lookup"><span data-stu-id="a60fa-118">After a pre-defined dwell duration (e.g., 800 ms), the dwell completes and an associated event is triggered.</span></span>
    - <span data-ttu-id="a60fa-119">Предоставьте возможность завершать аудит или визуальную обратную связь, чтобы сделать так, чтобы элемент был выбран.</span><span class="sxs-lookup"><span data-stu-id="a60fa-119">Provide some finalizing auditory or visual feedback to really bring home that the item got selected now.</span></span>

![Состояния вдаваясь](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a><span data-ttu-id="a60fa-121">Нацеливание на целевой объект</span><span class="sxs-lookup"><span data-stu-id="a60fa-121">Gaze targeting</span></span>

<span data-ttu-id="a60fa-122">Все взаимодействия построены на базе возможности пользователя нацеливаться на элемент, с которым они хотят взаимодействовать, независимо от модальности ввода.</span><span class="sxs-lookup"><span data-stu-id="a60fa-122">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="a60fa-123">В Windows Mixed Reality это обычно делается с помощью взгляда пользователя.</span><span class="sxs-lookup"><span data-stu-id="a60fa-123">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="a60fa-124">Чтобы пользователь получил возможность успешно работать с интерфейсом, рассчитанное понимание системой намерения пользователя и действительное намерение пользователя должны совпадать как можно точнее.</span><span class="sxs-lookup"><span data-stu-id="a60fa-124">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="a60fa-125">Удовлетворенность пользователя возрастает и производительность повышается настолько, насколько система правильно распознает намерения пользователя.</span><span class="sxs-lookup"><span data-stu-id="a60fa-125">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="a60fa-126">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="a60fa-126">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a60fa-127"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="a60fa-127"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a60fa-128"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a60fa-128"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a60fa-129"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a60fa-129"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a60fa-130"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="a60fa-130"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a60fa-131">Нацеливание на целевой объект</span><span class="sxs-lookup"><span data-stu-id="a60fa-131">Gaze targeting</span></span></td>
        <td><span data-ttu-id="a60fa-132">✔️</span><span class="sxs-lookup"><span data-stu-id="a60fa-132">✔️</span></span></td>
        <td><span data-ttu-id="a60fa-133">✔️</span><span class="sxs-lookup"><span data-stu-id="a60fa-133">✔️</span></span></td>
        <td><span data-ttu-id="a60fa-134">✔️</span><span class="sxs-lookup"><span data-stu-id="a60fa-134">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a60fa-135">Нацеленность на глаз</span><span class="sxs-lookup"><span data-stu-id="a60fa-135">Eye targeting</span></span></td>
        <td><span data-ttu-id="a60fa-136">❌</span><span class="sxs-lookup"><span data-stu-id="a60fa-136">❌</span></span></td>
        <td><span data-ttu-id="a60fa-137">✔️</span><span class="sxs-lookup"><span data-stu-id="a60fa-137">✔️</span></span></td>
        <td><span data-ttu-id="a60fa-138">❌</span><span class="sxs-lookup"><span data-stu-id="a60fa-138">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="a60fa-139">В [ближайшее время ожидается](index.md)более подробное руководство по HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a60fa-139">More guidance specific to HoloLens 2 [coming soon](index.md).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="a60fa-140">Изменение размера цели и обратная связь</span><span class="sxs-lookup"><span data-stu-id="a60fa-140">Target sizing and feedback</span></span>

<span data-ttu-id="a60fa-141">Вектор взгляда многократно успешно срабатывал при нацеливании на мелкие объекты, но зачастую он работает наилучшим образом при крупноразмерном нацеливании (определении в качестве цели больших объектов).</span><span class="sxs-lookup"><span data-stu-id="a60fa-141">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="a60fa-142">Минимальные размеры цели 1–1,5 градуса позволяют пользователю успешно выполнять действия в большинстве случаев, однако цели размером 3 градуса зачастую обеспечивают большую скорость.</span><span class="sxs-lookup"><span data-stu-id="a60fa-142">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="a60fa-143">Обратите внимание, что пользовательские цели — это фактически двумерная область, даже если это трехмерный элемент: проекция, которая обращена к пользователю, будет областью, на которую можно нацелиться.</span><span class="sxs-lookup"><span data-stu-id="a60fa-143">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="a60fa-144">Предоставление явного указания того, что элемент "активен" (пользователь нацелен на него), крайне полезно. Таким указанием может быть видимый эффект "зависания", аудио подсказки или щелчки, а также четкое выравнивание курсора по элементу.</span><span class="sxs-lookup"><span data-stu-id="a60fa-144">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="a60fa-145">![Оптимальный размер целевого объекта на расстоянии 2 метра](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a60fa-145">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="a60fa-146">*Оптимальный размер целевого объекта на расстоянии 2 метра*</span><span class="sxs-lookup"><span data-stu-id="a60fa-146">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="a60fa-147">![Пример выделения выбранного взглядом целевого объекта](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a60fa-147">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="a60fa-148">*Пример выделения выбранного взглядом целевого объекта*</span><span class="sxs-lookup"><span data-stu-id="a60fa-148">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="a60fa-149">Размещение цели</span><span class="sxs-lookup"><span data-stu-id="a60fa-149">Target placement</span></span>

<span data-ttu-id="a60fa-150">У пользователей часто не получается найти элементы интерфейса, расположенные очень высоко или очень низко в поле зрения, поскольку они фокусируют большую часть своего внимания на областях вокруг своей основной цели (обычно приблизительно на уровне глаз).</span><span class="sxs-lookup"><span data-stu-id="a60fa-150">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="a60fa-151">Размещение большинства целей в приемлемом диапазоне примерно на уровне глаз может исправить ситуацию.</span><span class="sxs-lookup"><span data-stu-id="a60fa-151">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="a60fa-152">Учитывая склонность пользователей в любой момент фокусироваться на относительно небольшой визуальной области (область фокусировки внимания в поле зрения составляет приблизительно 10 градусов), группирование элементов интерфейса в такой мере, чтобы они были концептуально связаны, может задействовать поведение, связанное с перемещением внимания с объекта на объект, по мере перемещения взгляда пользователя по области.</span><span class="sxs-lookup"><span data-stu-id="a60fa-152">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="a60fa-153">При разработке интерфейса учитывайте возможные значительные отклонения в поле зрения HoloLens и иммерсивной гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="a60fa-153">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="a60fa-154">![Пример сгруппированных элементов интерфейса для упрощения нацеливания взглядом в Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a60fa-154">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="a60fa-155">*Пример сгруппированных элементов интерфейса для упрощения нацеливания взглядом в Galaxy Explorer*</span><span class="sxs-lookup"><span data-stu-id="a60fa-155">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="a60fa-156">Улучшение поведения выбора цели</span><span class="sxs-lookup"><span data-stu-id="a60fa-156">Improving targeting behaviors</span></span>

<span data-ttu-id="a60fa-157">Если намерение пользователя нацелиться на что-либо можно определить (или оценить с достаточной точностью), может быть полезно принимать попытки взаимодействия с "близким прохождением" за такие, что были нацелены правильно.</span><span class="sxs-lookup"><span data-stu-id="a60fa-157">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="a60fa-158">Существует несколько успешных методов, которые можно внедрить в интерфейсы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="a60fa-158">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="a60fa-159">Взгляните на стабилизации ("тяжесть Wells")</span><span class="sxs-lookup"><span data-stu-id="a60fa-159">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="a60fa-160">Это должно быть включено большую часть времени или все время.</span><span class="sxs-lookup"><span data-stu-id="a60fa-160">This should be turned on most/all of the time.</span></span> <span data-ttu-id="a60fa-161">Эта технология позволяет исключить естественные подергивания головы и шеи, которые могут возникать у пользователей.</span><span class="sxs-lookup"><span data-stu-id="a60fa-161">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="a60fa-162">Также движения из-за перемещения взгляда или говорения.</span><span class="sxs-lookup"><span data-stu-id="a60fa-162">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="a60fa-163">Алгоритмы ближайшего звена</span><span class="sxs-lookup"><span data-stu-id="a60fa-163">Closest link algorithms</span></span>

<span data-ttu-id="a60fa-164">Они лучше всего работают в областях с разреженным интерактивным содержимым.</span><span class="sxs-lookup"><span data-stu-id="a60fa-164">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="a60fa-165">Если существует высокая вероятность того, что вы можете определить, с чем пользователь намеревался взаимодействовать, вы можете дополнить его возможности нацеливания с помощью простого взятия на себя определенного уровня намерения.</span><span class="sxs-lookup"><span data-stu-id="a60fa-165">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="a60fa-166">Датирование действий прошлым/будущим числом</span><span class="sxs-lookup"><span data-stu-id="a60fa-166">Backdating/postdating actions</span></span>

<span data-ttu-id="a60fa-167">Этот механизм полезен для задач, требующих скорости.</span><span class="sxs-lookup"><span data-stu-id="a60fa-167">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="a60fa-168">Когда пользователь проходит через серию нацеливания или активацию манеуверс на скорости, может быть полезно предположить некоторую намерение и позволить *пропущенным действиям* работать с целевыми объектами, на которые пользователь находился в фокусе немного раньше или немного после нажатия кнопки (50 мс до/после эффективно в ходе раннего тестирования).</span><span class="sxs-lookup"><span data-stu-id="a60fa-168">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="a60fa-169">Сглаживание</span><span class="sxs-lookup"><span data-stu-id="a60fa-169">Smoothing</span></span>

<span data-ttu-id="a60fa-170">Этот механизм полезен для создания пути движений с уменьшением незначительных подергиваний/качаний, вызванных естественными характеристиками движений головы.</span><span class="sxs-lookup"><span data-stu-id="a60fa-170">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="a60fa-171">При сглаживании движений создания пути сглаживайте по размеру/расстоянию движения, а не по времени.</span><span class="sxs-lookup"><span data-stu-id="a60fa-171">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="a60fa-172">Магнитность</span><span class="sxs-lookup"><span data-stu-id="a60fa-172">Magnetism</span></span>

<span data-ttu-id="a60fa-173">Этот механизм можно рассматривать как более общую версию алгоритмов ближайшего звена: подведение курсора к цели и простое увеличение области задействования (как видимой, так и невидимой) при приближении пользователя к вероятной цели, использование определенных знаний о структуре для улучшения определения намерения пользователя.</span><span class="sxs-lookup"><span data-stu-id="a60fa-173">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="a60fa-174">Это может быть особенно эффективно для небольших целей.</span><span class="sxs-lookup"><span data-stu-id="a60fa-174">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="a60fa-175">Закрепление фокуса</span><span class="sxs-lookup"><span data-stu-id="a60fa-175">Focus stickiness</span></span>

<span data-ttu-id="a60fa-176">Предоставьте текущему элементу в фокусе преимущество при определении, на какой ближайший интерактивный элемент перевести фокус.</span><span class="sxs-lookup"><span data-stu-id="a60fa-176">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="a60fa-177">Это поможет снизить уровень хаотичной смены фокуса при остановке посередине между двумя элементами с естественным шумом.</span><span class="sxs-lookup"><span data-stu-id="a60fa-177">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="a60fa-178">См. также</span><span class="sxs-lookup"><span data-stu-id="a60fa-178">See also</span></span>
* [<span data-ttu-id="a60fa-179">Жесты</span><span class="sxs-lookup"><span data-stu-id="a60fa-179">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="a60fa-180">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="a60fa-180">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="a60fa-181">Курсоры</span><span class="sxs-lookup"><span data-stu-id="a60fa-181">Cursors</span></span>](cursors.md)
