---
title: Учебники по возможностям для нескольких пользователей — 2. Подготовка Unity к разработке
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 6abf4fa8fc87afc7007d6f7c76becfbd88ed7a12
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901519"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="d76cd-105">2. Подготовка Unity к разработке</span><span class="sxs-lookup"><span data-stu-id="d76cd-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="d76cd-106">В этом руководстве вы узнаете, как подготовить и настроить Unity для разработки приложений, включая импорт набора средств для смешанной реальности, настройку параметров сборки и подготовку сцены.</span><span class="sxs-lookup"><span data-stu-id="d76cd-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="d76cd-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="d76cd-107">Objectives</span></span>

* <span data-ttu-id="d76cd-108">Настройка Unity для разработки приложений</span><span class="sxs-lookup"><span data-stu-id="d76cd-108">Configure Unity for application development</span></span>
* <span data-ttu-id="d76cd-109">Импорт набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="d76cd-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="d76cd-110">Подготовка сцены проекта</span><span class="sxs-lookup"><span data-stu-id="d76cd-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="d76cd-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="d76cd-111">Instructions</span></span>

1. <span data-ttu-id="d76cd-112">Скачайте и сохраните пакет Unity для набора средств Mixed Reality, щелкнув [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="d76cd-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="d76cd-113">В Unity откройте меню активы и выберите Импорт пакета, а затем щелкните пользовательский пакет.</span><span class="sxs-lookup"><span data-stu-id="d76cd-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="d76cd-115">Выберите пакет Unity, который вы только что скачали, по ссылке, предоставленной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="d76cd-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="d76cd-116">После появления всплывающего окна Импорт в Unity нажмите кнопку Импорт, чтобы начать импорт МРТК.</span><span class="sxs-lookup"><span data-stu-id="d76cd-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="d76cd-117">Это может занять несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="d76cd-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="d76cd-119">Загруженный пакет находится в локальной папке, в которой сохранен файл.</span><span class="sxs-lookup"><span data-stu-id="d76cd-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="d76cd-120">На приведенном выше рисунке не отображать, где находится пакет.</span><span class="sxs-lookup"><span data-stu-id="d76cd-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="d76cd-121">Создайте новую сцену.</span><span class="sxs-lookup"><span data-stu-id="d76cd-121">Create a new scene.</span></span> <span data-ttu-id="d76cd-122">Это можно сделать, щелкнув файл и выбрав создать сцену.</span><span class="sxs-lookup"><span data-stu-id="d76cd-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="d76cd-123">Сохраните его как Хлшаредпрожектмаин.</span><span class="sxs-lookup"><span data-stu-id="d76cd-123">Save it as HLSharedProjectMain.</span></span>

    <span data-ttu-id="d76cd-124">Вы можете получить всплывающее окно, похожее на изображение ниже.</span><span class="sxs-lookup"><span data-stu-id="d76cd-124">You may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="d76cd-125">Пока нажмите кнопку нет.</span><span class="sxs-lookup"><span data-stu-id="d76cd-125">For now, click No.</span></span>
    <span data-ttu-id="d76cd-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span><span class="sxs-lookup"><span data-stu-id="d76cd-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span></span>

5. <span data-ttu-id="d76cd-127">В разделе набор средств для смешанной реальности щелкните Добавить в сцену и настроить.</span><span class="sxs-lookup"><span data-stu-id="d76cd-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="d76cd-129">После завершения работы появится новый файл конфигурации, в котором можно настроить профиль.</span><span class="sxs-lookup"><span data-stu-id="d76cd-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="d76cd-131">Выберите набор средств смешанной реальности (МРТК) из иерархии.</span><span class="sxs-lookup"><span data-stu-id="d76cd-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="d76cd-132">На панели инспектора Найдите сценарий набора средств Mixed Reality и нажмите кнопку "Копировать & настроить", как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d76cd-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="d76cd-133">После этого появится POP и выбрать параметр клонировать во всплывающем меню.</span><span class="sxs-lookup"><span data-stu-id="d76cd-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="d76cd-136">Прокрутите вниз и снимите флажок Включить систему диагностики, если необходимо скрыть окно Диагностика.</span><span class="sxs-lookup"><span data-stu-id="d76cd-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="d76cd-137">Рекомендуется поддерживать Окно диагностики во время разработки приложения для мониторинга производительности, а затем отключать его во время демонстрации рабочей среды или приложения.</span><span class="sxs-lookup"><span data-stu-id="d76cd-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="d76cd-139">Откройте параметры сборки, нажав клавиши CTRL + SHIFT + B или перейдя в файловые > параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="d76cd-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="d76cd-140">Обратите внимание, что программа в настоящее время задается в автономной платформе PC, Mac и Linux.</span><span class="sxs-lookup"><span data-stu-id="d76cd-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="d76cd-141">Для разработки HoloLens 2 Задайте универсальная платформа Windows платформы.</span><span class="sxs-lookup"><span data-stu-id="d76cd-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="d76cd-142">Выберите его и щелкните Сменить платформу.</span><span class="sxs-lookup"><span data-stu-id="d76cd-142">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="d76cd-144">После завершения щелкните рамку Add Open сцен (Добавить открытые сцены).</span><span class="sxs-lookup"><span data-stu-id="d76cd-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="d76cd-145">Теперь перейдите на панель инспектора и убедитесь, что установлен флажок справа от параметра Virtual Reality Supported (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="d76cd-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="d76cd-146">Также убедитесь, что флажок рядом с параметром сцена/Хлшаредпрожектмаин также установлен, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d76cd-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="d76cd-148">В разделе "Параметры публикации" на панели инспектора прокрутите вниз до пункта возможности и убедитесь, что установлены следующие флажки:</span><span class="sxs-lookup"><span data-stu-id="d76cd-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="d76cd-150">Импортируйте указанные пользовательские пакеты:</span><span class="sxs-lookup"><span data-stu-id="d76cd-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="d76cd-151">А.</span><span class="sxs-lookup"><span data-stu-id="d76cd-151">a.</span></span> <span data-ttu-id="d76cd-152">[Азуреспатиаланчорс. пакет unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (версия 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="d76cd-152">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>

    <span data-ttu-id="d76cd-153">Б.</span><span class="sxs-lookup"><span data-stu-id="d76cd-153">b.</span></span> [<span data-ttu-id="d76cd-154">МРТК. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.1.0.1. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="d76cd-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)

    <span data-ttu-id="d76cd-155">в.</span><span class="sxs-lookup"><span data-stu-id="d76cd-155">c.</span></span> [<span data-ttu-id="d76cd-156">МРТК. HoloLens2. Unity. Tutorials. Assets. Азуреспатиаланчорс. 2.1.0.1. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="d76cd-156">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

    <span data-ttu-id="d76cd-157">г.</span><span class="sxs-lookup"><span data-stu-id="d76cd-157">d.</span></span> [<span data-ttu-id="d76cd-158">МРТК. HoloLens2. Unity. Tutorials. Assets. Мултиусеркапабилитиес. 2.1.0.1. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="d76cd-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="d76cd-159">Напоминание о том, как настроить проект Unity для пространственных привязок Azure, см. в учебнике [Приступая к работе с пространственными привязками](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) Azure, который является частью серии руководств по [пространственной привязке Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) .</span><span class="sxs-lookup"><span data-stu-id="d76cd-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. <span data-ttu-id="d76cd-161">На панели проект перейдите в папку Prefabs.</span><span class="sxs-lookup"><span data-stu-id="d76cd-161">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="d76cd-162">В следующих шагах в сцену будет реализовано несколько Prefabs.</span><span class="sxs-lookup"><span data-stu-id="d76cd-162">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="d76cd-163">В папке Prefabs щелкните и перетащите окно prefab, отладку в иерархию.</span><span class="sxs-lookup"><span data-stu-id="d76cd-163">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="d76cd-164">По завершении сохраните проект, щелкнув файл, а затем сохранить или нажмите клавиши CTRL + S.</span><span class="sxs-lookup"><span data-stu-id="d76cd-164">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="d76cd-166">Вы можете заметить, что всплывающее окно отображается, когда вы щелкнули prefab, и запрашивается о параметрах TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="d76cd-166">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="d76cd-167">Щелкните Импортировать TMP Essentials по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="d76cd-167">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="d76cd-168">При появлении этого всплывающего окна может потребоваться удалить prefab из иерархии и повторно перетащить его в иерархию, чтобы избежать потенциальных ошибок, связанных с текстом.</span><span class="sxs-lookup"><span data-stu-id="d76cd-168">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="d76cd-170">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d76cd-170">Congratulations</span></span>

<span data-ttu-id="d76cd-171">Теперь проект Unity готов для Photon.</span><span class="sxs-lookup"><span data-stu-id="d76cd-171">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="d76cd-172">В следующих учебных курсах мы создадим эту сцену и наш проект Unity в полном объеме для совместной работы.</span><span class="sxs-lookup"><span data-stu-id="d76cd-172">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="d76cd-173">[Следующее руководство: 3. Подключение нескольких пользователей](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="d76cd-173">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
