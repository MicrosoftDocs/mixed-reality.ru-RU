---
title: Руководства по Пространственным привязкам Azure — часть 3. Отображение отзывов по пространственной привязке Azure
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 11342bada65e963db6393d35c99e2c2fbffe8ff1
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031255"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="79ef4-105">3. Отображение отзывов по пространственной привязке Azure</span><span class="sxs-lookup"><span data-stu-id="79ef4-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="79ef4-106">В третьем учебнике серии вы узнаете, как предоставить пользователям информацию о событиях обнаружения и состояниях привязки при использовании Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="79ef4-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="79ef4-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="79ef4-107">Objectives</span></span>

* <span data-ttu-id="79ef4-108">Сведения о том, как настроить панель пользовательского интерфейса для отображения важных сведений о текущем сеансе Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="79ef4-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="79ef4-109">Понимание и изучение элементов обратной связи, которые пакет SDK для Пространственных привязок Azure предоставляет пользователям</span><span class="sxs-lookup"><span data-stu-id="79ef4-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="79ef4-110">Настройка панели пользовательского интерфейса для обратной связи Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="79ef4-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="79ef4-111">В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши объект **Instructions** (Инструкции) > **TextContent** и выберите действие **3D Object** (Трехмерный объект) > **Text - TextMeshPro** (Текст — TextMeshPro), чтобы создать текстовый объект TextMeshPro в качестве дочернего для объекта Instructions (Инструкции) > TextContent, и присвойте ему произвольное имя, например **Feedback**:</span><span class="sxs-lookup"><span data-stu-id="79ef4-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="79ef4-113">Чтобы со сценой было проще работать, отключите параметр <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Видимость сцены) для объекта ParentAnchor, щелкнув значок с изображением глаза слева от этого объекта.</span><span class="sxs-lookup"><span data-stu-id="79ef4-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="79ef4-114">Так вы спрячете объект в окне сцены, не изменяя его внутриигровой видимости.</span><span class="sxs-lookup"><span data-stu-id="79ef4-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="79ef4-115">Сохраняя выделение объекта **Feedback**, измените его положение и размер в окне Inspector (Инспектор) так, чтобы он был расположен прямо под текстом инструкций, например так:</span><span class="sxs-lookup"><span data-stu-id="79ef4-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="79ef4-116">для Rect Transform укажите значение **Pos Y** = -0,24;</span><span class="sxs-lookup"><span data-stu-id="79ef4-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="79ef4-117">для Rect Transform укажите значение **Width** = 0,555;</span><span class="sxs-lookup"><span data-stu-id="79ef4-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="79ef4-118">для Rect Transform укажите значение **Height** = 0,1.</span><span class="sxs-lookup"><span data-stu-id="79ef4-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="79ef4-119">Теперь выберите свойства шрифта так, чтобы этот текст хорошо размещался в текстовой зоне, например так:</span><span class="sxs-lookup"><span data-stu-id="79ef4-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="79ef4-120">в разделе Text Mesh Pro (Script) укажите для **Font Style** (Стиль шрифта) значение Bold (Полужирный);</span><span class="sxs-lookup"><span data-stu-id="79ef4-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="79ef4-121">в разделе Text Mesh Pro (Script) укажите для **Font Size** (Размер шрифта) значение 0,17;</span><span class="sxs-lookup"><span data-stu-id="79ef4-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="79ef4-122">в разделе Text Mesh Pro (Script) укажите для **Alignment** (Выравнивание) значения Center (по центру) и Middle (посередине).</span><span class="sxs-lookup"><span data-stu-id="79ef4-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="79ef4-124">Сохраняя выделение объекта **Feedback**, в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить к этому объекту компонент **Anchor Feedback Script (Script)** (Скрипт обратной связи по привязке — скрипт).</span><span class="sxs-lookup"><span data-stu-id="79ef4-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="79ef4-126">Присвойте сам объект **Feedback** полю **Feedback Text** (Текст обратной связи) компонента **Anchor Feedback Script (Script)** (Скрипт обратной связи по привязке — скрипт).</span><span class="sxs-lookup"><span data-stu-id="79ef4-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="79ef4-128">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="79ef4-128">Congratulations</span></span>

<span data-ttu-id="79ef4-129">В этом учебнике вы узнали, как создать панель пользовательского интерфейса для отображения текущего состояния взаимодействия с Пространственной привязкой Azure, чтобы предоставлять пользователю обратную связь в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="79ef4-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
