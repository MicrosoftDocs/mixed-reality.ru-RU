---
title: Модуль MR Learning ASA. пространственный якорь Azure в HoloLens 2
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: cfd6ac9997a8a5d962603922f473bd6fc5d708ed
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485734"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="316f2-104">3. Отображение обратной связи с пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="316f2-104">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="316f2-105">На этом занятии вы узнаете, как предоставить пользователям Отзывы об обнаружении привязок, событиях и состоянии при использовании пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="316f2-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="316f2-106">Цели</span><span class="sxs-lookup"><span data-stu-id="316f2-106">Objectives</span></span>

* <span data-ttu-id="316f2-107">Узнайте, как настроить панель пользовательского интерфейса, отображающую важные сведения о текущем сеансе ASA.</span><span class="sxs-lookup"><span data-stu-id="316f2-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="316f2-108">Знакомство и изучение элементов отзывов, доступных пользователям с помощью пакета SDK для ASA</span><span class="sxs-lookup"><span data-stu-id="316f2-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="316f2-109">Инструкция</span><span class="sxs-lookup"><span data-stu-id="316f2-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="316f2-110">Настройка панели пользовательского интерфейса для обратной связи ASA</span><span class="sxs-lookup"><span data-stu-id="316f2-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="316f2-111">На этом занятии мы не используем кнопки "Савеанчортодиск" и "Шареанчор", поэтому установите обе кнопки и снимите флажок на панели инспектора (как показано ниже), чтобы скрыть эти кнопки.</span><span class="sxs-lookup"><span data-stu-id="316f2-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="316f2-113">Затем создайте панель инструкций.</span><span class="sxs-lookup"><span data-stu-id="316f2-113">Next, create the instruction panel.</span></span> <span data-ttu-id="316f2-114">Для начала щелкните правой кнопкой мыши кнопку "инструкции", наведите указатель на пункт "трехмерный объект" и выберите "текстмешпро-Text".</span><span class="sxs-lookup"><span data-stu-id="316f2-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="316f2-116">Измените масштаб и расположение текста так, чтобы оно совпадало с инструкциями в сцене.</span><span class="sxs-lookup"><span data-stu-id="316f2-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="316f2-117">Кроме того, убедитесь, что выравнивание для всего текста осуществляется по центру.</span><span class="sxs-lookup"><span data-stu-id="316f2-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="316f2-118">Затем удалите образец текста из текстового редактора, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="316f2-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="316f2-120">Измените имя объекта Текстмешпро на "Фидбаккпанел".</span><span class="sxs-lookup"><span data-stu-id="316f2-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="316f2-122">На панели Проект выберите "активы" и щелкните правой кнопкой мыши, а затем выберите "показывать в проводнике".</span><span class="sxs-lookup"><span data-stu-id="316f2-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="316f2-124">Теперь щелкните [здесь](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) , чтобы скачать файлы, необходимые в следующих шагах.</span><span class="sxs-lookup"><span data-stu-id="316f2-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="316f2-125">После открытия проводника выберите папку Assets, затем папку "Асамодулесассетс" и скопируйте сценарий обратной связи и файлы сценариев модуля привязки в папку.</span><span class="sxs-lookup"><span data-stu-id="316f2-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="316f2-127">Примечание. Если появится всплывающее окно с запросом о том, что вы хотите перезаписать старую версию или сохранить старую, убедитесь, что выбран параметр Перезаписать.</span><span class="sxs-lookup"><span data-stu-id="316f2-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="316f2-128">Теперь вернитесь в папку Assets.</span><span class="sxs-lookup"><span data-stu-id="316f2-128">Now return to the Assets folder.</span></span> <span data-ttu-id="316f2-129">Затем перейдите в папку "Азуреспатиаланчорсплугин", затем папку examples, а затем папку Scripts и скопируйте в нее демонстрационную оболочку пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="316f2-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="316f2-131">Теперь, когда файлы передаются, убедитесь, что выбран текст "фидбаккпанел", в иерархии ASA_feedback и щелкните "добавить компонент" и добавьте сценарий обратной связи, выполнив поиск и выбрав его после появления.</span><span class="sxs-lookup"><span data-stu-id="316f2-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="316f2-133">Перетащите текстовый объект Фидбаккпанел из иерархии ASA_Feedback в пустой слот под сценарием, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="316f2-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="316f2-135">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="316f2-135">Congratulations</span></span>

<span data-ttu-id="316f2-136">На этом занятии мы узнали, как создать панель пользовательского интерфейса для отображения текущего состояния работы с пространственными привязками Azure для предоставления пользователю обратной связи в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="316f2-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


