---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416125"
---
# <a name="setting-up-photon"></a><span data-ttu-id="da9a6-104">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="da9a6-104">Setting Up Photon</span></span>

<span data-ttu-id="da9a6-105">На этом занятии будет рассказано также Подготовка для создания общего качества, импортировав сети Photon Unity (СОВМЕСТНОЙ) в проекте Unity.</span><span class="sxs-lookup"><span data-stu-id="da9a6-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="da9a6-106">Photon — один из нескольких сетевых параметров для смешанной реальности разработчикам создать публикацию.</span><span class="sxs-lookup"><span data-stu-id="da9a6-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="da9a6-107">Мы будет показано, как создать учетную запись Photon и импортировать Photon создания необязательно локального сервера</span><span class="sxs-lookup"><span data-stu-id="da9a6-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="da9a6-108">Цели:</span><span class="sxs-lookup"><span data-stu-id="da9a6-108">Objectives:</span></span>

* <span data-ttu-id="da9a6-109">Узнайте, как создать учетную запись с Photon</span><span class="sxs-lookup"><span data-stu-id="da9a6-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="da9a6-110">Узнайте, как найти и импортировать сетевые подключения Unity Photon</span><span class="sxs-lookup"><span data-stu-id="da9a6-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="da9a6-111">Настройка локального сервера Photon</span><span class="sxs-lookup"><span data-stu-id="da9a6-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="da9a6-112">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="da9a6-112">Setting Up Photon</span></span>

1. <span data-ttu-id="da9a6-113">Настройка [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) учетной записи.</span><span class="sxs-lookup"><span data-stu-id="da9a6-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="da9a6-114">Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="da9a6-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="da9a6-115">Следуйте инструкциям на странице регистрации, чтобы создать учетную запись.</span><span class="sxs-lookup"><span data-stu-id="da9a6-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="da9a6-118">Создайте идентификатор приложения, нажав кнопку «Создать новое приложение».</span><span class="sxs-lookup"><span data-stu-id="da9a6-118">Create an application ID by clicking the "create a new app" button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="da9a6-120">Выберите «Photon СОВМЕСТНОЙ» в раскрывающемся меню в разделе «photon type».</span><span class="sxs-lookup"><span data-stu-id="da9a6-120">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="da9a6-121">Затем присвойте ему имя, в этом примере, мы назвали «HoloLensPhotonProject.»</span><span class="sxs-lookup"><span data-stu-id="da9a6-121">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="da9a6-122">По завершении нажмите кнопку «Создать».</span><span class="sxs-lookup"><span data-stu-id="da9a6-122">Once finished, click the "CREATE" button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="da9a6-124">После этого вернуться на страницу приложения, и вы увидите нечто, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="da9a6-124">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="da9a6-125">Щелкните идентификатор приложения и скопируйте его.</span><span class="sxs-lookup"><span data-stu-id="da9a6-125">Click on the app ID and copy it.</span></span> <span data-ttu-id="da9a6-126">Вставить находится где-нибудь, которые можно легко получить.</span><span class="sxs-lookup"><span data-stu-id="da9a6-126">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="da9a6-128">Создайте новый проект unity и назовите его «HLSharingProject.»</span><span class="sxs-lookup"><span data-stu-id="da9a6-128">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="da9a6-129">Инструкции по созданию нового проекта Unity, обратитесь к [раздел «Создание проекта Unity» базового модуля](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="da9a6-129">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="da9a6-130">После загрузки проекта, откройте вкладку «активы store», как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="da9a6-130">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="da9a6-131">Затем в поле поиска, выделены на рисунке ниже, введите «СОВМЕСТНОЙ» и выберите ресурс «Photon СОВМЕСТНОЙ 2 — бесплатный» в результатах поиска.</span><span class="sxs-lookup"><span data-stu-id="da9a6-131">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="da9a6-133">Скачайте и импортируйте этот ресурс нажатием кнопки «Загрузить» и «Импорт».</span><span class="sxs-lookup"><span data-stu-id="da9a6-133">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="da9a6-135">После завершения процесса импорта Photon совместной мастера будут отображаться.</span><span class="sxs-lookup"><span data-stu-id="da9a6-135">Once Photon has completed the importing process, the Pun Wizard will appear.</span></span> <span data-ttu-id="da9a6-136">Использовать идентификатор приложения (который должен быть в буфер обмена) из шага 4 и вставьте его в окне "AppID" и нажмите кнопку «Настройка проект».</span><span class="sxs-lookup"><span data-stu-id="da9a6-136">Take the application ID (which should be in your clipboard) from step 4 and paste it into the AppID box and press the "Setup Project" button.</span></span> 
<span data-ttu-id="da9a6-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="da9a6-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="da9a6-138">После успешного добавления AppID, перейдите к «Фотон «->» PhotonUnityNetworking» -> «Ресурсы» -> «PhotonServerSettings» в средствах.</span><span class="sxs-lookup"><span data-stu-id="da9a6-138">After successfully adding the AppID, navigate to "Photon"->"PhotonUnityNetworking" -> "Resources" ->  "PhotonServerSettings" in Assets.</span></span> <span data-ttu-id="da9a6-139">Выберите параметр «Использовать имя сервера» и задайте фиксированную область «США» или вашего региона photon службы.</span><span class="sxs-lookup"><span data-stu-id="da9a6-139">Select "Use Name Server" option and set the fixed region to "us" or your photon service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="da9a6-141">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="da9a6-141">Congratulations</span></span>

<span data-ttu-id="da9a6-142">Вы успешно создали учетную запись Photon, настроить локальный сервер Photon и импортировать СОВМЕСТНОЙ в Unity.</span><span class="sxs-lookup"><span data-stu-id="da9a6-142">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="da9a6-143">Следующий шаг — проект, а затем разрешить соединения с другими пользователями, таким образом, чтобы несколько пользователей можно увидеть результаты работы.</span><span class="sxs-lookup"><span data-stu-id="da9a6-143">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="da9a6-144">[Следующий урок. Sharing(Photon) занятие 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="da9a6-144">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

