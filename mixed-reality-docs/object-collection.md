---
title: Коллекция объектов
description: Коллекция объектов — это элемент управления макета, который служит для размещения является массивом объектов в стандартных трехмерной фигуры.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, элементы управления, разработки
ms.openlocfilehash: 88ab0359d5083d43d5d6312ef1185f67ca0caa7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605013"
---
# <a name="object-collection"></a><span data-ttu-id="cad5e-104">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="cad5e-104">Object collection</span></span>

<span data-ttu-id="cad5e-105">Коллекция объектов — это элемент управления макета, который служит для размещения является массивом объектов в стандартных трехмерной фигуры.</span><span class="sxs-lookup"><span data-stu-id="cad5e-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="cad5e-106">Он поддерживает четыре различных стилей поверхности - **плоскости, цилиндр, sphere** и **точечной**.</span><span class="sxs-lookup"><span data-stu-id="cad5e-106">It supports four different surface styles - **plane, cylinder, sphere** and **scatter**.</span></span> <span data-ttu-id="cad5e-107">Можно настроить radius и размер объектов, а также пробела между ними.</span><span class="sxs-lookup"><span data-stu-id="cad5e-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="cad5e-108">Коллекция объектов поддерживает любой объект из Unity — 2D и 3D.</span><span class="sxs-lookup"><span data-stu-id="cad5e-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="cad5e-109">В  **[смешанной реальности Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, мы создали сценарий Unity и [сцены пример](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) , помогут вам создать коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="cad5e-109">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, we have created Unity script and [example scene](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) that will help you create an object collection.</span></span>

<span data-ttu-id="cad5e-110">![Коллекция объектов, используемых в таблице периодически элементы приложения](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="cad5e-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="cad5e-111">*Коллекция объектов, используемых в таблице периодически элементов примера приложения*</span><span class="sxs-lookup"><span data-stu-id="cad5e-111">*Object collection used in the Periodic Table of the Elements sample app*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="cad5e-112">Примеры коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="cad5e-112">Object collection examples</span></span>

<span data-ttu-id="cad5e-113">[Периодическая таблица элементов](periodic-table-of-the-elements.md) — это пример приложения, демонстрирующий, как работает коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="cad5e-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="cad5e-114">Коллекция объектов используется для размещения 3D химических элемент поля в различных фигур.</span><span class="sxs-lookup"><span data-stu-id="cad5e-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="cad5e-115">![Примеры коллекции объектов, приведенных в таблице периодически элементы приложения](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="cad5e-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="cad5e-116">*Примеры коллекции объектов, в таблице периодически элементов примера приложения*</span><span class="sxs-lookup"><span data-stu-id="cad5e-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="cad5e-117">Трехмерные объекты</span><span class="sxs-lookup"><span data-stu-id="cad5e-117">3D objects</span></span>

<span data-ttu-id="cad5e-118">Коллекция объектов можно использовать для размещения импортируемых трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="cad5e-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="cad5e-119">В приведенном ниже примере показано плоскость и макет цилиндра некоторых объектов 3D кресло.</span><span class="sxs-lookup"><span data-stu-id="cad5e-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="cad5e-120">![Примеры плоскости и значениями в цилиндрической макеты трехмерных объектов](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="cad5e-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="cad5e-121">*Примеры плоскости и значениями в цилиндрической макеты трехмерных объектов*</span><span class="sxs-lookup"><span data-stu-id="cad5e-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="cad5e-122">Двухмерные объекты</span><span class="sxs-lookup"><span data-stu-id="cad5e-122">2D objects</span></span>

<span data-ttu-id="cad5e-123">Двумерные изображения также можно с помощью коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="cad5e-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="cad5e-124">В примерах ниже показано, как двумерные изображения могут отображаться в сетке.</span><span class="sxs-lookup"><span data-stu-id="cad5e-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Пример изображения с помощью коллекции объектов](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="cad5e-126">![Пример изображения с помощью коллекции объектов](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="cad5e-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="cad5e-127">*Примеры двумерные изображения с помощью коллекции объектов*</span><span class="sxs-lookup"><span data-stu-id="cad5e-127">*Examples of 2D images with object collection*</span></span>

## <a name="see-also"></a><span data-ttu-id="cad5e-128">См. также</span><span class="sxs-lookup"><span data-stu-id="cad5e-128">See also</span></span>
* [<span data-ttu-id="cad5e-129">Сценарии и prefabs для коллекции объектов в смешанной реальности Toolkit на сайте GitHub</span><span class="sxs-lookup"><span data-stu-id="cad5e-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)
* [<span data-ttu-id="cad5e-130">Элементом объекта</span><span class="sxs-lookup"><span data-stu-id="cad5e-130">Interactable object</span></span>](interactable-object.md)
