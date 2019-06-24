---
title: Модуль ASA обучения MR Azure пространственных привязка в HoloLens 2
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326800"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="1f851-104">Отображение отзывов Azure пространственных привязки</span><span class="sxs-lookup"><span data-stu-id="1f851-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="1f851-105">На этом занятии вы узнаете о том, как предоставить пользователям возможность отзыв о привязки обнаружения, события и состояние, при использовании привязки пространственных Azure.</span><span class="sxs-lookup"><span data-stu-id="1f851-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="1f851-106">Цели:</span><span class="sxs-lookup"><span data-stu-id="1f851-106">Objectives:</span></span>

* <span data-ttu-id="1f851-107">Узнайте, как настроить пользовательский Интерфейс панель, в которой отображаются важные сведения о текущем сеансе ASA</span><span class="sxs-lookup"><span data-stu-id="1f851-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="1f851-108">Изучение отзывов элементы, которые пакет SDK ASA делает доступными пользователям вопроса</span><span class="sxs-lookup"><span data-stu-id="1f851-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

  

## <a name="instructions"></a><span data-ttu-id="1f851-109">Инструкция</span><span class="sxs-lookup"><span data-stu-id="1f851-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="1f851-110">Настроить панель пользовательского интерфейса ASA отзывов</span><span class="sxs-lookup"><span data-stu-id="1f851-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="1f851-111">На этом занятии мы не используем «SaveAnchorToDisk» и «ShareAnchor» кнопки, поэтому выберите обе кнопки и снимите этот флажок, на панели инспектора (как показано ниже), чтобы скрыть эти кнопки.</span><span class="sxs-lookup"><span data-stu-id="1f851-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="1f851-113">Создайте панели «инструкции».</span><span class="sxs-lookup"><span data-stu-id="1f851-113">Next, create the instruction panel.</span></span> <span data-ttu-id="1f851-114">Запустить, щелкнув правой кнопкой мыши кнопку «instructions», наведите указатель мыши «трехмерный объект» и выберите «textmeshpro-text».</span><span class="sxs-lookup"><span data-stu-id="1f851-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. <span data-ttu-id="1f851-116">Измените масштаб и позиционирования текста, чтобы он соответствовал с инструкциями в сцене.</span><span class="sxs-lookup"><span data-stu-id="1f851-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="1f851-117">Кроме того убедитесь, что выравнивание для весь текст выравнивается по центру.</span><span class="sxs-lookup"><span data-stu-id="1f851-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="1f851-118">Удалите текст из текстового редактора, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="1f851-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="1f851-120">Измените имя объекта TextMeshPro на «FeedbackPanel.»</span><span class="sxs-lookup"><span data-stu-id="1f851-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. <span data-ttu-id="1f851-122">На панели «Проект» выберите «активы» и щелкните правой кнопкой мыши, а затем выберите «Показать в обозревателе».</span><span class="sxs-lookup"><span data-stu-id="1f851-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="1f851-124">Теперь щелкните [здесь](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) для загрузки файлов требуется в следующих шагах.</span><span class="sxs-lookup"><span data-stu-id="1f851-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="1f851-125">После открытия обозревателя выберите папку assets, а затем папку «ASAmodulesAssets» и скопируйте скрипт обратной связи привязки и файлы скриптов модуля привязки в папку.</span><span class="sxs-lookup"><span data-stu-id="1f851-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="1f851-127">Обратите внимание: Если появится всплывающее окно, запросом, вас, если вы хотите перезаписать старую или сохранить старую обязательно выберите перезапись.</span><span class="sxs-lookup"><span data-stu-id="1f851-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="1f851-128">Теперь вернемся к папке средств.</span><span class="sxs-lookup"><span data-stu-id="1f851-128">Now return to the Assets folder.</span></span> <span data-ttu-id="1f851-129">Затем перейдите в папку «AzureSpatialAnchorsPlugin», а затем папки с примерами и, наконец, в папку scripts и скопируйте оболочки Демонстрация Azure пространственных привязки в эту папку.</span><span class="sxs-lookup"><span data-stu-id="1f851-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="1f851-131">Теперь, когда файлы передаются, убедитесь, что текст «feedbackpanel» выбран в иерархии ASA_feedback и нажмите кнопку «Добавить компонент» и добавьте скрипт обратной связи привязки, его поиск и выбрав его, как только он появится.</span><span class="sxs-lookup"><span data-stu-id="1f851-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="1f851-133">Перетащите объект текст «feedbackPanel» из иерархии ASA_Feedback в пустой слот под сценарий, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="1f851-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a><span data-ttu-id="1f851-135">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="1f851-135">Congratulations</span></span>

<span data-ttu-id="1f851-136">В этом уроке мы узнали, как для создания области пользовательского интерфейса для отображения текущего состояния запуска привязки пространственных Azure для предоставления пользователю обратной связи в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="1f851-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


