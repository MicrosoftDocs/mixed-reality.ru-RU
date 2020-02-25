---
title: Учебники по пространственной привязке Azure — 3. Отображение обратной связи с пространственными привязками Azure
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 3d762950ea8e211fd5a8e4cf8af717674d3fe7e1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553954"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="1b5aa-105">3. Отображение обратной связи с пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="1b5aa-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="1b5aa-106">В этом руководстве вы узнаете, как предоставить пользователям Отзывы о процессе обнаружения привязки, событиях и состоянии при использовании пространственных привязок Azure (ASA).</span><span class="sxs-lookup"><span data-stu-id="1b5aa-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="1b5aa-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="1b5aa-107">Objectives</span></span>

* <span data-ttu-id="1b5aa-108">Узнайте, как настроить панель пользовательского интерфейса, отображающую важные сведения о текущем сеансе ASA.</span><span class="sxs-lookup"><span data-stu-id="1b5aa-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="1b5aa-109">Знакомство и изучение элементов отзывов, доступных пользователям с помощью пакета SDK для ASA</span><span class="sxs-lookup"><span data-stu-id="1b5aa-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="1b5aa-110">Настройка панели пользовательского интерфейса для обратной связи ASA</span><span class="sxs-lookup"><span data-stu-id="1b5aa-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="1b5aa-111">В окне Иерархия щелкните правой кнопкой мыши **инструкции** > объект **TextContent** и выберите **трехмерный объект** > **Text-текстмешпро** , чтобы создать текстовый объект Текстмешпро в качестве дочернего элемента для инструкций > TextContent и присвоить ему подходящее имя, например, **обратная связь**:</span><span class="sxs-lookup"><span data-stu-id="1b5aa-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="1b5aa-113">Чтобы упростить работу с сценой, установите <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">видимость сцены</a> для объекта парентанчор, щелкнув значок глаза слева от объекта.</span><span class="sxs-lookup"><span data-stu-id="1b5aa-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="1b5aa-114">Это скрывает объект в окне сцены, не изменяя видимую для игры видимость.</span><span class="sxs-lookup"><span data-stu-id="1b5aa-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="1b5aa-115">Если объект **обратной связи** все еще выбран, в окне инспектора измените его расположение и размер так, чтобы он размещался под текстом инструкции, например:</span><span class="sxs-lookup"><span data-stu-id="1b5aa-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="1b5aa-116">Изменение преобразования Rect **POS Y** на-0,24</span><span class="sxs-lookup"><span data-stu-id="1b5aa-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="1b5aa-117">Изменение **ширины** преобразования Rect на 0,555</span><span class="sxs-lookup"><span data-stu-id="1b5aa-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="1b5aa-118">Изменение **высоты** преобразования Rect на 0,1</span><span class="sxs-lookup"><span data-stu-id="1b5aa-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="1b5aa-119">Затем выберите свойства шрифта, чтобы текст соответствовал тексту в области, например:</span><span class="sxs-lookup"><span data-stu-id="1b5aa-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="1b5aa-120">Изменение **стиля шрифта** (скрипт) для текстового сетки на полужирный</span><span class="sxs-lookup"><span data-stu-id="1b5aa-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="1b5aa-121">Измените **Размер шрифта** Pro (скрипт) для сетки текста на 0,17</span><span class="sxs-lookup"><span data-stu-id="1b5aa-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="1b5aa-122">Изменение **выравнивания** (сценария) сетки текста по центру и по середине</span><span class="sxs-lookup"><span data-stu-id="1b5aa-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="1b5aa-124">Выбрав объект **Feedback** , в окне инспектора нажмите кнопку **Добавить компонент** , чтобы добавить компонент " **Скрипт обратной связи" (скрипт)** в объект обратной связи:</span><span class="sxs-lookup"><span data-stu-id="1b5aa-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="1b5aa-126">Назначьте объект **обратной связи** в **текстовое поле Feedback** **(сценарий)** для компонента обратной связи:</span><span class="sxs-lookup"><span data-stu-id="1b5aa-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="1b5aa-128">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="1b5aa-128">Congratulations</span></span>

<span data-ttu-id="1b5aa-129">В этом учебнике вы узнали, как создать панель пользовательского интерфейса для отображения текущего состояния работы с пространственными привязками Azure для предоставления пользователям обратной связи в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="1b5aa-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
