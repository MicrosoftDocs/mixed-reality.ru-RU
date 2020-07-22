---
title: Непосредственное манипулирование руками
description: Обзор модели ввода с помощью непосредственного манипулирования
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hands near, HoloLens
ms.openlocfilehash: 2a63f53464e354ae49f8c63fafbf592508bd5e3b
ms.sourcegitcommit: 0eb99fae933d4374af2c032af4e9ceda1807e532
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86156785"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="d022a-104">Непосредственное манипулирование руками</span><span class="sxs-lookup"><span data-stu-id="d022a-104">Direct manipulation with hands</span></span>

![Кнопка](images/UX/UX_Hero_Manipulation.jpg)

<span data-ttu-id="d022a-106">Непосредственное манипулирование —это модель ввода, которая предполагает прикосновение к голограммам непосредственно руками.</span><span class="sxs-lookup"><span data-stu-id="d022a-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="d022a-107">Суть этого принципа состоит в том, что объекты ведут себя так же, как в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="d022a-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="d022a-108">Кнопки можно активировать, просто нажимая их, объекты можно выбирать, хватая их, а двумерное содержимое ведет себя как виртуальный сенсорный экран.</span><span class="sxs-lookup"><span data-stu-id="d022a-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="d022a-109">Поэтому пользователям легко и интересно осваивать непосредственное манипулирование.</span><span class="sxs-lookup"><span data-stu-id="d022a-109">This makes direct manipulation easy for users to learn, and fun.</span></span> <span data-ttu-id="d022a-110">Оно считается моделью "ближнего" ввода. Это означает, что непосредственное манипулирование лучше всего использовать для взаимодействия с содержимым, которое находится в пределах досягаемости.</span><span class="sxs-lookup"><span data-stu-id="d022a-110">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

<span data-ttu-id="d022a-111">Непосредственное манипулирование основано на возможностях интерфейса, и оно удобно для пользователей.</span><span class="sxs-lookup"><span data-stu-id="d022a-111">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="d022a-112">Оно не подразумевает символические жесты.</span><span class="sxs-lookup"><span data-stu-id="d022a-112">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="d022a-113">Все взаимодействия построены вокруг визуального элемента, который вы можете тронуть или схватить.</span><span class="sxs-lookup"><span data-stu-id="d022a-113">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="d022a-114">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="d022a-114">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="d022a-115"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="d022a-115"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="d022a-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d022a-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="d022a-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d022a-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="d022a-118"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="d022a-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="d022a-119">Непосредственное манипулирование руками</span><span class="sxs-lookup"><span data-stu-id="d022a-119">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="d022a-120">❌ Не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="d022a-120">❌ Not supported</span></span></td>
     <td><span data-ttu-id="d022a-121">✔️ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="d022a-121">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="d022a-122">➕ Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="d022a-122">➕ Supported.</span></span>  <span data-ttu-id="d022a-123">Для пользовательского интерфейса рекомендуем использовать <a href="point-and-commit.md">наведение и фиксацию с помощью рук</a>.</span><span class="sxs-lookup"><span data-stu-id="d022a-123">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="d022a-124">Непосредственное манипулирование является основной моделью ввода в HoloLens 2, где используется новая система отслеживания рук.</span><span class="sxs-lookup"><span data-stu-id="d022a-124">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="d022a-125">Модель ввода также доступна для иммерсивных гарнитур благодаря использованию контроллеров движения, но не рекомендуется в качестве основного средства взаимодействия вне манипулирования объектами.</span><span class="sxs-lookup"><span data-stu-id="d022a-125">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="d022a-126">Непосредственное манипулирование недоступно в HoloLens (1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="d022a-126">Direct manipulation is not available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="d022a-127">Кончик пальца с обратной связью</span><span class="sxs-lookup"><span data-stu-id="d022a-127">Collidable fingertip</span></span>

<span data-ttu-id="d022a-128">На устройстве HoloLens 2 руки пользователя распознаются и интерпретируются как модели скелета левой и правой руки.</span><span class="sxs-lookup"><span data-stu-id="d022a-128">On HoloLens 2, the user's hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="d022a-129">Чтобы реализовать идею прикосновения к голограммам непосредственно с помощью рук, в идеале можно прикрепить пять индикаторов обратной связи к пяти кончикам пальцев каждой скелетной модели руки.</span><span class="sxs-lookup"><span data-stu-id="d022a-129">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="d022a-130">Однако из-за отсутствия тактильной обратной связи десяти кончиков пальцев с обратной связью вызывали неожиданные и непредсказуемые столкновения с голограммами.</span><span class="sxs-lookup"><span data-stu-id="d022a-130">However, due to the lack of tactile feedback, ten collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="d022a-131">Следовательно, мы предлагаем размещать индикатор обратной связи только на каждый указательный палец.</span><span class="sxs-lookup"><span data-stu-id="d022a-131">Hence, we suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="d022a-132">Кончики указательных пальцев с обратной связью могут по-прежнему служить активными точками касания для различных жестов с участием других пальцев, таких как нажатие одним пальцем, касание одним пальцем, нажатие двумя пальцами и нажатие 5 пальцами, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d022a-132">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as One-finger press, One-finger tap, Two-finger press and Five-finger press, as shown in the image below.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d022a-133">![Кончик пальца с обратной связью](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-133">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="d022a-134">**Кончик пальца с обратной связью**</span><span class="sxs-lookup"><span data-stu-id="d022a-134">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-135">![Нажатие одним пальцем](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-135">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="d022a-136">**Нажатие одним пальцем**</span><span class="sxs-lookup"><span data-stu-id="d022a-136">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-137">![Касание одним пальцем](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-137">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="d022a-138">**Касание одним пальцем**</span><span class="sxs-lookup"><span data-stu-id="d022a-138">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-139">![Нажатие пятью пальцами](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-139">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="d022a-140">**Нажатие пятью пальцами**</span><span class="sxs-lookup"><span data-stu-id="d022a-140">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="d022a-141">Сферический индикатор обратной связи</span><span class="sxs-lookup"><span data-stu-id="d022a-141">Sphere collider</span></span>

<span data-ttu-id="d022a-142">Вместо случайной универсальной формы мы предлагаем использовать сферический индикатор обратной связи</span><span class="sxs-lookup"><span data-stu-id="d022a-142">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="d022a-143">и визуализировать его, чтобы обеспечить лучшее восприятие ближнего прицеливания.</span><span class="sxs-lookup"><span data-stu-id="d022a-143">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="d022a-144">Диаметр сферы должен соответствовать толщине указательного пальца, чтобы повысить точность касания.</span><span class="sxs-lookup"><span data-stu-id="d022a-144">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="d022a-145">Получить переменную толщину пальца будет легче, вызвав API для работы с руками.</span><span class="sxs-lookup"><span data-stu-id="d022a-145">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="d022a-146">Курсор для кончика пальца</span><span class="sxs-lookup"><span data-stu-id="d022a-146">Fingertip cursor</span></span>

<span data-ttu-id="d022a-147">Помимо рендеринга интерактивной сферы для кончика указательного пальца, мы создали продвинутый курсор для кончика пальца, чтобы оптимизировать возможности ближнего прицеливания.</span><span class="sxs-lookup"><span data-stu-id="d022a-147">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to interactively achieve a better near-targeting experience.</span></span> <span data-ttu-id="d022a-148">Это указатель в форме кольца, прикрепленный к кончику указательного пальца.</span><span class="sxs-lookup"><span data-stu-id="d022a-148">It is a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="d022a-149">По мере приближения он динамически реагирует на цель с точки зрения ориентации и размера, как описано ниже:</span><span class="sxs-lookup"><span data-stu-id="d022a-149">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="d022a-150">Когда указательный палец приближается к голограмме, курсор всегда параллелен поверхности голограммы и постепенно соответственно уменьшается в размере.</span><span class="sxs-lookup"><span data-stu-id="d022a-150">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="d022a-151">Как только палец касается поверхности, курсор сжимается до точки и создается событие касания.</span><span class="sxs-lookup"><span data-stu-id="d022a-151">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="d022a-152">Благодаря интерактивной обратной связи пользователи могут достигать высокой точности при выполнении задач ближнего прицеливания, таких как запуск гиперссылки на странице или нажатие кнопки, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="d022a-152">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="d022a-153">![Курсор для кончика пальца вдали](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-153">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="d022a-154">**Курсор для кончика пальца вдали**</span><span class="sxs-lookup"><span data-stu-id="d022a-154">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-155">![Курсор для кончика пальца близко](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-155">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="d022a-156">**Курсор для кончика пальца близко**</span><span class="sxs-lookup"><span data-stu-id="d022a-156">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-157">![Контакт курсора для кончика пальца](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-157">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="d022a-158">**Контакт курсора для кончика пальца**</span><span class="sxs-lookup"><span data-stu-id="d022a-158">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="d022a-159">Ограничивающая рамка с шейдером приближения</span><span class="sxs-lookup"><span data-stu-id="d022a-159">Bounding box with proximity shader</span></span>

<span data-ttu-id="d022a-160">Для самой голограммы также требуется способность обеспечивать как визуальную, так и звуковую обратную связь, чтобы компенсировать отсутствие тактильной обратной связи.</span><span class="sxs-lookup"><span data-stu-id="d022a-160">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="d022a-161">Для этого мы придумали концепцию ограничивающей рамки с шейдером приближения.</span><span class="sxs-lookup"><span data-stu-id="d022a-161">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="d022a-162">Ограничивающая рамка — это минимальная объемная область, включающая трехмерный объект.</span><span class="sxs-lookup"><span data-stu-id="d022a-162">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="d022a-163">Ограничивающая рамка имеет интерактивный механизм визуализации, называемый шейдером приближения.</span><span class="sxs-lookup"><span data-stu-id="d022a-163">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="d022a-164">Поведение шейдера приближения:</span><span class="sxs-lookup"><span data-stu-id="d022a-164">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d022a-165">![Наведение (издали) с визуальной обратной связью](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-165">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="d022a-166">**Наведение (издали)**</span><span class="sxs-lookup"><span data-stu-id="d022a-166">**Hover (far)**</span></span><br>
       <span data-ttu-id="d022a-167">Когда указательный палец находится в пределах диапазона, указатель кончика пальца проецируется на поверхность ограничивающей рамки.</span><span class="sxs-lookup"><span data-stu-id="d022a-167">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-168">![Наведение (вблизи) с визуальной обратной связью](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-168">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="d022a-169">**Наведение (вблизи)**</span><span class="sxs-lookup"><span data-stu-id="d022a-169">**Hover (near)**</span></span><br>
        <span data-ttu-id="d022a-170">Когда кончик пальца приближается к поверхности, указатель сжимается соответственно.</span><span class="sxs-lookup"><span data-stu-id="d022a-170">When the fingertip gets closer to the surface, the spotlight shrinks accordingly.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-171">![Контакт начинается](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-171">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="d022a-172">**Контакт начинается**</span><span class="sxs-lookup"><span data-stu-id="d022a-172">**Contact begins**</span></span><br>
       <span data-ttu-id="d022a-173">Как только кончик пальца коснется поверхности, вся ограничивающая рамка изменит цвет или создаст визуальный эффект для индикации состояния касания.</span><span class="sxs-lookup"><span data-stu-id="d022a-173">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-174">![Контакт завершается](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-174">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="d022a-175">**Контакт завершается**</span><span class="sxs-lookup"><span data-stu-id="d022a-175">**Contact ends**</span></span><br>
       <span data-ttu-id="d022a-176">Для усиления визуальной обратной связи касания можно активировать звуковой эффект.</span><span class="sxs-lookup"><span data-stu-id="d022a-176">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="d022a-177">Нажимаемая кнопка</span><span class="sxs-lookup"><span data-stu-id="d022a-177">Pressable button</span></span>

<span data-ttu-id="d022a-178">Благодаря обратной связи с помощью кончика пальца пользователи могут взаимодействовать с основополагающим компонентом голографического интерфейса — нажимаемой кнопкой.</span><span class="sxs-lookup"><span data-stu-id="d022a-178">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="d022a-179">Нажимаемая кнопка — это голографическая кнопка, предназначенная для непосредственного нажатия пальцем.</span><span class="sxs-lookup"><span data-stu-id="d022a-179">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="d022a-180">Опять же, из-за отсутствия тактильной обратной связи нажимаемая кнопка оснащена несколькими механизмами для решения проблем, связанных с тактильной обратной связью.</span><span class="sxs-lookup"><span data-stu-id="d022a-180">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="d022a-181">Первый механизм — это ограничивающий прямоугольник с шейдером приближения. Этот механизм подробно описан в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="d022a-181">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="d022a-182">Он служит для того, чтобы пользователи чувствовали приближение и контакт с кнопкой.</span><span class="sxs-lookup"><span data-stu-id="d022a-182">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="d022a-183">Второй механизм — надавливание.</span><span class="sxs-lookup"><span data-stu-id="d022a-183">The second mechanism is depression.</span></span> <span data-ttu-id="d022a-184">Он создает ощущение нажатия после контакта пальца с кнопкой.</span><span class="sxs-lookup"><span data-stu-id="d022a-184">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="d022a-185">Механизм обеспечивает перемещение кнопки вплотную к кончику пальца вдоль оси глубины.</span><span class="sxs-lookup"><span data-stu-id="d022a-185">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="d022a-186">Кнопка может сработать, когда она достигает заданной глубины (при нажатии) или поднимается (при отпускании) после прохождения через нее.</span><span class="sxs-lookup"><span data-stu-id="d022a-186">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="d022a-187">Для улучшения обратной связи нужно добавить звуковой эффект, активируемый при нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="d022a-187">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d022a-188">![Нажимаемая кнопка вдали](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-188">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="d022a-189">**Палец вдали**</span><span class="sxs-lookup"><span data-stu-id="d022a-189">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-190">![Нажимаемая кнопка близко](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-190">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="d022a-191">**Палец приближается**</span><span class="sxs-lookup"><span data-stu-id="d022a-191">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-192">![Начинается контакт с нажимаемой кнопкой](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-192">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="d022a-193">**Контакт начинается**</span><span class="sxs-lookup"><span data-stu-id="d022a-193">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-194">![Нажатие нажимаемой кнопки](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-194">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="d022a-195">**Нажатие**</span><span class="sxs-lookup"><span data-stu-id="d022a-195">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="d022a-196">Взаимодействие с двумерным экраном</span><span class="sxs-lookup"><span data-stu-id="d022a-196">2D slate interaction</span></span>

<span data-ttu-id="d022a-197">Двухмерный [экран](slate.md) — это голографический контейнер, используемый для размещения содержимого двухмерных приложений, таких как веб-браузер.</span><span class="sxs-lookup"><span data-stu-id="d022a-197">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="d022a-198">Концепция для взаимодействия с двумерным экраном с помощью непосредственного манипулирования заключается в применении мысленной модели взаимодействия с физическим сенсорным экраном.</span><span class="sxs-lookup"><span data-stu-id="d022a-198">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="d022a-199">Для взаимодействия с экраном планшета:</span><span class="sxs-lookup"><span data-stu-id="d022a-199">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d022a-200">![Сенсорный ввод](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-200">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="d022a-201">**Сенсорный ввод**</span><span class="sxs-lookup"><span data-stu-id="d022a-201">**Touch**</span></span><br>
       <span data-ttu-id="d022a-202">Используйте указательный палец, чтобы нажать гиперссылку или кнопку.</span><span class="sxs-lookup"><span data-stu-id="d022a-202">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-203">![Прокрутка](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-203">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="d022a-204">**Прокрутка**</span><span class="sxs-lookup"><span data-stu-id="d022a-204">**Scroll**</span></span><br>
        <span data-ttu-id="d022a-205">Используйте указательный палец для прокрутки содержимого экрана вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="d022a-205">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-206">![Масштабирование](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="d022a-207">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="d022a-207">**Zoom**</span></span><br>
       <span data-ttu-id="d022a-208">С помощью двух указательных пальцев пользователя можно увеличивать и уменьшать содержимое экрана в соответствии с относительным движением пальцев.</span><span class="sxs-lookup"><span data-stu-id="d022a-208">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="d022a-209">Для манипуляции самим двумерным экраном планшета:</span><span class="sxs-lookup"><span data-stu-id="d022a-209">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d022a-210">![Перемещение](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-210">![Move](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="d022a-211">**Перемещение**</span><span class="sxs-lookup"><span data-stu-id="d022a-211">**Move**</span></span><br>
       <span data-ttu-id="d022a-212">Поднесите руки к углам и краям, чтобы выявить самые близкие возможности для манипуляции.</span><span class="sxs-lookup"><span data-stu-id="d022a-212">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="d022a-213">Захватите голографическую панель в верхней части двумерного экрана планшета, что позволит переместить весь экран.</span><span class="sxs-lookup"><span data-stu-id="d022a-213">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-214">![Масштабирование](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-214">![Scale](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="d022a-215">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="d022a-215">**Scale**</span></span><br>
        <span data-ttu-id="d022a-216">Захватите возможности для манипуляции и выполните равномерное масштабирование с помощью угловых возможностей.</span><span class="sxs-lookup"><span data-stu-id="d022a-216">Grab the manipulation affordances and perform uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-217">![Адаптация](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-217">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="d022a-218">**Адаптация**</span><span class="sxs-lookup"><span data-stu-id="d022a-218">**Reflow**</span></span><br>
       <span data-ttu-id="d022a-219">Захватите возможности для манипуляции и выполните адаптацию с помощью крайних возможностей.</span><span class="sxs-lookup"><span data-stu-id="d022a-219">Grab the manipulation affordances and perform reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="d022a-220">Манипуляция трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="d022a-220">3D object manipulation</span></span>

<span data-ttu-id="d022a-221">HoloLens 2 позволяет пользователям с помощью рук управлять трехмерными голографическими объектами, применяя ограничивающий прямоугольник к каждому такому объекту.</span><span class="sxs-lookup"><span data-stu-id="d022a-221">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="d022a-222">Ограничивающая рамка обеспечивает лучшее восприятие глубины благодаря шейдеру приближения.</span><span class="sxs-lookup"><span data-stu-id="d022a-222">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="d022a-223">С ограничивающей рамкой доступно два подхода для манипулирования трехмерными объектами.</span><span class="sxs-lookup"><span data-stu-id="d022a-223">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="d022a-224">Манипуляция на основе возможностей</span><span class="sxs-lookup"><span data-stu-id="d022a-224">Affordance-based manipulation</span></span>

<span data-ttu-id="d022a-225">Манипулирование на основе возможностей позволяет манипулировать трехмерным объектом с помощью ограничивающей рамки и возможностей для манипулирования вокруг него.</span><span class="sxs-lookup"><span data-stu-id="d022a-225">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="d022a-226">![Перемещение](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-226">![Move](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="d022a-227">**Перемещение**</span><span class="sxs-lookup"><span data-stu-id="d022a-227">**Move**</span></span><br>
       <span data-ttu-id="d022a-228">Как только рука пользователя приближается к трехмерному объекту, появляются ограничивающая рамка и ближайшая возможность.</span><span class="sxs-lookup"><span data-stu-id="d022a-228">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="d022a-229">Пользователи могут захватить ограничивающий прямоугольник, чтобы переместить весь объект.</span><span class="sxs-lookup"><span data-stu-id="d022a-229">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-230">![Поворот](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-230">![Rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="d022a-231">**Поворот**</span><span class="sxs-lookup"><span data-stu-id="d022a-231">**Rotate**</span></span><br>
        <span data-ttu-id="d022a-232">Пользователи могут захватить крайние возможности, чтобы выполнить поворот.</span><span class="sxs-lookup"><span data-stu-id="d022a-232">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-233">![Масштабирование](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-233">![Scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="d022a-234">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="d022a-234">**Scale**</span></span><br>
       <span data-ttu-id="d022a-235">Пользователи могут захватить угловые возможности, чтобы выполнить равномерное масштабирование.</span><span class="sxs-lookup"><span data-stu-id="d022a-235">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="d022a-236">Манипуляция без использования возможностей</span><span class="sxs-lookup"><span data-stu-id="d022a-236">Non-affordance based manipulation</span></span>

<span data-ttu-id="d022a-237">При таком манипулировании возможности не прикрепляются к ограничивающей рамке.</span><span class="sxs-lookup"><span data-stu-id="d022a-237">Non-affordance-based manipulation does not attach affordance to the bounding box.</span></span> <span data-ttu-id="d022a-238">Пользователи могут только отобразить ограничивающую рамку, а затем напрямую взаимодействовать с ней.</span><span class="sxs-lookup"><span data-stu-id="d022a-238">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="d022a-239">Если ограничивающая рамка захватывается одной рукой, перемещение и вращение объекта связаны с движением и ориентацией руки.</span><span class="sxs-lookup"><span data-stu-id="d022a-239">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="d022a-240">Когда объект хватается двумя руками, пользователи могут переносить, масштабировать и вращать его в соответствии с относительными движениями двух рук.</span><span class="sxs-lookup"><span data-stu-id="d022a-240">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="d022a-241">Для определенных манипуляций требуется точность.</span><span class="sxs-lookup"><span data-stu-id="d022a-241">Specific manipulation requires precision.</span></span> <span data-ttu-id="d022a-242">Рекомендуется использовать **манипулирование на основе возможностей**, так как оно обеспечивает высокий уровень точности.</span><span class="sxs-lookup"><span data-stu-id="d022a-242">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="d022a-243">Для гибкого манипулирования мы рекомендуем использовать **манипулирование без использования возможностей**, так как оно позволяет получить мгновенные и забавные эффекты.</span><span class="sxs-lookup"><span data-stu-id="d022a-243">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="d022a-244">Инстинктивные жесты</span><span class="sxs-lookup"><span data-stu-id="d022a-244">Instinctual gestures</span></span>

<span data-ttu-id="d022a-245">При работе с HoloLens (1-го поколения) мы обучили пользователей нескольким предопределенным жестам, таким как раскрытие ладони и касание.</span><span class="sxs-lookup"><span data-stu-id="d022a-245">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="d022a-246">В случае с HoloLens 2 мы не просим пользователей запоминать какие-либо символические жесты.</span><span class="sxs-lookup"><span data-stu-id="d022a-246">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="d022a-247">Все необходимые жесты пользователя, с помощью которых можно взаимодействовать с голограммами и содержимым, являются инстинктивными.</span><span class="sxs-lookup"><span data-stu-id="d022a-247">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="d022a-248">Способ достижения инстинктивного жеста состоит в том, чтобы побуждать пользователей выполнять жесты на основе дизайна возможностей пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d022a-248">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="d022a-249">Например, если нам требуется, чтобы пользователь захватил объект или контрольную точку двумя пальцами, объект или контрольная точка должны быть маленькими.</span><span class="sxs-lookup"><span data-stu-id="d022a-249">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="d022a-250">Если мы хотим, чтобы пользователь захватил элемент пятью пальцами, объект или контрольная точка должны быть относительно большими.</span><span class="sxs-lookup"><span data-stu-id="d022a-250">If we want the user to perform five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="d022a-251">Как и при работе с настоящими кнопками, крошечную кнопку пользователь нажмет одним пальцем, в то время как большая кнопка будет побуждать пользователей нажимать ее ладонью.</span><span class="sxs-lookup"><span data-stu-id="d022a-251">Similar to buttons, a tiny button would limit users to press it with a single finger; a large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="d022a-252">![Перемещение](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-252">![Move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="d022a-253">**Маленький объект**</span><span class="sxs-lookup"><span data-stu-id="d022a-253">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-254">![Поворот](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-254">![Rotate](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="d022a-255">**Средний объект**</span><span class="sxs-lookup"><span data-stu-id="d022a-255">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d022a-256">![Масштабирование](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="d022a-256">![Scale](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="d022a-257">**Крупный объект**</span><span class="sxs-lookup"><span data-stu-id="d022a-257">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="d022a-258">Симметричный дизайн для работы с помощью рук и контроллеров с шестью степенями свободы</span><span class="sxs-lookup"><span data-stu-id="d022a-258">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="d022a-259">Возможно, вы заметили параллели при взаимодействии с помощью рук в дополненной реальности и контроллерами движений в виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="d022a-259">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="d022a-260">Оба способа ввода можно использовать для выполнения непосредственного манипулирования в соответствующих средах.</span><span class="sxs-lookup"><span data-stu-id="d022a-260">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="d022a-261">В HoloLens 2 захват и перетаскивание руками на близком расстоянии работает почти так же, как кнопка захвата на контроллерах движения в WMR.</span><span class="sxs-lookup"><span data-stu-id="d022a-261">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="d022a-262">Это позволяет пользователям лучше понять разницу взаимодействия между двумя платформами и может оказаться полезным, если вы когда-нибудь решите перенести свое приложение из одной из них в другую.</span><span class="sxs-lookup"><span data-stu-id="d022a-262">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application from one to the other.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="d022a-263">Оптимизация с помощью отслеживания глаз</span><span class="sxs-lookup"><span data-stu-id="d022a-263">Optimize with eye tracking</span></span>

<span data-ttu-id="d022a-264">Непосредственное манипулирование может показаться магией, если оно работает так, как задумано.</span><span class="sxs-lookup"><span data-stu-id="d022a-264">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="d022a-265">Но если при любом движении рук непреднамеренно активируется голограмма, это может раздражать.</span><span class="sxs-lookup"><span data-stu-id="d022a-265">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="d022a-266">Отслеживание глаз потенциально может помочь лучше определить намерения пользователя.</span><span class="sxs-lookup"><span data-stu-id="d022a-266">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="d022a-267">**Если**. Уменьшение непреднамеренного срабатывания ответа на действие манипулирования.</span><span class="sxs-lookup"><span data-stu-id="d022a-267">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="d022a-268">Отслеживание глаз позволяет лучше понять, что в настоящее время интересует пользователя.</span><span class="sxs-lookup"><span data-stu-id="d022a-268">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="d022a-269">Например, представьте, что вы читаете голографический (учебный) текст и протягиваете руку, чтобы схватить реальный рабочий инструмент.</span><span class="sxs-lookup"><span data-stu-id="d022a-269">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="d022a-270">Таким образом, вы случайно перемещаете руку над различными интерактивными голографическими кнопками, на которые вы не обращали внимания (например, они могут быть вне поля зрения пользователя).</span><span class="sxs-lookup"><span data-stu-id="d022a-270">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (e.g. it  may be outside the user's field-of-view (FoV)).</span></span>

  <span data-ttu-id="d022a-271">Говоря кратко, если пользователь некоторое время не смотрел на голограмму, но было обнаружено событие касания или захвата, вероятно, пользователь фактически не намеревался взаимодействовать с этой голограммой.</span><span class="sxs-lookup"><span data-stu-id="d022a-271">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="d022a-272">**Который элемент**.  Помимо ложноположительных активаций, иногда требуется более совершенное определение голограмм, которые нужно захватить или активировать, так как точная точка пересечения может быть неясной с вашей точки зрения, особенно если несколько голограмм расположены близко друг к другу.</span><span class="sxs-lookup"><span data-stu-id="d022a-272">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="d022a-273">Хотя отслеживание глаз в HoloLens 2 имеет ограничение точности определения вашего взгляда, оно все равно может быть очень полезно для близких взаимодействий из-за дисбаланса глубины при взаимодействии посредством ввода руками.</span><span class="sxs-lookup"><span data-stu-id="d022a-273">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span> <span data-ttu-id="d022a-274">Это означает, что иногда трудно определить, где находится ваша рука (позади или перед голограммой), чтобы, например, точно захватить виджет манипулирования.</span><span class="sxs-lookup"><span data-stu-id="d022a-274">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="d022a-275">**Где**. Использование информации о том, на что смотрит пользователь, выполняющий быстрые жесты.</span><span class="sxs-lookup"><span data-stu-id="d022a-275">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="d022a-276">Захватите голограмму и небрежно переместите ее в место назначения.</span><span class="sxs-lookup"><span data-stu-id="d022a-276">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="d022a-277">Иногда это работает, однако быстрое выполнение жестов руками может привести к очень неточному определению направлений.</span><span class="sxs-lookup"><span data-stu-id="d022a-277">While this sometimes works, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="d022a-278">Тем не менее, отслеживание глаз может повысить точность жестов.</span><span class="sxs-lookup"><span data-stu-id="d022a-278">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="d022a-279">Манипуляции в MRTK (наборе средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="d022a-279">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="d022a-280">В **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** можно легко настроить типичное поведение при манипуляции, используя скрипт **ObjectManipulator**.</span><span class="sxs-lookup"><span data-stu-id="d022a-280">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="d022a-281">Благодаря ObjectManipulator можно захватывать и перемещать объекты непосредственно руками или с помощью телекинеза.</span><span class="sxs-lookup"><span data-stu-id="d022a-281">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="d022a-282">Этот скрипт также поддерживает манипуляции двумя руками для масштабирования и поворота объекта.</span><span class="sxs-lookup"><span data-stu-id="d022a-282">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="d022a-283">MRTK — манипуляции</span><span class="sxs-lookup"><span data-stu-id="d022a-283">MRTK - Manipulation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)


---

## <a name="see-also"></a><span data-ttu-id="d022a-284">См. также статью</span><span class="sxs-lookup"><span data-stu-id="d022a-284">See also</span></span>

* [<span data-ttu-id="d022a-285">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="d022a-285">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="d022a-286">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="d022a-286">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="d022a-287">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="d022a-287">Instinctual interactions</span></span>](interaction-fundamentals.md)
