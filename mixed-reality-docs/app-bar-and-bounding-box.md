---
title: Ограничивающим поле, а также панель приложения
description: Панели приложения — это меню уровня объектов, содержащий ряд кнопок, которое будет отображаться на нижнего края границы голограмма.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Смешанная реальность Windows, приложения, линейчатым диаграммам, ограничивающий прямоугольник
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829683"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="55e32-104">Ограничивающим поле, а также панель приложения</span><span class="sxs-lookup"><span data-stu-id="55e32-104">Bounding box and App bar</span></span>
![Ограничивающего прямоугольника имеет стандартный интерфейс для обработки объекта в смешанной реальности.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="55e32-106">Что такое ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="55e32-106">What is the Bounding box?</span></span>

<span data-ttu-id="55e32-107">Ограничивающего прямоугольника имеет стандартный интерфейс для обработки объекта в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="55e32-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="55e32-108">Он предоставляет пользователю affordance, что объект имеет в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="55e32-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="55e32-109">Углы сообщить пользователю, что объект можно также масштабировать.</span><span class="sxs-lookup"><span data-stu-id="55e32-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="55e32-110">Этот visual affordance отображаются пользователи общей области объекта — даже если она не отображается за пределами режим проверки коррекции.</span><span class="sxs-lookup"><span data-stu-id="55e32-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="55e32-111">Это особенно важно, так как если бы не существует, привязываются к другому объекту или поверхность объекта может вести себя как в случае отсутствия пространство вокруг него, не должны присутствовать.</span><span class="sxs-lookup"><span data-stu-id="55e32-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="55e32-112">По 2 HoloLens ограничивающего работает с манипуляции прямой руки и отвечает на пальцем пользователя с учетом расположения.</span><span class="sxs-lookup"><span data-stu-id="55e32-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="55e32-113">Он показывает визуальную обратную связь, чтобы помочь пользователю воспринимают расстояние от объекта.</span><span class="sxs-lookup"><span data-stu-id="55e32-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="55e32-114">![HoloLens точки зрения масштабирования объекта с помощью ограничивающий прямоугольник](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="55e32-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="55e32-115">*Масштабирование объекта с помощью ограничивающий прямоугольник*</span><span class="sxs-lookup"><span data-stu-id="55e32-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="55e32-116">Маркеры в углах ограничивающего широко изученных шаблону для настройки масштабирования.</span><span class="sxs-lookup"><span data-stu-id="55e32-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="55e32-117">![HoloLens точки зрения вращения объекта с помощью ограничивающий прямоугольник](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="55e32-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="55e32-118">*Поворот объекта с помощью ограничивающий прямоугольник*</span><span class="sxs-lookup"><span data-stu-id="55e32-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="55e32-119">![Визуальную обратную связь от руки близости](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="55e32-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="55e32-120">*Визуальную обратную связь на основе приближенности*</span><span class="sxs-lookup"><span data-stu-id="55e32-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="55e32-121">Вертикальная прямоугольный читаемости на края ограничивающего прямоугольника являются признаком поворота.</span><span class="sxs-lookup"><span data-stu-id="55e32-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="55e32-122">В этом случае пользователь более тонкая настройка – их помещено голограммы.</span><span class="sxs-lookup"><span data-stu-id="55e32-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="55e32-123">Не только можно их настроить масштабирование, но теперь повернуть также.</span><span class="sxs-lookup"><span data-stu-id="55e32-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="55e32-124">Для разработки приложений Unity, см. в разделе [ограничивающий прямоугольник в смешанной реальности Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="55e32-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="55e32-125">Что такое панели приложения?</span><span class="sxs-lookup"><span data-stu-id="55e32-125">What is the App bar?</span></span>

<span data-ttu-id="55e32-126">Панели приложения — это меню уровня объектов, содержащий ряд кнопок, которое будет отображаться на нижнего края границы голограмма.</span><span class="sxs-lookup"><span data-stu-id="55e32-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="55e32-127">Этот шаблон часто используется для предоставления пользователям возможности удалять и настраивать голограммы.</span><span class="sxs-lookup"><span data-stu-id="55e32-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="55e32-128">Так как этот шаблон используется с объектами, которые являются world заблокирован, когда пользователь перемещает вокруг объекта панели приложения всегда будет отображаться на стороне объектов ближе к пользователю.</span><span class="sxs-lookup"><span data-stu-id="55e32-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="55e32-129">Хотя это не биллбординга, он эффективно дает тот же результат; Предотвращение положение, чтобы скрывать или функциональности блоков, в противном случае будет доступен в другом расположении в среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="55e32-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="55e32-130">![Прогулке по голограмма.</span><span class="sxs-lookup"><span data-stu-id="55e32-130">![Walking around a hologram.</span></span> <span data-ttu-id="55e32-131">Ниже панели приложения.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="55e32-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="55e32-132">*Прогулке по голограмма, ниже панели приложения*</span><span class="sxs-lookup"><span data-stu-id="55e32-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="55e32-133">Панели приложения была разработана в основном это способ управления размещенных объектов в среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="55e32-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="55e32-134">В сочетании с ограничивающим прямоугольником, пользователь имеет полный контроль над местом и способом объекты располагается в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="55e32-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="55e32-135">Для разработки приложений Unity, см. в разделе [панели приложения в смешанной реальности Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="55e32-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="55e32-136">См. также</span><span class="sxs-lookup"><span data-stu-id="55e32-136">See also</span></span>
* [<span data-ttu-id="55e32-137">Активный объект</span><span class="sxs-lookup"><span data-stu-id="55e32-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="55e32-138">Текст в Unity</span><span class="sxs-lookup"><span data-stu-id="55e32-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="55e32-139">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="55e32-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="55e32-140">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="55e32-140">Displaying progress</span></span>](progress.md)
