---
title: Коллекция объектов
description: Коллекция объектов — это элемент управления макета, который помогает размещать массив объектов в предопределенной трехмерной форме.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, элементы управления, проектирование
ms.openlocfilehash: 9a111fcbe4c49972cc5ef22fb647f89544188af5
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143155"
---
# <a name="object-collection"></a><span data-ttu-id="b316a-104">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="b316a-104">Object collection</span></span>

![Коллекция объектов, используемая в периодической таблице приложения Elements](images/UX/UX_Hero_ObjectCollection.jpg)<br>


<span data-ttu-id="b316a-106">Коллекция объектов — это элемент управления макета, который помогает размещать массив объектов в предопределенной трехмерной форме.</span><span class="sxs-lookup"><span data-stu-id="b316a-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="b316a-107">Он поддерживает различные стили поверхности — **плоскость, цилиндр, шар** и **радиальный**.</span><span class="sxs-lookup"><span data-stu-id="b316a-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="b316a-108">Вы можете настроить радиус и размер объектов, а также пространство между ними.</span><span class="sxs-lookup"><span data-stu-id="b316a-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="b316a-109">Коллекция объектов поддерживает любой объект из Unity — как 2D, так и 3D.</span><span class="sxs-lookup"><span data-stu-id="b316a-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="b316a-110">В **[наборе средств для смешанной реальности](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** мы создали скрипт Unity и примеры, которые помогут создать коллекцию объектов.</span><span class="sxs-lookup"><span data-stu-id="b316a-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="b316a-111">Примеры коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="b316a-111">Object collection examples</span></span>

<span data-ttu-id="b316a-112">[Периодическая таблица элементов](periodic-table-of-the-elements.md) — это пример приложения, демонстрирующий работу коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="b316a-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="b316a-113">Он использует коллекцию объектов для размещения трехмерных визуальных полей в различных фигурах.</span><span class="sxs-lookup"><span data-stu-id="b316a-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="b316a-114">![примеры коллекции объектов, показанные в периодической таблице приложения Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b316a-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="b316a-115">*Примеры коллекции объектов, показанные в периодической таблице примера приложения Elements*</span><span class="sxs-lookup"><span data-stu-id="b316a-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="b316a-116">Трехмерные объекты</span><span class="sxs-lookup"><span data-stu-id="b316a-116">3D objects</span></span>

<span data-ttu-id="b316a-117">Коллекцию объектов можно использовать для размещения импортированных трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="b316a-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="b316a-118">В приведенном ниже примере показана плоскость и макет цилиндра для некоторых объектов трехмерного стула.</span><span class="sxs-lookup"><span data-stu-id="b316a-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="b316a-119">![примерами плоскости и цилиндрической разметки трехмерных объектов](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b316a-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="b316a-120">*Примеры плоскости и цилиндрических макетов трехмерных объектов*</span><span class="sxs-lookup"><span data-stu-id="b316a-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="b316a-121">Двумерные объекты</span><span class="sxs-lookup"><span data-stu-id="b316a-121">2D objects</span></span>

<span data-ttu-id="b316a-122">Также можно использовать 2D-изображения с коллекцией объектов.</span><span class="sxs-lookup"><span data-stu-id="b316a-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="b316a-123">В приведенных ниже примерах показано, как можно отобразить 2D-изображения в сетке.</span><span class="sxs-lookup"><span data-stu-id="b316a-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Пример двумерных изображений с коллекцией объектов](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="b316a-125">![Пример двумерных изображений с коллекцией объектов](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="b316a-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="b316a-126">*Примеры использования коллекции объектов с 2D-изображениями*</span><span class="sxs-lookup"><span data-stu-id="b316a-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="b316a-127">Коллекция объектов в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="b316a-127">Object collection in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="b316a-128">МРТК — коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="b316a-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="b316a-129">См. также</span><span class="sxs-lookup"><span data-stu-id="b316a-129">See also</span></span>

* [<span data-ttu-id="b316a-130">Курсоры</span><span class="sxs-lookup"><span data-stu-id="b316a-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="b316a-131">Рука</span><span class="sxs-lookup"><span data-stu-id="b316a-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="b316a-132">Button</span><span class="sxs-lookup"><span data-stu-id="b316a-132">Button</span></span>](button.md)
* [<span data-ttu-id="b316a-133">Активный объект</span><span class="sxs-lookup"><span data-stu-id="b316a-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b316a-134">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="b316a-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="b316a-135">Управлять</span><span class="sxs-lookup"><span data-stu-id="b316a-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b316a-136">Меню руки</span><span class="sxs-lookup"><span data-stu-id="b316a-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="b316a-137">Ближайшее меню</span><span class="sxs-lookup"><span data-stu-id="b316a-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="b316a-138">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="b316a-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="b316a-139">Voice, команда</span><span class="sxs-lookup"><span data-stu-id="b316a-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="b316a-140">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="b316a-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="b316a-141">Сказок</span><span class="sxs-lookup"><span data-stu-id="b316a-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="b316a-142">Рекламы</span><span class="sxs-lookup"><span data-stu-id="b316a-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="b316a-143">Slider</span><span class="sxs-lookup"><span data-stu-id="b316a-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="b316a-144">Шейдера</span><span class="sxs-lookup"><span data-stu-id="b316a-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="b316a-145">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="b316a-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="b316a-146">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="b316a-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="b316a-147">Магнит поверхности</span><span class="sxs-lookup"><span data-stu-id="b316a-147">Surface magnetism</span></span>](surface-magnetism.md)
