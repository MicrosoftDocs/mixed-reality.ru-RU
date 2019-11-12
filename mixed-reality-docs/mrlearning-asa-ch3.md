---
title: Учебники по пространственной привязке Azure — 3. Отображение обратной связи с пространственными привязками Azure
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 9f57cb9874aade2d6b19d0c061fd83eb04b9ef11
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914382"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="d252d-105">3. Отображение обратной связи с пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="d252d-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="d252d-106">На этом занятии вы узнаете, как предоставить пользователям Отзывы об обнаружении привязок, событиях и состоянии при использовании пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d252d-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="d252d-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="d252d-107">Objectives</span></span>

* <span data-ttu-id="d252d-108">Узнайте, как настроить панель пользовательского интерфейса, отображающую важные сведения о текущем сеансе ASA.</span><span class="sxs-lookup"><span data-stu-id="d252d-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="d252d-109">Знакомство и изучение элементов отзывов, доступных пользователям с помощью пакета SDK для ASA</span><span class="sxs-lookup"><span data-stu-id="d252d-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="d252d-110">Инструкция</span><span class="sxs-lookup"><span data-stu-id="d252d-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="d252d-111">Настройка панели пользовательского интерфейса для обратной связи ASA</span><span class="sxs-lookup"><span data-stu-id="d252d-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="d252d-112">На этом занятии мы не используем кнопки "Савеанчортодиск" и "Шареанчор", поэтому установите обе кнопки и снимите флажок на панели инспектора (как показано ниже), чтобы скрыть эти кнопки.</span><span class="sxs-lookup"><span data-stu-id="d252d-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="d252d-114">Создайте панель инструкций.</span><span class="sxs-lookup"><span data-stu-id="d252d-114">Create the instruction panel.</span></span> <span data-ttu-id="d252d-115">Для начала щелкните правой кнопкой мыши кнопку "инструкции", наведите указатель на пункт "трехмерный объект" и выберите "текстмешпро-Text".</span><span class="sxs-lookup"><span data-stu-id="d252d-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="d252d-117">Измените масштаб и расположение текста, чтобы он совпадал с инструкциями в сцене.</span><span class="sxs-lookup"><span data-stu-id="d252d-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="d252d-118">Кроме того, убедитесь, что выравнивание для всего текста осуществляется по центру.</span><span class="sxs-lookup"><span data-stu-id="d252d-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="d252d-119">Затем удалите образец текста из текстового редактора, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d252d-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="d252d-121">Измените имя объекта Текстмешпро на "Фидбаккпанел".</span><span class="sxs-lookup"><span data-stu-id="d252d-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="d252d-123">Убедитесь, что в иерархии ASA_feedback выбран текст "фидбаккпанел", нажмите кнопку "добавить компонент" и добавьте сценарий обратной связи, выполнив поиск и выбрав его после появления.</span><span class="sxs-lookup"><span data-stu-id="d252d-123">Ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. <span data-ttu-id="d252d-125">Перетащите текстовый объект Фидбаккпанел из иерархии ASA_Feedback в пустой слот под сценарием, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d252d-125">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="d252d-127">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d252d-127">Congratulations</span></span>

<span data-ttu-id="d252d-128">На этом занятии мы узнали, как создать панель пользовательского интерфейса для отображения текущего состояния работы с пространственными привязками Azure для предоставления пользователям обратной связи в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="d252d-128">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


