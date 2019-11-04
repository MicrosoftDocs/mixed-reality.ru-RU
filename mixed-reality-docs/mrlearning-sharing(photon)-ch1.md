---
title: Учебники по возможностям для нескольких пользователей — 1. Настройка сети Unity Photon
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: c6a2bea3d50669000e81cad7c83ae6a69b8a847f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437748"
---
#  <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="b3b6d-105">1. Настройка сети Unity Photon</span><span class="sxs-lookup"><span data-stu-id="b3b6d-105">1. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="b3b6d-106">В этом руководстве вы узнаете, как подготовиться к созданию общего интерфейса, импортировав Photon Unity Networking (шутка) в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-106">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="b3b6d-107">Photon — это один из нескольких сетевых возможностей, доступных разработчикам смешанной реальности для создания общих возможностей.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-107">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="b3b6d-108">Вы узнаете, как создать учетную запись Photon, импортировать Photon и создать необязательный локальный сервер.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-108">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="b3b6d-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="b3b6d-109">Objectives</span></span>

* <span data-ttu-id="b3b6d-110">Узнайте, как создать учетную запись Photon.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-110">Learn how to create a Photon account</span></span>

* <span data-ttu-id="b3b6d-111">Узнайте, как найти и импортировать сеть Unity Photon</span><span class="sxs-lookup"><span data-stu-id="b3b6d-111">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="b3b6d-112">Настройка локального сервера Photon</span><span class="sxs-lookup"><span data-stu-id="b3b6d-112">Set up a local Photon server</span></span>

  

## <a name="setting-up-photon"></a><span data-ttu-id="b3b6d-113">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="b3b6d-113">Setting up Photon</span></span>

1. <span data-ttu-id="b3b6d-114">Настройте учетную запись [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="b3b6d-114">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="b3b6d-115">Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="b3b6d-115">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="b3b6d-116">Чтобы создать учетную запись, следуйте инструкциям на странице регистрации.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-116">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="b3b6d-119">Создайте идентификатор приложения, нажав кнопку Создать новое приложение.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-119">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="b3b6d-121">Выберите Photon шутка в раскрывающемся меню в разделе Тип Photon.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-121">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="b3b6d-122">Затем присвойте ему имя.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-122">Then give it a name.</span></span> <span data-ttu-id="b3b6d-123">В этом примере мы назвали IT Хололенсфотонпрожект.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-123">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="b3b6d-124">По завершении нажмите кнопку Создать.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-124">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="b3b6d-126">Вернитесь на страницу приложений, и вы увидите примерно следующее изображение.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-126">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="b3b6d-127">Щелкните идентификатор приложения и скопируйте его.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-127">Click the application ID and copy it.</span></span> <span data-ttu-id="b3b6d-128">Вставьте его в любом месте, к которому вы можете легко получить доступ.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-128">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="b3b6d-130">Создайте новый проект Unity и назовите его Хлшарингпрожект.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-130">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="b3b6d-131">Инструкции по созданию нового проекта Unity см. в [разделе "Создание проекта Unity" базового модуля](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="b3b6d-131">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="b3b6d-132">После загрузки проекта перейдите на вкладку хранилище ресурсов, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-132">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="b3b6d-133">Затем в поле поиска, выделенном на изображении ниже, введите шутка и в результатах поиска выберите ресурс Photon шутка 2 (бесплатный).</span><span class="sxs-lookup"><span data-stu-id="b3b6d-133">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="b3b6d-135">Скачайте и импортируйте этот ресурс, нажав кнопку Скачать и импортировать.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-135">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="b3b6d-137">После завершения процесса импорта Photon появится мастер шутка.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-137">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="b3b6d-138">Возьмите идентификатор приложения (который должен находиться в буфере обмена) из шага 4, вставьте его в поле AppID и нажмите кнопку проект установки.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-138">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="b3b6d-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="b3b6d-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="b3b6d-140">После успешного добавления AppID перейдите в раздел Photon-> Фотонунитинетворкинг-> Resources-> Фотонсерверсеттингс in Assets.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-140">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="b3b6d-141">Выберите параметр использовать сервер имен и задайте для параметра фиксированный регион значение US или регион службы Photon.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-141">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="b3b6d-143">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="b3b6d-143">Congratulations</span></span>

<span data-ttu-id="b3b6d-144">Вы успешно создали учетную запись Photon, настроили локальный сервер Photon и импортировали шутка в Unity.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-144">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="b3b6d-145">Следующим шагом является настройка проекта и разрешение подключений с другими пользователями, чтобы несколько пользователей могли видеть вашу работу.</span><span class="sxs-lookup"><span data-stu-id="b3b6d-145">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="b3b6d-146">[Следующий учебник: 2. Подготовка Unity к разработке](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="b3b6d-146">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

