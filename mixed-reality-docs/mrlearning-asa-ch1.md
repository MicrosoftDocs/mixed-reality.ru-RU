---
title: Учебники по пространственной привязке Azure — 1. Приступая к работе с пространственными привязками Azure
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 861c42f9449fcb3cf038258af91088fc927941e5
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940982"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="a9d11-105">1. Приступая к работе с пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="a9d11-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="a9d11-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="a9d11-106">Overview</span></span>

<span data-ttu-id="a9d11-107">Добро пожаловать на второй ряд учебников по HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a9d11-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="a9d11-108">В этой серии руководств из трех частей вы узнаете об основах использования пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a9d11-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="a9d11-109">В этом первом учебнике [Приступая к работе с пространственными привязками Azure](mrlearning-asa-ch1.md)вы узнаете о различных шагах, необходимых для запуска и завершения сеанса Azure, а также создания, отправки и скачивания привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="a9d11-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="a9d11-110">Во втором учебном курсе, [сохранении, извлечении и совместном использовании пространственных привязок Azure](mrlearning-asa-ch2.md)вы узнаете, как сохранять пространственные привязки Azure в нескольких сеансах приложения, сохраняя сведения о привязке в хранилище HoloLens 2 и совместное использование этих данных привязки с другими устройствами для выравнивания привязок на нескольких устройствах.</span><span class="sxs-lookup"><span data-stu-id="a9d11-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="a9d11-111">В третьем руководстве, в [котором отображается отзыв о пространственной привязке Azure](mrlearning-asa-ch3.md), вы узнаете, как предоставить пользователям Отзывы о событиях и состояниях привязки при использовании пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a9d11-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="a9d11-112">Задачи</span><span class="sxs-lookup"><span data-stu-id="a9d11-112">Objectives</span></span>

* <span data-ttu-id="a9d11-113">Изучите основы разработки с помощью пространственных привязок Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a9d11-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="a9d11-114">Создание, передача и скачивание пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="a9d11-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a9d11-115">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="a9d11-115">Prerequisites</span></span>

* <span data-ttu-id="a9d11-116">Выполните требования, перечисленные в разделе " [Предварительные требования](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) " [краткого руководства по созданию приложения Unity HoloLens, в котором используется учебник по пространственным привязок Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .</span><span class="sxs-lookup"><span data-stu-id="a9d11-116">Meet the requirements listed in the [Prerequisites](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) section of the  [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="a9d11-117">Выполните инструкции из раздела [Создание ресурса пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) в разделе [Краткое руководство. Создание приложения Unity HoloLens, использующего учебник по пространственным привязок Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .</span><span class="sxs-lookup"><span data-stu-id="a9d11-117">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="a9d11-118">Если вы еще не выполнили серию [учебников по началу работы](mrlearning-base.md) , рекомендуется сначала выполнить эти учебники.</span><span class="sxs-lookup"><span data-stu-id="a9d11-118">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="a9d11-119">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="a9d11-119">Creating the Unity project</span></span>

<span data-ttu-id="a9d11-120">В этом разделе вы создадите новый проект Unity и настроите его для Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a9d11-120">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="a9d11-121">Создайте проект Unity и присвойте ему подходящее имя, например, _учебник по пространственным привязок Azure_.</span><span class="sxs-lookup"><span data-stu-id="a9d11-121">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="a9d11-122">Настройка проекта Unity для Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a9d11-122">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="a9d11-123">Напоминание о том, как создать проект Unity и настроить его для Windows Mixed Reality, можно найти в разделах [Создание проекта Unity](mrlearning-base-ch1.md#create-new-unity-project) и [Настройка проекта Unity для Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) статьи [Инициализация проекта и первого приложения](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , которое является частью [руководства по началу работы](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="a9d11-123">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="a9d11-124">Добавление встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="a9d11-124">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="a9d11-125">В этом разделе вы добавите нестандартные активы и пакеты Unity, необходимые для набора средств и пакетов SDK, которые будут использоваться в проекте.</span><span class="sxs-lookup"><span data-stu-id="a9d11-125">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="a9d11-126">Импорт необходимых ресурсов TMP.</span><span class="sxs-lookup"><span data-stu-id="a9d11-126">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a9d11-127">Мы добавляем этот пакет, так как он необходим для набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a9d11-127">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="a9d11-128">В меню Unity выберите пункт **окно** > **Текстмешпро** > **импортировать нужные ресурсы tmp**.</span><span class="sxs-lookup"><span data-stu-id="a9d11-128">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="a9d11-130">Во всплывающем окне Импорт пакета Unity сначала убедитесь, что выбраны все ресурсы, нажав кнопку **все** , а затем импортируйте ресурсы, нажав кнопку **Импорт** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-130">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="a9d11-132">Установите AR Foundation.</span><span class="sxs-lookup"><span data-stu-id="a9d11-132">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a9d11-133">Мы добавляем этот пакет, так как он требуется пакетом SDK для пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a9d11-133">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="a9d11-134">В меню Unity выберите пункт **окно** > **Диспетчер пакетов**.</span><span class="sxs-lookup"><span data-stu-id="a9d11-134">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="a9d11-136">В окне Диспетчер пакетов выберите **AR Foundation** и установите пакет, нажав кнопку **установить** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-136">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="a9d11-137">В списке появится пакет AR Foundation, который может занять несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="a9d11-137">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="a9d11-139">Импорт ресурсов учебника</span><span class="sxs-lookup"><span data-stu-id="a9d11-139">Importing the tutorial assets</span></span>

<span data-ttu-id="a9d11-140">В этом разделе вы скачиваете и импортируете все ресурсы учебника.</span><span class="sxs-lookup"><span data-stu-id="a9d11-140">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="a9d11-141">Скачайте ресурсы.</span><span class="sxs-lookup"><span data-stu-id="a9d11-141">Download the assets.</span></span>

    * <span data-ttu-id="a9d11-142">[Азуреспатиаланчорс. пакет unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (версия 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="a9d11-142">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="a9d11-143">Microsoft. Микседреалити. Toolkit. Unity. Foundation. 2.1.0. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="a9d11-143">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="a9d11-144">МРТК. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.1.0.1. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="a9d11-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="a9d11-145">МРТК. HoloLens2. Unity. Tutorials. Assets. Азуреспатиаланчорс. 2.1.0.1. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="a9d11-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="a9d11-146">Импортируйте ресурсы.</span><span class="sxs-lookup"><span data-stu-id="a9d11-146">Import the assets.</span></span>

    <span data-ttu-id="a9d11-147">В меню Unity выберите **активы** > **импортировать пакет** > **настраиваемый пакет..** ..</span><span class="sxs-lookup"><span data-stu-id="a9d11-147">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="a9d11-149">В пакете импорта... (всплывающее окно) выберите **азуреспатиаланчорс. пакет unitypackage** и нажмите кнопку **Открыть** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-149">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="a9d11-151">Во всплывающем окне Импорт пакета Unity сначала убедитесь, что выбраны все ресурсы, нажав кнопку **все** , а затем импортируйте ресурсы, нажав кнопку **Импорт** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-151">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="a9d11-153">Повторите эти действия, чтобы импортировать оставшиеся пакеты ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a9d11-153">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="a9d11-154">По завершении в папке **Assets** проекта Unity должны содержаться эти вложенные папки.</span><span class="sxs-lookup"><span data-stu-id="a9d11-154">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="a9d11-156">Создание и подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="a9d11-156">Creating and preparing the scene</span></span>

<span data-ttu-id="a9d11-157">В этом разделе вы создадите и подготовите сцену, добавив набор средств для смешанной реальности и часть учебника Prefabs.</span><span class="sxs-lookup"><span data-stu-id="a9d11-157">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="a9d11-158">Создайте новую сцену.</span><span class="sxs-lookup"><span data-stu-id="a9d11-158">Create a new scene.</span></span>

    <span data-ttu-id="a9d11-159">В меню Unity выберите **файл** > **создать сцену**.</span><span class="sxs-lookup"><span data-stu-id="a9d11-159">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="a9d11-161">В меню Unity выберите **файл** > **Сохранить как...** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-161">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="a9d11-163">Во всплывающем окне Сохранить сцену перейдите к папке **сцен** проекта, присвойте сцене подходящее имя, например _асатуториалсцене_, и сохраните сцену, нажав кнопку **сохранить** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-163">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="a9d11-165">Вы можете сохранить сцену в любом месте, пока она находится внутри папки ресурсов проекта.</span><span class="sxs-lookup"><span data-stu-id="a9d11-165">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="a9d11-166">Однако, чтобы хранить проект в Организации, обычно рекомендуется сохранить его в папке «сцены» проекта.</span><span class="sxs-lookup"><span data-stu-id="a9d11-166">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="a9d11-167">Добавьте набор средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a9d11-167">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="a9d11-168">В меню Unity выберите **набор средств для смешанной реальности** > **Добавить в сцену и настроить...** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-168">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="a9d11-170">Во всплывающем окне Выбор Микседреалититулкитконфигуратионпрофиле щелкните **DefaultHoloLens2ConfigurationProfile** , чтобы задать его в качестве профиля конфигурации мртк сцены.</span><span class="sxs-lookup"><span data-stu-id="a9d11-170">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="a9d11-172">В меню Unity выберите **файл** > **сохранить** , чтобы сохранить сцену.</span><span class="sxs-lookup"><span data-stu-id="a9d11-172">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="a9d11-174">Чтобы быстро сохранить сцену при работе с этим руководством, можно использовать сочетание клавиш CTRL + S (Command + S в macOS).</span><span class="sxs-lookup"><span data-stu-id="a9d11-174">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="a9d11-175">Добавьте учебник Prefabs.</span><span class="sxs-lookup"><span data-stu-id="a9d11-175">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="a9d11-176">На панели проект перейдите к разделу **активы** > **мртк. Учебник. Азуреспатиаланчорс** > **Prefabs** папку.</span><span class="sxs-lookup"><span data-stu-id="a9d11-176">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="a9d11-177">Удерживая нажатой кнопку CTRL (Command on macOS), щелкните **буттонпарент**, **DebugWindow**и **парентанчор** , чтобы выбрать три Prefabs.</span><span class="sxs-lookup"><span data-stu-id="a9d11-177">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="a9d11-179">Выбрав три Prefabs, перетащите их на панель Иерархия, чтобы добавить их в сцену.</span><span class="sxs-lookup"><span data-stu-id="a9d11-179">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="a9d11-181">Чтобы сосредоточиться на объектах в сцене, можно дважды щелкнуть объект Парентанчор, а затем немного увеличить его.</span><span class="sxs-lookup"><span data-stu-id="a9d11-181">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="a9d11-183">Если вы найдете крупные значки в сцене, например, большие значки «'T» отвлекается от значков, их можно скрыть, переключив <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">приспособлений</a> в положение OFF.</span><span class="sxs-lookup"><span data-stu-id="a9d11-183">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="a9d11-184">Настройка кнопок для функционирования сцены</span><span class="sxs-lookup"><span data-stu-id="a9d11-184">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="a9d11-185">В этом разделе вы добавите Prefabs и сценарии в сцену, чтобы создать ряд кнопок, демонстрирующих принципы поведения как локальных, так и пространственных привязок Azure в приложении.</span><span class="sxs-lookup"><span data-stu-id="a9d11-185">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="a9d11-186">Настройте Холоый компонент "линза 2 (скрипт)" для нажатой кнопки.</span><span class="sxs-lookup"><span data-stu-id="a9d11-186">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="a9d11-187">На панели Иерархия разверните объект **буттонпарент** и выберите первый дочерний объект с именем **стартазуресессион**.</span><span class="sxs-lookup"><span data-stu-id="a9d11-187">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="a9d11-189">На панели инспектора прокрутите вниз до **нажатой кнопки Холо линза 2 (скрипт)** и добавьте новый прослушиватель событий в событие **нажатия кнопки ()** , щелкнув значок **+** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-189">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="a9d11-191">Когда объект Стартазуресессион все еще выбран на панели Иерархия, щелкните и перетащите объект **парентанчор** на панели Иерархия в пустое поле **None (Object) (пустой объект)** только что добавленного прослушивателя событий, чтобы объект парентанчор прослушивает события нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="a9d11-191">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="a9d11-193">Щелкните раскрывающийся список **без функций** того же прослушивателя событий, а затем выберите **анчормодулескрипт** > **стартазуресессион ()** , чтобы задать функцию стартазуресессион () в качестве действия, запускаемого при срабатывании события нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="a9d11-193">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="a9d11-195">Настройте компонент, поддерживающий взаимодействие (скрипт).</span><span class="sxs-lookup"><span data-stu-id="a9d11-195">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="a9d11-196">Если объект Стартазуресессион все еще выбран на панели «Иерархия», на панели инспектора прокрутите вниз до компонента « **взаимодействие (скрипт)** » и повторите тот же процесс, что и в шаге 1 выше для события **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-196">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="a9d11-198">Настройка оставшихся кнопок</span><span class="sxs-lookup"><span data-stu-id="a9d11-198">Configure the remaining buttons</span></span>

    <span data-ttu-id="a9d11-199">Для каждой из оставшихся кнопок выполните процедуру, описанную в шагах 1 и 2, чтобы назначить функции для событий нажатия кнопки () и onclick () ниже.</span><span class="sxs-lookup"><span data-stu-id="a9d11-199">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="a9d11-200">Для объекта **стопазуресессион** назначьте функцию **стопазуресессион ()** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-200">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="a9d11-201">Для объекта **креатеанчор** назначьте функцию **креатеазуреанчор ()** , а затем перетащите **Парентанчор** в пустое поле **None (Game Object)** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-201">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="a9d11-202">Чтобы **начать поиск объекта привязки** , назначьте функцию **финдазуреанчор ()** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-202">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="a9d11-203">Чтобы **удалить объект привязки Azure** , назначьте функцию **делетеазуреанчор ()** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-203">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="a9d11-204">Для объекта **удалить локальную привязку** присвойте функцию **ремовелокаланчор ()** , а затем перетащите **Парентанчор** в поле пустое **значение (объект игрового объекта)** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-204">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="a9d11-205">Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="a9d11-205">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="a9d11-206">На панели «Иерархия» выберите объект **парентанчор** и на панели инспектора прокрутите вниз до компонента « **Диспетчер пространственных привязок» (script)** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-206">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="a9d11-207">Затем в разделе **учетные данные** вставьте идентификатор учетной записи пространственных привязок и ключ в соответствующие поля **идентификатор учетной записи пространственных** привязок и **ключ учетной записи пространственных привязок** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-207">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a9d11-208">Вы создали идентификатор и ключ учетной записи пространственных привязок в рамках [предварительных требований](mrlearning-asa-ch1.md#prerequisites)этого руководства.</span><span class="sxs-lookup"><span data-stu-id="a9d11-208">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="a9d11-210">Обязательно сохраните сцену.</span><span class="sxs-lookup"><span data-stu-id="a9d11-210">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="a9d11-211">Попытка базового поведения пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="a9d11-211">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="a9d11-212">Теперь, когда сцена настроена на демонстрацию основ пространственных привязок Azure, пора развернуть приложение, чтобы вы могли работать с пространственными привязками Azure.</span><span class="sxs-lookup"><span data-stu-id="a9d11-212">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="a9d11-213">Добавьте дополнительные необходимые возможности.</span><span class="sxs-lookup"><span data-stu-id="a9d11-213">Add additional required capabilities.</span></span>

    <span data-ttu-id="a9d11-214">В меню Unity выберите **изменить** > **Параметры проекта...** , чтобы открыть панель Параметры проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="a9d11-214">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="a9d11-216">На панели Параметры проигрывателя выберите **проигрыватель** , а затем **Параметры публикации**.</span><span class="sxs-lookup"><span data-stu-id="a9d11-216">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="a9d11-218">В **параметрах публикации**прокрутите вниз до раздела **возможности** и дважды проверьте, что **спатиалперцептион**, который был включен при создании проекта в начале этого руководства, включен.</span><span class="sxs-lookup"><span data-stu-id="a9d11-218">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="a9d11-219">Затем включены возможности **InternetClient**, **интернетклиентсервер**, **приватенетворкклиентсервер**, **Ремоваблестораже**, **веб-камеры**и **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-219">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="a9d11-221">Разверните приложение в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a9d11-221">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="a9d11-222">Напоминание о том, как создать и развернуть проект Unity в HoloLens 2, можно найти в разделах [Создание приложения для устройства](mrlearning-base-ch1.md#build-your-application-to-your-device) статьи [Инициализация проекта и первое](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) руководство по приложениям, которое входит в серию [руководств по началу работы](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="a9d11-222">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="a9d11-223">Запустите приложение и следуйте инструкциям в приложении.</span><span class="sxs-lookup"><span data-stu-id="a9d11-223">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="a9d11-224">Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки, чтобы убедиться, что устройство подключено к Интернету.</span><span class="sxs-lookup"><span data-stu-id="a9d11-224">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="a9d11-225">Когда приложение запускается на устройстве, следуйте инструкциям на экране, отображаемым на панели **инструкций по модулю пространственного якоря Azure** .</span><span class="sxs-lookup"><span data-stu-id="a9d11-225">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="a9d11-227">Привязка интерфейса</span><span class="sxs-lookup"><span data-stu-id="a9d11-227">Anchoring an experience</span></span>

<span data-ttu-id="a9d11-228">В предыдущих разделах вы узнали основы пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a9d11-228">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a9d11-229">Мы использовали куб для представления и визуализации родительского объекта Game с присоединенной привязкой.</span><span class="sxs-lookup"><span data-stu-id="a9d11-229">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="a9d11-230">В этом разделе вы узнаете, как закрепить весь интерфейс, поместив его в качестве дочернего элемента объекта Парентанчор.</span><span class="sxs-lookup"><span data-stu-id="a9d11-230">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="a9d11-231">Добавьте интерфейс запуска Rocket.</span><span class="sxs-lookup"><span data-stu-id="a9d11-231">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="a9d11-232">На панели проект перейдите к разделу **активы** > **мртк. Учебник. GettingStarted** > **Prefabs** и выберите **Rocket Launcher_Complete** prefab.</span><span class="sxs-lookup"><span data-stu-id="a9d11-232">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="a9d11-234">Выбрав Rocket Launcher_Complete prefab, перетащите его поверх объекта **парентанчор** на панели Иерархия, чтобы сделать его дочерним элементом объекта парентанчор.</span><span class="sxs-lookup"><span data-stu-id="a9d11-234">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="a9d11-236">Изменение расположения процесса запуска Rocket.</span><span class="sxs-lookup"><span data-stu-id="a9d11-236">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="a9d11-237">Переместите модуль **Rocket Launcher_Complete** , чтобы **парентанчор** (куб) по-прежнему был открыт.</span><span class="sxs-lookup"><span data-stu-id="a9d11-237">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![мрлеарнинг-ASA](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="a9d11-239">В приложении пользователи теперь могут перемещать весь процесс запуска Rocket, перемещая куб.</span><span class="sxs-lookup"><span data-stu-id="a9d11-239">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="a9d11-240">Существует множество потоков взаимодействия с пользователем для изменения положения, включая использование объекта изменения положения (например, Куба, используемого в этом руководстве), использование кнопки для переключения ограничивающего прямоугольника, окружающего интерфейс, использование положения и вращения. приспособлений и многое другое.</span><span class="sxs-lookup"><span data-stu-id="a9d11-240">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a9d11-241">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="a9d11-241">Congratulations</span></span>

<span data-ttu-id="a9d11-242">В этом руководстве вы узнали основы пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a9d11-242">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a9d11-243">На этом занятии приводятся несколько кнопок, позволяющих изучить различные шаги, необходимые для запуска и завершения сеанса Azure, а также для создания, отправки и скачивания привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="a9d11-243">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="a9d11-244">На следующем занятии вы узнаете, как сохранять идентификаторы привязки Azure в HoloLens 2 для получения, даже после перезапуска приложения, а также как передавать идентификаторы привязки между несколькими устройствами для достижения пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="a9d11-244">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="a9d11-245">Следующее занятие: 2. сохранение, получение и совместное использование пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="a9d11-245">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
