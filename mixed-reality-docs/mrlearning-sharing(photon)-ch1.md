---
title: Учебники по возможностям для нескольких пользователей — 1. Настройка сети Unity Photon
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 57a23e34404e4bff653d74b7f6afc65adff8b19c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334331"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="0e06f-105">1. Настройка сети Unity Photon</span><span class="sxs-lookup"><span data-stu-id="0e06f-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="0e06f-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="0e06f-106">Overview</span></span>

<span data-ttu-id="0e06f-107">В этом руководстве вы узнаете, как подготовиться к созданию общего интерфейса, импортировав Photon Unity Networking (шутка) в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="0e06f-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="0e06f-108">Photon — это один из нескольких сетевых возможностей, доступных разработчикам смешанной реальности для создания общих возможностей.</span><span class="sxs-lookup"><span data-stu-id="0e06f-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="0e06f-109">Вы узнаете, как создать учетную запись Photon, импортировать Photon и создать необязательный локальный сервер.</span><span class="sxs-lookup"><span data-stu-id="0e06f-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="0e06f-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="0e06f-110">Objectives</span></span>

* <span data-ttu-id="0e06f-111">Узнайте, как создать учетную запись Photon.</span><span class="sxs-lookup"><span data-stu-id="0e06f-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="0e06f-112">Узнайте, как найти и импортировать сеть Unity Photon</span><span class="sxs-lookup"><span data-stu-id="0e06f-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="0e06f-113">Настройка локального сервера Photon</span><span class="sxs-lookup"><span data-stu-id="0e06f-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0e06f-114">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="0e06f-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="0e06f-115">Если вы еще не выполнили серию [учебников по началу работы](mrlearning-base.md) , рекомендуется сначала выполнить эти учебники.</span><span class="sxs-lookup"><span data-stu-id="0e06f-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="0e06f-116">КОМПЬЮТЕР с Windows 10 с [установленными](install-the-tools.md) правильными инструментами</span><span class="sxs-lookup"><span data-stu-id="0e06f-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="0e06f-117">Windows 10 SDK 10.0.18362.0 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="0e06f-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="0e06f-118">Некоторые базовые C# возможности программирования</span><span class="sxs-lookup"><span data-stu-id="0e06f-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="0e06f-119">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="0e06f-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
><span data-ttu-id="0e06f-120">Для этой серии руководств требуется <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019,1</a> , а рекомендуемая версия — Unity 2019.1.14.</span><span class="sxs-lookup"><span data-stu-id="0e06f-120">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="0e06f-121">Это заменяет все требования к версии Unity или рекомендации, указанные в связанных выше условиях.</span><span class="sxs-lookup"><span data-stu-id="0e06f-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="0e06f-122">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="0e06f-122">Setting up Photon</span></span>

1. <span data-ttu-id="0e06f-123">Настройте учетную запись [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="0e06f-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="0e06f-124">Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="0e06f-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="0e06f-125">Чтобы создать учетную запись, следуйте инструкциям на странице регистрации.</span><span class="sxs-lookup"><span data-stu-id="0e06f-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="0e06f-128">Создайте идентификатор приложения, нажав кнопку Создать новое приложение.</span><span class="sxs-lookup"><span data-stu-id="0e06f-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="0e06f-130">Выберите Photon шутка в раскрывающемся меню в разделе Тип Photon.</span><span class="sxs-lookup"><span data-stu-id="0e06f-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="0e06f-131">Затем присвойте ему имя.</span><span class="sxs-lookup"><span data-stu-id="0e06f-131">Then give it a name.</span></span> <span data-ttu-id="0e06f-132">В этом примере мы назвали IT Хололенсфотонпрожект.</span><span class="sxs-lookup"><span data-stu-id="0e06f-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="0e06f-133">По завершении нажмите кнопку Создать.</span><span class="sxs-lookup"><span data-stu-id="0e06f-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="0e06f-135">Вернитесь на страницу приложений, и вы увидите примерно следующее изображение.</span><span class="sxs-lookup"><span data-stu-id="0e06f-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="0e06f-136">Щелкните идентификатор приложения и скопируйте его.</span><span class="sxs-lookup"><span data-stu-id="0e06f-136">Click the application ID and copy it.</span></span> <span data-ttu-id="0e06f-137">Вставьте его в любом месте, к которому вы можете легко получить доступ.</span><span class="sxs-lookup"><span data-stu-id="0e06f-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="0e06f-139">Создайте новый проект Unity и назовите его Хлшарингпрожект.</span><span class="sxs-lookup"><span data-stu-id="0e06f-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="0e06f-140">Инструкции по созданию нового проекта Unity см. в [разделе "Создание проекта Unity" базового модуля](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="0e06f-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="0e06f-141">После загрузки проекта перейдите на вкладку хранилище ресурсов, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="0e06f-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="0e06f-142">Затем в поле поиска, выделенном на изображении ниже, введите шутка и в результатах поиска выберите ресурс Photon шутка 2 (бесплатный).</span><span class="sxs-lookup"><span data-stu-id="0e06f-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="0e06f-144">Скачайте и импортируйте этот ресурс, нажав кнопку Скачать и импортировать.</span><span class="sxs-lookup"><span data-stu-id="0e06f-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="0e06f-146">После завершения процесса импорта Photon появится мастер шутка.</span><span class="sxs-lookup"><span data-stu-id="0e06f-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="0e06f-147">Возьмите идентификатор приложения (который должен находиться в буфере обмена) из шага 4, вставьте его в поле AppID и нажмите кнопку проект установки.</span><span class="sxs-lookup"><span data-stu-id="0e06f-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="0e06f-149">После успешного добавления AppID перейдите в раздел Photon-> Фотонунитинетворкинг-> Resources-> Фотонсерверсеттингс in Assets.</span><span class="sxs-lookup"><span data-stu-id="0e06f-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="0e06f-150">Выберите параметр использовать сервер имен и задайте для параметра фиксированный регион значение US или регион службы Photon.</span><span class="sxs-lookup"><span data-stu-id="0e06f-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="0e06f-152">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="0e06f-152">Congratulations</span></span>

<span data-ttu-id="0e06f-153">Вы успешно создали учетную запись Photon, настроили локальный сервер Photon и импортировали шутка в Unity.</span><span class="sxs-lookup"><span data-stu-id="0e06f-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="0e06f-154">Следующим шагом является настройка проекта и разрешение подключений с другими пользователями, чтобы несколько пользователей могли видеть вашу работу.</span><span class="sxs-lookup"><span data-stu-id="0e06f-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="0e06f-155">[Следующий учебник: 2. Подготовка Unity к разработке](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="0e06f-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
