---
title: Руководства по многопользовательским возможностям, часть 1. Настройка Photon Unity Networking
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031329"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="e9085-105">1. Настройка Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="e9085-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="e9085-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="e9085-106">Overview</span></span>

<span data-ttu-id="e9085-107">В этом руководстве вы узнаете, как подготовиться к созданию совместного взаимодействия, импортировав Photon Unity Networking (PUN) в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="e9085-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="e9085-108">Photon — это одна из нескольких сетевых платформ, на основе которых разработчики смешанной реальности могут создавать возможности для совместного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="e9085-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="e9085-109">Здесь вы узнаете, как создать учетную запись Photon, импортировать Photon и создать (необязательно) локальный сервер.</span><span class="sxs-lookup"><span data-stu-id="e9085-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="e9085-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="e9085-110">Objectives</span></span>

* <span data-ttu-id="e9085-111">Вы научитесь создавать учетную запись Photon.</span><span class="sxs-lookup"><span data-stu-id="e9085-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="e9085-112">Вы узнаете, как найти и импортировать Photon Unity Networking.</span><span class="sxs-lookup"><span data-stu-id="e9085-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="e9085-113">Вы настроите сервер Photon.</span><span class="sxs-lookup"><span data-stu-id="e9085-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e9085-114">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="e9085-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="e9085-115">Если вы еще не прошли учебники [по началу работы](mrlearning-base.md) или [по началу работы с Пространственными привязками Azure](mrlearning-asa-ch1.md), мы рекомендуем начать знакомство именно с этих серий.</span><span class="sxs-lookup"><span data-stu-id="e9085-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="e9085-116">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="e9085-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="e9085-117">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="e9085-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="e9085-118">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="e9085-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="e9085-119">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="e9085-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="e9085-120">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="e9085-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="e9085-121">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="e9085-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="e9085-122">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="e9085-122">Setting up Photon</span></span>

1. <span data-ttu-id="e9085-123">Создайте учетную запись [Photon](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="e9085-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="e9085-124">Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="e9085-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="e9085-125">На странице регистрации следуйте инструкциям по созданию учетной записи.</span><span class="sxs-lookup"><span data-stu-id="e9085-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="e9085-128">Создайте идентификатор приложения, нажав кнопку Create a New App (Создать новое приложение).</span><span class="sxs-lookup"><span data-stu-id="e9085-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="e9085-130">Выберите PUN для Photon в раскрывающемся списке Photon Type (Тип Photon).</span><span class="sxs-lookup"><span data-stu-id="e9085-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="e9085-131">Присвойте любое имя.</span><span class="sxs-lookup"><span data-stu-id="e9085-131">Then give it a name.</span></span> <span data-ttu-id="e9085-132">В нашем примере это имя HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="e9085-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="e9085-133">Завершив эти действия, нажмите кнопку Create (Создать).</span><span class="sxs-lookup"><span data-stu-id="e9085-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="e9085-135">Вернитесь на страницу приложений, и вы увидите примерно следующее изображение.</span><span class="sxs-lookup"><span data-stu-id="e9085-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="e9085-136">Щелкните идентификатор приложения и скопируйте его.</span><span class="sxs-lookup"><span data-stu-id="e9085-136">Click the application ID and copy it.</span></span> <span data-ttu-id="e9085-137">Вставьте его куда-либо, где потом сможете легко его получить.</span><span class="sxs-lookup"><span data-stu-id="e9085-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="e9085-139">Создайте новый проект Unity и присвойте ему имя HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="e9085-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="e9085-140">Инструкции по созданию проекта Unity см. в разделе [Create Unity Project](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project) (Создание проекта Unity) базового модуля.</span><span class="sxs-lookup"><span data-stu-id="e9085-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="e9085-141">После загрузки проекта перейдите на вкладку Assets Store (Хранилище активов), как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="e9085-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="e9085-142">Затем в поле поиска, которое выделено на изображении ниже, введите значение PUN и в результатах поиска выберите актив "Photon PUN 2 - FREE".</span><span class="sxs-lookup"><span data-stu-id="e9085-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="e9085-144">Скачайте и импортируйте этот актив, нажав кнопки Download (Скачивание) и Import (Импорт).</span><span class="sxs-lookup"><span data-stu-id="e9085-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="e9085-146">Когда процесс импорта Photon завершится, откроется мастер PUN.</span><span class="sxs-lookup"><span data-stu-id="e9085-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="e9085-147">Возьмите идентификатор приложения из шага 4 (он должен находиться в буфере обмена), вставьте его в поле AppID и нажмите кнопку Setup Project (Настроить проект).</span><span class="sxs-lookup"><span data-stu-id="e9085-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="e9085-149">После успешного добавления AppID перейдите в списке активов к разделу Photon >PhotonUnityNetworking ->Resources (Ресурсы)->PhotonServerSettings.</span><span class="sxs-lookup"><span data-stu-id="e9085-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="e9085-150">Выберите вариант Use Name Server (Использовать сервер имен) и задайте фиксированный регион "США" или регион вашей службы Photon.</span><span class="sxs-lookup"><span data-stu-id="e9085-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="e9085-152">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="e9085-152">Congratulations</span></span>

<span data-ttu-id="e9085-153">Вы успешно создали учетную запись Photon, настроили локальный сервер Photon и импортировали PUN в Unity.</span><span class="sxs-lookup"><span data-stu-id="e9085-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="e9085-154">Следующим шагом будет настройка проекта и разрешение подключений для других пользователей, чтобы вашу работу могли видеть несколько пользователей.</span><span class="sxs-lookup"><span data-stu-id="e9085-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="e9085-155">[Следующее руководство: 2. Подготовка Unity к работе](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="e9085-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
