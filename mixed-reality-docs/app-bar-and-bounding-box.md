---
title: Ограничивающий прямоугольник и панель приложений
description: Панель приложения — это меню уровня объекта, содержащее ряд кнопок, отображаемых на нижней границе границ голограммы.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, панель приложений, ограничивающий прямоугольник
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829683"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="b522a-104">Ограничивающий прямоугольник и панель приложений</span><span class="sxs-lookup"><span data-stu-id="b522a-104">Bounding box and App bar</span></span>
![Это стандартный интерфейс для манипуляций с объектами в смешанной реальности.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="b522a-106">Что такое ограничивающий прямоугольник?</span><span class="sxs-lookup"><span data-stu-id="b522a-106">What is the Bounding box?</span></span>

<span data-ttu-id="b522a-107">Это стандартный интерфейс для манипуляций с объектами в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b522a-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="b522a-108">Он предоставляет пользователю право на то, что объект в данный момент является изменяемым.</span><span class="sxs-lookup"><span data-stu-id="b522a-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="b522a-109">Углы указывают пользователю, что объект может также масштабироваться.</span><span class="sxs-lookup"><span data-stu-id="b522a-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="b522a-110">Этот визуальный доступ показывает пользователям общую область объекта, даже если он не виден за пределами режима коррекции.</span><span class="sxs-lookup"><span data-stu-id="b522a-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="b522a-111">Это особенно важно, так как в противном случае объект, привязанный к другому объекту или поверхности, может выглядеть так, как если бы на нем было недостаточно свободного пространства.</span><span class="sxs-lookup"><span data-stu-id="b522a-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="b522a-112">В HoloLens 2 ограничивающий прямоугольник работает с непосредственной манипуляцией и реагирует на финжер'с пользователя.</span><span class="sxs-lookup"><span data-stu-id="b522a-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="b522a-113">Он показывает визуальную обратную связь, которая помогает пользователю воспринимать расстояние от объекта.</span><span class="sxs-lookup"><span data-stu-id="b522a-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="b522a-114">![Точка HoloLens — представление масштабирования объекта через ограничивающий прямоугольник](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="b522a-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="b522a-115">*Масштабирование объекта с помощью ограничивающего прямоугольника*</span><span class="sxs-lookup"><span data-stu-id="b522a-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="b522a-116">Маркеры в углах ограничивающего прямоугольника соответствуют широкому расприятному шаблону для настройки масштаба.</span><span class="sxs-lookup"><span data-stu-id="b522a-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="b522a-117">![Точка HoloLens — вид поворота объекта через ограничивающий прямоугольник](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="b522a-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="b522a-118">*Вращение объекта через ограничивающий прямоугольник*</span><span class="sxs-lookup"><span data-stu-id="b522a-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="b522a-119">![Визуальный отзыв о близком к рукой](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="b522a-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="b522a-120">*Визуальная обратная связь на основе сходства*</span><span class="sxs-lookup"><span data-stu-id="b522a-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="b522a-121">Вертикальная прямоугольная аффорданцес на краях ограничивающего прямоугольника — это индикаторы вращения.</span><span class="sxs-lookup"><span data-stu-id="b522a-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="b522a-122">Это дает пользователю более точную корректировку по своим голограммам.</span><span class="sxs-lookup"><span data-stu-id="b522a-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="b522a-123">Можно не только настраивать и масштабировать, но и теперь также вращать.</span><span class="sxs-lookup"><span data-stu-id="b522a-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="b522a-124">Сведения о разработке приложений Unity см. [в разделе ограничивающий прямоугольник в наборе средств смешанной реальности — Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) .</span><span class="sxs-lookup"><span data-stu-id="b522a-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="b522a-125">Что такое панель приложений?</span><span class="sxs-lookup"><span data-stu-id="b522a-125">What is the App bar?</span></span>

<span data-ttu-id="b522a-126">Панель приложения — это меню уровня объекта, содержащее ряд кнопок, отображаемых на нижней границе границ голограммы.</span><span class="sxs-lookup"><span data-stu-id="b522a-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="b522a-127">Этот шаблон обычно используется для предоставления пользователям возможности удалять и изменять голограммы.</span><span class="sxs-lookup"><span data-stu-id="b522a-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="b522a-128">Так как этот шаблон используется с объектами, которые заблокированы в мире, по мере того как пользователь перемещается по объекту, панель приложения всегда будет отображаться на стороне объектов, ближайшей к пользователю.</span><span class="sxs-lookup"><span data-stu-id="b522a-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="b522a-129">Хотя это и не является объявлением, оно эффективно достигает того же результата; запрет на положение пользователя в окклуде или блокировать функциональность, которая в противном случае будет доступна из другого расположения в своей среде.</span><span class="sxs-lookup"><span data-stu-id="b522a-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="b522a-130">![Проход вокруг голограммы.</span><span class="sxs-lookup"><span data-stu-id="b522a-130">![Walking around a hologram.</span></span> <span data-ttu-id="b522a-131">Ниже приведена панель приложений.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="b522a-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="b522a-132">*Последуя голограмме, на панели приложения следует следующее.*</span><span class="sxs-lookup"><span data-stu-id="b522a-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="b522a-133">Панель приложений была разработана в основном как способ управления размещенными объектами в среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="b522a-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="b522a-134">В сочетании с ограничивающим прямоугольником пользователь имеет полный контроль над тем, где и как объекты ориентированы в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b522a-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="b522a-135">Сведения о разработке приложений Unity см. [в разделе Панель приложений в наборе средств смешанной реальности — Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) .</span><span class="sxs-lookup"><span data-stu-id="b522a-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="b522a-136">См. также</span><span class="sxs-lookup"><span data-stu-id="b522a-136">See also</span></span>
* [<span data-ttu-id="b522a-137">Активный объект</span><span class="sxs-lookup"><span data-stu-id="b522a-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b522a-138">Текст в Unity</span><span class="sxs-lookup"><span data-stu-id="b522a-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="b522a-139">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="b522a-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="b522a-140">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="b522a-140">Displaying progress</span></span>](progress.md)
