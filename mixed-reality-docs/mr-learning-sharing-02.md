---
title: Руководства по многопользовательским возможностям, часть 2. Настройка Photon Unity Networking
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: ed55d1f84db7ee8dc33f0f738de2b6b98a305fd3
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376406"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="49c9d-105">2. Настройка Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="49c9d-105">2. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="49c9d-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="49c9d-106">Overview</span></span>

<span data-ttu-id="49c9d-107">В этом учебнике показано, как подготовиться к созданию совместного взаимодействия с помощью Photon Unity Networking (PUN).</span><span class="sxs-lookup"><span data-stu-id="49c9d-107">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="49c9d-108">Вы узнаете, как создать приложение PUN, импортировать активы PUN в проект Unity и подключить проект Unity к приложению PUN.</span><span class="sxs-lookup"><span data-stu-id="49c9d-108">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="49c9d-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="49c9d-109">Objectives</span></span>

* <span data-ttu-id="49c9d-110">Узнать, как создать приложение PUN.</span><span class="sxs-lookup"><span data-stu-id="49c9d-110">Learn how to create a PUN app</span></span>
* <span data-ttu-id="49c9d-111">Узнать, как найти и импортировать активы PUN.</span><span class="sxs-lookup"><span data-stu-id="49c9d-111">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="49c9d-112">Узнать, как подключить проект Unity к приложению PUN.</span><span class="sxs-lookup"><span data-stu-id="49c9d-112">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="49c9d-113">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="49c9d-113">Creating and preparing the Unity project</span></span>

<span data-ttu-id="49c9d-114">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="49c9d-114">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="49c9d-115">Для этого сначала выполните инструкции из руководства [Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md) (исключая раздел [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2)), в том числе следующие действия:</span><span class="sxs-lookup"><span data-stu-id="49c9d-115">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="49c9d-116">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="49c9d-116">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="49c9d-117">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="49c9d-117">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="49c9d-118">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="49c9d-118">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="49c9d-119">Импорт набора средств для Смешанной реальности (MRTK).</span><span class="sxs-lookup"><span data-stu-id="49c9d-119">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="49c9d-120">Настройка проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="49c9d-120">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="49c9d-121">[Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей понятного имени, например *MultiUserCapabilities*.</span><span class="sxs-lookup"><span data-stu-id="49c9d-121">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="49c9d-122">Затем выполните инструкции из раздела [Изменение параметра отображения отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option):</span><span class="sxs-lookup"><span data-stu-id="49c9d-122">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="49c9d-123">Измените **профиль конфигурации MRTK** на **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="49c9d-123">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="49c9d-124">Измените **параметры отображения сетки отслеживания пространственного положения** на **Occlusion** (Загораживание).</span><span class="sxs-lookup"><span data-stu-id="49c9d-124">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="49c9d-125">Включение дополнительных возможностей</span><span class="sxs-lookup"><span data-stu-id="49c9d-125">Enabling additional capabilities</span></span>

<span data-ttu-id="49c9d-126">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player** >  **Publishing Settings** (Проигрыватель > Параметры публикации).</span><span class="sxs-lookup"><span data-stu-id="49c9d-126">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="49c9d-128">В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient**, **Microphone**, **SpatialPerception** и **GazeInput**, которые вы включили при выполнении шага [Настройка проекта Unity](mr-learning-base-02.md#configuring-the-unity-project) ранее.</span><span class="sxs-lookup"><span data-stu-id="49c9d-128">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="49c9d-129">Затем включите следующие дополнительные возможности:</span><span class="sxs-lookup"><span data-stu-id="49c9d-129">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="49c9d-130">возможность **InternetClientServer**;</span><span class="sxs-lookup"><span data-stu-id="49c9d-130">**InternetClientServer** capability</span></span>
* <span data-ttu-id="49c9d-131">возможность **PrivateNetworkClientServer**.</span><span class="sxs-lookup"><span data-stu-id="49c9d-131">**PrivateNetworkClientServer** capability</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="49c9d-133">Установка встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="49c9d-133">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="49c9d-134">В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.</span><span class="sxs-lookup"><span data-stu-id="49c9d-134">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="49c9d-136">Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.</span><span class="sxs-lookup"><span data-stu-id="49c9d-136">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="49c9d-137">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="49c9d-137">Importing the tutorial assets</span></span>

<span data-ttu-id="49c9d-138">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="49c9d-138">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="49c9d-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (версия 2.2.1);</span><span class="sxs-lookup"><span data-stu-id="49c9d-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* <span data-ttu-id="49c9d-140">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="49c9d-140">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)</span></span>
* <span data-ttu-id="49c9d-141">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="49c9d-141">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)</span></span>
* <span data-ttu-id="49c9d-142">[MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="49c9d-142">[MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)</span></span>

<span data-ttu-id="49c9d-143">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="49c9d-143">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="49c9d-145">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт набора средств для Смешанной реальности](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="49c9d-145">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="49c9d-146">После импорта пакета учебных активов MultiUserCapabilities в окне консоли появятся несколько ошибок [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246). Они указывают на отсутствие типа или пространства имен.</span><span class="sxs-lookup"><span data-stu-id="49c9d-146">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="49c9d-147">Это ожидаемое поведение, и ошибки будут устранены при работе со следующим разделом при импорте активов PUN.</span><span class="sxs-lookup"><span data-stu-id="49c9d-147">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="49c9d-148">Импорт активов PUN</span><span class="sxs-lookup"><span data-stu-id="49c9d-148">Importing the PUN assets</span></span>

<span data-ttu-id="49c9d-149">В меню Unity последовательно выберите **Window** > **Asset Store** (Окно > Asset Store), чтобы открыть окно Asset Store. Найдите и выберите актив **PUN 2 — FREE** от Exit Games, а затем нажмите кнопку **Download** (Скачать), чтобы скачать пакет активов в учетную запись Unity.</span><span class="sxs-lookup"><span data-stu-id="49c9d-149">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="49c9d-150">После скачивания нажмите кнопку **Импорт**, чтобы открыть окно Import Unity Package (Импорт пакета Unity).</span><span class="sxs-lookup"><span data-stu-id="49c9d-150">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="49c9d-152">В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="49c9d-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="49c9d-154">Когда в Unity завершится процесс импорта, появится окно мастера PUN с открытым меню PUN Setup (Настройка PUN). На данный момент вы можете проигнорировать или закрыть это окно.</span><span class="sxs-lookup"><span data-stu-id="49c9d-154">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="49c9d-156">Создание приложения PUN</span><span class="sxs-lookup"><span data-stu-id="49c9d-156">Creating the PUN application</span></span>

<span data-ttu-id="49c9d-157">В этом разделе показано, как создать учетную запись Photon, если у вас ее еще нет, а также приложение PUN.</span><span class="sxs-lookup"><span data-stu-id="49c9d-157">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="49c9d-158">Перейдите на <a href="https://dashboard.photonengine.com/account/signin" target="_blank">панель мониторинга</a> Photon и войдите в систему, если у вас уже есть учетная запись, которую вы хотите использовать. В противном случае щелкните ссылку **Создать** и следуйте инструкциям, чтобы зарегистрировать новую учетную запись.</span><span class="sxs-lookup"><span data-stu-id="49c9d-158">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="49c9d-160">После входа нажмите кнопку **Создать приложение**.</span><span class="sxs-lookup"><span data-stu-id="49c9d-160">Once signed in, click the **Create a New App** button:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="49c9d-162">На странице создания приложения введите приведенные ниже значения.</span><span class="sxs-lookup"><span data-stu-id="49c9d-162">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="49c9d-163">В раскрывающемся списке Photon Type (Тип Photon) выберите PUN.</span><span class="sxs-lookup"><span data-stu-id="49c9d-163">For Photon Type, select PUN</span></span>
* <span data-ttu-id="49c9d-164">В поле "Имя" введите подходящее имя, например _MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="49c9d-164">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="49c9d-165">В поле "Описание" можно ввести описание (необязательно).</span><span class="sxs-lookup"><span data-stu-id="49c9d-165">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="49c9d-166">Поле "URL-адрес" оставьте пустым.</span><span class="sxs-lookup"><span data-stu-id="49c9d-166">For Url, leave the field empty</span></span>

<span data-ttu-id="49c9d-167">Затем нажмите кнопку **Create** (Создать), чтобы создать приложение.</span><span class="sxs-lookup"><span data-stu-id="49c9d-167">Then click the **Create** button to create the new app:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="49c9d-169">Когда Photon завершит процесс создания, на панели мониторинга появится новое приложение PUN.</span><span class="sxs-lookup"><span data-stu-id="49c9d-169">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="49c9d-171">Подключение проекта Unity к приложению PUN</span><span class="sxs-lookup"><span data-stu-id="49c9d-171">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="49c9d-172">В этом разделе показано, как подключить проект Unity к приложению PUN, которое вы создали при работе с предыдущим разделом.</span><span class="sxs-lookup"><span data-stu-id="49c9d-172">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="49c9d-173">На панели мониторинга Photon щелкните поле **ИД приложения**, чтобы отобразить идентификатор приложения, а затем скопируйте его в буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="49c9d-173">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="49c9d-175">В меню Unity последовательно выберите **Window** > **Photon Unity Networking** > **PUN Wizard** (Окно > Photon Unity Networking > Мастер PUN), чтобы открыть окно мастера PUN. Затем нажмите кнопку **Проект установки**, чтобы открыть меню PUN Setup (Настройка PUN), и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="49c9d-175">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="49c9d-176">В поле **AppId or Email** (Идентификатор приложения или адрес электронной почты) вставьте идентификатор приложения PUN, скопированный на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="49c9d-176">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="49c9d-177">Затем нажмите кнопку **Проект установки**, чтобы применить идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="49c9d-177">Then click the **Setup Project** button to apply the app ID:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="49c9d-179">Когда в Unity завершится процесс настройки PUN, в меню PUN Setup (Настройка PUN) появится сообщение **Готово!**</span><span class="sxs-lookup"><span data-stu-id="49c9d-179">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="49c9d-180">В окне Project (Проект) будет автоматически выбран актив **PhotonServerSettings**, чтобы в окне Inspector (Инспектор) отображались его свойства.</span><span class="sxs-lookup"><span data-stu-id="49c9d-180">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="49c9d-182">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="49c9d-182">Congratulations</span></span>

<span data-ttu-id="49c9d-183">Вы успешно создали приложение PUN и подключили его к проекту Unity.</span><span class="sxs-lookup"><span data-stu-id="49c9d-183">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="49c9d-184">Следующим шагом будет разрешение подключений для других пользователей, чтобы несколько пользователей могли видеть работу друг друга.</span><span class="sxs-lookup"><span data-stu-id="49c9d-184">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

[<span data-ttu-id="49c9d-185">Следующее руководство: 3. Подключение нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="49c9d-185">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)
