---
title: Учебники по пространственной привязке Azure — 1. Приступая к работе с пространственными привязками Azure
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: e62d3626ec6f2dbf8b66378212afab7db2f56422
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334450"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="5851e-105">1. Приступая к работе с пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="5851e-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="5851e-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="5851e-106">Overview</span></span>

<span data-ttu-id="5851e-107">Добро пожаловать на второй ряд учебников по HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5851e-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="5851e-108">В этой серии руководств из трех частей вы узнаете об основах использования пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="5851e-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="5851e-109">В этом первом учебнике [Приступая к работе с пространственными привязками Azure](mrlearning-asa-ch1.md)вы узнаете о различных шагах, необходимых для запуска и завершения сеанса Azure, а также создания, отправки и скачивания привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="5851e-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="5851e-110">Во втором учебном курсе, [сохранении, извлечении и совместном использовании пространственных привязок Azure](mrlearning-asa-ch2.md)вы узнаете, как сохранять пространственные привязки Azure в нескольких сеансах приложения, сохраняя сведения о привязке в хранилище HoloLens 2 и совместное использование этих данных привязки с другими устройствами для выравнивания привязок на нескольких устройствах.</span><span class="sxs-lookup"><span data-stu-id="5851e-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="5851e-111">В третьем руководстве, в [котором отображается отзыв о пространственной привязке Azure](mrlearning-asa-ch3.md), вы узнаете, как предоставить пользователям Отзывы о событиях и состояниях привязки при использовании пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="5851e-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="5851e-112">Задачи</span><span class="sxs-lookup"><span data-stu-id="5851e-112">Objectives</span></span>

* <span data-ttu-id="5851e-113">Изучите основы разработки с помощью пространственных привязок Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5851e-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="5851e-114">Создание, передача и скачивание пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="5851e-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5851e-115">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="5851e-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="5851e-116">Если вы еще не выполнили серию [учебников по началу работы](mrlearning-base.md) , рекомендуется сначала выполнить эти учебники.</span><span class="sxs-lookup"><span data-stu-id="5851e-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="5851e-117">КОМПЬЮТЕР с Windows 10 с [установленными](install-the-tools.md) правильными инструментами</span><span class="sxs-lookup"><span data-stu-id="5851e-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="5851e-118">Windows 10 SDK 10.0.18362.0 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="5851e-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="5851e-119">Некоторые базовые C# возможности программирования</span><span class="sxs-lookup"><span data-stu-id="5851e-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="5851e-120">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="5851e-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="5851e-121">Выполните инструкции из раздела [Создание ресурса пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) в разделе [Краткое руководство. Создание приложения Unity HoloLens, использующего учебник по пространственным привязок Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .</span><span class="sxs-lookup"><span data-stu-id="5851e-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

>[!IMPORTANT]
><span data-ttu-id="5851e-122">Для этой серии руководств требуется <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019,1</a> , а рекомендуемая версия — Unity 2019.1.14.</span><span class="sxs-lookup"><span data-stu-id="5851e-122">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="5851e-123">Это заменяет все требования к версии Unity или рекомендации, указанные в связанных выше условиях.</span><span class="sxs-lookup"><span data-stu-id="5851e-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="5851e-124">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="5851e-124">Creating the Unity project</span></span>

<span data-ttu-id="5851e-125">В этом разделе вы создадите новый проект Unity и настроите его для Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5851e-125">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="5851e-126">Создайте проект Unity и присвойте ему подходящее имя, например, _учебник по пространственным привязок Azure_.</span><span class="sxs-lookup"><span data-stu-id="5851e-126">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="5851e-127">Настройка проекта Unity для Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5851e-127">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="5851e-128">Напоминание о том, как создать проект Unity и настроить его для Windows Mixed Reality, можно найти в разделах [Создание проекта Unity](mrlearning-base-ch1.md#create-new-unity-project) и [Настройка проекта Unity для Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) статьи [Инициализация проекта и первого приложения](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , которое является частью [руководства по началу работы](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="5851e-128">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="5851e-129">Добавление встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="5851e-129">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="5851e-130">В этом разделе вы добавите нестандартные активы и пакеты Unity, необходимые для набора средств и пакетов SDK, которые будут использоваться в проекте.</span><span class="sxs-lookup"><span data-stu-id="5851e-130">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="5851e-131">Импорт необходимых ресурсов TMP.</span><span class="sxs-lookup"><span data-stu-id="5851e-131">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="5851e-132">Мы добавляем этот пакет, так как он необходим для набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5851e-132">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="5851e-133">В меню Unity выберите пункт **окно** > **Текстмешпро** > **импортировать нужные ресурсы tmp**.</span><span class="sxs-lookup"><span data-stu-id="5851e-133">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="5851e-135">Во всплывающем окне Импорт пакета Unity сначала убедитесь, что выбраны все ресурсы, нажав кнопку **все** , а затем импортируйте ресурсы, нажав кнопку **Импорт** .</span><span class="sxs-lookup"><span data-stu-id="5851e-135">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="5851e-137">Установите AR Foundation.</span><span class="sxs-lookup"><span data-stu-id="5851e-137">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="5851e-138">Мы добавляем этот пакет, так как он требуется пакетом SDK для пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="5851e-138">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="5851e-139">В меню Unity выберите пункт **окно** > **Диспетчер пакетов**.</span><span class="sxs-lookup"><span data-stu-id="5851e-139">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="5851e-141">В окне Диспетчер пакетов выберите **AR Foundation** и установите пакет, нажав кнопку **установить** .</span><span class="sxs-lookup"><span data-stu-id="5851e-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="5851e-142">В списке появится пакет AR Foundation, который может занять несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="5851e-142">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="5851e-144">Импорт ресурсов учебника</span><span class="sxs-lookup"><span data-stu-id="5851e-144">Importing the tutorial assets</span></span>

<span data-ttu-id="5851e-145">В этом разделе вы скачиваете и импортируете все ресурсы учебника.</span><span class="sxs-lookup"><span data-stu-id="5851e-145">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="5851e-146">Скачайте ресурсы.</span><span class="sxs-lookup"><span data-stu-id="5851e-146">Download the assets.</span></span>

    * <span data-ttu-id="5851e-147">[Азуреспатиаланчорс. пакет unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (версия 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="5851e-147">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="5851e-148">Microsoft. Микседреалити. Toolkit. Unity. Foundation. 2.1.0. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="5851e-148">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="5851e-149">МРТК. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.1.0.1. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="5851e-149">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="5851e-150">МРТК. HoloLens2. Unity. Tutorials. Assets. Азуреспатиаланчорс. 2.1.0.1. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="5851e-150">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="5851e-151">Импортируйте ресурсы.</span><span class="sxs-lookup"><span data-stu-id="5851e-151">Import the assets.</span></span>

    <span data-ttu-id="5851e-152">В меню Unity выберите **активы** > **импортировать пакет** > **настраиваемый пакет..** ..</span><span class="sxs-lookup"><span data-stu-id="5851e-152">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="5851e-154">В пакете импорта... (всплывающее окно) выберите **азуреспатиаланчорс. пакет unitypackage** и нажмите кнопку **Открыть** .</span><span class="sxs-lookup"><span data-stu-id="5851e-154">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="5851e-156">Во всплывающем окне Импорт пакета Unity сначала убедитесь, что выбраны все ресурсы, нажав кнопку **все** , а затем импортируйте ресурсы, нажав кнопку **Импорт** .</span><span class="sxs-lookup"><span data-stu-id="5851e-156">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="5851e-158">Повторите эти действия, чтобы импортировать оставшиеся пакеты ресурсов.</span><span class="sxs-lookup"><span data-stu-id="5851e-158">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="5851e-159">По завершении в папке **Assets** проекта Unity должны содержаться эти вложенные папки.</span><span class="sxs-lookup"><span data-stu-id="5851e-159">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="5851e-161">Создание и подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="5851e-161">Creating and preparing the scene</span></span>

<span data-ttu-id="5851e-162">В этом разделе вы создадите и подготовите сцену, добавив набор средств для смешанной реальности и часть учебника Prefabs.</span><span class="sxs-lookup"><span data-stu-id="5851e-162">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="5851e-163">Создайте новую сцену.</span><span class="sxs-lookup"><span data-stu-id="5851e-163">Create a new scene.</span></span>

    <span data-ttu-id="5851e-164">В меню Unity выберите **файл** > **создать сцену**.</span><span class="sxs-lookup"><span data-stu-id="5851e-164">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="5851e-166">В меню Unity выберите **файл** > **Сохранить как...** .</span><span class="sxs-lookup"><span data-stu-id="5851e-166">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="5851e-168">Во всплывающем окне Сохранить сцену перейдите к папке **сцен** проекта, присвойте сцене подходящее имя, например _асатуториалсцене_, и сохраните сцену, нажав кнопку **сохранить** .</span><span class="sxs-lookup"><span data-stu-id="5851e-168">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="5851e-170">Вы можете сохранить сцену в любом месте, пока она находится внутри папки ресурсов проекта.</span><span class="sxs-lookup"><span data-stu-id="5851e-170">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="5851e-171">Однако, чтобы хранить проект в Организации, обычно рекомендуется сохранить его в папке «сцены» проекта.</span><span class="sxs-lookup"><span data-stu-id="5851e-171">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="5851e-172">Добавьте набор средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5851e-172">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="5851e-173">В меню Unity выберите **набор средств для смешанной реальности** > **Добавить в сцену и настроить...** .</span><span class="sxs-lookup"><span data-stu-id="5851e-173">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="5851e-175">Во всплывающем окне Выбор Микседреалититулкитконфигуратионпрофиле щелкните **DefaultHoloLens2ConfigurationProfile** , чтобы задать его в качестве профиля конфигурации мртк сцены.</span><span class="sxs-lookup"><span data-stu-id="5851e-175">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="5851e-177">В меню Unity выберите **файл** > **сохранить** , чтобы сохранить сцену.</span><span class="sxs-lookup"><span data-stu-id="5851e-177">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="5851e-179">Чтобы быстро сохранить сцену при работе с этим руководством, можно использовать сочетание клавиш CTRL + S (Command + S в macOS).</span><span class="sxs-lookup"><span data-stu-id="5851e-179">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="5851e-180">Добавьте учебник Prefabs.</span><span class="sxs-lookup"><span data-stu-id="5851e-180">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="5851e-181">На панели проект перейдите к разделу **активы** > **мртк. Учебник. Азуреспатиаланчорс** > **Prefabs** папку.</span><span class="sxs-lookup"><span data-stu-id="5851e-181">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="5851e-182">Удерживая нажатой кнопку CTRL (Command on macOS), щелкните **буттонпарент**, **DebugWindow**и **парентанчор** , чтобы выбрать три Prefabs.</span><span class="sxs-lookup"><span data-stu-id="5851e-182">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="5851e-184">Выбрав три Prefabs, перетащите их на панель Иерархия, чтобы добавить их в сцену.</span><span class="sxs-lookup"><span data-stu-id="5851e-184">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="5851e-186">Чтобы сосредоточиться на объектах в сцене, можно дважды щелкнуть объект Парентанчор, а затем немного увеличить его.</span><span class="sxs-lookup"><span data-stu-id="5851e-186">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="5851e-188">Если вы найдете крупные значки в сцене, например, большие значки «'T» отвлекается от значков, их можно скрыть, переключив <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">приспособлений</a> в положение OFF.</span><span class="sxs-lookup"><span data-stu-id="5851e-188">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="5851e-189">Настройка кнопок для функционирования сцены</span><span class="sxs-lookup"><span data-stu-id="5851e-189">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="5851e-190">В этом разделе вы добавите Prefabs и сценарии в сцену, чтобы создать ряд кнопок, демонстрирующих принципы поведения как локальных, так и пространственных привязок Azure в приложении.</span><span class="sxs-lookup"><span data-stu-id="5851e-190">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="5851e-191">Настройте Холоый компонент "линза 2 (скрипт)" для нажатой кнопки.</span><span class="sxs-lookup"><span data-stu-id="5851e-191">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="5851e-192">На панели Иерархия разверните объект **буттонпарент** и выберите первый дочерний объект с именем **стартазуресессион**.</span><span class="sxs-lookup"><span data-stu-id="5851e-192">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="5851e-194">На панели инспектора прокрутите вниз до **нажатой кнопки Холо линза 2 (скрипт)** и добавьте новый прослушиватель событий в событие **нажатия кнопки ()** , щелкнув значок **+** .</span><span class="sxs-lookup"><span data-stu-id="5851e-194">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="5851e-196">Когда объект Стартазуресессион все еще выбран на панели Иерархия, щелкните и перетащите объект **парентанчор** на панели Иерархия в пустое поле **None (Object) (пустой объект)** только что добавленного прослушивателя событий, чтобы объект парентанчор прослушивает события нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="5851e-196">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="5851e-198">Щелкните раскрывающийся список **без функций** того же прослушивателя событий, а затем выберите **анчормодулескрипт** > **стартазуресессион ()** , чтобы задать функцию стартазуресессион () в качестве действия, запускаемого при срабатывании события нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="5851e-198">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="5851e-200">Настройте компонент, поддерживающий взаимодействие (скрипт).</span><span class="sxs-lookup"><span data-stu-id="5851e-200">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="5851e-201">Если объект Стартазуресессион все еще выбран на панели «Иерархия», на панели инспектора прокрутите вниз до компонента « **взаимодействие (скрипт)** » и повторите тот же процесс, что и в шаге 1 выше для события **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="5851e-201">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="5851e-203">Настройка оставшихся кнопок</span><span class="sxs-lookup"><span data-stu-id="5851e-203">Configure the remaining buttons</span></span>

    <span data-ttu-id="5851e-204">Для каждой из оставшихся кнопок выполните процедуру, описанную в шагах 1 и 2, чтобы назначить функции для событий нажатия кнопки () и onclick () ниже.</span><span class="sxs-lookup"><span data-stu-id="5851e-204">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="5851e-205">Для объекта **стопазуресессион** назначьте функцию **стопазуресессион ()** .</span><span class="sxs-lookup"><span data-stu-id="5851e-205">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="5851e-206">Для объекта **креатеанчор** назначьте функцию **креатеазуреанчор ()** , а затем перетащите **Парентанчор** в пустое поле **None (Game Object)** .</span><span class="sxs-lookup"><span data-stu-id="5851e-206">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="5851e-207">Чтобы **начать поиск объекта привязки** , назначьте функцию **финдазуреанчор ()** .</span><span class="sxs-lookup"><span data-stu-id="5851e-207">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="5851e-208">Чтобы **удалить объект привязки Azure** , назначьте функцию **делетеазуреанчор ()** .</span><span class="sxs-lookup"><span data-stu-id="5851e-208">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="5851e-209">Для объекта **удалить локальную привязку** присвойте функцию **ремовелокаланчор ()** , а затем перетащите **Парентанчор** в поле пустое **значение (объект игрового объекта)** .</span><span class="sxs-lookup"><span data-stu-id="5851e-209">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="5851e-210">Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="5851e-210">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="5851e-211">На панели «Иерархия» выберите объект **парентанчор** и на панели инспектора прокрутите вниз до компонента « **Диспетчер пространственных привязок» (script)** .</span><span class="sxs-lookup"><span data-stu-id="5851e-211">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="5851e-212">Затем в разделе **учетные данные** вставьте идентификатор учетной записи пространственных привязок и ключ в соответствующие поля **идентификатор учетной записи пространственных** привязок и **ключ учетной записи пространственных привязок** .</span><span class="sxs-lookup"><span data-stu-id="5851e-212">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="5851e-213">Вы создали идентификатор и ключ учетной записи пространственных привязок в рамках [предварительных требований](mrlearning-asa-ch1.md#prerequisites)этого руководства.</span><span class="sxs-lookup"><span data-stu-id="5851e-213">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="5851e-215">Обязательно сохраните сцену.</span><span class="sxs-lookup"><span data-stu-id="5851e-215">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="5851e-216">Попытка базового поведения пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="5851e-216">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="5851e-217">Теперь, когда сцена настроена на демонстрацию основ пространственных привязок Azure, пора развернуть приложение, чтобы вы могли работать с пространственными привязками Azure.</span><span class="sxs-lookup"><span data-stu-id="5851e-217">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="5851e-218">Добавьте дополнительные необходимые возможности.</span><span class="sxs-lookup"><span data-stu-id="5851e-218">Add additional required capabilities.</span></span>

    <span data-ttu-id="5851e-219">В меню Unity выберите **изменить** > **Параметры проекта...** , чтобы открыть панель Параметры проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="5851e-219">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="5851e-221">На панели Параметры проигрывателя выберите **проигрыватель** , а затем **Параметры публикации**.</span><span class="sxs-lookup"><span data-stu-id="5851e-221">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="5851e-223">В **параметрах публикации**прокрутите вниз до раздела **возможности** и дважды проверьте, что **спатиалперцептион**, который был включен при создании проекта в начале этого руководства, включен.</span><span class="sxs-lookup"><span data-stu-id="5851e-223">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="5851e-224">Затем включены возможности **InternetClient**, **интернетклиентсервер**, **приватенетворкклиентсервер**, **Ремоваблестораже**, **веб-камеры**и **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="5851e-224">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="5851e-226">Разверните приложение в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5851e-226">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="5851e-227">Напоминание о том, как создать и развернуть проект Unity в HoloLens 2, можно найти в разделах [Создание приложения для устройства](mrlearning-base-ch1.md#build-your-application-to-your-device) статьи [Инициализация проекта и первое](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) руководство по приложениям, которое входит в серию [руководств по началу работы](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="5851e-227">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="5851e-228">Запустите приложение и следуйте инструкциям в приложении.</span><span class="sxs-lookup"><span data-stu-id="5851e-228">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="5851e-229">Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки, чтобы убедиться, что устройство подключено к Интернету.</span><span class="sxs-lookup"><span data-stu-id="5851e-229">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="5851e-230">Когда приложение запускается на устройстве, следуйте инструкциям на экране, отображаемым на панели **инструкций по модулю пространственного якоря Azure** .</span><span class="sxs-lookup"><span data-stu-id="5851e-230">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="5851e-232">Привязка интерфейса</span><span class="sxs-lookup"><span data-stu-id="5851e-232">Anchoring an experience</span></span>

<span data-ttu-id="5851e-233">В предыдущих разделах вы узнали основы пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="5851e-233">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="5851e-234">Мы использовали куб для представления и визуализации родительского объекта Game с присоединенной привязкой.</span><span class="sxs-lookup"><span data-stu-id="5851e-234">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="5851e-235">В этом разделе вы узнаете, как закрепить весь интерфейс, поместив его в качестве дочернего элемента объекта Парентанчор.</span><span class="sxs-lookup"><span data-stu-id="5851e-235">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="5851e-236">Добавьте интерфейс запуска Rocket.</span><span class="sxs-lookup"><span data-stu-id="5851e-236">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="5851e-237">На панели проект перейдите к разделу **активы** > **мртк. Учебник. GettingStarted** > **Prefabs** и выберите **Rocket Launcher_Complete** prefab.</span><span class="sxs-lookup"><span data-stu-id="5851e-237">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="5851e-239">Выбрав Rocket Launcher_Complete prefab, перетащите его поверх объекта **парентанчор** на панели Иерархия, чтобы сделать его дочерним элементом объекта парентанчор.</span><span class="sxs-lookup"><span data-stu-id="5851e-239">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="5851e-241">Изменение расположения процесса запуска Rocket.</span><span class="sxs-lookup"><span data-stu-id="5851e-241">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="5851e-242">Переместите модуль **Rocket Launcher_Complete** , чтобы **парентанчор** (куб) по-прежнему был открыт.</span><span class="sxs-lookup"><span data-stu-id="5851e-242">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="5851e-244">В приложении пользователи теперь могут перемещать весь процесс запуска Rocket, перемещая куб.</span><span class="sxs-lookup"><span data-stu-id="5851e-244">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="5851e-245">Существует множество потоков взаимодействия с пользователем для изменения положения, включая использование объекта изменения положения (например, Куба, используемого в этом руководстве), использование кнопки для переключения ограничивающего прямоугольника, окружающего интерфейс, использование положения и вращения. приспособлений и многое другое.</span><span class="sxs-lookup"><span data-stu-id="5851e-245">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5851e-246">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="5851e-246">Congratulations</span></span>

<span data-ttu-id="5851e-247">В этом руководстве вы узнали основы пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="5851e-247">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="5851e-248">На этом занятии приводятся несколько кнопок, позволяющих изучить различные шаги, необходимые для запуска и завершения сеанса Azure, а также для создания, отправки и скачивания привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="5851e-248">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="5851e-249">На следующем занятии вы узнаете, как сохранять идентификаторы привязки Azure в HoloLens 2 для получения, даже после перезапуска приложения, а также как передавать идентификаторы привязки между несколькими устройствами для достижения пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="5851e-249">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="5851e-250">Следующее занятие: 2. сохранение, получение и совместное использование пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="5851e-250">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
