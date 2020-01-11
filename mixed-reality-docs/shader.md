---
title: Шейдера
description: Стандартный шейдер МРТК предоставляет различные типы визуальных эффектов, которые можно использовать с голограммами.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, Пользовательский интерфейс, UX
ms.openlocfilehash: 8d0e01bb26347d95a80703884c4e9408653e03ed
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901460"
---
# <a name="shader"></a><span data-ttu-id="8a401-104">Шейдера</span><span class="sxs-lookup"><span data-stu-id="8a401-104">Shader</span></span>

![Шейдера](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="8a401-106">Так как holographic объектов вместе с физическими в реальной среде, важно предоставить пользователю визуальные подсказки.</span><span class="sxs-lookup"><span data-stu-id="8a401-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="8a401-107">Стандартный шейдер МРТК предоставляет различные типы визуальных эффектов, которые можно использовать с голограммами.</span><span class="sxs-lookup"><span data-stu-id="8a401-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="8a401-108">Стандартная система затенения МРТК использует один гибкий шейдер, который может достигать визуальных элементов, аналогичных стандартному шейдеру Unity, реализует основные [принципы разработки](https://www.microsoft.com/design/fluent/#/)и продолжает работать на устройствах смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8a401-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="8a401-109">Примеры визуальных эффектов с использованием шейдера МРТК Standard</span><span class="sxs-lookup"><span data-stu-id="8a401-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="8a401-110">![Перемещение](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="8a401-110">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="8a401-111">**Неблизкое освещение**</span><span class="sxs-lookup"><span data-stu-id="8a401-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8a401-112">![Поворот](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="8a401-112">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="8a401-113">**Источник границы**</span><span class="sxs-lookup"><span data-stu-id="8a401-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="8a401-114">Стандартный шейдер МРТК в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="8a401-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="8a401-115">МРТК — Стандартный шейдер</span><span class="sxs-lookup"><span data-stu-id="8a401-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="8a401-116">См. также статью</span><span class="sxs-lookup"><span data-stu-id="8a401-116">See also</span></span>

* [<span data-ttu-id="8a401-117">Курсоры</span><span class="sxs-lookup"><span data-stu-id="8a401-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8a401-118">Телекинез</span><span class="sxs-lookup"><span data-stu-id="8a401-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="8a401-119">Button</span><span class="sxs-lookup"><span data-stu-id="8a401-119">Button</span></span>](button.md)
* [<span data-ttu-id="8a401-120">Активный объект</span><span class="sxs-lookup"><span data-stu-id="8a401-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8a401-121">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="8a401-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8a401-122">Оперирование</span><span class="sxs-lookup"><span data-stu-id="8a401-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8a401-123">Меню руки</span><span class="sxs-lookup"><span data-stu-id="8a401-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="8a401-124">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="8a401-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="8a401-125">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="8a401-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8a401-126">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="8a401-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="8a401-127">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="8a401-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="8a401-128">Подсказка</span><span class="sxs-lookup"><span data-stu-id="8a401-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="8a401-129">Планшет</span><span class="sxs-lookup"><span data-stu-id="8a401-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="8a401-130">Ползунок</span><span class="sxs-lookup"><span data-stu-id="8a401-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="8a401-131">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="8a401-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8a401-132">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="8a401-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="8a401-133">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="8a401-133">Surface magnetism</span></span>](surface-magnetism.md)
