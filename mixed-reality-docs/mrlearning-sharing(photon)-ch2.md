---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 957813d24de95aad52c26b4bd0f0996a60d01358
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327969"
---
# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="a87a6-104">**Подготовка к работе, для разработки Unity**</span><span class="sxs-lookup"><span data-stu-id="a87a6-104">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="a87a6-105">На этом занятии будет рассказано Подготовка и настройка Unity для разработки приложений, включая Импорт смешанной реальности Toolkit, Настройка параметров сборки и подготовка наших сцены.</span><span class="sxs-lookup"><span data-stu-id="a87a6-105">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="a87a6-106">Цели:</span><span class="sxs-lookup"><span data-stu-id="a87a6-106">Objectives:</span></span>

- <span data-ttu-id="a87a6-107">Настройка Unity для разработки приложений</span><span class="sxs-lookup"><span data-stu-id="a87a6-107">Configure Unity for app development</span></span>

- <span data-ttu-id="a87a6-108">Импорт набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="a87a6-108">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="a87a6-109">Подготовка проекта сцены</span><span class="sxs-lookup"><span data-stu-id="a87a6-109">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="a87a6-110">Инструкция</span><span class="sxs-lookup"><span data-stu-id="a87a6-110">Instructions</span></span>

1. <span data-ttu-id="a87a6-111">Скачайте и сохраните пакет unity смешанной реальности Toolkit, щелкнув [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="a87a6-111">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span></span>
2. <span data-ttu-id="a87a6-112">В Unity выберите в меню "средства" и выберите «Импорт пакета», а затем щелкните «Custom Package».</span><span class="sxs-lookup"><span data-stu-id="a87a6-112">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="a87a6-114">Выберите пакет Unity, который вы загрузили по ссылке, указанный на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="a87a6-114">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="a87a6-115">После импорта появится всплывающее окно в Unity, нажмите кнопку «Импорт», чтобы начать импорт.</span><span class="sxs-lookup"><span data-stu-id="a87a6-115">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="a87a6-116">Импорт MRTK может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="a87a6-116">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="a87a6-118">Примечание. Скачанный пакет будет в локальной папке, где вы сохранили файл.</span><span class="sxs-lookup"><span data-stu-id="a87a6-118">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="a87a6-119">На рисунке выше не представляют, где вы найдете пакета.</span><span class="sxs-lookup"><span data-stu-id="a87a6-119">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="a87a6-120">Создание новой сцены (это можно сделать, щелкнув «файл» и выбрав «Создать сцену»).</span><span class="sxs-lookup"><span data-stu-id="a87a6-120">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="a87a6-121">Сохранить сцену как «HLSharedProjectMain.»</span><span class="sxs-lookup"><span data-stu-id="a87a6-121">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="a87a6-122">Примечание: может появиться всплывающее окно, похожее на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="a87a6-122">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="a87a6-123">Сейчас просто нажмите кнопку «Нет».</span><span class="sxs-lookup"><span data-stu-id="a87a6-123">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="a87a6-125">В разделе «Смешанной реальности Toolkit» щелкните «Добавить сцену и настройка».</span><span class="sxs-lookup"><span data-stu-id="a87a6-125">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="a87a6-127">После ее завершения, новый файл конфигурации будет отображаться, предоставляя выбор для его настройки.</span><span class="sxs-lookup"><span data-stu-id="a87a6-127">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="a87a6-128">Нажмите кнопку «Копировать и настройка».</span><span class="sxs-lookup"><span data-stu-id="a87a6-128">Click "copy and customize."</span></span>

![Module3Chapter2step6im](images/module3chapter2step6im.PNG)

7. <span data-ttu-id="a87a6-130">Прокрутите вниз и снимите флажок «Включить систему диагностики» Если вы хотите скрыть окно диагностики.</span><span class="sxs-lookup"><span data-stu-id="a87a6-130">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="a87a6-131">Рекомендуется оставить окно диагностики включена во время разработки приложения для наблюдения за производительностью и ее отключение во время демонстрации рабочей среды или приложения.</span><span class="sxs-lookup"><span data-stu-id="a87a6-131">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span>

![Module3Chapter2step7im](images/module3chapter2step7im.PNG)

8. <span data-ttu-id="a87a6-133">Открытие параметров сборки, нажав клавиши control + shift + B или перейдите к файлу > Параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="a87a6-133">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="a87a6-134">Обратите внимание, что в настоящее время программа указана в разделе «отдельно ПК, Mac и Linux» платформы.</span><span class="sxs-lookup"><span data-stu-id="a87a6-134">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="a87a6-135">Для разработки HoloLens 2 задайте платформы, чтобы быть «Универсальной платформы Windows».</span><span class="sxs-lookup"><span data-stu-id="a87a6-135">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="a87a6-136">Выберите его и нажмите кнопку «коммутатор платформы».</span><span class="sxs-lookup"><span data-stu-id="a87a6-136">Select it and click "switch platform."</span></span>

   ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

   9. <span data-ttu-id="a87a6-138">После завершения щелкните поле с текстом «добавить откройте сцены».</span><span class="sxs-lookup"><span data-stu-id="a87a6-138">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="a87a6-139">Теперь перейдите к панели инспектора и убедитесь, что флажок справа от «поддерживается виртуальной реальности» (как показано на рисунке ниже) установлен.</span><span class="sxs-lookup"><span data-stu-id="a87a6-139">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="a87a6-140">Также убедитесь, что флажок рядом с «сцены/HLSharedProjectMain» также проверяется, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="a87a6-140">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>

   ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

   10. <span data-ttu-id="a87a6-142">В разделе «Параметры публикации» статьи инспектор панели прокрутите список вниз до «Возможности» и убедитесь, что отмечены флажки:</span><span class="sxs-lookup"><span data-stu-id="a87a6-142">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>
    - <span data-ttu-id="a87a6-143">Интернет-клиент</span><span class="sxs-lookup"><span data-stu-id="a87a6-143">internet client</span></span>
       
       - <span data-ttu-id="a87a6-144">клиент-сервер Интернета</span><span class="sxs-lookup"><span data-stu-id="a87a6-144">internet client server</span></span>
       
       - <span data-ttu-id="a87a6-145">клиент-сервер частной сети</span><span class="sxs-lookup"><span data-stu-id="a87a6-145">private network client server</span></span>
   
       - <span data-ttu-id="a87a6-146">камера/веб-камеры</span><span class="sxs-lookup"><span data-stu-id="a87a6-146">camera/webcam</span></span>

       - <span data-ttu-id="a87a6-147">микрофон</span><span class="sxs-lookup"><span data-stu-id="a87a6-147">microphone</span></span>
   
   11. <span data-ttu-id="a87a6-148">Импортируйте пользовательский пакет, называемый занятие «2», который можно скачать здесь.</span><span class="sxs-lookup"><span data-stu-id="a87a6-148">Import the custom package called "Lesson2" which can be downloaded here.</span></span> <span data-ttu-id="a87a6-149">TODO: Укажите ссылку на пакет ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a87a6-149">TODO: Provide link to asset pack.</span></span>
   
   ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)
   
   12. <span data-ttu-id="a87a6-151">Теперь в панели «проект» перейдите к папке «prefabs» так, как в следующих шагах будет реализовано несколько prefabs на сцене.</span><span class="sxs-lookup"><span data-stu-id="a87a6-151">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="a87a6-152">В папке «prefabs» щелкните и перетащите готового блока, «DebugWindow» в иерархии.</span><span class="sxs-lookup"><span data-stu-id="a87a6-152">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="a87a6-153">По завершении сохраните проект (щелкните файл, а затем сохраните, или нажмите клавиши control + S)</span><span class="sxs-lookup"><span data-stu-id="a87a6-153">Once finished, save the project (click file, then save, or press control+S)</span></span>
   
       ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)
   
   > <span data-ttu-id="a87a6-155">Примечание. Вы можете заметить всплывающее окно отображается при выборе готового блока, запрашивающее о TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="a87a6-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="a87a6-156">Нажмите кнопку «Импорт TMP Essentials», как они потребуются.</span><span class="sxs-lookup"><span data-stu-id="a87a6-156">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="a87a6-157">Если это всплывающее окно отображается, может потребоваться удалить взята из иерархии и повторно перетащить его в иерархии, чтобы избежать потенциальных ошибок, относящихся к тексту.</span><span class="sxs-lookup"><span data-stu-id="a87a6-157">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="a87a6-159">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="a87a6-159">Congratulations</span></span>

<span data-ttu-id="a87a6-160">Проект Unity теперь готов для Photon!</span><span class="sxs-lookup"><span data-stu-id="a87a6-160">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="a87a6-161">На следующих занятиях мы выполним сборку от этой сценой и наш проект Unity к полной общей функциональности.</span><span class="sxs-lookup"><span data-stu-id="a87a6-161">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="a87a6-162">[Следующий урок. Sharing(Photon) занятие 3](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="a87a6-162">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>

