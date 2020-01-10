---
title: Ограничивающий прямоугольник и панель приложений
description: Панель приложения — это меню уровня объекта, содержащее ряд кнопок, отображаемых на нижней границе границ голограммы.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, панель приложений, ограничивающий прямоугольник
ms.openlocfilehash: dab41207c2558fe8bb3fe07fca666cb2668f4e45
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723203"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="68215-104">Ограничивающий прямоугольник и панель приложений</span><span class="sxs-lookup"><span data-stu-id="68215-104">Bounding box and App bar</span></span>
<span data-ttu-id="68215-105">![ное ограничение является стандартным интерфейсом для манипулирования объектами в смешанной реальности.](images/UX/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="68215-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="68215-106">Что такое ограничивающий прямоугольник?</span><span class="sxs-lookup"><span data-stu-id="68215-106">What is the Bounding box?</span></span>

<span data-ttu-id="68215-107">Это стандартный интерфейс для манипуляций с объектами в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="68215-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="68215-108">Он предоставляет пользователю право на то, что объект в данный момент является изменяемым.</span><span class="sxs-lookup"><span data-stu-id="68215-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="68215-109">В HoloLens 2 ограничивающий прямоугольник работает с непосредственной манипуляцией и реагирует на финжер'с пользователя.</span><span class="sxs-lookup"><span data-stu-id="68215-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="68215-110">Он показывает визуальную обратную связь, которая помогает пользователю воспринимать расстояние от объекта.</span><span class="sxs-lookup"><span data-stu-id="68215-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="68215-111">Масштабирование объекта</span><span class="sxs-lookup"><span data-stu-id="68215-111">Scaling an object</span></span><br>
        <span data-ttu-id="68215-112">Углы ограничивающего прямоугольника указывают пользователю, что объект может масштабироваться.</span><span class="sxs-lookup"><span data-stu-id="68215-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="68215-113">Дескрипторы соответствуют широкому понятному шаблону для настройки масштабирования.</span><span class="sxs-lookup"><span data-stu-id="68215-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="68215-114">Этот визуальный доступ показывает пользователям общую область объекта, даже если он не виден за пределами режима коррекции.</span><span class="sxs-lookup"><span data-stu-id="68215-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="68215-115">Это особенно важно, так как в противном случае объект, привязанный к другому объекту или поверхности, может выглядеть так, как если бы на нем было недостаточно свободного пространства.</span><span class="sxs-lookup"><span data-stu-id="68215-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="68215-116">*Цикл видео: масштабирование объекта через ограничивающий прямоугольник*</span><span class="sxs-lookup"><span data-stu-id="68215-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="68215-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="68215-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="68215-118">![точки HoloLens — представление масштабирования объекта с помощью ограничивающего прямоугольника](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="68215-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="68215-119">Вращение объекта</span><span class="sxs-lookup"><span data-stu-id="68215-119">Rotating an object</span></span><br>
        <span data-ttu-id="68215-120">Вертикальная прямоугольная аффорданцес на краях ограничивающего прямоугольника — это индикаторы вращения.</span><span class="sxs-lookup"><span data-stu-id="68215-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="68215-121">Это дает пользователю более точную корректировку по своим голограммам.</span><span class="sxs-lookup"><span data-stu-id="68215-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="68215-122">Можно не только настраивать и масштабировать, но и теперь также вращать.</span><span class="sxs-lookup"><span data-stu-id="68215-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="68215-123">*Цикл видео: поворот объекта через ограничивающий прямоугольник*</span><span class="sxs-lookup"><span data-stu-id="68215-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="68215-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="68215-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="68215-125">![точку HoloLens для поворота объекта с помощью ограничивающего прямоугольника](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="68215-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="68215-126">Визуальная обратная связь с учетом расположения HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="68215-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="68215-127">В HoloLens 2 есть дополнительная визуальная подсказка, которая может помочь пользователю в восприятии глубины.</span><span class="sxs-lookup"><span data-stu-id="68215-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="68215-128">Кольцо рядом с ним отображается и масштабируется по мере того, как прокрутка будет ближе к объекту.</span><span class="sxs-lookup"><span data-stu-id="68215-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="68215-129">В конечном итоге, если достигнуто нажатое состояние, кольцо будет находиться в точке.</span><span class="sxs-lookup"><span data-stu-id="68215-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="68215-130">Этот визуальный подход позволяет пользователю понять, насколько далеко они от объекта.</span><span class="sxs-lookup"><span data-stu-id="68215-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="68215-131">*Цикл видео. пример визуальной обратной связи на основе сходства с ограничивающим прямоугольником*</span><span class="sxs-lookup"><span data-stu-id="68215-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="68215-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="68215-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="68215-133">![визуальной обратной связи](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="68215-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="68215-134">**Сведения о разработке приложений Unity см [. в разделе ограничивающий прямоугольник в наборе средств для смешанной реальности — Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="68215-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="68215-135">Что такое панель приложений?</span><span class="sxs-lookup"><span data-stu-id="68215-135">What is the App bar?</span></span>

<span data-ttu-id="68215-136">Панель приложения — это меню уровня объекта, содержащее ряд кнопок, отображаемых на нижней границе границ голограммы.</span><span class="sxs-lookup"><span data-stu-id="68215-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="68215-137">Этот шаблон обычно используется для предоставления пользователям возможности удалять и изменять голограммы.</span><span class="sxs-lookup"><span data-stu-id="68215-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="68215-138">Панель приложений была разработана в основном как способ управления размещенными объектами в среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="68215-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="68215-139">В сочетании с ограничивающим прямоугольником пользователь имеет полный контроль над тем, где и как объекты ориентированы в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="68215-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="68215-140">Панель приложений следует за пользователем</span><span class="sxs-lookup"><span data-stu-id="68215-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="68215-141">Так как этот шаблон используется с объектами, которые заблокированы в мире, по мере того как пользователь перемещается по объекту, панель приложения всегда будет отображаться на стороне объектов, ближайшей к пользователю.</span><span class="sxs-lookup"><span data-stu-id="68215-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="68215-142">Хотя это и не является объявлением, оно эффективно достигает того же результата; запрет на положение пользователя в окклуде или блокировать функциональность, которая в противном случае будет доступна из другого расположения в своей среде.</span><span class="sxs-lookup"><span data-stu-id="68215-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="68215-143">*Цикл видео. обходится голограмма, следующая панель приложения*</span><span class="sxs-lookup"><span data-stu-id="68215-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="68215-144">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="68215-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="68215-145">![обходится голограмма.</span><span class="sxs-lookup"><span data-stu-id="68215-145">![Walking around a hologram.</span></span> <span data-ttu-id="68215-146">Ниже приведена панель приложений.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="68215-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="68215-147">Ограничивающий прямоугольник в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="68215-147">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="68215-148">**[Мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет скрипты и Prefabs для ограничивающего прямоугольника и панели приложений.</span><span class="sxs-lookup"><span data-stu-id="68215-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="68215-149">Можно добавить ограничивающий прямоугольник, просто назначив сценарий BoundingBox.cs на любой объект.</span><span class="sxs-lookup"><span data-stu-id="68215-149">You can add a Bounding box by simply assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="68215-150">МРТК-ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="68215-150">MRTK - Bounding Box</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="68215-151">См. также статью</span><span class="sxs-lookup"><span data-stu-id="68215-151">See also</span></span>

* [<span data-ttu-id="68215-152">Курсоры</span><span class="sxs-lookup"><span data-stu-id="68215-152">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="68215-153">Телекинез</span><span class="sxs-lookup"><span data-stu-id="68215-153">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="68215-154">Button</span><span class="sxs-lookup"><span data-stu-id="68215-154">Button</span></span>](button.md)
* [<span data-ttu-id="68215-155">Активный объект</span><span class="sxs-lookup"><span data-stu-id="68215-155">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="68215-156">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="68215-156">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="68215-157">Оперирование</span><span class="sxs-lookup"><span data-stu-id="68215-157">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="68215-158">Меню руки</span><span class="sxs-lookup"><span data-stu-id="68215-158">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="68215-159">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="68215-159">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="68215-160">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="68215-160">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="68215-161">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="68215-161">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="68215-162">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="68215-162">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="68215-163">Подсказка</span><span class="sxs-lookup"><span data-stu-id="68215-163">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="68215-164">Планшет</span><span class="sxs-lookup"><span data-stu-id="68215-164">Slate</span></span>](slate.md)
* [<span data-ttu-id="68215-165">Ползунок</span><span class="sxs-lookup"><span data-stu-id="68215-165">Slider</span></span>](slider.md)
* [<span data-ttu-id="68215-166">Шейдер</span><span class="sxs-lookup"><span data-stu-id="68215-166">Shader</span></span>](shader.md)
* [<span data-ttu-id="68215-167">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="68215-167">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="68215-168">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="68215-168">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="68215-169">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="68215-169">Surface magnetism</span></span>](surface-magnetism.md)
