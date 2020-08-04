---
title: Руководства по Пространственным привязкам Azure, часть 4 Отображение отзывов по Пространственным привязкам Azure
description: Пройдите этот курс и узнайте, как реализовать Пространственные привязки Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: afcd7753fb2296503e67a1977b183df951124560
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376526"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a><span data-ttu-id="d4970-105">4. Отображение отзывов по Пространственным привязкам Azure</span><span class="sxs-lookup"><span data-stu-id="d4970-105">4. Displaying feedback from Azure Spatial Anchors</span></span>

<span data-ttu-id="d4970-106">В этом руководстве показано, как предоставить пользователям обратную связь о событиях обнаружения и состояниях привязки при использовании Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d4970-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="d4970-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="d4970-107">Objectives</span></span>

* <span data-ttu-id="d4970-108">Узнать, как настроить панель пользовательского интерфейса для отображения важных сведений о текущем сеансе Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d4970-108">Learn how to set up a UI panel that displays essential information about the current ASA session</span></span>
* <span data-ttu-id="d4970-109">Узнать об элементах обратной связи, которые пакет SDK для Пространственных привязок Azure предоставляет пользователям.</span><span class="sxs-lookup"><span data-stu-id="d4970-109">learn about and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="setting-up-asa-feedback-panel"></a><span data-ttu-id="d4970-110">Настройка панели пользовательского интерфейса для предоставления обратной связи о Пространственных привязках Azure</span><span class="sxs-lookup"><span data-stu-id="d4970-110">Setting up ASA feedback panel</span></span>

<span data-ttu-id="d4970-111">В окне иерархии щелкните правой кнопкой мыши объект **Instructions** > **TextContent** (Инструкции > TextContent).</span><span class="sxs-lookup"><span data-stu-id="d4970-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object.</span></span> <span data-ttu-id="d4970-112">Выберите **3D Object** > **Text - TextMeshPro** (Трехмерный объект > Текст — TextMeshPro), чтобы создать текстовый объект TextMeshPro как дочерний объект объекта TextContent.</span><span class="sxs-lookup"><span data-stu-id="d4970-112">Select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="d4970-114">Чтобы со сценой было проще работать, отключите параметр <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Видимость сцены) для объекта ParentAnchor, щелкнув значок с изображением глаза слева от этого объекта.</span><span class="sxs-lookup"><span data-stu-id="d4970-114">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="d4970-115">Так вы спрячете объект в окне сцены, не изменяя его внутриигровой видимости.</span><span class="sxs-lookup"><span data-stu-id="d4970-115">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="d4970-116">Переименуйте созданный текстовый объект (TMP) в **Feedback** (Обратная связь), а затем в окне инспектора измените его расположение и размер, чтобы он размещался под текстом инструкции, например:</span><span class="sxs-lookup"><span data-stu-id="d4970-116">Rename the newly created Text (TMP) object **Feedback**, then, in the Inspector window, change its position and size, so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="d4970-117">измените значение **Pos Y** (Позиция Y) компонента Rect Transform на -0,24;</span><span class="sxs-lookup"><span data-stu-id="d4970-117">Change the Rect Transform component's **Pos Y** to -0.24.</span></span>
* <span data-ttu-id="d4970-118">измените значение **Width** (Ширина) компонента Rect Transform на 0,555;</span><span class="sxs-lookup"><span data-stu-id="d4970-118">Change the Rect Transform component's **Width** to 0.555.</span></span>
* <span data-ttu-id="d4970-119">измените значение **Height** (Высота) компонента Rect Transform на 0,1.</span><span class="sxs-lookup"><span data-stu-id="d4970-119">Change the Rect Transform component's **Height** to 0.1.</span></span>

<span data-ttu-id="d4970-120">Теперь выберите свойства шрифта так, чтобы текст размещался в текстовой зоне, например:</span><span class="sxs-lookup"><span data-stu-id="d4970-120">Then choose font properties, so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="d4970-121">измените значение **Font Style** (Стиль шрифта) текстового компонента TextMeshPro на Bold;</span><span class="sxs-lookup"><span data-stu-id="d4970-121">Change the TextMeshPro - Text component's **Font Style** to Bold.</span></span>
* <span data-ttu-id="d4970-122">измените значение **Font Size** (Размер шрифта) текстового компонента TextMeshPro на 0.17;</span><span class="sxs-lookup"><span data-stu-id="d4970-122">Change the TextMeshPro - Text component's **Font Size** to 0.17.</span></span>
* <span data-ttu-id="d4970-123">измените значение **Alignment** (Выравнивание) текстового компонента TextMeshPro на Center (По центру) и Middle (Посередине).</span><span class="sxs-lookup"><span data-stu-id="d4970-123">Change the TextMeshPro - Text component's **Alignment** to Center and Middle.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

<span data-ttu-id="d4970-125">В окне иерархии выберите объект **Feedback** (Обратная связь), а затем в окне инспектора используйте кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **Anchor Feedback Script (Script)** (Скрипт обратной связи по привязке — скрипт) и настроить его следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d4970-125">In the Hierarchy window, select the **Feedback** object still, then in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="d4970-126">В поле **Feedback Text** (Текст обратной связи) компонента **Anchor Feedback Script (Script)** (Скрипт обратной связи по привязке — скрипт) укажите сам объект **Feedback** (Обратная связь).</span><span class="sxs-lookup"><span data-stu-id="d4970-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="d4970-128">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d4970-128">Congratulations</span></span>

<span data-ttu-id="d4970-129">В этом руководстве показано, как создать панель пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d4970-129">In this tutorial, you learned how to create a UI panel.</span></span> <span data-ttu-id="d4970-130">На ней отображается текущее состояние взаимодействия с Пространственными привязками Azure для предоставления пользователям обратной связи в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="d4970-130">It displays the current status of the Azure Spatial Anchors experience for providing users with real-time feedback.</span></span>

[<span data-ttu-id="d4970-131">Следующее руководство: 5. Пространственные привязки Azure для Android и iOS</span><span class="sxs-lookup"><span data-stu-id="d4970-131">Next Tutorial: 5. Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)
