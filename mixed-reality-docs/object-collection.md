---
title: Коллекция объектов
description: Коллекция объектов — это элемент управления макета, который служит для размещения является массивом объектов в стандартных трехмерной фигуры.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, элементы управления, разработки
ms.openlocfilehash: 7c3bbd82ec909b5a2e3c81f122366be564934f4d
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813889"
---
# <a name="object-collection"></a><span data-ttu-id="25a8d-104">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="25a8d-104">Object collection</span></span>

<span data-ttu-id="25a8d-105">Коллекция объектов — это элемент управления макета, который служит для размещения является массивом объектов в стандартных трехмерной фигуры.</span><span class="sxs-lookup"><span data-stu-id="25a8d-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="25a8d-106">Он поддерживает различные стили поверхности - **плоскости, цилиндр, sphere** и **радиального**.</span><span class="sxs-lookup"><span data-stu-id="25a8d-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="25a8d-107">Можно настроить radius и размер объектов, а также пробела между ними.</span><span class="sxs-lookup"><span data-stu-id="25a8d-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="25a8d-108">Коллекция объектов поддерживает любой объект из Unity — 2D и 3D.</span><span class="sxs-lookup"><span data-stu-id="25a8d-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="25a8d-109">В  **[смешанной реальности Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , мы создали скриптов Unity, и примеры, которые помогут вам создать коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="25a8d-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="25a8d-110">![Коллекция объектов, используемых в таблице периодически элементы приложения](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="25a8d-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="25a8d-111">*Примеры использования коллекции объектов*</span><span class="sxs-lookup"><span data-stu-id="25a8d-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="25a8d-112">Примеры коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="25a8d-112">Object collection examples</span></span>

<span data-ttu-id="25a8d-113">[Периодическая таблица элементов](periodic-table-of-the-elements.md) — это пример приложения, демонстрирующий, как работает коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="25a8d-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="25a8d-114">Коллекция объектов используется для размещения 3D химических элемент поля в различных фигур.</span><span class="sxs-lookup"><span data-stu-id="25a8d-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="25a8d-115">![Примеры коллекции объектов, приведенных в таблице периодически элементы приложения](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="25a8d-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="25a8d-116">*Примеры коллекции объектов, в таблице периодически элементов примера приложения*</span><span class="sxs-lookup"><span data-stu-id="25a8d-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="25a8d-117">Трехмерные объекты</span><span class="sxs-lookup"><span data-stu-id="25a8d-117">3D objects</span></span>

<span data-ttu-id="25a8d-118">Коллекция объектов можно использовать для размещения импортируемых трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="25a8d-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="25a8d-119">В приведенном ниже примере показано плоскость и макет цилиндра некоторых объектов 3D кресло.</span><span class="sxs-lookup"><span data-stu-id="25a8d-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="25a8d-120">![Примеры плоскости и значениями в цилиндрической макеты трехмерных объектов](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="25a8d-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="25a8d-121">*Примеры плоскости и значениями в цилиндрической макеты трехмерных объектов*</span><span class="sxs-lookup"><span data-stu-id="25a8d-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="25a8d-122">Двухмерные объекты</span><span class="sxs-lookup"><span data-stu-id="25a8d-122">2D objects</span></span>

<span data-ttu-id="25a8d-123">Двумерные изображения также можно с помощью коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="25a8d-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="25a8d-124">В примерах ниже показано, как двумерные изображения могут отображаться в сетке.</span><span class="sxs-lookup"><span data-stu-id="25a8d-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Пример изображения с помощью коллекции объектов](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="25a8d-126">![Пример изображения с помощью коллекции объектов](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="25a8d-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="25a8d-127">*Примеры использования коллекции объектов с двумерные изображения*</span><span class="sxs-lookup"><span data-stu-id="25a8d-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="25a8d-128">См. также</span><span class="sxs-lookup"><span data-stu-id="25a8d-128">See also</span></span>
* [<span data-ttu-id="25a8d-129">Сценарии и prefabs для коллекции объектов в смешанной реальности Toolkit на сайте GitHub</span><span class="sxs-lookup"><span data-stu-id="25a8d-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="25a8d-130">Активный объект</span><span class="sxs-lookup"><span data-stu-id="25a8d-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="25a8d-131">Ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="25a8d-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)
