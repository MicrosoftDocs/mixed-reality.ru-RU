---
title: Шейдера
description: Стандартный шейдер МРТК предоставляет различные типы визуальных эффектов, которые можно использовать с голограммами.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, Пользовательский интерфейс, UX
ms.openlocfilehash: 4d95e335b3f7020766beae916423d0588ee66572
ms.sourcegitcommit: 270ca09ec61e1153a83cf44942d7ba3783ef1805
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694168"
---
# <a name="shader"></a><span data-ttu-id="5933b-104">Шейдера</span><span class="sxs-lookup"><span data-stu-id="5933b-104">Shader</span></span>

![Шейдера](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="5933b-106">Поскольку holographic объектов вместе с физическими в среде, важно обеспечить визуальные подсказки в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5933b-106">Since holographic objects are mixed with the physical ones in the environment, it's important to provide visual cues in mixed reality.</span></span> <span data-ttu-id="5933b-107">Стандартный шейдер МРТК предоставляет различные типы визуальных эффектов, которые можно использовать с голограммами.</span><span class="sxs-lookup"><span data-stu-id="5933b-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="5933b-108">Стандартная система затенения МРТК использует один гибкий шейдер, который может обеспечить визуализацию визуальных элементов, аналогичных стандартному шейдеру Unity, реализует основные [принципы разработки](https://www.microsoft.com/design/fluent/#/)и оставаться на устройствах смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5933b-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="5933b-109">Примеры визуальных эффектов с использованием шейдера МРТК Standard</span><span class="sxs-lookup"><span data-stu-id="5933b-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="5933b-110">![Перемещение](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="5933b-110">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="5933b-111">**Неблизкое освещение**</span><span class="sxs-lookup"><span data-stu-id="5933b-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5933b-112">![Поворот](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="5933b-112">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="5933b-113">**Источник границы**</span><span class="sxs-lookup"><span data-stu-id="5933b-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="5933b-114">Стандартный шейдер МРТК в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="5933b-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="5933b-115">МРТК — Стандартный шейдер</span><span class="sxs-lookup"><span data-stu-id="5933b-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="5933b-116">См. также статью</span><span class="sxs-lookup"><span data-stu-id="5933b-116">See also</span></span>

* [<span data-ttu-id="5933b-117">Курсоры</span><span class="sxs-lookup"><span data-stu-id="5933b-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="5933b-118">Телекинез</span><span class="sxs-lookup"><span data-stu-id="5933b-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="5933b-119">Button</span><span class="sxs-lookup"><span data-stu-id="5933b-119">Button</span></span>](button.md)
* [<span data-ttu-id="5933b-120">Активный объект</span><span class="sxs-lookup"><span data-stu-id="5933b-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="5933b-121">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="5933b-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="5933b-122">Оперирование</span><span class="sxs-lookup"><span data-stu-id="5933b-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5933b-123">Меню руки</span><span class="sxs-lookup"><span data-stu-id="5933b-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="5933b-124">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="5933b-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="5933b-125">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="5933b-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5933b-126">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="5933b-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="5933b-127">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="5933b-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="5933b-128">Подсказка</span><span class="sxs-lookup"><span data-stu-id="5933b-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="5933b-129">Планшет</span><span class="sxs-lookup"><span data-stu-id="5933b-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="5933b-130">Ползунок</span><span class="sxs-lookup"><span data-stu-id="5933b-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="5933b-131">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="5933b-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="5933b-132">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="5933b-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="5933b-133">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="5933b-133">Surface magnetism</span></span>](surface-magnetism.md)
