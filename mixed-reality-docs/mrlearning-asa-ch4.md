---
title: Модуль MR Learning ASA. пространственный якорь Azure в HoloLens 2
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 141aa90f2bf5d90527a0fe1e6a812c1ce56bd0eb
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437801"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="f2d71-104">Photon (исправьте меня, если меня не так)</span><span class="sxs-lookup"><span data-stu-id="f2d71-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="f2d71-105">На этом занятии</span><span class="sxs-lookup"><span data-stu-id="f2d71-105">In this lesson,</span></span> 

<span data-ttu-id="f2d71-106">Служит</span><span class="sxs-lookup"><span data-stu-id="f2d71-106">Objectives:</span></span>

* <span data-ttu-id="f2d71-107">Узнайте, как _____________________________________________</span><span class="sxs-lookup"><span data-stu-id="f2d71-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="f2d71-108">Узнайте, как _________________________________________________</span><span class="sxs-lookup"><span data-stu-id="f2d71-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="f2d71-109">Инструкция</span><span class="sxs-lookup"><span data-stu-id="f2d71-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="f2d71-110">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="f2d71-110">Setting Up Photon</span></span>

1. <span data-ttu-id="f2d71-111">Настройте учетную запись [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="f2d71-111">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="f2d71-112">Это будет состоять из ввода электронной почты и выполнения некоторых шагов проверки.</span><span class="sxs-lookup"><span data-stu-id="f2d71-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="f2d71-114">После регистрации щелкните пакеты SDK.</span><span class="sxs-lookup"><span data-stu-id="f2d71-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="f2d71-115">На этой странице щелкните "сервер" и убедитесь в том, что он находится в "собственном размещении".</span><span class="sxs-lookup"><span data-stu-id="f2d71-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="f2d71-116">Затем прокрутите вниз и щелкните "сервер", как показано на втором рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="f2d71-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="f2d71-119">Это приведет к появлению текстового поля с надписью «Read Me».</span><span class="sxs-lookup"><span data-stu-id="f2d71-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="f2d71-120">Прочтите этот раздел.</span><span class="sxs-lookup"><span data-stu-id="f2d71-120">Go ahead and read it.</span></span> <span data-ttu-id="f2d71-121">По завершении щелкните ссылку рядом с "Довнлоадсдк", чтобы скачать ее.</span><span class="sxs-lookup"><span data-stu-id="f2d71-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="f2d71-123">Дважды щелкните папку после завершения загрузки.</span><span class="sxs-lookup"><span data-stu-id="f2d71-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="f2d71-124">После того как проводник откроет папку SDK, скопируйте папку SDK.</span><span class="sxs-lookup"><span data-stu-id="f2d71-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="f2d71-125">Следующий шаг — перейти на диск Windows C: и создать новую папку с именем Server.</span><span class="sxs-lookup"><span data-stu-id="f2d71-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="f2d71-127">Теперь откройте папку и вставьте скопированную ранее папку SDK.</span><span class="sxs-lookup"><span data-stu-id="f2d71-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="f2d71-129">По завершении откройте папку SDK и последовательно выберите "развернуть", "bin_Win64", а затем дважды щелкните "элемент управления Photon".</span><span class="sxs-lookup"><span data-stu-id="f2d71-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="f2d71-131">Примечание. Если у вас есть вопросы по IP-адресу или на другие похожие вопросы, на панели инструментов можно найти большую часть информации (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="f2d71-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="f2d71-133">Теперь, когда сервер настроен и запущен, вернитесь на веб-сайт Photon и щелкните значок профиля (в штучной упаковке на рисунке ниже) и выберите "ваши приложения".</span><span class="sxs-lookup"><span data-stu-id="f2d71-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="f2d71-135">Создайте идентификатор приложения, нажав кнопку "создать новое приложение".</span><span class="sxs-lookup"><span data-stu-id="f2d71-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="f2d71-137">Выберите "Photon RUN" в раскрывающемся меню в разделе "тип Photon".</span><span class="sxs-lookup"><span data-stu-id="f2d71-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="f2d71-138">Затем присвойте ему имя (что вы запомнили).</span><span class="sxs-lookup"><span data-stu-id="f2d71-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="f2d71-139">В этом примере мы назвали его «Хололенсфотонпрожект».</span><span class="sxs-lookup"><span data-stu-id="f2d71-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="f2d71-140">После завершения нажмите кнопку "создать".</span><span class="sxs-lookup"><span data-stu-id="f2d71-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="f2d71-142">После этого вернитесь на страницу приложения, и вы увидите примерно следующее изображение.</span><span class="sxs-lookup"><span data-stu-id="f2d71-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="f2d71-143">Щелкните идентификатор приложения и скопируйте его.</span><span class="sxs-lookup"><span data-stu-id="f2d71-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="f2d71-144">Вставить — куда вы можете легко получить доступ.</span><span class="sxs-lookup"><span data-stu-id="f2d71-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="f2d71-146">Создайте новый проект Unity.</span><span class="sxs-lookup"><span data-stu-id="f2d71-146">Create a new unity project.</span></span> <span data-ttu-id="f2d71-147">Откройте центр Unity и щелкните "создать".</span><span class="sxs-lookup"><span data-stu-id="f2d71-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="f2d71-148">Назовите его «Хлшарингпрожект».</span><span class="sxs-lookup"><span data-stu-id="f2d71-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="f2d71-149">Затем нажмите кнопку Создать.</span><span class="sxs-lookup"><span data-stu-id="f2d71-149">Then click create.</span></span> 

   > <span data-ttu-id="f2d71-150">Примечание. Загрузка может занять до 2 минут в зависимости от скорости вашего компьютера.</span><span class="sxs-lookup"><span data-stu-id="f2d71-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="f2d71-152">Примечание. Выберите место для сохранения проекта на компьютере, изменив параметр "расположение".</span><span class="sxs-lookup"><span data-stu-id="f2d71-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="f2d71-153">Сохраните его на месте, и вы запомнитее и сможете легко получить доступ к.</span><span class="sxs-lookup"><span data-stu-id="f2d71-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="f2d71-154">После загрузки проекта щелкните "магазин ресурсов".</span><span class="sxs-lookup"><span data-stu-id="f2d71-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="f2d71-155">Затем в поле поиска, показанном на рисунке ниже, введите "шутка" и выберите ресурс "Photon шутка 2 FREE".</span><span class="sxs-lookup"><span data-stu-id="f2d71-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="f2d71-157">Скачайте и импортируйте!</span><span class="sxs-lookup"><span data-stu-id="f2d71-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="f2d71-159">**Настройка проекта Unity**</span><span class="sxs-lookup"><span data-stu-id="f2d71-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="f2d71-160">Скачайте новый ресурс, необходимый для настройки PHOTON в Unity, щелкнув [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="f2d71-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="f2d71-161">В Unity щелкните меню активы и выберите "Импорт ресурсов", а затем щелкните "настраиваемые активы".</span><span class="sxs-lookup"><span data-stu-id="f2d71-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="f2d71-163">Выберите пакет Unity, который вы только что скачали, по ссылке, предоставленной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="f2d71-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="f2d71-164">Когда в Unity появится кнопка импорт, щелкните ее.</span><span class="sxs-lookup"><span data-stu-id="f2d71-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="f2d71-166">Примечание. когда вы загрузили пакет в место его поиска,</span><span class="sxs-lookup"><span data-stu-id="f2d71-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="f2d71-167">На приведенном выше рисунке не отображать, где находится пакет.</span><span class="sxs-lookup"><span data-stu-id="f2d71-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="f2d71-168">Создайте новую сцену (это можно сделать с помощью Control/Command + N или щелкнув "файл" и выбрав "создать сцену").</span><span class="sxs-lookup"><span data-stu-id="f2d71-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="f2d71-169">Сохраните сцену как «Хлшаредпрожектмаин».</span><span class="sxs-lookup"><span data-stu-id="f2d71-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="f2d71-170">Примечание. Вы можете получить всплывающее окно, похожее на изображение ниже.</span><span class="sxs-lookup"><span data-stu-id="f2d71-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="f2d71-171">Пока просто щелкните "нет".</span><span class="sxs-lookup"><span data-stu-id="f2d71-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="f2d71-173">В разделе "набор средств для смешанной реальности" щелкните "добавить в сцену и настроить".</span><span class="sxs-lookup"><span data-stu-id="f2d71-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="f2d71-175">После завершения этого процесса появится новый файл конфигурации, в котором вы сможете настроить профиль.</span><span class="sxs-lookup"><span data-stu-id="f2d71-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="f2d71-176">Щелкните "копировать и настроить".</span><span class="sxs-lookup"><span data-stu-id="f2d71-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="f2d71-178">Прокрутите вниз и снимите флажок "включить систему диагностики".</span><span class="sxs-lookup"><span data-stu-id="f2d71-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="f2d71-179">Это упростит настройку этого проекта.</span><span class="sxs-lookup"><span data-stu-id="f2d71-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="f2d71-181">Откройте параметры сборки (Control + Shift + B).</span><span class="sxs-lookup"><span data-stu-id="f2d71-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="f2d71-182">Обратите внимание, что программа в настоящее время задается на платформе "компьютер, Mac и Linux изолированно".</span><span class="sxs-lookup"><span data-stu-id="f2d71-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="f2d71-183">Для этого проекта задайте для параметра платформа значение "универсальная платформа Windows".</span><span class="sxs-lookup"><span data-stu-id="f2d71-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="f2d71-184">Выберите его и щелкните "сменить платформу".</span><span class="sxs-lookup"><span data-stu-id="f2d71-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="f2d71-186">После завершения щелкните поле с текстом "Добавить открытые сцены".</span><span class="sxs-lookup"><span data-stu-id="f2d71-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="f2d71-187">Теперь перейдите на панель инспектора и убедитесь в том, что установлен флажок справа от параметра "поддерживается виртуальная реальность" (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="f2d71-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="f2d71-189">Примечание. также убедитесь в том, что флажок "сцены" («сцена/Хлшаредпрожектмаин») также установлен.</span><span class="sxs-lookup"><span data-stu-id="f2d71-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="f2d71-190">В разделе "Параметры публикации" на панели инспектора прокрутите вниз до пункта "возможности" и убедитесь, что отмечены только следующие флажки:</span><span class="sxs-lookup"><span data-stu-id="f2d71-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="f2d71-191">Интернет клиента</span><span class="sxs-lookup"><span data-stu-id="f2d71-191">internet client</span></span>
- <span data-ttu-id="f2d71-192">сервер клиентского Интернет</span><span class="sxs-lookup"><span data-stu-id="f2d71-192">internet client server</span></span>
- <span data-ttu-id="f2d71-193">сервер клиента частной сети</span><span class="sxs-lookup"><span data-stu-id="f2d71-193">private network client server</span></span>
- <span data-ttu-id="f2d71-194">Камера и веб-камера</span><span class="sxs-lookup"><span data-stu-id="f2d71-194">camera/webcam</span></span>
- <span data-ttu-id="f2d71-195">микрофон</span><span class="sxs-lookup"><span data-stu-id="f2d71-195">microphone</span></span>

21. <span data-ttu-id="f2d71-196">Как и в шаге 12, следующим шагом будет импорт другого пользовательского пакета с именем «Lesson2», который можно скачать [здесь.] [ссылка на lesson2. пакет unitypackage здесь] Импортируйте этот пакет.</span><span class="sxs-lookup"><span data-stu-id="f2d71-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="f2d71-198">Теперь на панели проект перейдите к папке "Prefabs", так как в следующих шагах будет реализовано несколько Prefabs в сцене.</span><span class="sxs-lookup"><span data-stu-id="f2d71-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="f2d71-199">В папке "Prefabs" щелкните и перетащите prefab, "DebugWindow" в иерархию.</span><span class="sxs-lookup"><span data-stu-id="f2d71-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="f2d71-200">По завершении сохраните проект (щелкните файл, затем сохранить или Control + S).</span><span class="sxs-lookup"><span data-stu-id="f2d71-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="f2d71-202">Примечание. Вы можете заметить, что всплывающее окно отображается при щелчке prefab, предлагающем о параметрах TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="f2d71-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="f2d71-203">Щелкните "Импорт основных компонентов TMP", так как они понадобятся.</span><span class="sxs-lookup"><span data-stu-id="f2d71-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="f2d71-205">**Подключение нескольких пользователей**</span><span class="sxs-lookup"><span data-stu-id="f2d71-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="f2d71-206">Как и в шаге 22, в папке «Prefabs» на панели «проект» следующий шаг заключается в перетаскивании «Нетворклобби» prefab в иерархию.</span><span class="sxs-lookup"><span data-stu-id="f2d71-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="f2d71-208">При открытии родительского prefab "Нетворклобби" должен отобразиться дочерний prefab "Нетворкрум".</span><span class="sxs-lookup"><span data-stu-id="f2d71-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="f2d71-209">Выбрав его, перейдите на панель инспектора и нажмите кнопку "добавить компонент".</span><span class="sxs-lookup"><span data-stu-id="f2d71-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="f2d71-210">Выполните поиск по запросу "Фотонвиев" и добавьте компонент.</span><span class="sxs-lookup"><span data-stu-id="f2d71-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="f2d71-212">Создайте новый пустой объект Game в иерархии (щелкните правой кнопкой мыши в иерархии и выберите "пусто").</span><span class="sxs-lookup"><span data-stu-id="f2d71-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="f2d71-213">Убедитесь, что для положения задано значение x = 0, y = 0, z = 0 и имя объекта «Фотонусер».</span><span class="sxs-lookup"><span data-stu-id="f2d71-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="f2d71-215">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="f2d71-215">Congratulations</span></span>



