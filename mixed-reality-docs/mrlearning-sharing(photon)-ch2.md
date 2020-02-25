---
title: Учебники по возможностям для нескольких пользователей — 2. Подготовка Unity к разработке
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 2bcec7e70949186c6e711120c36ee8649c006ec7
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553848"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="0304e-105">2. Подготовка Unity к разработке</span><span class="sxs-lookup"><span data-stu-id="0304e-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="0304e-106">В этом руководстве вы узнаете, как подготовить и настроить Unity для разработки приложений, включая импорт набора средств для смешанной реальности, настройку параметров сборки и подготовку сцены.</span><span class="sxs-lookup"><span data-stu-id="0304e-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="0304e-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="0304e-107">Objectives</span></span>

* <span data-ttu-id="0304e-108">Настройка Unity для разработки приложений</span><span class="sxs-lookup"><span data-stu-id="0304e-108">Configure Unity for application development</span></span>
* <span data-ttu-id="0304e-109">Импорт набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="0304e-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="0304e-110">Подготовка сцены проекта</span><span class="sxs-lookup"><span data-stu-id="0304e-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="0304e-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0304e-111">Instructions</span></span>

1. <span data-ttu-id="0304e-112">Скачайте и сохраните пакет Unity для набора средств Mixed Reality, щелкнув [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="0304e-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="0304e-113">В Unity откройте меню активы и выберите Импорт пакета, а затем щелкните пользовательский пакет.</span><span class="sxs-lookup"><span data-stu-id="0304e-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="0304e-115">Выберите пакет Unity, который вы только что скачали, по ссылке, предоставленной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="0304e-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="0304e-116">После появления всплывающего окна Импорт в Unity нажмите кнопку Импорт, чтобы начать импорт МРТК.</span><span class="sxs-lookup"><span data-stu-id="0304e-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="0304e-117">Это может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="0304e-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="0304e-119">Загруженный пакет находится в локальной папке, в которой сохранен файл.</span><span class="sxs-lookup"><span data-stu-id="0304e-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="0304e-120">На приведенном выше рисунке не отображать, где находится пакет.</span><span class="sxs-lookup"><span data-stu-id="0304e-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="0304e-121">После импорта пакета должно отобразиться окно конфигуратора проекта МРТК.</span><span class="sxs-lookup"><span data-stu-id="0304e-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="0304e-122">Если это не так, откройте его, выбрав набор средств для смешанной реальности > Служебные программы > настроить проект Unity в меню Unity.</span><span class="sxs-lookup"><span data-stu-id="0304e-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="0304e-123">В окне конфигуратора проектов МРТК разверните раздел Modify Configurations (изменение конфигураций), снимите флажок Включить MSBuild для Unity, убедитесь, что установлены все остальные параметры, и нажмите кнопку Применить, чтобы применить эти параметры.</span><span class="sxs-lookup"><span data-stu-id="0304e-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="0304e-125">Так как MSBuild для Unity может поддерживать не все пакеты SDK, которые будут использоваться, с отключением могут быть проблемы.</span><span class="sxs-lookup"><span data-stu-id="0304e-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="0304e-126">Поэтому настоятельно рекомендуется не включать MSBuild для Unity.</span><span class="sxs-lookup"><span data-stu-id="0304e-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="0304e-127">Создайте новую сцену.</span><span class="sxs-lookup"><span data-stu-id="0304e-127">Create a new scene.</span></span> <span data-ttu-id="0304e-128">Это можно сделать, щелкнув файл и выбрав создать сцену.</span><span class="sxs-lookup"><span data-stu-id="0304e-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="0304e-129">Сохраните его как Хлшаредпрожектмаин.</span><span class="sxs-lookup"><span data-stu-id="0304e-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="0304e-130">В разделе набор средств для смешанной реальности щелкните Добавить в сцену и настроить.</span><span class="sxs-lookup"><span data-stu-id="0304e-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="0304e-132">По завершении выберите набор средств смешанной реальности (МРТК) из иерархии.</span><span class="sxs-lookup"><span data-stu-id="0304e-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="0304e-133">На панели инспектора измените профиль конфигурации МРТК на DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="0304e-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="0304e-135">Выберите набор средств смешанной реальности (МРТК) из иерархии.</span><span class="sxs-lookup"><span data-stu-id="0304e-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="0304e-136">На панели инспектора Найдите сценарий набора средств Mixed Reality и нажмите кнопку "Копировать & настроить", как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="0304e-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="0304e-137">После этого появится POP и выбрать параметр клонировать во всплывающем меню.</span><span class="sxs-lookup"><span data-stu-id="0304e-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="0304e-140">Прокрутите вниз и снимите флажок Включить систему диагностики, если необходимо скрыть окно Диагностика.</span><span class="sxs-lookup"><span data-stu-id="0304e-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="0304e-141">Рекомендуется поддерживать Окно диагностики во время разработки приложения для мониторинга производительности, а затем отключать его во время демонстрации рабочей среды или приложения.</span><span class="sxs-lookup"><span data-stu-id="0304e-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="0304e-143">Откройте параметры сборки, нажав клавиши CTRL + SHIFT + B или перейдя в файловые > параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="0304e-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="0304e-144">Обратите внимание, что программа в настоящее время задается в автономной платформе PC, Mac и Linux.</span><span class="sxs-lookup"><span data-stu-id="0304e-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="0304e-145">Для разработки HoloLens 2 Задайте универсальная платформа Windows платформы.</span><span class="sxs-lookup"><span data-stu-id="0304e-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="0304e-146">Выберите его и щелкните Сменить платформу.</span><span class="sxs-lookup"><span data-stu-id="0304e-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="0304e-148">После завершения щелкните рамку Add Open сцен (Добавить открытые сцены).</span><span class="sxs-lookup"><span data-stu-id="0304e-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="0304e-149">Теперь перейдите на панель инспектора и убедитесь, что установлен флажок справа от параметра Virtual Reality Supported (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="0304e-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="0304e-150">Также убедитесь, что флажок рядом с параметром сцена/Хлшаредпрожектмаин также установлен, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="0304e-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="0304e-152">В разделе "Параметры публикации" на панели инспектора прокрутите вниз до пункта возможности и убедитесь, что установлены следующие флажки:</span><span class="sxs-lookup"><span data-stu-id="0304e-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="0304e-154">Импортируйте указанные пользовательские пакеты:</span><span class="sxs-lookup"><span data-stu-id="0304e-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="0304e-155">[Азуреспатиаланчорс. пакет unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (версия:/с)</span><span class="sxs-lookup"><span data-stu-id="0304e-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * [<span data-ttu-id="0304e-156">МРТК. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.3.0.2. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="0304e-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [<span data-ttu-id="0304e-157">МРТК. HoloLens2. Unity. Tutorials. Assets. Азуреспатиаланчорс. 2.3.0.0. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="0304e-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [<span data-ttu-id="0304e-158">МРТК. HoloLens2. Unity. Tutorials. Assets. Мултиусеркапабилитиес. 2.1.0.1. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="0304e-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="0304e-159">Напоминание о том, как настроить проект Unity для пространственных привязок Azure, см. в учебнике [Приступая к работе с пространственными привязками](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) Azure, который является частью серии руководств по [пространственной привязке Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) .</span><span class="sxs-lookup"><span data-stu-id="0304e-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="0304e-160">На панели проект перейдите в папку Prefabs.</span><span class="sxs-lookup"><span data-stu-id="0304e-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="0304e-161">В следующих шагах в сцену будет реализовано несколько Prefabs.</span><span class="sxs-lookup"><span data-stu-id="0304e-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="0304e-162">В папке Prefabs щелкните и перетащите окно prefab, отладку в иерархию.</span><span class="sxs-lookup"><span data-stu-id="0304e-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="0304e-163">По завершении сохраните проект, щелкнув файл, а затем сохранить или нажмите клавиши CTRL + S.</span><span class="sxs-lookup"><span data-stu-id="0304e-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="0304e-165">Вы можете заметить, что всплывающее окно отображается, когда вы щелкнули prefab, и запрашивается о параметрах TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="0304e-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="0304e-166">Щелкните Импортировать TMP Essentials по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="0304e-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="0304e-167">При появлении этого всплывающего окна может потребоваться удалить prefab из иерархии и повторно перетащить его в иерархию, чтобы избежать потенциальных ошибок, связанных с текстом.</span><span class="sxs-lookup"><span data-stu-id="0304e-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="0304e-169">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="0304e-169">Congratulations</span></span>

<span data-ttu-id="0304e-170">Теперь проект Unity готов для Photon.</span><span class="sxs-lookup"><span data-stu-id="0304e-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="0304e-171">В следующих учебных курсах мы создадим эту сцену и наш проект Unity в полном объеме для совместной работы.</span><span class="sxs-lookup"><span data-stu-id="0304e-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="0304e-172">[Следующее руководство: 3. Подключение нескольких пользователей](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="0304e-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
