<span data-ttu-id="c9579-101">**Подготовка к работе, для разработки Unity**</span><span class="sxs-lookup"><span data-stu-id="c9579-101">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="c9579-102">На этом занятии будет рассказано Подготовка и настройка Unity для разработки приложений, включая Импорт смешанной реальности Toolkit, Настройка параметров сборки и подготовка наших сцены.</span><span class="sxs-lookup"><span data-stu-id="c9579-102">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="c9579-103">Цели:</span><span class="sxs-lookup"><span data-stu-id="c9579-103">Objectives:</span></span>

- <span data-ttu-id="c9579-104">Настройка Unity для разработки приложений</span><span class="sxs-lookup"><span data-stu-id="c9579-104">Configure Unity for app development</span></span>

- <span data-ttu-id="c9579-105">Импорт набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="c9579-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="c9579-106">Подготовка проекта сцены</span><span class="sxs-lookup"><span data-stu-id="c9579-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="c9579-107">Инструкция</span><span class="sxs-lookup"><span data-stu-id="c9579-107">Instructions</span></span>

1. <span data-ttu-id="c9579-108">Скачайте и сохраните пакет unity смешанной реальности Toolkit, щелкнув [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="c9579-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="c9579-109">В Unity выберите в меню "средства" и выберите «Импорт пакета», а затем щелкните «Custom Package».</span><span class="sxs-lookup"><span data-stu-id="c9579-109">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="c9579-111">Выберите пакет Unity, который вы загрузили по ссылке, указанный на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="c9579-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="c9579-112">После импорта появится всплывающее окно в Unity, нажмите кнопку «Импорт», чтобы начать импорт.</span><span class="sxs-lookup"><span data-stu-id="c9579-112">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="c9579-113">Импорт MRTK может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="c9579-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="c9579-115">Примечание. Скачанный пакет будет в локальной папке, где вы сохранили файл.</span><span class="sxs-lookup"><span data-stu-id="c9579-115">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="c9579-116">На рисунке выше не представляют, где вы найдете пакета.</span><span class="sxs-lookup"><span data-stu-id="c9579-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="c9579-117">Создание новой сцены (это можно сделать, щелкнув «файл» и выбрав «Создать сцену»).</span><span class="sxs-lookup"><span data-stu-id="c9579-117">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="c9579-118">Сохранить сцену как «HLSharedProjectMain.»</span><span class="sxs-lookup"><span data-stu-id="c9579-118">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="c9579-119">Примечание: может появиться всплывающее окно, похожее на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="c9579-119">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="c9579-120">Сейчас просто нажмите кнопку «Нет».</span><span class="sxs-lookup"><span data-stu-id="c9579-120">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="c9579-122">В разделе «Смешанной реальности Toolkit» щелкните «Добавить сцену и настройка».</span><span class="sxs-lookup"><span data-stu-id="c9579-122">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="c9579-124">После ее завершения, новый файл конфигурации будет отображаться, предоставляя выбор для его настройки.</span><span class="sxs-lookup"><span data-stu-id="c9579-124">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="c9579-125">Нажмите кнопку «Копировать и настройка».</span><span class="sxs-lookup"><span data-stu-id="c9579-125">Click "copy and customize."</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="c9579-129">Прокрутите вниз и снимите флажок «Включить систему диагностики» Если вы хотите скрыть окно диагностики.</span><span class="sxs-lookup"><span data-stu-id="c9579-129">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="c9579-130">Рекомендуется оставить окно диагностики включена во время разработки приложения для наблюдения за производительностью и ее отключение во время демонстрации рабочей среды или приложения.</span><span class="sxs-lookup"><span data-stu-id="c9579-130">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="c9579-132">Открытие параметров сборки, нажав клавиши control + shift + B или перейдите к файлу > Параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="c9579-132">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="c9579-133">Обратите внимание, что в настоящее время программа указана в разделе «отдельно ПК, Mac и Linux» платформы.</span><span class="sxs-lookup"><span data-stu-id="c9579-133">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="c9579-134">Для разработки HoloLens 2 задайте платформы, чтобы быть «Универсальной платформы Windows».</span><span class="sxs-lookup"><span data-stu-id="c9579-134">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="c9579-135">Выберите его и нажмите кнопку «коммутатор платформы».</span><span class="sxs-lookup"><span data-stu-id="c9579-135">Select it and click "switch platform."</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="c9579-137">После завершения щелкните поле с текстом «добавить откройте сцены».</span><span class="sxs-lookup"><span data-stu-id="c9579-137">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="c9579-138">Теперь перейдите к панели инспектора и убедитесь, что флажок справа от «поддерживается виртуальной реальности» (как показано на рисунке ниже) установлен.</span><span class="sxs-lookup"><span data-stu-id="c9579-138">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="c9579-139">Также убедитесь, что флажок рядом с «сцены/HLSharedProjectMain» также проверяется, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="c9579-139">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="c9579-141">В разделе «Параметры публикации» статьи инспектор панели прокрутите список вниз до «Возможности» и убедитесь, что отмечены флажки:</span><span class="sxs-lookup"><span data-stu-id="c9579-141">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="c9579-143">Импортируйте пользовательский пакет называется «SharingAssetCollection», который можно скачать [здесь.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="c9579-143">Import the custom package called "SharingAssetCollection" which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="c9579-144">Теперь в панели «проект» перейдите к папке «prefabs» так, как в следующих шагах будет реализовано несколько prefabs на сцене.</span><span class="sxs-lookup"><span data-stu-id="c9579-144">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="c9579-145">В папке «prefabs» щелкните и перетащите готового блока, «DebugWindow» в иерархии.</span><span class="sxs-lookup"><span data-stu-id="c9579-145">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="c9579-146">По завершении сохраните проект (щелкните файл, а затем сохраните, или нажмите клавиши control + S)</span><span class="sxs-lookup"><span data-stu-id="c9579-146">Once finished, save the project (click file, then save, or press control+S)</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="c9579-148">Примечание. Вы можете заметить всплывающее окно отображается при выборе готового блока, запрашивающее о TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="c9579-148">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="c9579-149">Нажмите кнопку «Импорт TMP Essentials», как они потребуются.</span><span class="sxs-lookup"><span data-stu-id="c9579-149">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="c9579-150">Если это всплывающее окно отображается, может потребоваться удалить взята из иерархии и повторно перетащить его в иерархии, чтобы избежать потенциальных ошибок, относящихся к тексту.</span><span class="sxs-lookup"><span data-stu-id="c9579-150">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="c9579-152">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="c9579-152">Congratulations</span></span>

<span data-ttu-id="c9579-153">Проект Unity теперь готов для Photon!</span><span class="sxs-lookup"><span data-stu-id="c9579-153">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="c9579-154">На следующих занятиях мы выполним сборку от этой сценой и наш проект Unity к полной общей функциональности.</span><span class="sxs-lookup"><span data-stu-id="c9579-154">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="c9579-155">[Следующий урок. Sharing(Photon) занятие 3](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="c9579-155">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>

