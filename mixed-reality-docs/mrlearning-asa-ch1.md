---
title: Руководства по Пространственным привязкам Azure, часть 1 Начало работы с Пространственными привязками Azure
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: fa0ebc409fa38f664bdd0966906c6fd77f7a6081
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376151"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="9f959-105">1. Начало работы с Пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="9f959-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="9f959-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="9f959-106">Overview</span></span>

<span data-ttu-id="9f959-107">Вас приветствует вторая серия руководств по HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9f959-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="9f959-108">В трех частях этой серии руководств вы получите основные сведения о Пространственных привязках Azure.</span><span class="sxs-lookup"><span data-stu-id="9f959-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="9f959-109">Первое руководство [Начало работы с Пространственными привязками Azure](mrlearning-asa-ch1.md) поможет изучить процессы, необходимые для запуска и завершения сеанса Azure, а также для создания, отправки и скачивания привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="9f959-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="9f959-110">Из второго руководства [Сохранение, извлечение и совместное использование Пространственных привязок Azure](mrlearning-asa-ch2.md) вы узнаете, как сохранять Пространственные привязки Azure в нескольких сеансах приложения, сохраняя сведения о привязке в хранилище HoloLens 2, и как передать эти сведения о привязке на другие устройства для согласования привязок между несколькими устройствами.</span><span class="sxs-lookup"><span data-stu-id="9f959-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="9f959-111">Из третьего руководства [Отображение отзывов от Пространственной привязки Azure](mrlearning-asa-ch3.md) вы узнаете, как предоставить пользователям информацию о событиях и состояниях привязки при использовании Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="9f959-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="9f959-112">Задачи</span><span class="sxs-lookup"><span data-stu-id="9f959-112">Objectives</span></span>

* <span data-ttu-id="9f959-113">Изучите основы разработки Пространственных привязок Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9f959-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="9f959-114">Создание, передача и скачивание пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="9f959-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9f959-115">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="9f959-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="9f959-116">Если вы еще не прошли руководства из серии, посвященной [началу работы](mrlearning-base.md), мы рекомендуем начать знакомство именно с этой серии.</span><span class="sxs-lookup"><span data-stu-id="9f959-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="9f959-117">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="9f959-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="9f959-118">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="9f959-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9f959-119">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="9f959-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="9f959-120">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="9f959-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="9f959-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="9f959-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="9f959-122">Выполните инструкции из раздела [Создание ресурса Пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) в статье [Краткое руководство. Создание приложения Unity HoloLens, которое использует Пространственные привязки Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="9f959-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f959-123">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="9f959-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="9f959-124">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="9f959-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="9f959-125">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="9f959-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="9f959-126">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="9f959-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="9f959-127">Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mrlearning-base-ch1.md), за исключением раздела [Разработка приложения для устройства](mrlearning-base-ch1.md#build-your-application-to-your-device), то есть следующие действия:</span><span class="sxs-lookup"><span data-stu-id="9f959-127">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="9f959-128">[Создайте новый проект Unity](mrlearning-base-ch1.md#create-new-unity-project) и присвойте ему понятное имя, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="9f959-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. <span data-ttu-id="9f959-129">[Настройте проект Unity для Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="9f959-129">[Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)</span></span>

3. <span data-ttu-id="9f959-130">[Импортируйте требуемые ресурсы TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources).</span><span class="sxs-lookup"><span data-stu-id="9f959-130">[Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)</span></span>

4. <span data-ttu-id="9f959-131">[Импортируйте Набор средств для смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="9f959-131">[Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)</span></span>

5. <span data-ttu-id="9f959-132">[Настройте проект Unity для Набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="9f959-132">[Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)</span></span>

6. <span data-ttu-id="9f959-133">[Добавьте Набор средств для смешанной реальности к сцене Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) и присвойте этой сцене понятное имя, например *AzureSpatialAnchors*.</span><span class="sxs-lookup"><span data-stu-id="9f959-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="9f959-134">Затем следуйте инструкциям [по настройке профилей Набора средств для смешанной реальности (изменение параметра отображения сведений о пространственном состоянии)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option), чтобы указать для сцены профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** и значение **Перекрытие** для метода отображения сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="9f959-134">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="9f959-135">Как описано в инструкции по [настройке проекта Unity для Набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), ссылка на которую предложена выше, мы настоятельно рекомендуем не включать MSBuild для Unity.</span><span class="sxs-lookup"><span data-stu-id="9f959-135">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="9f959-136">Добавление встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="9f959-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="9f959-137">В рамках этого раздела вы установите встроенный пакет AR Foundation для Unity, который необходим для пакета SDK Пространственных привязок Azure, который вы будете импортировать в рамках следующей части руководства.</span><span class="sxs-lookup"><span data-stu-id="9f959-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="9f959-138">В меню Unity последовательно выберите **Window** > **Диспетчер пакетов**:</span><span class="sxs-lookup"><span data-stu-id="9f959-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9f959-140">Может пройти несколько секунд, прежде чем пакет AR Foundation появится в списке.</span><span class="sxs-lookup"><span data-stu-id="9f959-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="9f959-141">В окне диспетчера пакетов выберите **AR Foundation** и установите этот пакет, щелкнув кнопку **Установить**:</span><span class="sxs-lookup"><span data-stu-id="9f959-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="9f959-143">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="9f959-143">Importing the tutorial assets</span></span>

<span data-ttu-id="9f959-144">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="9f959-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="9f959-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (версия 2.1.1);</span><span class="sxs-lookup"><span data-stu-id="9f959-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* <span data-ttu-id="9f959-146">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="9f959-146">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)</span></span>
* <span data-ttu-id="9f959-147">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="9f959-147">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)</span></span>

> [!TIP]
> <span data-ttu-id="9f959-148">Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="9f959-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="9f959-149">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="9f959-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="9f959-151">Создание и подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="9f959-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="9f959-152">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="9f959-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="9f959-153">В окне проекта перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Заготовки).</span><span class="sxs-lookup"><span data-stu-id="9f959-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="9f959-154">Удерживая нажатой клавишу CTRL, последовательно щелкните заготовки **ButtonParent**, **DebugWindow**, **Instructions** и **ParentAnchor**, чтобы выбрать их:</span><span class="sxs-lookup"><span data-stu-id="9f959-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="9f959-156">Когда все четыре заготовки будут выбраны, перетащите их вместе в окно "Иерархия", чтобы добавить в сцену:</span><span class="sxs-lookup"><span data-stu-id="9f959-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="9f959-158">Чтобы перенести фокус на объекты сцены, дважды щелкните объект ParentAnchor и немного уменьшите масштаб представления:</span><span class="sxs-lookup"><span data-stu-id="9f959-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="9f959-160">Если вы считаете, что большие значки в сцене (как большие "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение.</span><span class="sxs-lookup"><span data-stu-id="9f959-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="9f959-161">Настройка кнопок для управления сценой</span><span class="sxs-lookup"><span data-stu-id="9f959-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="9f959-162">В рамках этого раздела вы добавите в сцену скрипты, чтобы создать серию событий кнопок для демонстрации базовых приемов работы и поведения локальных привязок, а также Пространственных привязок Azure в приложении.</span><span class="sxs-lookup"><span data-stu-id="9f959-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="9f959-163">1. Настройка компонента Pressable Button Holo Lens 2 (Script)</span><span class="sxs-lookup"><span data-stu-id="9f959-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="9f959-164">В окне "Иерархия" разверните объект **ButtonParent**. Выберите в нем первый дочерний объект с именем **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="9f959-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="9f959-166">В окне "Инспектор" найдите компонент **Pressable Button Holo Lens 2 (Script)** (Нажимаемая кнопка Holo Lens 2 — скрипт). Добавьте новый прослушиватель событий к событию **Button Pressed ()** (Нажатие кнопки), щелкнув значок **+** :</span><span class="sxs-lookup"><span data-stu-id="9f959-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="9f959-168">Сохраняя объект StartAzureSession выделенным в окне "Иерархия", щелкните и перетащите объект **ParentAnchor** из окна "Иерархия" в пустое поле **None (Object)** только что созданного прослушивателя событий, чтобы объект ParentAnchor ожидал передачи данных о событии нажатия для этой кнопки:</span><span class="sxs-lookup"><span data-stu-id="9f959-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="9f959-170">Щелкните раскрывающийся список **No Function** (Нет функции) для того же прослушивателя событий. Затем выберите **AnchorModuleScript** > **StartAzureSession ()** , чтобы назначить функции StartAzureSession () роль действия, которое вызывается при получении от этой кнопки событий нажатия кнопки:</span><span class="sxs-lookup"><span data-stu-id="9f959-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="9f959-172">2. Настройка компонента Interactable (Script)</span><span class="sxs-lookup"><span data-stu-id="9f959-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="9f959-173">Сохраняя объект StartAzureSession выделенным в окне "Иерархия", найдите в окне "Инспектор" компонент **Interactable (Script)** (Взаимодействие — скрипт). Повторно выполните описанный выше в шаге 1 процесс для события **OnClick ()** (Щелчок):</span><span class="sxs-lookup"><span data-stu-id="9f959-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="9f959-175">3. Настройка остальных кнопок</span><span class="sxs-lookup"><span data-stu-id="9f959-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="9f959-176">Для всех остальных кнопок повторно выполните процессы, которые описаны выше в шагах 1 и 2, чтобы назначить функции событиям **Button Pressed ()** (Нажатие кнопки) и **OnClick ()** (Щелчок) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9f959-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="9f959-177">Для объекта **StopAzureSession** назначьте функцию AnchorModuleScript > **StopAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="9f959-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="9f959-178">Для объекта **CreateAzureAnchor** назначьте функцию AnchorModuleScript > **CreateAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="9f959-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="9f959-179">Затем снова перетащите **ParentAnchor** в пустое поле **None (Game Object)** .</span><span class="sxs-lookup"><span data-stu-id="9f959-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="9f959-180">Для объекта **RemoveLocalAnchor** назначьте функцию AnchorModuleScript > **RemoveLocalAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="9f959-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="9f959-181">Затем снова перетащите **ParentAnchor** в пустое поле **None (Game Object)** .</span><span class="sxs-lookup"><span data-stu-id="9f959-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="9f959-182">Для объекта **FindAzureAnchor** назначьте функцию AnchorModuleScript > **FindAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="9f959-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="9f959-183">Для объекта **DeleteAzureAnchor** назначьте функцию AnchorModuleScript > **DeleteAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="9f959-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="9f959-184">4. Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="9f959-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="9f959-185">В окне "Иерархия" выберите объект **ParentAnchor**. Затем в окне "Инспектор" прокрутите содержимое вниз до компонента **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт).</span><span class="sxs-lookup"><span data-stu-id="9f959-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="9f959-186">Теперь в разделе **Учетные данные** вставьте значения идентификатора и ключа учетной записи Пространственных привязок, которую вы создали при подготовке [предварительных условий](mrlearning-asa-ch1.md#prerequisites) для этого руководства, в соответствующие поля **Spatial Anchors Account Id** (Идентификатор учетной записи пространственных привязок) и **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок):</span><span class="sxs-lookup"><span data-stu-id="9f959-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="9f959-188">Изучение базового поведения Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="9f959-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="9f959-189">Теперь, когда в сцене все готово для работы с основными функциями Пространственных привязок Azure, можно развернуть приложение и познакомиться с Пространственными привязками Azure.</span><span class="sxs-lookup"><span data-stu-id="9f959-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="9f959-190">1. Добавление дополнительных требуемых возможностей</span><span class="sxs-lookup"><span data-stu-id="9f959-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="9f959-191">В меню Unity последовательно щелкните элементы **Edit (Правка)**  > **Project Settings... (Параметры проекта...)** , чтобы открыть окно параметров проигрывателя:</span><span class="sxs-lookup"><span data-stu-id="9f959-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="9f959-193">В окне "Параметры проигрывателя" выберите элемент **Проигрыватель**, а затем — элемент **Параметры публикации**:</span><span class="sxs-lookup"><span data-stu-id="9f959-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="9f959-195">В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient** (Интернет-клиент), **Microphone** (Микрофон) и **SpatialPerception** (Пространственное восприятие), которые вы включили при создании проекта в начале работы с этим руководством.</span><span class="sxs-lookup"><span data-stu-id="9f959-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="9f959-196">Теперь включите возможности **InternetClientServer** (Сервер интернет-клиента), **PrivateNetworkClientServer** (Сервер клиента частной сети), **RemovableStorage** (Съемный носитель) и **Webcam** (Веб-камера):</span><span class="sxs-lookup"><span data-stu-id="9f959-196">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="9f959-198">2. Разверните приложение на устройстве HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9f959-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="9f959-199">Пространственные привязки Azure не могут работать в Unity. Поэтому для проверки функциональных возможностей этой службы вам придется развернуть проект на устройстве.</span><span class="sxs-lookup"><span data-stu-id="9f959-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="9f959-200">Чтобы вспомнить, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, воспользуйтесь инструкциями из раздела о [разработке приложения для устройства](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="9f959-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="9f959-201">3. Запустите приложение на HoloLens 2 и следуйте предоставленным инструкциям</span><span class="sxs-lookup"><span data-stu-id="9f959-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="9f959-202">Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки. Поэтому обеспечьте подключение устройства к Интернету.</span><span class="sxs-lookup"><span data-stu-id="9f959-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="9f959-203">Запустив на устройстве приложение, выполните инструкции, представленные на экране панели со сведениями для руководства по Пространственным привязкам Azure.</span><span class="sxs-lookup"><span data-stu-id="9f959-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="9f959-205">Привязка к взаимодействию</span><span class="sxs-lookup"><span data-stu-id="9f959-205">Anchoring an experience</span></span>

<span data-ttu-id="9f959-206">В предыдущих разделах вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="9f959-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="9f959-207">С помощью куба мы представили и визуализировали родительский объект игры с прикрепленной привязкой.</span><span class="sxs-lookup"><span data-stu-id="9f959-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="9f959-208">Из этого раздела вы узнаете, как привязать взаимодействие целиком, разместив его в дочернем элементе объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="9f959-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="9f959-209">1. Добавление взаимодействия Rocket Launcher</span><span class="sxs-lookup"><span data-stu-id="9f959-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="9f959-210">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** и выберите заготовку **RocketLauncher_Complete**:</span><span class="sxs-lookup"><span data-stu-id="9f959-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="9f959-212">Сохраняя выбранной заготовку RocketLauncher_Complete, перетащите ее поверх объекта **ParentAnchor** в окне "Иерархия", чтобы сделать дочерним элементом объекта ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="9f959-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="9f959-214">2. Перемещение взаимодействия Rocket Launcher</span><span class="sxs-lookup"><span data-stu-id="9f959-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="9f959-215">Вы можете изменять положение, угол наклона и масштаб объекта **RocketLauncher_Complete** произвольным образом, сохраняя объект **ParentAnchor** открытым, например:</span><span class="sxs-lookup"><span data-stu-id="9f959-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="9f959-216">для параметра преобразования **Position** (Положение) укажите значения X = 0, Y = 0, Z = 3.75;</span><span class="sxs-lookup"><span data-stu-id="9f959-216">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="9f959-217">для параметра преобразования **Rotation** (Поворот) укажите значения X = 0, Y = 90, Z = 0;</span><span class="sxs-lookup"><span data-stu-id="9f959-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="9f959-218">для параметра преобразования **Scale** (Масштаб) укажите значения X = 10, Y = 10, Z = 10.</span><span class="sxs-lookup"><span data-stu-id="9f959-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="9f959-220">В этом приложении пользователи могут перемещать взаимодействие Rocket Launcher целиком, передвигая соответствующий куб.</span><span class="sxs-lookup"><span data-stu-id="9f959-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="9f959-221">Есть много потоков взаимодействия с пользователем для изменения положения, в том числе: перемещение объекта (например, куба в этом руководстве), включение ограничивающего прямоугольника вокруг взаимодействия нажатием кнопки, применение манипуляторов положения и вращения и другие.</span><span class="sxs-lookup"><span data-stu-id="9f959-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9f959-222">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="9f959-222">Congratulations</span></span>

<span data-ttu-id="9f959-223">В рамках этого руководства вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="9f959-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="9f959-224">Этого руководство предоставило вам несколько кнопок, которые помогли изучить процессы, необходимые для запуска и завершения сеанса Пространственных привязок Azure, а также создания, отправки и скачивания привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="9f959-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="9f959-225">Из следующего урока вы узнаете, как сохранить идентификаторы привязок Azure на устройстве HoloLens 2 таким образом, чтобы их можно было извлечь даже после перезапуска, и как передавать идентификаторы привязок между несколькими устройствами для достижения пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="9f959-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="9f959-226">Следующий урок. 2. Сохранение, получение и совместное использование пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="9f959-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
