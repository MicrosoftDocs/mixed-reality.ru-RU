---
title: Модуль ASA обучения MR Azure пространственных привязка в HoloLens 2
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326868"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="4825a-104">Photon (исправить мне, если я не так)</span><span class="sxs-lookup"><span data-stu-id="4825a-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="4825a-105">На этом занятии</span><span class="sxs-lookup"><span data-stu-id="4825a-105">In this lesson,</span></span> 

<span data-ttu-id="4825a-106">Цели:</span><span class="sxs-lookup"><span data-stu-id="4825a-106">Objectives:</span></span>

* <span data-ttu-id="4825a-107">Узнайте, как ___</span><span class="sxs-lookup"><span data-stu-id="4825a-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="4825a-108">Узнайте, как ___</span><span class="sxs-lookup"><span data-stu-id="4825a-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="4825a-109">Инструкция</span><span class="sxs-lookup"><span data-stu-id="4825a-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="4825a-110">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="4825a-110">Setting Up Photon</span></span>

1. <span data-ttu-id="4825a-111">Настройка [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) учетной записи.</span><span class="sxs-lookup"><span data-stu-id="4825a-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="4825a-112">Таким образом будет состоять из ввода ваш адрес электронной почты и проход через несколько шагов проверки.</span><span class="sxs-lookup"><span data-stu-id="4825a-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="4825a-114">Как только вы зарегистрированы, щелкните пакеты SDK.</span><span class="sxs-lookup"><span data-stu-id="4825a-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="4825a-115">После перехода на эту страницу, щелкните «сервер» и убедиться, он говорит: «резидентной.»</span><span class="sxs-lookup"><span data-stu-id="4825a-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="4825a-116">Прокрутите вниз и выберите команду «сервер», как показано на втором рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="4825a-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="4825a-119">Приведет к отображается с меткой, для текстового поля «read me».</span><span class="sxs-lookup"><span data-stu-id="4825a-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="4825a-120">Продолжим и его чтение.</span><span class="sxs-lookup"><span data-stu-id="4825a-120">Go ahead and read it.</span></span> <span data-ttu-id="4825a-121">По завершении щелкните ссылку рядом с «downloadSDK», чтобы загрузить его.</span><span class="sxs-lookup"><span data-stu-id="4825a-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="4825a-123">Дважды щелкните папку, после завершения загрузки.</span><span class="sxs-lookup"><span data-stu-id="4825a-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="4825a-124">Открыв проводнике раскрытия в папку пакета SDK, скопируйте в папку пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="4825a-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="4825a-125">Следующим шагом будет перейти на диске C: windows и создайте новую папку с именем «сервер».</span><span class="sxs-lookup"><span data-stu-id="4825a-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="4825a-127">Теперь откройте папку и вставьте в папку пакета SDK, скопированный ранее.</span><span class="sxs-lookup"><span data-stu-id="4825a-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="4825a-129">После завершения, откройте папку пакета SDK и перейдите в раздел «Развертывание» выберите «bin_Win64», затем дважды щелкните «Фотон control».</span><span class="sxs-lookup"><span data-stu-id="4825a-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="4825a-131">Примечание. Если у вас возникнут вопросы по IP-адрес или другие аналогичные вопросы, можно найти большую часть информации в панели инструментов (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="4825a-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="4825a-133">Теперь, когда сервер настраивается и инициированный, вернитесь на веб-сайт Photon и щелкнуть значок «профиль» (boxed на рисунке ниже) и выберите «вашего приложения.»</span><span class="sxs-lookup"><span data-stu-id="4825a-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="4825a-135">Создайте идентификатор приложения, нажав кнопку «Создать новое приложение».</span><span class="sxs-lookup"><span data-stu-id="4825a-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="4825a-137">Выберите команду «Запустить Photon» в раскрывающемся меню в разделе «photon type».</span><span class="sxs-lookup"><span data-stu-id="4825a-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="4825a-138">Затем присвойте ему имя, (то, что должен был бы запоминать).</span><span class="sxs-lookup"><span data-stu-id="4825a-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="4825a-139">В этом примере мы назвали ее «HoloLensPhotonProject.»</span><span class="sxs-lookup"><span data-stu-id="4825a-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="4825a-140">По завершении нажмите кнопку «Создать».</span><span class="sxs-lookup"><span data-stu-id="4825a-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="4825a-142">После этого вернуться на страницу приложения, и вы увидите нечто, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="4825a-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="4825a-143">Щелкните идентификатор приложения и скопируйте его.</span><span class="sxs-lookup"><span data-stu-id="4825a-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="4825a-144">Вставить находится где-нибудь, которые можно легко получить.</span><span class="sxs-lookup"><span data-stu-id="4825a-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="4825a-146">Создайте новый проект unity.</span><span class="sxs-lookup"><span data-stu-id="4825a-146">Create a new unity project.</span></span> <span data-ttu-id="4825a-147">Откройте центр Unity и выберите команду «new».</span><span class="sxs-lookup"><span data-stu-id="4825a-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="4825a-148">Назовите его «HLSharingProject.»</span><span class="sxs-lookup"><span data-stu-id="4825a-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="4825a-149">Нажмите кнопку Создать.</span><span class="sxs-lookup"><span data-stu-id="4825a-149">Then click create.</span></span> 

   > <span data-ttu-id="4825a-150">Примечание. Это может занять до 2 минут, чтобы загрузить, в зависимости от быстродействия компьютера.</span><span class="sxs-lookup"><span data-stu-id="4825a-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="4825a-152">Примечание: выберите место для сохранения проекта на своем компьютере, изменив параметр «расположение».</span><span class="sxs-lookup"><span data-stu-id="4825a-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="4825a-153">Сохраните его в место будет запомнить и иметь быстрый доступ к.</span><span class="sxs-lookup"><span data-stu-id="4825a-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="4825a-154">После загрузки проекта, щелкните «ресурсы хранилища».</span><span class="sxs-lookup"><span data-stu-id="4825a-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="4825a-155">Затем в поле поиска, показано на рисунке ниже, введите «СОВМЕСТНОЙ» и выберите «Бесплатная СОВМЕСТНОЙ 2 Photon» ресурс.</span><span class="sxs-lookup"><span data-stu-id="4825a-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="4825a-157">Загрузите и импортируйте!</span><span class="sxs-lookup"><span data-stu-id="4825a-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="4825a-159">**Настройка проекта Unity**</span><span class="sxs-lookup"><span data-stu-id="4825a-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="4825a-160">Загрузите новые средства, необходимые для настройки Photon в Unity, нажав кнопку [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="4825a-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="4825a-161">В Unity щелкните в меню "средства" и выберите «Импорт ресурсов», а затем щелкните «пользовательские ресурсы».</span><span class="sxs-lookup"><span data-stu-id="4825a-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="4825a-163">Выберите пакет Unity, который вы загрузили по ссылке, указанный на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="4825a-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="4825a-164">Как только «импорт» появится в Unity, щелкните его.</span><span class="sxs-lookup"><span data-stu-id="4825a-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="4825a-166">Примечание: везде, где загруженный пакет будет где его найти.</span><span class="sxs-lookup"><span data-stu-id="4825a-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="4825a-167">На рисунке выше не представляют, где вы найдете пакета.</span><span class="sxs-lookup"><span data-stu-id="4825a-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="4825a-168">Создание новой сцены (это может быть реализована с помощью элемента управления / command + N или щелкнув «file» и выбрав команду «Создать сцену.»).</span><span class="sxs-lookup"><span data-stu-id="4825a-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="4825a-169">Сохранить сцену как «HLSharedProjectMain.»</span><span class="sxs-lookup"><span data-stu-id="4825a-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="4825a-170">Примечание: может появиться всплывающее окно, похожее на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="4825a-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="4825a-171">Сейчас просто нажмите кнопку «Нет».</span><span class="sxs-lookup"><span data-stu-id="4825a-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="4825a-173">В разделе «Смешанной реальности Toolkit» щелкните «Добавить сцену и настройка».</span><span class="sxs-lookup"><span data-stu-id="4825a-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="4825a-175">После ее завершения, новый файл конфигурации будет отображаться, предоставляя выбор для его настройки.</span><span class="sxs-lookup"><span data-stu-id="4825a-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="4825a-176">Нажмите кнопку «Копировать и настройка».</span><span class="sxs-lookup"><span data-stu-id="4825a-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="4825a-178">Прокрутите список вниз и снимите флажок «Включить систему диагностики».</span><span class="sxs-lookup"><span data-stu-id="4825a-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="4825a-179">Это облегчит настроили этот проект.</span><span class="sxs-lookup"><span data-stu-id="4825a-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="4825a-181">Откройте параметры сборки (элемент управления + shift + B).</span><span class="sxs-lookup"><span data-stu-id="4825a-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="4825a-182">Обратите внимание, что в настоящее время программа указана в разделе «отдельно ПК, Mac и Linux» платформы.</span><span class="sxs-lookup"><span data-stu-id="4825a-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="4825a-183">Для этого проекта задайте платформы, чтобы быть «универсальная платформа windows.»</span><span class="sxs-lookup"><span data-stu-id="4825a-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="4825a-184">Выберите его и нажмите кнопку «коммутатор платформы».</span><span class="sxs-lookup"><span data-stu-id="4825a-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="4825a-186">После завершения щелкните поле с текстом «добавить откройте сцены».</span><span class="sxs-lookup"><span data-stu-id="4825a-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="4825a-187">Теперь перейдите к панели инспектора и убедитесь, что флажок справа от «поддерживается виртуальной реальности» (как показано на рисунке ниже) установлен.</span><span class="sxs-lookup"><span data-stu-id="4825a-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="4825a-189">Примечание. Также убедитесь, что также установлен флажок рядом с «сцены/HLSharedProjectMain».</span><span class="sxs-lookup"><span data-stu-id="4825a-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="4825a-190">В разделе «Параметры публикации» на панели Инспектора прокрутите вниз до «возможности» и пометить только следующие флажки:</span><span class="sxs-lookup"><span data-stu-id="4825a-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="4825a-191">Интернет-клиент</span><span class="sxs-lookup"><span data-stu-id="4825a-191">internet client</span></span>
- <span data-ttu-id="4825a-192">клиент-сервер Интернета</span><span class="sxs-lookup"><span data-stu-id="4825a-192">internet client server</span></span>
- <span data-ttu-id="4825a-193">клиент-сервер частной сети</span><span class="sxs-lookup"><span data-stu-id="4825a-193">private network client server</span></span>
- <span data-ttu-id="4825a-194">камера/веб-камеры</span><span class="sxs-lookup"><span data-stu-id="4825a-194">camera/webcam</span></span>
- <span data-ttu-id="4825a-195">микрофон</span><span class="sxs-lookup"><span data-stu-id="4825a-195">microphone</span></span>

21. <span data-ttu-id="4825a-196">Так же, как и шаг 12 следующим шагом было бы импортировать другой пользовательский пакет называется занятие «2», который можно скачать [здесь]. [здесь отображается ссылка lesson2.unitypackage] Импорт этого пакета.</span><span class="sxs-lookup"><span data-stu-id="4825a-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="4825a-198">Теперь в панели «проект» перейдите к папке «prefabs» так, как в следующих шагах будет реализовано несколько prefabs на сцене.</span><span class="sxs-lookup"><span data-stu-id="4825a-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="4825a-199">В папке «prefabs» щелкните и перетащите готового блока, «DebugWindow» в иерархии.</span><span class="sxs-lookup"><span data-stu-id="4825a-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="4825a-200">По завершении сохраните проект (щелкните файл, затем сохраните или control + S)</span><span class="sxs-lookup"><span data-stu-id="4825a-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="4825a-202">Примечание. Вы можете заметить всплывающее окно отображается при выборе готового блока, запрашивающее о TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="4825a-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="4825a-203">Нажмите кнопку «Импорт TMP Essentials», как они потребуются.</span><span class="sxs-lookup"><span data-stu-id="4825a-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="4825a-205">**Подключение нескольких пользователей**</span><span class="sxs-lookup"><span data-stu-id="4825a-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="4825a-206">Шаг 22, в папке «prefabs» в панели «проект», как следующий шаг — путем перетаскивания prefab «NetworkLobby» иерархии.</span><span class="sxs-lookup"><span data-stu-id="4825a-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="4825a-208">При разворачивании родительского готового блока, «NetworkLobby», должна появиться prefab, дочерний «NetworkRoom.»</span><span class="sxs-lookup"><span data-stu-id="4825a-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="4825a-209">С его включенным перейдите в панель инспектора и нажмите кнопку «Добавить компонент».</span><span class="sxs-lookup"><span data-stu-id="4825a-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="4825a-210">Поиск «PhotonView» и добавить компонент.</span><span class="sxs-lookup"><span data-stu-id="4825a-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="4825a-212">Создайте новый пустой объект игр в иерархии (правой кнопкой мыши в иерархии и выберите «empty»).</span><span class="sxs-lookup"><span data-stu-id="4825a-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="4825a-213">Настройте расположение x = 0, y = 0, z = 0 и имя объекта «PhotonUser.»</span><span class="sxs-lookup"><span data-stu-id="4825a-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="4825a-215">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="4825a-215">Congratulations</span></span>



