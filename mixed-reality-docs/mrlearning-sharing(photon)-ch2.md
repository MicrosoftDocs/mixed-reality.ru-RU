---
title: Руководства по многопользовательским возможностям, часть 2. Подготовка Unity к разработке
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031242"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="c1577-105">2. Подготовка Unity к разработке</span><span class="sxs-lookup"><span data-stu-id="c1577-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="c1577-106">Из этого руководства вы узнаете, как подготовить и настроить Unity для разработки приложений, включая импорт Набора средств для смешанной реальности, настройку параметров сборки и подготовку сцены.</span><span class="sxs-lookup"><span data-stu-id="c1577-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="c1577-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="c1577-107">Objectives</span></span>

* <span data-ttu-id="c1577-108">Настройка Unity для разработки приложений</span><span class="sxs-lookup"><span data-stu-id="c1577-108">Configure Unity for application development</span></span>
* <span data-ttu-id="c1577-109">Импорт набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="c1577-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="c1577-110">Подготовка сцены проекта</span><span class="sxs-lookup"><span data-stu-id="c1577-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="c1577-111">Инструкции</span><span class="sxs-lookup"><span data-stu-id="c1577-111">Instructions</span></span>

1. <span data-ttu-id="c1577-112">Скачайте и сохраните Набор средств Unity для смешанной реальности, щелкнув [здесь](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="c1577-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="c1577-113">В Unity откройте меню Assets (Активы) и выберите Import Package (Импорт пакета), а затем щелкните Custom Package (Пользовательский пакет).</span><span class="sxs-lookup"><span data-stu-id="c1577-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="c1577-115">Выберите пакет Unity, который вы скачали по ссылке на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="c1577-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="c1577-116">Когда в Unity откроется всплывающее окно импорта, нажмите кнопку Import (Импорт), чтобы начать импорт МRТК.</span><span class="sxs-lookup"><span data-stu-id="c1577-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="c1577-117">Это может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="c1577-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="c1577-119">Скачанный пакет будет размещен в локальной папке, в которой вы сохранили файл.</span><span class="sxs-lookup"><span data-stu-id="c1577-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="c1577-120">Приведенный выше рисунок не соответствует реальному расположению пакета на вашем компьютере.</span><span class="sxs-lookup"><span data-stu-id="c1577-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="c1577-121">После импорта пакета должно отобразиться окно конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="c1577-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="c1577-122">В противном случае откройте это окно, щелкнув Mixed Reality Toolkit > Utilities > Configure Unity Project (Набор средств для смешанной реальности > Служебные программы > Настроить проект Unity) в меню Unity.</span><span class="sxs-lookup"><span data-stu-id="c1577-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="c1577-123">В окне конфигуратора проектов MRTK разверните раздел Modify Configurations (Изменение конфигураций), снимите флажок Enable MSBuild for Unity (Включить MSBuild для Unity), убедитесь, что настроены остальные параметры, и нажмите кнопку Apply (Применить), чтобы применить эти параметры.</span><span class="sxs-lookup"><span data-stu-id="c1577-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="c1577-125">Так как MSBuild для Unity может поддерживать не все пакеты SDK, которые будут использоваться, с отключением могут быть проблемы.</span><span class="sxs-lookup"><span data-stu-id="c1577-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="c1577-126">Поэтому настоятельно рекомендуется не включать MSBuild для Unity.</span><span class="sxs-lookup"><span data-stu-id="c1577-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="c1577-127">Создайте новую сцену.</span><span class="sxs-lookup"><span data-stu-id="c1577-127">Create a new scene.</span></span> <span data-ttu-id="c1577-128">Это можно сделать, щелкнув меню File (Файл) и выбрав New Scene (Создать сцену).</span><span class="sxs-lookup"><span data-stu-id="c1577-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="c1577-129">Сохраните ее с именем HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="c1577-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="c1577-130">В разделе Mixed Reality Toolkit (Набор средств для смешанной реальности) щелкните Add to Scene (Добавить в сцену) и Configure (Настроить).</span><span class="sxs-lookup"><span data-stu-id="c1577-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="c1577-132">Завершив этот процесс, выберите Набор средств для смешанной реальности (MRTK) в иерархии.</span><span class="sxs-lookup"><span data-stu-id="c1577-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="c1577-133">На панели инспектора измените профиль конфигурации MRTK на DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="c1577-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="c1577-135">Выберите Набор средств для смешанной реальности (MRTK) в иерархии.</span><span class="sxs-lookup"><span data-stu-id="c1577-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="c1577-136">На панели инспектора найдите Mixed Reality Toolkit Script (Скрипт Набора средств для смешанной реальности) и нажмите кнопку Copy & Customize (Скопировать и настроить), как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="c1577-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="c1577-137">Откроется всплывающее меню, в котором нужно выбрать действие Clone (Клонировать).</span><span class="sxs-lookup"><span data-stu-id="c1577-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="c1577-140">Прокрутите вниз и снимите флажок Enable Diagnostics system (Включить систему диагностики), если вам не нужно это окно диагностики.</span><span class="sxs-lookup"><span data-stu-id="c1577-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="c1577-141">Мы рекомендуем держать окно диагностики открытым во время разработки приложения для мониторинга производительности, а затем отключать его в рабочей среде или при демонстрации приложения.</span><span class="sxs-lookup"><span data-stu-id="c1577-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="c1577-143">Откройте окно параметров сборки, нажав сочетание клавиш CTRL+SHIFT+B или выбрав пункт меню File (Файл) > Build Settings (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="c1577-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="c1577-144">Обратите внимание, что программа сейчас настроена для автономной платформы ПК, Mac и Linux.</span><span class="sxs-lookup"><span data-stu-id="c1577-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="c1577-145">При разработке для HoloLens 2 выберите универсальную платформу Windows.</span><span class="sxs-lookup"><span data-stu-id="c1577-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="c1577-146">Выберите этот вариант и щелкните Switch Platform (Сменить платформу).</span><span class="sxs-lookup"><span data-stu-id="c1577-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="c1577-148">Завершив процесс, щелкните флажок Add Open Scenes (Добавить открытые сцены).</span><span class="sxs-lookup"><span data-stu-id="c1577-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="c1577-149">Теперь перейдите на панель Inspector (Инспектор) и убедитесь, что здесь установлен флажок справа от элемента Virtual Reality Supported (Поддержка виртуальной реальности), как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="c1577-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="c1577-150">Также убедитесь, что установлен флажок рядом с элементом scenes/HLSharedProjectMain, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="c1577-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="c1577-152">В разделе Publishing Settings (Параметры публикации) на панели Inspector (Инспектор) прокрутите содержимое вниз до элемента Capabilities (Возможности) и убедитесь, что установлены следующие флажки.</span><span class="sxs-lookup"><span data-stu-id="c1577-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="c1577-154">Импортируйте указанные здесь пользовательские пакеты.</span><span class="sxs-lookup"><span data-stu-id="c1577-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="c1577-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (версия 2.1.1);</span><span class="sxs-lookup"><span data-stu-id="c1577-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * <span data-ttu-id="c1577-156">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="c1577-156">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)</span></span>
    * <span data-ttu-id="c1577-157">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="c1577-157">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)</span></span>
    * <span data-ttu-id="c1577-158">[MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="c1577-158">[MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)</span></span>

    >[!TIP]
    ><span data-ttu-id="c1577-159">Остальные процессы настройки проекта Unity для Пространственных привязок Azure вы можете найти в руководстве по [началу работы с Пространственными привязками Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) из серии, посвященной [Пространственным привязкам Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1).</span><span class="sxs-lookup"><span data-stu-id="c1577-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="c1577-160">На панели Project (Проект) откройте папку Prefabs (Заготовки).</span><span class="sxs-lookup"><span data-stu-id="c1577-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="c1577-161">На следующих шагах вы добавите в сцену несколько заготовок.</span><span class="sxs-lookup"><span data-stu-id="c1577-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="c1577-162">В папке Prefabs щелкните заготовку Debug Window (Окно отладки) и перетащите ее в иерархию.</span><span class="sxs-lookup"><span data-stu-id="c1577-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="c1577-163">Завершив этот процесс, сохраните проект, выбрав пункты меню File > Save (Файл > Сохранить) или нажав сочетание клавиш Ctrl+S.</span><span class="sxs-lookup"><span data-stu-id="c1577-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="c1577-165">Возможно, при щелчке по заготовке появится всплывающее окно с запросом о компоненте TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="c1577-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="c1577-166">Щелкните кнопку импорта TMP Essentials, так как это обязательный компонент.</span><span class="sxs-lookup"><span data-stu-id="c1577-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="c1577-167">Если появится это всплывающее окно, вам лучше удалить заготовку из иерархии и повторно перетащить ее в эту иерархию, чтобы избежать потенциальных проблем с текстами.</span><span class="sxs-lookup"><span data-stu-id="c1577-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="c1577-169">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="c1577-169">Congratulations</span></span>

<span data-ttu-id="c1577-170">Теперь проект Unity готов к работе с Photon.</span><span class="sxs-lookup"><span data-stu-id="c1577-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="c1577-171">В следующих руководствах мы будем дальше развивать эту сцену и проект Unity в целом, чтобы создать полноценное взаимодействие для совместного использования.</span><span class="sxs-lookup"><span data-stu-id="c1577-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="c1577-172">[Следующее руководство: 3. Подключение нескольких пользователей](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="c1577-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
