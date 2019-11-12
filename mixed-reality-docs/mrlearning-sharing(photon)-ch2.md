---
title: Учебники по возможностям для нескольких пользователей — 2. Подготовка Unity к разработке
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 91935cb5b465e51d3948f68b818f93ba52b215f1
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914434"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="16fc1-105">2. Подготовка Unity к разработке</span><span class="sxs-lookup"><span data-stu-id="16fc1-105">2. Getting Unity ready for development</span></span> 


<span data-ttu-id="16fc1-106">В этом руководстве вы узнаете, как подготовить и настроить Unity для разработки приложений, включая импорт набора средств для смешанной реальности, настройку параметров сборки и подготовку сцены.</span><span class="sxs-lookup"><span data-stu-id="16fc1-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="16fc1-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="16fc1-107">Objectives</span></span>

- <span data-ttu-id="16fc1-108">Настройка Unity для разработки приложений</span><span class="sxs-lookup"><span data-stu-id="16fc1-108">Configure Unity for application development</span></span>

- <span data-ttu-id="16fc1-109">Импорт набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="16fc1-109">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="16fc1-110">Подготовка сцены проекта</span><span class="sxs-lookup"><span data-stu-id="16fc1-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="16fc1-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="16fc1-111">Instructions</span></span>

1. <span data-ttu-id="16fc1-112">Скачайте и сохраните пакет Unity для набора средств Mixed Reality, щелкнув [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="16fc1-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="16fc1-113">В Unity откройте меню активы и выберите Импорт пакета, а затем щелкните пользовательский пакет.</span><span class="sxs-lookup"><span data-stu-id="16fc1-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="16fc1-115">Выберите пакет Unity, который вы только что скачали, по ссылке, предоставленной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="16fc1-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="16fc1-116">После появления всплывающего окна Импорт в Unity нажмите кнопку Импорт, чтобы начать импорт МРТК.</span><span class="sxs-lookup"><span data-stu-id="16fc1-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="16fc1-117">Это может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="16fc1-117">This may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="16fc1-119">Примечание. загруженный пакет находится в локальной папке, в которой сохранен файл.</span><span class="sxs-lookup"><span data-stu-id="16fc1-119">Note: The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="16fc1-120">На приведенном выше рисунке не отображать, где находится пакет.</span><span class="sxs-lookup"><span data-stu-id="16fc1-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="16fc1-121">Создайте новую сцену.</span><span class="sxs-lookup"><span data-stu-id="16fc1-121">Create a new scene.</span></span> <span data-ttu-id="16fc1-122">Это можно сделать, щелкнув файл и выбрав создать сцену.</span><span class="sxs-lookup"><span data-stu-id="16fc1-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="16fc1-123">Сохраните его как Хлшаредпрожектмаин.</span><span class="sxs-lookup"><span data-stu-id="16fc1-123">Save it as HLSharedProjectMain.</span></span>

> <span data-ttu-id="16fc1-124">Примечание. Вы можете получить всплывающее окно, похожее на изображение ниже.</span><span class="sxs-lookup"><span data-stu-id="16fc1-124">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="16fc1-125">Пока нажмите кнопку нет.</span><span class="sxs-lookup"><span data-stu-id="16fc1-125">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="16fc1-127">В разделе набор средств для смешанной реальности щелкните Добавить в сцену и настроить.</span><span class="sxs-lookup"><span data-stu-id="16fc1-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="16fc1-129">После завершения работы появится новый файл конфигурации, в котором можно настроить профиль.</span><span class="sxs-lookup"><span data-stu-id="16fc1-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> 

![Module2Chapter1step4im](images/Module2Chapter1step4im.PNG)

7. <span data-ttu-id="16fc1-131">Выберите набор средств смешанной реальности (МРТК) из иерархии.</span><span class="sxs-lookup"><span data-stu-id="16fc1-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="16fc1-132">На панели инспектора Найдите сценарий набора средств Mixed Reality и нажмите кнопку "Копировать & настроить", как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="16fc1-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="16fc1-133">После этого появится POP и выбрать параметр клонировать во всплывающем меню.</span><span class="sxs-lookup"><span data-stu-id="16fc1-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

7. <span data-ttu-id="16fc1-136">Прокрутите вниз и снимите флажок Включить систему диагностики, если необходимо скрыть окно Диагностика.</span><span class="sxs-lookup"><span data-stu-id="16fc1-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="16fc1-137">Рекомендуется поддерживать Окно диагностики во время разработки приложения для мониторинга производительности, а затем отключать его во время демонстрации рабочей среды или приложения.</span><span class="sxs-lookup"><span data-stu-id="16fc1-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="16fc1-139">Откройте параметры сборки, нажав клавиши CTRL + SHIFT + B или перейдя в файловые > параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="16fc1-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="16fc1-140">Обратите внимание, что программа в настоящее время задается в автономной платформе PC, Mac и Linux.</span><span class="sxs-lookup"><span data-stu-id="16fc1-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="16fc1-141">Для разработки HoloLens 2 Задайте универсальная платформа Windows платформы.</span><span class="sxs-lookup"><span data-stu-id="16fc1-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="16fc1-142">Выберите его и щелкните Сменить платформу.</span><span class="sxs-lookup"><span data-stu-id="16fc1-142">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="16fc1-144">После завершения щелкните рамку Add Open сцен (Добавить открытые сцены).</span><span class="sxs-lookup"><span data-stu-id="16fc1-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="16fc1-145">Теперь перейдите на панель инспектора и убедитесь, что установлен флажок справа от параметра Virtual Reality Supported (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="16fc1-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="16fc1-146">Также убедитесь, что флажок рядом с параметром сцена/Хлшаредпрожектмаин также установлен, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="16fc1-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="16fc1-148">В разделе "Параметры публикации" на панели инспектора прокрутите вниз до пункта возможности и убедитесь, что установлены следующие флажки:</span><span class="sxs-lookup"><span data-stu-id="16fc1-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="16fc1-150">Импортируйте пользовательский пакет с именем Шарингассетколлектион, который можно скачать [здесь.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span><span class="sxs-lookup"><span data-stu-id="16fc1-150">Import the custom package called SharingAssetCollection, which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="16fc1-152">На панели проект перейдите в папку Prefabs.</span><span class="sxs-lookup"><span data-stu-id="16fc1-152">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="16fc1-153">В следующих шагах в сцену будет реализовано несколько Prefabs.</span><span class="sxs-lookup"><span data-stu-id="16fc1-153">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="16fc1-154">В папке Prefabs щелкните и перетащите окно prefab, отладку в иерархию.</span><span class="sxs-lookup"><span data-stu-id="16fc1-154">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="16fc1-155">По завершении сохраните проект, щелкнув файл, а затем сохранить или нажмите клавиши CTRL + S.</span><span class="sxs-lookup"><span data-stu-id="16fc1-155">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="16fc1-157">Примечание. Вы можете заметить, что всплывающее окно отображается при щелчке prefab, предлагающем о параметрах TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="16fc1-157">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="16fc1-158">Щелкните Импортировать TMP Essentials по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="16fc1-158">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="16fc1-159">При появлении этого всплывающего окна может потребоваться удалить prefab из иерархии и повторно перетащить его в иерархию, чтобы избежать потенциальных ошибок, связанных с текстом.</span><span class="sxs-lookup"><span data-stu-id="16fc1-159">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="16fc1-161">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="16fc1-161">Congratulations</span></span>

<span data-ttu-id="16fc1-162">Теперь проект Unity готов для Photon.</span><span class="sxs-lookup"><span data-stu-id="16fc1-162">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="16fc1-163">В следующих учебных курсах мы создадим эту сцену и наш проект Unity в полном объеме для совместной работы.</span><span class="sxs-lookup"><span data-stu-id="16fc1-163">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="16fc1-164">[Следующее руководство: 3. Подключение нескольких пользователей](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="16fc1-164">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

