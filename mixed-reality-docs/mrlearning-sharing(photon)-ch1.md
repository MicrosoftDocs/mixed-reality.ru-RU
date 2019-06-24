---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326785"
---
# <a name="setting-up-photon"></a><span data-ttu-id="d0451-104">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="d0451-104">Setting Up Photon</span></span>

<span data-ttu-id="d0451-105">На этом занятии будет рассказано также Подготовка для создания общего качества, импортировав сети Photon Unity (СОВМЕСТНОЙ) в проекте Unity.</span><span class="sxs-lookup"><span data-stu-id="d0451-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="d0451-106">Photon — один из нескольких сетевых параметров для смешанной реальности разработчикам создать публикацию.</span><span class="sxs-lookup"><span data-stu-id="d0451-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="d0451-107">Мы будет показано, как создать учетную запись Photon и импортировать Photon создания необязательно локального сервера</span><span class="sxs-lookup"><span data-stu-id="d0451-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="d0451-108">Цели:</span><span class="sxs-lookup"><span data-stu-id="d0451-108">Objectives:</span></span>

* <span data-ttu-id="d0451-109">Узнайте, как создать учетную запись с Photon</span><span class="sxs-lookup"><span data-stu-id="d0451-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="d0451-110">Узнайте, как найти и импортировать сетевые подключения Unity Photon</span><span class="sxs-lookup"><span data-stu-id="d0451-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="d0451-111">Настройка локального сервера Photon</span><span class="sxs-lookup"><span data-stu-id="d0451-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="d0451-112">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="d0451-112">Setting Up Photon</span></span>

1. <span data-ttu-id="d0451-113">Настройка [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) учетной записи.</span><span class="sxs-lookup"><span data-stu-id="d0451-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="d0451-114">Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="d0451-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="d0451-115">Следуйте инструкциям на странице регистрации, чтобы создать учетную запись.</span><span class="sxs-lookup"><span data-stu-id="d0451-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. <span data-ttu-id="d0451-117">Как только вы зарегистрированы, щелкните пакеты SDK.</span><span class="sxs-lookup"><span data-stu-id="d0451-117">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="d0451-118">После перехода на эту страницу, щелкните «сервер» и убедиться, он говорит: «резидентной.»</span><span class="sxs-lookup"><span data-stu-id="d0451-118">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="d0451-119">Прокрутите вниз и выберите команду «сервер», как показано на втором рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d0451-119">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. <span data-ttu-id="d0451-122">Приведет к отображается с меткой, для текстового поля «read me».</span><span class="sxs-lookup"><span data-stu-id="d0451-122">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="d0451-123">Продолжим и его чтение.</span><span class="sxs-lookup"><span data-stu-id="d0451-123">Go ahead and read it.</span></span> <span data-ttu-id="d0451-124">По завершении щелкните ссылку рядом с «downloadSDK», чтобы загрузить его.</span><span class="sxs-lookup"><span data-stu-id="d0451-124">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. <span data-ttu-id="d0451-126">Дважды щелкните папку, после завершения загрузки.</span><span class="sxs-lookup"><span data-stu-id="d0451-126">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="d0451-127">Открыв проводнике раскрытия в папку пакета SDK, скопируйте в папку пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="d0451-127">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="d0451-128">Следующим шагом будет перейти на диске C: windows и создайте новую папку с именем «сервер».</span><span class="sxs-lookup"><span data-stu-id="d0451-128">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - <span data-ttu-id="d0451-130">Теперь откройте папку и вставьте в папку пакета SDK, скопированный ранее.</span><span class="sxs-lookup"><span data-stu-id="d0451-130">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. <span data-ttu-id="d0451-132">После завершения, откройте папку пакета SDK и перейдите в раздел «Развертывание» выберите «bin_Win64», затем дважды щелкните «Фотон control».</span><span class="sxs-lookup"><span data-stu-id="d0451-132">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> <span data-ttu-id="d0451-134">Примечание. Если у вас возникнут вопросы по IP-адрес или другие аналогичные вопросы, можно найти большую часть информации в панели инструментов (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="d0451-134">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. <span data-ttu-id="d0451-136">Теперь, когда сервер настраивается и инициированный, вернитесь на веб-сайт Photon и убедитесь, что по-прежнему вы вошли (или снова войдите, если вы не являетесь). Щелкните значок профиля (упаковывается в правом верхнем углу на рисунке ниже) и выберите «вашего приложения.»</span><span class="sxs-lookup"><span data-stu-id="d0451-136">Now that the server is set up and initiated, go back to the Photon website and ensure that you are still signed in (or sign back in, if you are not.) Click on the profile icon (boxed in the top right corner of the image below) and select "your applications."</span></span>
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. <span data-ttu-id="d0451-138">Создайте идентификатор приложения, нажав кнопку «Создать новое приложение».</span><span class="sxs-lookup"><span data-stu-id="d0451-138">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - <span data-ttu-id="d0451-140">Выберите «Photon СОВМЕСТНОЙ» в раскрывающемся меню в разделе «photon type».</span><span class="sxs-lookup"><span data-stu-id="d0451-140">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="d0451-141">Затем присвойте ему имя, в этом примере, мы назвали «HoloLensPhotonProject.»</span><span class="sxs-lookup"><span data-stu-id="d0451-141">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="d0451-142">По завершении нажмите кнопку «Создать».</span><span class="sxs-lookup"><span data-stu-id="d0451-142">Once finished, click the "CREATE" button.</span></span>

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. <span data-ttu-id="d0451-144">После этого вернуться на страницу приложения, и вы увидите нечто, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d0451-144">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="d0451-145">Щелкните идентификатор приложения и скопируйте его.</span><span class="sxs-lookup"><span data-stu-id="d0451-145">Click on the app ID and copy it.</span></span> <span data-ttu-id="d0451-146">Вставить находится где-нибудь, которые можно легко получить.</span><span class="sxs-lookup"><span data-stu-id="d0451-146">Paste is somewhere you can easily access.</span></span>  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. <span data-ttu-id="d0451-148">Создайте новый проект unity и назовите его «HLSharingProject.»</span><span class="sxs-lookup"><span data-stu-id="d0451-148">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="d0451-149">Инструкции по созданию нового проекта Unity, обратитесь к [раздел «Создание проекта Unity» базового модуля](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="d0451-149">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 


10. <span data-ttu-id="d0451-150">После загрузки проекта, откройте вкладку «активы store», как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d0451-150">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="d0451-151">Затем в поле поиска, выделены на рисунке ниже, введите «СОВМЕСТНОЙ» и выберите «Бесплатная СОВМЕСТНОЙ 2 Photon» ресурс в результатах поиска.</span><span class="sxs-lookup"><span data-stu-id="d0451-151">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset from the search results.</span></span> 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. <span data-ttu-id="d0451-153">Скачайте и импортируйте этот ресурс нажатием кнопки «Загрузить» и «Импорт».</span><span class="sxs-lookup"><span data-stu-id="d0451-153">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="d0451-155">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d0451-155">Congratulations</span></span>

<span data-ttu-id="d0451-156">Вы успешно создали учетную запись Photon, настроить локальный сервер Photon и импортировать СОВМЕСТНОЙ в Unity.</span><span class="sxs-lookup"><span data-stu-id="d0451-156">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="d0451-157">Следующий шаг — проект, а затем разрешить соединения с другими пользователями, таким образом, чтобы несколько пользователей можно увидеть результаты работы.</span><span class="sxs-lookup"><span data-stu-id="d0451-157">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="d0451-158">[Следующий урок. Sharing(Photon) занятие 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="d0451-158">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

