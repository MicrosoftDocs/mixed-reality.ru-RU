---
title: Коллекция объектов
description: Коллекция объектов — это элемент управления макета, который помогает размещать массив объектов в предопределенной трехмерной форме.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, элементы управления, проектирование
ms.openlocfilehash: 7c3bbd82ec909b5a2e3c81f122366be564934f4d
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813889"
---
# <a name="object-collection"></a><span data-ttu-id="d46a2-104">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="d46a2-104">Object collection</span></span>

<span data-ttu-id="d46a2-105">Коллекция объектов — это элемент управления макета, который помогает размещать массив объектов в предопределенной трехмерной форме.</span><span class="sxs-lookup"><span data-stu-id="d46a2-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="d46a2-106">Он поддерживает различные стили поверхности — **плоскость, цилиндр, шар** и **радиальный**.</span><span class="sxs-lookup"><span data-stu-id="d46a2-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="d46a2-107">Вы можете настроить радиус и размер объектов, а также пространство между ними.</span><span class="sxs-lookup"><span data-stu-id="d46a2-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="d46a2-108">Коллекция объектов поддерживает любой объект из Unity — как 2D, так и 3D.</span><span class="sxs-lookup"><span data-stu-id="d46a2-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="d46a2-109">В **[наборе средств для смешанной реальности](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** мы создали скрипт Unity и примеры, которые помогут создать коллекцию объектов.</span><span class="sxs-lookup"><span data-stu-id="d46a2-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="d46a2-110">![Коллекция объектов, используемая в периодической таблице приложения Elements](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d46a2-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="d46a2-111">*Примеры использования коллекции объектов*</span><span class="sxs-lookup"><span data-stu-id="d46a2-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="d46a2-112">Примеры коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="d46a2-112">Object collection examples</span></span>

<span data-ttu-id="d46a2-113">[Периодическая таблица элементов](periodic-table-of-the-elements.md) — это пример приложения, демонстрирующий работу коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="d46a2-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="d46a2-114">Он использует коллекцию объектов для размещения трехмерных визуальных полей в различных фигурах.</span><span class="sxs-lookup"><span data-stu-id="d46a2-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="d46a2-115">![Примеры коллекции объектов, показанные в периодической таблице приложения Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d46a2-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="d46a2-116">*Примеры коллекции объектов, показанные в периодической таблице примера приложения Elements*</span><span class="sxs-lookup"><span data-stu-id="d46a2-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="d46a2-117">Трехмерные объекты</span><span class="sxs-lookup"><span data-stu-id="d46a2-117">3D objects</span></span>

<span data-ttu-id="d46a2-118">Коллекцию объектов можно использовать для размещения импортированных трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="d46a2-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="d46a2-119">В приведенном ниже примере показана плоскость и макет цилиндра для некоторых объектов трехмерного стула.</span><span class="sxs-lookup"><span data-stu-id="d46a2-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="d46a2-120">![Примеры плоскости и цилиндрических макетов трехмерных объектов](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d46a2-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="d46a2-121">*Примеры плоскости и цилиндрических макетов трехмерных объектов*</span><span class="sxs-lookup"><span data-stu-id="d46a2-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="d46a2-122">Двумерные объекты</span><span class="sxs-lookup"><span data-stu-id="d46a2-122">2D objects</span></span>

<span data-ttu-id="d46a2-123">Также можно использовать 2D-изображения с коллекцией объектов.</span><span class="sxs-lookup"><span data-stu-id="d46a2-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="d46a2-124">В приведенных ниже примерах показано, как можно отобразить 2D-изображения в сетке.</span><span class="sxs-lookup"><span data-stu-id="d46a2-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Пример двумерных изображений с коллекцией объектов](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="d46a2-126">![Пример двумерных изображений с коллекцией объектов](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="d46a2-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="d46a2-127">*Примеры использования коллекции объектов с 2D-изображениями*</span><span class="sxs-lookup"><span data-stu-id="d46a2-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="d46a2-128">См. также</span><span class="sxs-lookup"><span data-stu-id="d46a2-128">See also</span></span>
* [<span data-ttu-id="d46a2-129">Сценарии и Prefabs для коллекции объектов в наборе средств Mixed Reality в GitHub</span><span class="sxs-lookup"><span data-stu-id="d46a2-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="d46a2-130">Активный объект</span><span class="sxs-lookup"><span data-stu-id="d46a2-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d46a2-131">Ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="d46a2-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)
