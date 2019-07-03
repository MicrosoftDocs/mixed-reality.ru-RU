# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="0a604-101">Подготовка к работе, для разработки Unity</span><span class="sxs-lookup"><span data-stu-id="0a604-101">Getting Unity ready for development</span></span> 

<span data-ttu-id="0a604-102">В этом руководстве мы узнаем, как подготовка и настройка для разработки приложений, включая Импорт смешанной реальности Toolkit, Настройка параметров сборки и подготовка наших сцене Unity.</span><span class="sxs-lookup"><span data-stu-id="0a604-102">In this tutorial, we learn how to prepare and configure Unity for applicaiton development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="0a604-103">Цели:</span><span class="sxs-lookup"><span data-stu-id="0a604-103">Objectives:</span></span>

- <span data-ttu-id="0a604-104">Настройка Unity для разработки приложений</span><span class="sxs-lookup"><span data-stu-id="0a604-104">Configure Unity for applicaiton development</span></span>

- <span data-ttu-id="0a604-105">Импорт набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="0a604-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="0a604-106">Подготовка проекта сцены</span><span class="sxs-lookup"><span data-stu-id="0a604-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="0a604-107">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0a604-107">Instructions</span></span>

1. <span data-ttu-id="0a604-108">Скачайте и сохраните пакет unity смешанной реальности Toolkit, щелкнув [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="0a604-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="0a604-109">В Unity выберите в меню "средства" и выберите Импорт пакета, а затем щелкните пользовательского пакета.</span><span class="sxs-lookup"><span data-stu-id="0a604-109">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="0a604-111">Выберите пакет Unity, который вы загрузили по ссылке, указанный на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="0a604-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="0a604-112">После импорта появится всплывающее окно в Unity, нажмите кнопку «Импорт», чтобы начать импорт.</span><span class="sxs-lookup"><span data-stu-id="0a604-112">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="0a604-113">Импорт MRTK может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="0a604-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="0a604-115">Примечание. Скачанный пакет находится в локальной папке, где вы сохранили файл.</span><span class="sxs-lookup"><span data-stu-id="0a604-115">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="0a604-116">На рисунке выше не представляют, где вы найдете пакета.</span><span class="sxs-lookup"><span data-stu-id="0a604-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="0a604-117">Создание новой сцены.</span><span class="sxs-lookup"><span data-stu-id="0a604-117">Create a new scene.</span></span> <span data-ttu-id="0a604-118">В этой можно сделать, щелкнув файл и выбрав новую сцену»).</span><span class="sxs-lookup"><span data-stu-id="0a604-118">Tthis can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="0a604-119">Сохраните сцену как HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="0a604-119">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="0a604-120">Примечание: может появиться всплывающее окно, похожее на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="0a604-120">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="0a604-121">Сейчас, нажмите кнопку "Нет".</span><span class="sxs-lookup"><span data-stu-id="0a604-121">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="0a604-123">В смешанной реальности Toolkit щелкните Добавить, чтобы сцены и настройка.</span><span class="sxs-lookup"><span data-stu-id="0a604-123">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="0a604-125">После ее завершения, конфигурации появится новый файл, позволяющий настроить профиль.</span><span class="sxs-lookup"><span data-stu-id="0a604-125">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="0a604-126">Щелкните "Копировать" и настройки.</span><span class="sxs-lookup"><span data-stu-id="0a604-126">Click Copy and Customize.</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="0a604-130">Прокрутите вниз и снимите флажок Включить Siagnostics системы, если вы хотите скрыть окно диагностики.</span><span class="sxs-lookup"><span data-stu-id="0a604-130">Scroll down and uncheck Enable Siagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="0a604-131">Рекомендуется оставить окно диагностики включена во время разработки приложения для наблюдения за производительностью и ее отключение во время демонстрации рабочей среды или приложения.</span><span class="sxs-lookup"><span data-stu-id="0a604-131">We recommend keeping the diagnostics window enabled during applicaiton development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="0a604-133">Откройте параметры построения, нажав клавиши control + shift + B или перейдите к файлу "->" Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="0a604-133">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="0a604-134">Обратите внимание, что в настоящее время программа указана в разделе платформы автономных ПК, Mac и Linux.</span><span class="sxs-lookup"><span data-stu-id="0a604-134">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="0a604-135">Для разработки HoloLens 2 значение платформы, чтобы быть универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="0a604-135">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="0a604-136">Выберите его и нажмите кнопку Изменить платформу.</span><span class="sxs-lookup"><span data-stu-id="0a604-136">Select it and click Switch Platform.</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="0a604-138">После завершения щелкните поле с текстом добавить откройте сцены.</span><span class="sxs-lookup"><span data-stu-id="0a604-138">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="0a604-139">Теперь перейдите к панели инспектора и убедитесь, что установлен флажок справа от виртуальной реальности поддерживается (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="0a604-139">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="0a604-140">Также убедитесь, что флажок рядом с кадром/HLSharedProjectMain также проверяется, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="0a604-140">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="0a604-142">В разделе "Параметры публикации", на панели Инспектора прокрутите вниз до возможности и убедитесь, что отмечены флажки:</span><span class="sxs-lookup"><span data-stu-id="0a604-142">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="0a604-144">Импорт настраиваемого пакета вызывается SharingAssetCollection, который можно скачать [здесь.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="0a604-144">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="0a604-145">На панели «проект» перейдите в папку Prefabs.</span><span class="sxs-lookup"><span data-stu-id="0a604-145">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="0a604-146">В следующих шагах мы реализуем несколько prefabs в сцену.</span><span class="sxs-lookup"><span data-stu-id="0a604-146">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="0a604-147">В папку Prefabs щелкните и перетащите готового блока, DebugWindow в иерархии.</span><span class="sxs-lookup"><span data-stu-id="0a604-147">In the Prefabs folder, click and drag the prefab, DebugWindow into the hierarchy.</span></span> <span data-ttu-id="0a604-148">После завершения сохраните проект, clckin файл, а затем сохранить или нажмите клавиши CTRL + + S.</span><span class="sxs-lookup"><span data-stu-id="0a604-148">Once finished, save the project by clckin File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="0a604-150">Примечание. Вы можете заметить всплывающее окно отображается при выборе готового блока, запрашивающее о TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="0a604-150">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="0a604-151">Щелкните Essentials TMP импорта, когда они нужны.</span><span class="sxs-lookup"><span data-stu-id="0a604-151">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="0a604-152">Если это всплывающее окно отображается, может потребоваться удалить взята из иерархии и повторно перетащить его в иерархии, чтобы избежать потенциальных ошибок, относящихся к тексту.</span><span class="sxs-lookup"><span data-stu-id="0a604-152">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="0a604-154">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="0a604-154">Congratulations</span></span>

<span data-ttu-id="0a604-155">Проект Unity теперь готов для Photon.</span><span class="sxs-lookup"><span data-stu-id="0a604-155">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="0a604-156">В ближайшие учебных курсах мы выполним сборку от этой сценой и наш проект Unity к полной общей функциональности.</span><span class="sxs-lookup"><span data-stu-id="0a604-156">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="0a604-157">[Следующему руководству: Подключение нескольких пользователей](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="0a604-157">[Next tutorial: Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

