---
title: Учебники по возможностям для нескольких пользователей — 2. Подготовка Unity к разработке
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 9d42811157db108baad51eab3f367a06a11b7f7b
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701981"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="2b7d9-105">2. Подготовка Unity к разработке</span><span class="sxs-lookup"><span data-stu-id="2b7d9-105">2. Getting Unity ready for development</span></span> 


<span data-ttu-id="2b7d9-106">В этом руководстве мы научитесь подготавливать и настраивать Unity для разработки приложений, включая импорт набора средств для смешанной реальности, настройку параметров сборки и подготовку сцены.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-106">In this tutorial, we learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="2b7d9-107">Цели</span><span class="sxs-lookup"><span data-stu-id="2b7d9-107">Objectives</span></span>

- <span data-ttu-id="2b7d9-108">Настройка Unity для разработки приложений</span><span class="sxs-lookup"><span data-stu-id="2b7d9-108">Configure Unity for application development</span></span>

- <span data-ttu-id="2b7d9-109">Импорт набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="2b7d9-109">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="2b7d9-110">Подготовка сцены проекта</span><span class="sxs-lookup"><span data-stu-id="2b7d9-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="2b7d9-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2b7d9-111">Instructions</span></span>

1. <span data-ttu-id="2b7d9-112">Скачайте и сохраните пакет Unity для набора средств Mixed Reality, щелкнув [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="2b7d9-112">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>

2. <span data-ttu-id="2b7d9-113">В Unity щелкните меню активы и выберите Импорт пакета, а затем щелкните пользовательский пакет.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-113">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="2b7d9-115">Выберите пакет Unity, который вы только что скачали, по ссылке, предоставленной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="2b7d9-116">После появления всплывающего окна Импорт в Unity нажмите кнопку Импорт, чтобы начать импорт.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-116">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="2b7d9-117">Импорт МРТК может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-117">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="2b7d9-119">Примечание. Загруженный пакет находится в локальной папке, в которую был сохранен файл.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-119">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="2b7d9-120">На приведенном выше рисунке не отображать, где находится пакет.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="2b7d9-121">Создайте новую сцену.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-121">Create a new scene.</span></span> <span data-ttu-id="2b7d9-122">Это можно сделать, щелкнув файл и выбрав создать сцену.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-122">This can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="2b7d9-123">Сохраните сцену как Хлшаредпрожектмаин.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-123">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="2b7d9-124">Примечание. Вы можете получить всплывающее окно, похожее на изображение ниже.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-124">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="2b7d9-125">Пока нажмите кнопку нет.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-125">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="2b7d9-127">В разделе набор средств для смешанной реальности щелкните Добавить в сцену и настроить.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="2b7d9-129">После завершения работы появится новый файл конфигурации, в котором можно настроить профиль.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="2b7d9-130">Щелкните Копировать и настроить.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-130">Click Copy and Customize.</span></span>

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="2b7d9-134">Прокрутите вниз и снимите флажок Включить систему диагностики, если необходимо скрыть окно Диагностика.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-134">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="2b7d9-135">Рекомендуется поддерживать Окно диагностики во время разработки приложения, чтобы отслеживать производительность и отключать его во время демонстрации рабочей среды или приложения.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-135">We recommend keeping the diagnostics window enabled during application development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="2b7d9-137">Откройте параметры сборки, нажав клавиши CTRL + SHIFT + B или перейдя в файловые > параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-137">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="2b7d9-138">Обратите внимание, что программа в настоящее время задается в автономной платформе PC, Mac и Linux.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-138">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="2b7d9-139">Для разработки HoloLens 2 Задайте универсальная платформа Windows платформы.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-139">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="2b7d9-140">Выберите его и щелкните Сменить платформу.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-140">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="2b7d9-142">По завершении установите флажок Добавить открытые сцены.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-142">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="2b7d9-143">Теперь перейдите на панель инспектора и убедитесь, что установлен флажок справа от параметра Virtual Reality Supported (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="2b7d9-143">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="2b7d9-144">Также убедитесь, что флажок рядом с параметром сцены и Хлшаредпрожектмаин также установлен, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-144">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="2b7d9-146">В разделе "Параметры публикации" на панели инспектора прокрутите вниз до пункта "возможности" и убедитесь, что следующие флажки помечены:</span><span class="sxs-lookup"><span data-stu-id="2b7d9-146">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="2b7d9-148">Импортируйте пользовательский пакет с именем Шарингассетколлектион, который можно скачать [здесь.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span><span class="sxs-lookup"><span data-stu-id="2b7d9-148">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="2b7d9-150">На панели проект перейдите в папку Prefabs.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-150">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="2b7d9-151">В следующих шагах вы реализуете несколько Prefabs в сцене.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-151">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="2b7d9-152">В папке Prefabs щелкните и перетащите окно prefab, отладку в иерархию.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-152">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="2b7d9-153">По завершении сохраните проект, щелкнув файл, а затем сохранить или нажмите клавиши CTRL + S.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-153">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="2b7d9-155">Примечание. Вы можете заметить, что всплывающее окно отображается, когда вы щелкнули prefab, и запрашивается о параметрах TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="2b7d9-156">Щелкните Импортировать TMP Essentials по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-156">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="2b7d9-157">При появлении этого всплывающего окна может потребоваться удалить prefab из иерархии и повторно перетащить его в иерархию, чтобы избежать потенциальных ошибок, связанных с текстом.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-157">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="2b7d9-159">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="2b7d9-159">Congratulations</span></span>

<span data-ttu-id="2b7d9-160">Теперь проект Unity готов для Photon.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-160">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="2b7d9-161">В следующих учебных курсах мы создадим эту сцену и наш проект Unity в полном объеме для совместной работы.</span><span class="sxs-lookup"><span data-stu-id="2b7d9-161">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="2b7d9-162">[Следующий учебник: 3. Подключение нескольких пользователей](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="2b7d9-162">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

