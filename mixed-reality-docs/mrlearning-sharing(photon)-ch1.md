---
title: Учебники по возможностям для нескольких пользователей — 1. Настройка сети Unity Photon
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: acb6966ace81180e95e6a0fe447d350572f7c0dd
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701969"
---
#  <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="cb0ee-105">1. Настройка сети Unity Photon</span><span class="sxs-lookup"><span data-stu-id="cb0ee-105">1. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="cb0ee-106">Из этого руководства вы узнаете, как подготовиться к созданию общего интерфейса, импортировав Photon Unity Networking (шутка) в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-106">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="cb0ee-107">Photon — это один из нескольких сетевых возможностей, доступных разработчикам смешанной реальности для создания общих возможностей.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-107">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="cb0ee-108">Мы научитесь создавать учетную запись Photon, импортировать Photon и создавать необязательный локальный сервер.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-108">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="cb0ee-109">Цели</span><span class="sxs-lookup"><span data-stu-id="cb0ee-109">Objectives</span></span>

* <span data-ttu-id="cb0ee-110">Узнайте, как создать учетную запись Photon.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-110">Learn how to create a Photon account</span></span>

* <span data-ttu-id="cb0ee-111">Узнайте, как найти и импортировать сеть Unity Photon</span><span class="sxs-lookup"><span data-stu-id="cb0ee-111">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="cb0ee-112">Настройка локального сервера Photon</span><span class="sxs-lookup"><span data-stu-id="cb0ee-112">Set up a local Photon server</span></span>

  

## <a name="setting-up-photon"></a><span data-ttu-id="cb0ee-113">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="cb0ee-113">Setting up Photon</span></span>

1. <span data-ttu-id="cb0ee-114">Настройте учетную запись [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="cb0ee-114">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="cb0ee-115">Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="cb0ee-115">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="cb0ee-116">Чтобы создать учетную запись, следуйте инструкциям на странице регистрации.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-116">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="cb0ee-119">Создайте идентификатор приложения, нажав кнопку Создать новое приложение.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-119">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="cb0ee-121">Выберите Photon шутка в раскрывающемся меню в разделе Тип Photon.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-121">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="cb0ee-122">Затем присвойте ему имя.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-122">Then give it a name.</span></span> <span data-ttu-id="cb0ee-123">В этом примере мы назвали IT Хололенсфотонпрожект.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-123">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="cb0ee-124">По завершении нажмите кнопку Создать.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-124">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="cb0ee-126">После этого вернитесь на страницу приложения, и вы увидите примерно следующее изображение.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-126">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="cb0ee-127">Щелкните идентификатор приложения и скопируйте его.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-127">Click on the application ID and copy it.</span></span> <span data-ttu-id="cb0ee-128">Вставьте его в любом месте, к которому вы можете легко получить доступ.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-128">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="cb0ee-130">Создайте новый проект Unity и назовите его Хлшарингпрожект.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-130">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="cb0ee-131">Инструкции по созданию нового проекта Unity см. в [разделе "Создание проекта Unity" базового модуля](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="cb0ee-131">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="cb0ee-132">После загрузки проекта перейдите на вкладку Asset Store (ресурсы магазина), как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-132">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="cb0ee-133">Затем в поле поиска, выделенном на изображении ниже, введите шутка и в результатах поиска выберите ресурс Photon шутка 2 (бесплатный).</span><span class="sxs-lookup"><span data-stu-id="cb0ee-133">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="cb0ee-135">Скачайте и импортируйте этот ресурс, нажав кнопку Скачать и импортировать.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-135">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="cb0ee-137">После завершения процесса импорта Photon появится мастер шутка.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-137">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="cb0ee-138">Возьмите идентификатор приложения (который должен находиться в буфере обмена) из шага 4, вставьте его в поле AppID и нажмите кнопку проект установки.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-138">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="cb0ee-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="cb0ee-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="cb0ee-140">После успешного добавления AppID перейдите в раздел Photon-> Фотонунитинетворкинг-> Resources-> Фотонсерверсеттингс in Assets.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-140">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="cb0ee-141">Выберите параметр использовать сервер имен и задайте для параметра фиксированный регион значение US или регион службы Photon.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-141">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="cb0ee-143">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="cb0ee-143">Congratulations</span></span>

<span data-ttu-id="cb0ee-144">Вы успешно создали учетную запись Photon, настроили локальный сервер Photon и импортировали шутка в Unity.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-144">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="cb0ee-145">Следующим шагом является настройка проекта и последующее разрешение подключения с другими пользователями, чтобы несколько пользователей могли видеть вашу работу.</span><span class="sxs-lookup"><span data-stu-id="cb0ee-145">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="cb0ee-146">[Следующий учебник: 2. Подготовка Unity к работе](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="cb0ee-146">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

