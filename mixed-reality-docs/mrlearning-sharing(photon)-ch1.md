---
title: Руководства по многопользовательским возможностям, часть 1. Настройка Photon Unity Networking
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610797"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="1396e-105">1. Настройка Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="1396e-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="1396e-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="1396e-106">Overview</span></span>

<span data-ttu-id="1396e-107">В этом учебнике вы узнаете, как подготовиться к созданию возможностей для совместного взаимодействия с помощью Photon Unity Networking (PUN).</span><span class="sxs-lookup"><span data-stu-id="1396e-107">In this tutorial, you will learn how to prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="1396e-108">Photon — это одна из нескольких сетевых платформ, на основе которых разработчики смешанной реальности могут создавать возможности для совместного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1396e-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="1396e-109">Вы узнаете, как создать приложение Photon PUN, импортировать активы Photon PUN в проект Unity и подключить проект Unity к приложению Photon PUN.</span><span class="sxs-lookup"><span data-stu-id="1396e-109">You will learn how to create a Photon PUN application, import Photon PUN assets into your Unity project, and connect your Unity project to the Photon PUN application.</span></span>

## <a name="objectives"></a><span data-ttu-id="1396e-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="1396e-110">Objectives</span></span>

* <span data-ttu-id="1396e-111">Вы научитесь создавать приложение Photon PUN.</span><span class="sxs-lookup"><span data-stu-id="1396e-111">Learn how to create a Photon PUN application</span></span>
* <span data-ttu-id="1396e-112">Вы узнаете, как найти и импортировать активы Photon PUN.</span><span class="sxs-lookup"><span data-stu-id="1396e-112">Learn how to find and import the Photon PUN assets</span></span>
* <span data-ttu-id="1396e-113">Вы узнаете, как подключить проект Unity к приложению Photon PUN.</span><span class="sxs-lookup"><span data-stu-id="1396e-113">Learn how to connect your Unity project to the Photon PUN application</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1396e-114">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="1396e-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="1396e-115">Если вы еще не прошли учебники по [началу работы](mrlearning-base.md) или по [Пространственным привязкам Azure](mrlearning-asa-ch1.md), мы рекомендуем начать знакомство именно с этих серий.</span><span class="sxs-lookup"><span data-stu-id="1396e-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="1396e-116">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1396e-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="1396e-117">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="1396e-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="1396e-118">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="1396e-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="1396e-119">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="1396e-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="1396e-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="1396e-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="1396e-121">Выполните инструкции из раздела [Создание ресурса Пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) в статье [Краткое руководство. Создание приложения Unity HoloLens, которое использует Пространственные привязки Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="1396e-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1396e-122">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="1396e-122">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="1396e-123">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="1396e-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="1396e-124">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="1396e-124">Creating and preparing the Unity project</span></span>

<span data-ttu-id="1396e-125">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="1396e-125">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="1396e-126">Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mrlearning-base-ch1.md), за исключением раздела [Разработка приложения для устройства](mrlearning-base-ch1.md#build-your-application-to-your-device), то есть следующие действия:</span><span class="sxs-lookup"><span data-stu-id="1396e-126">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="1396e-127">[Создайте новый проект Unity](mrlearning-base-ch1.md#create-new-unity-project) и присвойте ему понятное имя, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="1396e-127">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. <span data-ttu-id="1396e-128">[Настройте проект Unity для Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="1396e-128">[Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)</span></span>

3. <span data-ttu-id="1396e-129">[Импортируйте требуемые ресурсы TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources).</span><span class="sxs-lookup"><span data-stu-id="1396e-129">[Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)</span></span>

4. <span data-ttu-id="1396e-130">[Импортируйте Набор средств для смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="1396e-130">[Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)</span></span>

5. <span data-ttu-id="1396e-131">[Настройте проект Unity для Набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="1396e-131">[Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)</span></span>

6. <span data-ttu-id="1396e-132">[Добавьте Набор средств для смешанной реальности к сцене Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) и присвойте этой сцене понятное имя, например *MultiUserCapabilities*.</span><span class="sxs-lookup"><span data-stu-id="1396e-132">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="1396e-133">Затем следуйте инструкциям [по настройке профилей Набора средств для смешанной реальности (изменение параметра отображения сведений о пространственном состоянии)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option), чтобы указать для сцены профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** и значение **Перекрытие** для метода отображения сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="1396e-133">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="1396e-134">Как описано в инструкции по [настройке проекта Unity для Набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), ссылка на которую предложена выше, мы настоятельно рекомендуем не включать MSBuild для Unity.</span><span class="sxs-lookup"><span data-stu-id="1396e-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="1396e-135">Настройка функциональных возможностей</span><span class="sxs-lookup"><span data-stu-id="1396e-135">Configuring the capabilities</span></span>

<span data-ttu-id="1396e-136">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player** >  **Publishing Settings** (Проигрыватель > Параметры публикации).</span><span class="sxs-lookup"><span data-stu-id="1396e-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

<span data-ttu-id="1396e-138">В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient** (Интернет-клиент), **Microphone** (Микрофон) и **SpatialPerception** (Пространственное восприятие), которые вы включили при создании проекта в начале работы с этим руководством.</span><span class="sxs-lookup"><span data-stu-id="1396e-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="1396e-139">Теперь включите возможности **InternetClientServer**, **PrivateNetworkClientServer** и **RemovableStorage**:</span><span class="sxs-lookup"><span data-stu-id="1396e-139">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **RemovableStorage** capabilities:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="1396e-141">Добавление встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="1396e-141">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="1396e-142">В рамках этого раздела вы установите встроенный пакет AR Foundation для Unity, который необходим для пакета SDK Пространственных привязок Azure, который вы будете импортировать в рамках следующей части руководства.</span><span class="sxs-lookup"><span data-stu-id="1396e-142">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="1396e-143">В меню Unity последовательно выберите **Window** > **Диспетчер пакетов**:</span><span class="sxs-lookup"><span data-stu-id="1396e-143">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="1396e-145">Может пройти несколько секунд, прежде чем пакет AR Foundation появится в списке.</span><span class="sxs-lookup"><span data-stu-id="1396e-145">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="1396e-146">В окне диспетчера пакетов выберите **AR Foundation** и установите этот пакет, щелкнув кнопку **Установить**:</span><span class="sxs-lookup"><span data-stu-id="1396e-146">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="1396e-148">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="1396e-148">Importing the tutorial assets</span></span>

<span data-ttu-id="1396e-149">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="1396e-149">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="1396e-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (версия 2.1.1);</span><span class="sxs-lookup"><span data-stu-id="1396e-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="1396e-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="1396e-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="1396e-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="1396e-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [<span data-ttu-id="1396e-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="1396e-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="1396e-154">Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="1396e-154">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="1396e-155">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="1396e-155">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="1396e-157">После импорта пакета учебных активов MultiUserCapabilities в окне консоли появятся несколько ошибок [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246). Они указывают на отсутствие типа или пространства имен.</span><span class="sxs-lookup"><span data-stu-id="1396e-157">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="1396e-158">Этих проблем следовало ожидать, инструкции по их устранению будут приведены в следующем разделе при импорте активов Photon.</span><span class="sxs-lookup"><span data-stu-id="1396e-158">This is to be expected and will be resolved in the next section when you import the Photon assets.</span></span>

## <a name="importing-the-photon-assets"></a><span data-ttu-id="1396e-159">Импорт активов Photon</span><span class="sxs-lookup"><span data-stu-id="1396e-159">Importing the Photon assets</span></span>

<span data-ttu-id="1396e-160">В рамках этого раздела вы импортируете активы Photon Unity Network (PUN) из портала Asset Store в Unity.</span><span class="sxs-lookup"><span data-stu-id="1396e-160">In this section, you will import the Photon Unity Network (PUN) assets from Unity's Asset Store.</span></span>

<span data-ttu-id="1396e-161">В меню Unity последовательно выберите **Window** > **Asset Store** (Окно > Asset Store), чтобы открыть окно Asset Store. Найдите и выберите актив **PUN 2 — FREE** от Exit Games, а затем нажмите кнопку **Скачать**, чтобы скачать пакет активов в учетную запись Unity:</span><span class="sxs-lookup"><span data-stu-id="1396e-161">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, and then click the **Download** button to download the asset package to your Unity account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

<span data-ttu-id="1396e-163">После скачивания нажмите кнопку **Импорт**, чтобы открыть окно Import Unity Package (Импорт пакета Unity).</span><span class="sxs-lookup"><span data-stu-id="1396e-163">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

<span data-ttu-id="1396e-165">В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="1396e-165">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

<span data-ttu-id="1396e-167">Когда в Unity завершится процесс импорта, появится окно мастера PUN с открытым меню PUN Setup (Настройка PUN). На данный момент вы можете проигнорировать или закрыть это окно.</span><span class="sxs-lookup"><span data-stu-id="1396e-167">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a><span data-ttu-id="1396e-169">Настройка Photon</span><span class="sxs-lookup"><span data-stu-id="1396e-169">Setting up Photon</span></span>

<span data-ttu-id="1396e-170">В рамках этого раздела вы создадите учетную запись Photon, если у вас ее еще нет, а также создадите приложение PUN.</span><span class="sxs-lookup"><span data-stu-id="1396e-170">In this section, you will create a Photon account, if you don't already have one, and create a new PUN application.</span></span>

<span data-ttu-id="1396e-171">Перейдите на <a href="https://dashboard.photonengine.com/account/signin" target="_blank">панель мониторинга</a> Photon и войдите в систему, если у вас уже есть учетная запись, которую вы хотите использовать. В противном случае щелкните ссылку **Создать** и следуйте инструкциям, чтобы зарегистрировать новую учетную запись.</span><span class="sxs-lookup"><span data-stu-id="1396e-171">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

<span data-ttu-id="1396e-173">После входа нажмите кнопку **Создать приложение**.</span><span class="sxs-lookup"><span data-stu-id="1396e-173">Once signed in, click the **Create a New App** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

<span data-ttu-id="1396e-175">На странице создания приложения введите приведенные ниже значения.</span><span class="sxs-lookup"><span data-stu-id="1396e-175">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="1396e-176">В раскрывающемся списке Photon Type (Тип Photon) выберите Photon PUN.</span><span class="sxs-lookup"><span data-stu-id="1396e-176">For Photon Type, select Photon PUN</span></span>
* <span data-ttu-id="1396e-177">В поле "Имя" введите подходящее имя, например _MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="1396e-177">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="1396e-178">В поле "Описание" можно ввести описание (необязательно).</span><span class="sxs-lookup"><span data-stu-id="1396e-178">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="1396e-179">Поле "URL-адрес" оставьте пустым.</span><span class="sxs-lookup"><span data-stu-id="1396e-179">For Url, leave the field empty</span></span>

<span data-ttu-id="1396e-180">Затем нажмите кнопку **Создать**, чтобы создать приложение.</span><span class="sxs-lookup"><span data-stu-id="1396e-180">Then click the **Create** button to create the new application:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

<span data-ttu-id="1396e-182">Когда процесс создания завершится, на панели мониторинга появится новое приложение PUN.</span><span class="sxs-lookup"><span data-stu-id="1396e-182">Once Photon has finished the creation process, the new PUN application will appear on your dashboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="1396e-184">Подключение проекта Unity к приложению PUN</span><span class="sxs-lookup"><span data-stu-id="1396e-184">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="1396e-185">В рамках этого раздела вы подключите проект Unity к приложению PUN, которое вы создали в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="1396e-185">In this section, you will connect your Unity project to the PUN application you created in the previous section.</span></span>

<span data-ttu-id="1396e-186">На панели мониторинга Photon щелкните поле **ИД приложения**, чтобы отобразить идентификатор приложения, а затем скопируйте его в буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="1396e-186">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

<span data-ttu-id="1396e-188">В меню Unity последовательно выберите **Window** > **Photon Unity Networking** > **PUN Wizard** (Окно > Photon Unity Networking > Мастер PUN), чтобы открыть окно мастера PUN. Затем нажмите кнопку **Проект установки**, чтобы открыть меню PUN Setup (Настройка PUN), и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="1396e-188">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="1396e-189">В поле **AppId or Email** (Идентификатор приложения или адрес электронной почты) вставьте идентификатор приложения PUN, скопированный на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="1396e-189">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="1396e-190">Затем нажмите кнопку **Проект установки**, чтобы применить идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="1396e-190">Then click the **Setup Project** button to apply the app ID:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

<span data-ttu-id="1396e-192">Когда в Unity завершится процесс настройки PUN, в меню PUN Setup (Настройка PUN) появится сообщение **Готово!**</span><span class="sxs-lookup"><span data-stu-id="1396e-192">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="1396e-193">и в окне проекта будет автоматически выбран актив **PhotonServerSettings**, чтобы в окне "Инспектор" отображались его свойства.</span><span class="sxs-lookup"><span data-stu-id="1396e-193">and automatically select the **PhotonServerSettings** asset in the Project window so its properties are displayed in the Inspector window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="1396e-195">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="1396e-195">Congratulations</span></span>

<span data-ttu-id="1396e-196">Вы успешно создали приложение Photon PUN и подключили его к проекту Unity.</span><span class="sxs-lookup"><span data-stu-id="1396e-196">You have successfully created a Photon PUN application and connected it to your Unity project.</span></span> <span data-ttu-id="1396e-197">Следующим шагом будет разрешение подключений для других пользователей, чтобы несколько пользователей могли видеть работу друг друга.</span><span class="sxs-lookup"><span data-stu-id="1396e-197">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

<span data-ttu-id="1396e-198">[Следующее руководство: 2. Подключение нескольких пользователей](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="1396e-198">[Next tutorial: 2. Connecting multiple users](mrlearning-sharing(photon)-ch2.md)</span></span>
