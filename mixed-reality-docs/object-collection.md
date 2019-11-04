---
title: Коллекция объектов
description: Коллекция объектов — это элемент управления макета, который помогает размещать массив объектов в предопределенной трехмерной форме.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, элементы управления, проектирование
ms.openlocfilehash: 8f3629c6d9465383efc901ed784a3719cd6fdfb2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438172"
---
# <a name="object-collection"></a><span data-ttu-id="517b3-104">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="517b3-104">Object collection</span></span>

![Коллекция объектов, используемая в периодической таблице приложения Elements](images/640px-objectcollection-hero-640px.jpg)<br>


<span data-ttu-id="517b3-106">Коллекция объектов — это элемент управления макета, который помогает размещать массив объектов в предопределенной трехмерной форме.</span><span class="sxs-lookup"><span data-stu-id="517b3-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="517b3-107">Он поддерживает различные стили поверхности — **плоскость, цилиндр, шар** и **радиальный**.</span><span class="sxs-lookup"><span data-stu-id="517b3-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="517b3-108">Вы можете настроить радиус и размер объектов, а также пространство между ними.</span><span class="sxs-lookup"><span data-stu-id="517b3-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="517b3-109">Коллекция объектов поддерживает любой объект из Unity — как 2D, так и 3D.</span><span class="sxs-lookup"><span data-stu-id="517b3-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="517b3-110">В **[наборе средств для смешанной реальности](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** мы создали скрипт Unity и примеры, которые помогут создать коллекцию объектов.</span><span class="sxs-lookup"><span data-stu-id="517b3-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="517b3-111">Примеры коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="517b3-111">Object collection examples</span></span>

<span data-ttu-id="517b3-112">[Периодическая таблица элементов](periodic-table-of-the-elements.md) — это пример приложения, демонстрирующий работу коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="517b3-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="517b3-113">Он использует коллекцию объектов для размещения трехмерных визуальных полей в различных фигурах.</span><span class="sxs-lookup"><span data-stu-id="517b3-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="517b3-114">![примеры коллекции объектов, показанные в периодической таблице приложения Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="517b3-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="517b3-115">*Примеры коллекции объектов, показанные в периодической таблице примера приложения Elements*</span><span class="sxs-lookup"><span data-stu-id="517b3-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="517b3-116">Трехмерные объекты</span><span class="sxs-lookup"><span data-stu-id="517b3-116">3D objects</span></span>

<span data-ttu-id="517b3-117">Коллекцию объектов можно использовать для размещения импортированных трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="517b3-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="517b3-118">В приведенном ниже примере показана плоскость и макет цилиндра для некоторых объектов трехмерного стула.</span><span class="sxs-lookup"><span data-stu-id="517b3-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="517b3-119">![примерами плоскости и цилиндрической разметки трехмерных объектов](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="517b3-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="517b3-120">*Примеры плоскости и цилиндрических макетов трехмерных объектов*</span><span class="sxs-lookup"><span data-stu-id="517b3-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="517b3-121">Двумерные объекты</span><span class="sxs-lookup"><span data-stu-id="517b3-121">2D objects</span></span>

<span data-ttu-id="517b3-122">Также можно использовать 2D-изображения с коллекцией объектов.</span><span class="sxs-lookup"><span data-stu-id="517b3-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="517b3-123">В приведенных ниже примерах показано, как можно отобразить 2D-изображения в сетке.</span><span class="sxs-lookup"><span data-stu-id="517b3-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Пример двумерных изображений с коллекцией объектов](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="517b3-125">![Пример двумерных изображений с коллекцией объектов](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="517b3-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="517b3-126">*Примеры использования коллекции объектов с 2D-изображениями*</span><span class="sxs-lookup"><span data-stu-id="517b3-126">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="517b3-127">См. также</span><span class="sxs-lookup"><span data-stu-id="517b3-127">See also</span></span>
* [<span data-ttu-id="517b3-128">Сценарии и Prefabs для коллекции объектов в наборе средств Mixed Reality в GitHub</span><span class="sxs-lookup"><span data-stu-id="517b3-128">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="517b3-129">Активный объект</span><span class="sxs-lookup"><span data-stu-id="517b3-129">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="517b3-130">Ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="517b3-130">Bounding Box</span></span>](app-bar-and-bounding-box.md)
