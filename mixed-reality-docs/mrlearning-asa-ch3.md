---
title: Учебники по пространственной привязке Azure — 3. Отображение обратной связи с пространственными привязками Azure
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438415"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="575ee-105">3. Отображение обратной связи с пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="575ee-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="575ee-106">На этом занятии вы узнаете, как предоставить пользователям Отзывы об обнаружении привязок, событиях и состоянии при использовании пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="575ee-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="575ee-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="575ee-107">Objectives</span></span>

* <span data-ttu-id="575ee-108">Узнайте, как настроить панель пользовательского интерфейса, отображающую важные сведения о текущем сеансе ASA.</span><span class="sxs-lookup"><span data-stu-id="575ee-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="575ee-109">Знакомство и изучение элементов отзывов, доступных пользователям с помощью пакета SDK для ASA</span><span class="sxs-lookup"><span data-stu-id="575ee-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="575ee-110">Инструкция</span><span class="sxs-lookup"><span data-stu-id="575ee-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="575ee-111">Настройка панели пользовательского интерфейса для обратной связи ASA</span><span class="sxs-lookup"><span data-stu-id="575ee-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="575ee-112">На этом занятии мы не используем кнопки "Савеанчортодиск" и "Шареанчор", поэтому установите обе кнопки и снимите флажок на панели инспектора (как показано ниже), чтобы скрыть эти кнопки.</span><span class="sxs-lookup"><span data-stu-id="575ee-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="575ee-114">Создайте панель инструкций.</span><span class="sxs-lookup"><span data-stu-id="575ee-114">Create the instruction panel.</span></span> <span data-ttu-id="575ee-115">Для начала щелкните правой кнопкой мыши кнопку "инструкции", наведите указатель на пункт "трехмерный объект" и выберите "текстмешпро-Text".</span><span class="sxs-lookup"><span data-stu-id="575ee-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="575ee-117">Измените масштаб и расположение текста, чтобы он совпадал с инструкциями в сцене.</span><span class="sxs-lookup"><span data-stu-id="575ee-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="575ee-118">Кроме того, убедитесь, что выравнивание для всего текста осуществляется по центру.</span><span class="sxs-lookup"><span data-stu-id="575ee-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="575ee-119">Затем удалите образец текста из текстового редактора, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="575ee-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="575ee-121">Измените имя объекта Текстмешпро на "Фидбаккпанел".</span><span class="sxs-lookup"><span data-stu-id="575ee-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="575ee-123">На панели Проект выберите "активы" и щелкните правой кнопкой мыши, а затем выберите "показывать в проводнике".</span><span class="sxs-lookup"><span data-stu-id="575ee-123">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="575ee-125">Щелкните [здесь](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) , чтобы скачать файлы, необходимые в следующих шагах.</span><span class="sxs-lookup"><span data-stu-id="575ee-125">Click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="575ee-126">После открытия проводника выберите папку Assets, затем папку "Асамодулесассетс" и скопируйте сценарий обратной связи и файлы сценариев модуля привязки в папку.</span><span class="sxs-lookup"><span data-stu-id="575ee-126">Once Explorer opens, select the Assets folder, then the "ASAmodulesAssets" folder and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="575ee-128">Примечание. при появлении всплывающего сообщения с запросом на подтверждение перезаписи старого или сохранения старого нажмите кнопку перезаписать.</span><span class="sxs-lookup"><span data-stu-id="575ee-128">note: if you get a pop-up message asking if you to overwrite the old or keep the old, select overwrite.</span></span>

7. <span data-ttu-id="575ee-129">Вернитесь в папку Assets.</span><span class="sxs-lookup"><span data-stu-id="575ee-129">Return to the Assets folder.</span></span> <span data-ttu-id="575ee-130">Затем перейдите в папку «Азуреспатиаланчорсплугин», а затем папку «examples», а затем папку Scripts.</span><span class="sxs-lookup"><span data-stu-id="575ee-130">Then, go into the "AzureSpatialAnchorsPlugin" folder, followed by the Examples folder and finally the Scripts folder.</span></span> <span data-ttu-id="575ee-131">Затем скопируйте демонстрационную оболочку пространственных привязок Azure в эту папку.</span><span class="sxs-lookup"><span data-stu-id="575ee-131">Then copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="575ee-133">Теперь, когда файлы загружены, убедитесь, что в иерархии ASA_feedback выбран текст "фидбаккпанел", нажмите кнопку "добавить компонент" и добавьте сценарий обратной связи, выполнив поиск и выбрав его после появления.</span><span class="sxs-lookup"><span data-stu-id="575ee-133">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="575ee-135">Перетащите текстовый объект Фидбаккпанел из иерархии ASA_Feedback в пустой слот под сценарием, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="575ee-135">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="575ee-137">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="575ee-137">Congratulations</span></span>

<span data-ttu-id="575ee-138">На этом занятии мы узнали, как создать панель пользовательского интерфейса для отображения текущего состояния работы с пространственными привязками Azure для предоставления пользователям обратной связи в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="575ee-138">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


