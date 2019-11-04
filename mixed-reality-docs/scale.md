---
title: Масштаб
description: Ключом к отображению содержимого, которое выглядит реалистично в виде голограммы, является как можно более точная имитация визуальных статистических данных реального мира.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, стиль, Дизайн
ms.openlocfilehash: eeec28fbf98cf4386a57cde4452cd3f8977d7780
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437504"
---
# <a name="scale"></a><span data-ttu-id="50006-104">Масштаб</span><span class="sxs-lookup"><span data-stu-id="50006-104">Scale</span></span>

<span data-ttu-id="50006-105">Ключом к отображению содержимого, которое выглядит реалистично в виде голограммы, является как можно более точная имитация визуальных статистических данных реального мира.</span><span class="sxs-lookup"><span data-stu-id="50006-105">A key to displaying content that looks realistic in holographic form is to mimic the visual statistics of the real world as closely as possible.</span></span> <span data-ttu-id="50006-106">Это означает обработку как можно большего числа значимых визуальных подсказок (из реального мира), чтобы понять, где находятся объекты, насколько они велики и из его они сделаны.</span><span class="sxs-lookup"><span data-stu-id="50006-106">This means incorporating as many of the visual cues as we can that help us (in the real world) understand where objects are, how big they are, and what they’re made of.</span></span> <span data-ttu-id="50006-107">Масштаб объекта — одна из наиболее важных визуальных подсказок, позволяющая средству просмотра понять размер объекта, а также подсказки в его расположении (особенно для объектов, имеющих известный размер).</span><span class="sxs-lookup"><span data-stu-id="50006-107">The scale of an object is one of the most important of those visual cues, giving a viewer a sense of the size of an object as well as cues to its location (especially for objects which have a known size).</span></span> <span data-ttu-id="50006-108">Кроме того, просмотр объектов в реальном масштабе наблюдался как один из основных принципов работы с различными преимуществами для смешанной реальности, что не было возможно при просмотре на основе экрана ранее.</span><span class="sxs-lookup"><span data-stu-id="50006-108">Further, viewing objects at real scale has been seen as one of the key experience differentiators for mixed reality in general – something that hasn’t been possible on screen-based viewing previously.</span></span>

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a><span data-ttu-id="50006-109">Как предложить масштаб объектов и сред</span><span class="sxs-lookup"><span data-stu-id="50006-109">How to suggest the scale of objects and environments</span></span>

<span data-ttu-id="50006-110">Существует множество способов предложить масштаб объекта, некоторые из которых имеют возможные последствия для других искусственного факторов.</span><span class="sxs-lookup"><span data-stu-id="50006-110">There are many ways to suggest the scale of an object, some of which have possible effects on other perceptual factors.</span></span> <span data-ttu-id="50006-111">Основной целью является простое отображение объектов в реальном размере и поддержание этого реалистичного размера по мере перемещения пользователей.</span><span class="sxs-lookup"><span data-stu-id="50006-111">The key one is to simply display objects at a ‘real’ size, and maintain that realistic size as users move.</span></span> <span data-ttu-id="50006-112">Это означает, что голограммы будут занимать другую часть визуального угла пользователя по мере того, как они появляются ближе или дальше, так же, как и реальные объекты.</span><span class="sxs-lookup"><span data-stu-id="50006-112">This means holograms will take up a different amount of a user’s visual angle of a user as they come closer or further away, the same way that real objects do.</span></span>

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a><span data-ttu-id="50006-113">Использование расстояния от объектов по мере их представления пользователю</span><span class="sxs-lookup"><span data-stu-id="50006-113">Utilize the distance of objects as they are presented to the user</span></span>

<span data-ttu-id="50006-114">Одним из распространенных способов является использование расстояния от объектов по мере их представления пользователю.</span><span class="sxs-lookup"><span data-stu-id="50006-114">One common method is to utilize the distance of objects as they are presented to the user.</span></span> <span data-ttu-id="50006-115">Например, рассмотрим визуализацию крупного автомобиля в начале пользователя.</span><span class="sxs-lookup"><span data-stu-id="50006-115">For example, consider visualizing a large family car in front of the user.</span></span> <span data-ttu-id="50006-116">Если машина находилась непосредственно перед ними, то она будет слишком большой, чтобы уместиться в поле зрения пользователя.</span><span class="sxs-lookup"><span data-stu-id="50006-116">If the car were directly in front of them, within arm’s length, it would be too large to fit in the user’s field of view.</span></span> <span data-ttu-id="50006-117">Это потребует, чтобы пользователь переместит заголовок и текст, чтобы понять, что объект будет полностью понятен.</span><span class="sxs-lookup"><span data-stu-id="50006-117">This would require the user to move their head and body to understand the entirety of the object.</span></span> <span data-ttu-id="50006-118">Если машина была размещена в другом месте (в комнате), пользователь может оценить масштаб, просматривая объект в поле зрения, а затем переместив его ближе к нему, чтобы подробно изучить области.</span><span class="sxs-lookup"><span data-stu-id="50006-118">If the car were placed further away (across the room), the user can establish a sense of scale by seeing the entirety of the object in their field of view, then moving themselves closer to it to inspect areas in detail.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="50006-119">**[Компания Volvo использовал этот метод для создания шоврумного](https://www.youtube.com/watch?v=DilzwF90vec)** интерфейса для нового автомобиля, используя масштаб holographic-автомобиля так, чтобы он был реалистичным и интуитивно понятным для пользователя.</span><span class="sxs-lookup"><span data-stu-id="50006-119">**[Volvo used this technique to create a showroom](https://www.youtube.com/watch?v=DilzwF90vec)** experience for a new car, utilizing the scale of the holographic car in a way that felt realistic and intuitive to the user.</span></span> <span data-ttu-id="50006-120">Опыт начинается с голограммы автомобиля на физическую таблицу, позволяя пользователю понять общий размер и форму модели.</span><span class="sxs-lookup"><span data-stu-id="50006-120">The experience begins with a hologram of the car on a physical table, allowing the user to understand the total size and shape of the model.</span></span> <span data-ttu-id="50006-121">На более позднем опыте автомобиля увеличивается до большего масштаба (за пределами поля представления), но, так как пользователь уже получил рамку ссылки из модели меньшего размера, они могут адекватно перемещаться по функциям автомобиля.</span><span class="sxs-lookup"><span data-stu-id="50006-121">Later in the experience, the car expands to a larger scale (beyond the size of the device's field of view) but, since the user already acquired a frame of reference from the smaller model, they can adequately navigate around features of the car.</span></span><br>
        <br>
        <span data-ttu-id="50006-122">*Образ: возможности компания Volvo автомобилей для HoloLens*</span><span class="sxs-lookup"><span data-stu-id="50006-122">*Image: Volvo Cars experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![Компания Volvo автомобилей для HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a><span data-ttu-id="50006-124">Используйте голограммы, чтобы изменить реальное пространство пользователя</span><span class="sxs-lookup"><span data-stu-id="50006-124">Use holograms to modify the user's real space</span></span>

<span data-ttu-id="50006-125">Другой способ — использовать голограммы, чтобы изменить реальное пространство пользователя, заменить существующие стены или цеилингс с окружениями или добавить "отверстия" или "Windows", что позволит объектам с избыточным размером показалось бы «разбиваться на» физическое пространство.</span><span class="sxs-lookup"><span data-stu-id="50006-125">Another method is to use holograms to modify the user's real space, replacing the existing walls or ceilings with environments or appending ‘holes’ or ‘windows’, allowing over-sized objects to seemingly 'break-through' the physical space.</span></span> <span data-ttu-id="50006-126">Например, большое дерево может не уместиться в рабочих комнатах большинства пользователей, но, помещая виртуальный трансобъектный уровень на их потолк, физическое пространство расширяется до виртуального.</span><span class="sxs-lookup"><span data-stu-id="50006-126">For example, a large tree might not fit in most users’ living rooms, but by putting a virtual sky on their ceiling, the physical space expands into the virtual.</span></span> <span data-ttu-id="50006-127">Это позволяет пользователю пройти по базовому принципу виртуального дерева и собрать представление о том, как оно будет выглядеть в реальной жизни, а затем найти, чтобы увидеть, что он выходит далеко за пределы физического пространства комнаты.</span><span class="sxs-lookup"><span data-stu-id="50006-127">This allows the user to walk around the base of the virtual tree, and gather a sense of scale of how it would appear in real life, then look up to see it extend far beyond the physical space of the room.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="50006-128">**[Minecraft разработала концепцию,](https://minecraft.net/)** используя аналогичную методику.</span><span class="sxs-lookup"><span data-stu-id="50006-128">**[Minecraft developed a concept experiences](https://minecraft.net/)** using a similar technique.</span></span> <span data-ttu-id="50006-129">Добавив виртуальное окно в физическую поверхность комнаты, существующие объекты в комнате помещаются в контексте значительно большей среды, помимо ограничений физического масштабирования комнаты.</span><span class="sxs-lookup"><span data-stu-id="50006-129">By adding a virtual window to a physical surface in a room, the existing objects in the room are placed in the context of a vastly larger environment, beyond the physical scale limitations of the room.</span></span><br>
        <br>
        <span data-ttu-id="50006-130">*Образ: интерфейс Minecraft концепция для HoloLens*</span><span class="sxs-lookup"><span data-stu-id="50006-130">*Image: Minecraft concept experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![Принципы работы Minecraft для HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a><span data-ttu-id="50006-132">Эксперименты с масштабом</span><span class="sxs-lookup"><span data-stu-id="50006-132">Experimenting with scale</span></span>

<span data-ttu-id="50006-133">В некоторых случаях проектировщики экспериментируют с изменением масштаба (путем изменения отображаемого "фактического" размера объекта), сохраняя при этом одну точку объекта, чтобы приблизительно оценить объект в средстве просмотра без фактического перемещения.</span><span class="sxs-lookup"><span data-stu-id="50006-133">In some cases, designers have experimented with modifying the scale (by changing the displayed ‘real’ size of the object) while maintaining a single position of the object, to approximate an object getting closer or further to a viewer without any actual movement.</span></span> <span data-ttu-id="50006-134">В некоторых случаях это было протестировано как способ имитации и закрытия просмотра элементов, сохраняя при этом возможности просмотра виртуального содержимого ближе, чем представится «зона отдыха».</span><span class="sxs-lookup"><span data-stu-id="50006-134">This was tested in some cases as a way to simulate up-close viewing of items while still respecting potential comfort limitations of viewing virtual content closer than the “zone of comfort” would suggest.</span></span>

<span data-ttu-id="50006-135">Однако это может создать несколько возможных артефактов.</span><span class="sxs-lookup"><span data-stu-id="50006-135">This can create a few possible artifacts in the experience however:</span></span>
* <span data-ttu-id="50006-136">Для виртуальных объектов, представляющих некоторый объект с известным размером в средстве просмотра, изменение масштаба без изменения позиции приводит к конфликту визуальных подсказок — глаза могут по-прежнему видеть объект с некоторой глубиной из-за верженце подсказок (см. [комфортное](comfort.md) Дополнительные сведения об этом см. в статье, но размер выступает в качестве монокулар подсказки, которую объект может получить ближе.</span><span class="sxs-lookup"><span data-stu-id="50006-136">For virtual objects that represent some object with a ‘known’ size to the viewer, changing the scale without changing the position leads to conflicting visual cues – the eyes may still ‘see’ the object at some depth due to vergence cues (see the [Comfort](comfort.md) article for more on this), but the size acts as a monocular cue that the object might be getting closer.</span></span> <span data-ttu-id="50006-137">Эти конфликтующие подсказки ведут к запутанным восприятиям — читатели часто видят объект как есть (из-за постоянной частоты), но быстро увеличиваются.</span><span class="sxs-lookup"><span data-stu-id="50006-137">These conflicting cues lead to confused perceptions – viewers often see the object as staying in place (due to the constant depth cue) but growing rapidly.</span></span>
* <span data-ttu-id="50006-138">В некоторых случаях изменение масштаба рассматривается как подсказка "надвигающихся", где объект может или не отображаться для изменения масштаба средством просмотра, но кажется, что он перемещается непосредственно в глаза средства просмотра (что может быть неудобной неожиданностью).</span><span class="sxs-lookup"><span data-stu-id="50006-138">In some cases, change of scale is seen as a ‘looming’ cue instead, where the object may or may not be seen to change scale by a viewer, but does appear to be moving directly toward the viewer’s eyes (which can be an uncomfortable sensation).</span></span>
* <span data-ttu-id="50006-139">С помощью областей сравнения в реальном мире такие изменения масштабирования иногда отображаются как изменение расположения по нескольким осям — объекты могут перетаскиваться в нижнюю часть вместо того, чтобы перемещаться ближе друг к другу (аналогично плоской проекции трехмерного перемещения в некоторых случаях).</span><span class="sxs-lookup"><span data-stu-id="50006-139">With comparison surfaces in the real world, such scaling changes are sometimes seen as changing position along multiple axes – objects may appear to drop lower instead of moving closer (similar in a 2D projection of 3D movement in some cases).</span></span>
* <span data-ttu-id="50006-140">Наконец, для объектов без известного размера (например, произвольных фигур с произвольными размерами, элементами пользовательского интерфейса и т. д.) изменение масштаба может функционировать как способ имитировать изменения на расстоянии, то есть у зрителей не будет столько же верхних элементов, сколько уже существует. Изучите истинный размер или расположение объекта, чтобы масштаб можно было обрабатывать как важный элемент.</span><span class="sxs-lookup"><span data-stu-id="50006-140">Finally, for objects without a known ‘real world’ size (e.g. arbitrary shapes with arbitrary sizes, UI elements, etc.), changing scale may act functionally as a way to mimic changes in distance – viewers do not have as many preexisting top-down cues by which to understand the object’s true size or location, so the scale can be processed as a more important cue.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="50006-141">См. также</span><span class="sxs-lookup"><span data-stu-id="50006-141">See also</span></span>
* [<span data-ttu-id="50006-142">Цвет, свет и материалы</span><span class="sxs-lookup"><span data-stu-id="50006-142">Color, light and materials</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="50006-143">Оформление текста</span><span class="sxs-lookup"><span data-stu-id="50006-143">Typography</span></span>](typography.md)
* [<span data-ttu-id="50006-144">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="50006-144">Spatial sound design</span></span>](spatial-sound-design.md)
