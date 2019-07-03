---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523299"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="f4b30-104">Настройки доступа Unity Photon</span><span class="sxs-lookup"><span data-stu-id="f4b30-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="f4b30-105">В этом руководстве мы узнаем, как для подготовки к использованию для создания общего качества, импортировав сети Photon Unity (СОВМЕСТНОЙ) в проекте Unity.</span><span class="sxs-lookup"><span data-stu-id="f4b30-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="f4b30-106">Photon — один из нескольких сетевых параметров для смешанной реальности разработчикам создать публикацию.</span><span class="sxs-lookup"><span data-stu-id="f4b30-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="f4b30-107">Мы будет показано, как создать учетную запись Photon и импортировать Photon создания необязательно локального сервера</span><span class="sxs-lookup"><span data-stu-id="f4b30-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="f4b30-108">Цели:</span><span class="sxs-lookup"><span data-stu-id="f4b30-108">Objectives:</span></span>

* <span data-ttu-id="f4b30-109">Узнайте, как создать учетную запись Photon</span><span class="sxs-lookup"><span data-stu-id="f4b30-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="f4b30-110">Узнайте, как найти и импортировать сетевые подключения Unity Photon</span><span class="sxs-lookup"><span data-stu-id="f4b30-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="f4b30-111">Настройка локального сервера Photon</span><span class="sxs-lookup"><span data-stu-id="f4b30-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="f4b30-112">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="f4b30-112">Setting up Photon</span></span>

1. <span data-ttu-id="f4b30-113">Настройка [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) учетной записи.</span><span class="sxs-lookup"><span data-stu-id="f4b30-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="f4b30-114">Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="f4b30-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="f4b30-115">Следуйте инструкциям на странице регистрации, чтобы создать учетную запись.</span><span class="sxs-lookup"><span data-stu-id="f4b30-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="f4b30-118">Создайте идентификатор приложения, нажав кнопку Создать кнопку нового приложения.</span><span class="sxs-lookup"><span data-stu-id="f4b30-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="f4b30-120">Выберите в раскрывающемся меню в качестве типа Photon Photon СОВМЕСТНОЙ.</span><span class="sxs-lookup"><span data-stu-id="f4b30-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="f4b30-121">Затем присвойте ему имя.</span><span class="sxs-lookup"><span data-stu-id="f4b30-121">Then give it a name.</span></span> <span data-ttu-id="f4b30-122">В этом примере мы назвали его HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="f4b30-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="f4b30-123">По завершении нажмите кнопку «Создать».</span><span class="sxs-lookup"><span data-stu-id="f4b30-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="f4b30-125">После этого вернуться на страницу приложения, и вы увидите нечто, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="f4b30-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="f4b30-126">Щелкните идентификатор приложения и скопируйте его.</span><span class="sxs-lookup"><span data-stu-id="f4b30-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="f4b30-127">Вставить находится где-нибудь, которые можно легко получить.</span><span class="sxs-lookup"><span data-stu-id="f4b30-127">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="f4b30-129">Создайте новый проект unity и назовите его HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="f4b30-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="f4b30-130">Инструкции по созданию нового проекта Unity, обратитесь к [раздел «Создание проекта Unity» базового модуля](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="f4b30-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="f4b30-131">После загрузки проекта, откройте вкладку Store средств, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="f4b30-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="f4b30-132">Затем в поле поиска, выделены на рисунке ниже, введите в СОВМЕСТНОЙ и выберите 2 СОВМЕСТНОЙ Photon - FRE» ресурс в результатах поиска.</span><span class="sxs-lookup"><span data-stu-id="f4b30-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FRE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="f4b30-134">Скачайте и импортируйте этот ресурс нажатием кнопки загрузки и импорта.</span><span class="sxs-lookup"><span data-stu-id="f4b30-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="f4b30-136">После завершения процесса импорта Photon появится мастер совместной.</span><span class="sxs-lookup"><span data-stu-id="f4b30-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="f4b30-137">Использовать идентификатор приложения (который должен быть в буфер обмена) из шага 4 и вставьте его в окне "AppID" и нажмите кнопку проекта установки.</span><span class="sxs-lookup"><span data-stu-id="f4b30-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="f4b30-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="f4b30-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="f4b30-139">После успешного добавления AppID, перейдите к Photon "->" PhotonUnityNetworking "->" ресурсы "->" PhotonServerSettings в ресурсах.</span><span class="sxs-lookup"><span data-stu-id="f4b30-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="f4b30-140">Выберите параметр используйте имя сервера и задайте фиксированный нам или yourPphoton службы регионе.</span><span class="sxs-lookup"><span data-stu-id="f4b30-140">Select the Use Name Server option, and set the fixed region to US or yourPphoton service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="f4b30-142">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="f4b30-142">Congratulations</span></span>

<span data-ttu-id="f4b30-143">Вы успешно создали учетную запись Photon, настроить локальный сервер Photon и импортировать СОВМЕСТНОЙ в Unity.</span><span class="sxs-lookup"><span data-stu-id="f4b30-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="f4b30-144">Следующий шаг — проект, а затем разрешить соединения с другими пользователями, таким образом, чтобы несколько пользователей можно увидеть результаты работы.</span><span class="sxs-lookup"><span data-stu-id="f4b30-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="f4b30-145">[Следующему руководству: Подготовка к работе, для разработки Unity](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="f4b30-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

