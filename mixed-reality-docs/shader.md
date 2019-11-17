---
title: Шейдера
description: ''
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, Пользовательский интерфейс, UX
ms.openlocfilehash: 23371ae5d70e5e792415fd25c0d58def0a7cefbb
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143274"
---
# <a name="shader"></a><span data-ttu-id="9c06c-103">Шейдера</span><span class="sxs-lookup"><span data-stu-id="9c06c-103">Shader</span></span>

![Шейдера](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="9c06c-105">Поскольку holographic объектов смешаны с физическими элементами в среде, в смешанной реальности важно обеспечить визуальную подсказку.</span><span class="sxs-lookup"><span data-stu-id="9c06c-105">Since holographic objects are mixed with the physical ones in the environment, providing visual cue is important in mixed reality.</span></span> <span data-ttu-id="9c06c-106">Стандартный шейдер МРТК предоставляет различные типы визуальных эффектов, которые можно использовать с голограммами.</span><span class="sxs-lookup"><span data-stu-id="9c06c-106">MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="9c06c-107">Стандартная система затенения МРТК использует один гибкий шейдер, который может обеспечить визуальные элементы, аналогичные стандартному шейдеру Unity, реализовывать основные принципы разработки, а также работать на устройствах смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="9c06c-107">MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implement Fluent Design System principles, and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="9c06c-108">Примеры визуальных эффектов с использованием шейдера МРТК Standard</span><span class="sxs-lookup"><span data-stu-id="9c06c-108">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="9c06c-109">![Перемещение](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c06c-109">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="9c06c-110">**Неблизкое освещение**</span><span class="sxs-lookup"><span data-stu-id="9c06c-110">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="9c06c-111">![Поворот](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c06c-111">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="9c06c-112">**Источник границы**</span><span class="sxs-lookup"><span data-stu-id="9c06c-112">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

---

## <a name="mrtk-standard-shader-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="9c06c-113">Стандартный шейдер МРТК в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="9c06c-113">MRTK Standard shader in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="9c06c-114">МРТК — Стандартный шейдер</span><span class="sxs-lookup"><span data-stu-id="9c06c-114">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="9c06c-115">См. также</span><span class="sxs-lookup"><span data-stu-id="9c06c-115">See also</span></span>

* [<span data-ttu-id="9c06c-116">Курсоры</span><span class="sxs-lookup"><span data-stu-id="9c06c-116">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9c06c-117">Рука</span><span class="sxs-lookup"><span data-stu-id="9c06c-117">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="9c06c-118">Button</span><span class="sxs-lookup"><span data-stu-id="9c06c-118">Button</span></span>](button.md)
* [<span data-ttu-id="9c06c-119">Активный объект</span><span class="sxs-lookup"><span data-stu-id="9c06c-119">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9c06c-120">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="9c06c-120">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9c06c-121">Управлять</span><span class="sxs-lookup"><span data-stu-id="9c06c-121">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9c06c-122">Меню руки</span><span class="sxs-lookup"><span data-stu-id="9c06c-122">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="9c06c-123">Ближайшее меню</span><span class="sxs-lookup"><span data-stu-id="9c06c-123">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="9c06c-124">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="9c06c-124">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9c06c-125">Voice, команда</span><span class="sxs-lookup"><span data-stu-id="9c06c-125">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="9c06c-126">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="9c06c-126">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="9c06c-127">Сказок</span><span class="sxs-lookup"><span data-stu-id="9c06c-127">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="9c06c-128">Рекламы</span><span class="sxs-lookup"><span data-stu-id="9c06c-128">Slate</span></span>](slate.md)
* [<span data-ttu-id="9c06c-129">Slider</span><span class="sxs-lookup"><span data-stu-id="9c06c-129">Slider</span></span>](slider.md)
* [<span data-ttu-id="9c06c-130">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="9c06c-130">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9c06c-131">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="9c06c-131">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="9c06c-132">Магнит поверхности</span><span class="sxs-lookup"><span data-stu-id="9c06c-132">Surface magnetism</span></span>](surface-magnetism.md)
