---
title: Учебники по пространственной привязке Azure — 1. Приступая к работе с пространственными привязками Azure
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 0163b61bfbf8bd583532092581d94f63e1c2a624
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554683"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="d33ef-105">1. Приступая к работе с пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="d33ef-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="d33ef-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="d33ef-106">Overview</span></span>

<span data-ttu-id="d33ef-107">Добро пожаловать на второй ряд учебников по HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d33ef-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="d33ef-108">В этой серии руководств из трех частей вы узнаете об основах использования пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d33ef-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="d33ef-109">В этом первом учебнике [Приступая к работе с пространственными привязками Azure](mrlearning-asa-ch1.md)вы узнаете о различных шагах, необходимых для запуска и завершения сеанса Azure, а также создания, отправки и скачивания привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="d33ef-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="d33ef-110">Во втором учебном курсе, [сохранении, извлечении и совместном использовании пространственных привязок Azure](mrlearning-asa-ch2.md)вы узнаете, как сохранять пространственные привязки Azure в нескольких сеансах приложения, сохраняя сведения о привязке в хранилище HoloLens 2 и совместное использование этих данных привязки с другими устройствами для выравнивания привязок на нескольких устройствах.</span><span class="sxs-lookup"><span data-stu-id="d33ef-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="d33ef-111">В третьем руководстве, в [котором отображается отзыв о пространственной привязке Azure](mrlearning-asa-ch3.md), вы узнаете, как предоставить пользователям Отзывы о событиях и состояниях привязки при использовании пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d33ef-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="d33ef-112">Задачи</span><span class="sxs-lookup"><span data-stu-id="d33ef-112">Objectives</span></span>

* <span data-ttu-id="d33ef-113">Изучите основы разработки с помощью пространственных привязок Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d33ef-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="d33ef-114">Создание, передача и скачивание пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="d33ef-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d33ef-115">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="d33ef-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="d33ef-116">Если вы еще не выполнили серию [учебников по началу работы](mrlearning-base.md) , рекомендуется сначала выполнить эти учебники.</span><span class="sxs-lookup"><span data-stu-id="d33ef-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="d33ef-117">Компьютер с Windows 10, настроенный с требуемыми [установленными инструментами](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d33ef-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="d33ef-118">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="d33ef-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="d33ef-119">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="d33ef-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="d33ef-120">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="d33ef-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="d33ef-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="d33ef-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="d33ef-122">Выполните инструкции из раздела [Создание ресурса пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) в разделе [Краткое руководство. Создание приложения Unity HoloLens, использующего учебник по пространственным привязок Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .</span><span class="sxs-lookup"><span data-stu-id="d33ef-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d33ef-123">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="d33ef-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="d33ef-124">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="d33ef-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="d33ef-125">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="d33ef-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="d33ef-126">В этом разделе вы создадите новый проект Unity и готовы подготовить его к разработке МРТК.</span><span class="sxs-lookup"><span data-stu-id="d33ef-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="d33ef-127">Для этого сначала выполните [инициализацию проекта и первого приложения](mrlearning-base-ch1.md), за исключением [сборки приложения в инструкции устройства](mrlearning-base-ch1.md#build-your-application-to-your-device) , которые включают следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="d33ef-127">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="d33ef-128">[Создайте новый проект Unity](mrlearning-base-ch1.md#create-new-unity-project) и присвойте ему подходящее имя, например *учебники мртк*.</span><span class="sxs-lookup"><span data-stu-id="d33ef-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. [<span data-ttu-id="d33ef-129">Настройка проекта Unity для Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d33ef-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="d33ef-130">Импорт необходимых ресурсов Текстмеш Pro</span><span class="sxs-lookup"><span data-stu-id="d33ef-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="d33ef-131">Импорт набора средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d33ef-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="d33ef-132">Настройка проекта Unity для набора средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d33ef-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="d33ef-133">[Добавьте набор средств Mixed Reality к сцене Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) и присвойте сцене подходящее имя, например *азуреспатиаланчорс* .</span><span class="sxs-lookup"><span data-stu-id="d33ef-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="d33ef-134">Затем следуйте инструкциям в статье [Настройка профилей набора средств для смешанной реальности (изменение режима отображения пространственных сведений)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) , чтобы изменить профиль конфигурации мртк для сцены на **DefaultHoloLens2ConfigurationProfile** и изменить параметры отображения для сетки пространственной информации на **перекрытия**.</span><span class="sxs-lookup"><span data-stu-id="d33ef-134">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="d33ef-135">Как упоминалось в разделе [Настройка проекта Unity для инструкций по набору средств Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) , связанных выше, настоятельно рекомендуется не включать MSBuild для Unity.</span><span class="sxs-lookup"><span data-stu-id="d33ef-135">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="d33ef-136">Добавление встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="d33ef-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="d33ef-137">В этом разделе будет выполнена установка встроенного пакета AR Foundation для Unity, так как он необходим для пакета SDK для пространственных привязок Azure, который будет импортирован в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="d33ef-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="d33ef-138">В меню Unity выберите пункт **окно** > **Диспетчер пакетов**:</span><span class="sxs-lookup"><span data-stu-id="d33ef-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d33ef-140">В списке появится пакет AR Foundation, который может занять несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="d33ef-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="d33ef-141">В окне Диспетчер пакетов выберите **AR Foundation** и установите пакет, нажав кнопку **установить** .</span><span class="sxs-lookup"><span data-stu-id="d33ef-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="d33ef-143">Импорт ресурсов учебника</span><span class="sxs-lookup"><span data-stu-id="d33ef-143">Importing the tutorial assets</span></span>

<span data-ttu-id="d33ef-144">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в том порядке, в котором они перечислены**:</span><span class="sxs-lookup"><span data-stu-id="d33ef-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="d33ef-145">[Азуреспатиаланчорс. пакет unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (версия:/с)</span><span class="sxs-lookup"><span data-stu-id="d33ef-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="d33ef-146">МРТК. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.3.0.2. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="d33ef-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [<span data-ttu-id="d33ef-147">МРТК. HoloLens2. Unity. Tutorials. Assets. Азуреспатиаланчорс. 2.3.0.0. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="d33ef-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="d33ef-148">Напоминание о том, как импортировать пользовательский пакет Unity, можно найти в разделе Импорт инструкций по [набору средств для смешанной реальности](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .</span><span class="sxs-lookup"><span data-stu-id="d33ef-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="d33ef-149">После импорта ресурсов учебника окно проекта должно выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d33ef-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="d33ef-151">Создание и подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="d33ef-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="d33ef-152">В этом разделе вы будете подготавливаем сцену, добавив некоторые из учебника Prefabs.</span><span class="sxs-lookup"><span data-stu-id="d33ef-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="d33ef-153">В окне проекта перейдите к разделу **активы** > **мртк. Учебник. Азуреспатиаланчорс** > **Prefabs** папку.</span><span class="sxs-lookup"><span data-stu-id="d33ef-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="d33ef-154">Удерживая нажатой клавишу CTRL, щелкните **буттонпарент**, **DebugWindow**, **инструкции**и **парентанчор** , чтобы выбрать четыре Prefabs:</span><span class="sxs-lookup"><span data-stu-id="d33ef-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="d33ef-156">Выбрав четыре Prefabs, перетащите их в окно Иерархия, чтобы добавить их в сцену:</span><span class="sxs-lookup"><span data-stu-id="d33ef-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="d33ef-158">Чтобы сосредоточиться на объектах в сцене, можно дважды щелкнуть объект Парентанчор, а затем немного увеличить его:</span><span class="sxs-lookup"><span data-stu-id="d33ef-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="d33ef-160">Если вы найдете крупные значки в сцене, например, большие значки «'T» отвлекается от значков, их можно скрыть, переключив <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">приспособлений</a> в положение OFF.</span><span class="sxs-lookup"><span data-stu-id="d33ef-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="d33ef-161">Настройка кнопок для функционирования сцены</span><span class="sxs-lookup"><span data-stu-id="d33ef-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="d33ef-162">В этом разделе вы добавите скрипты в сцену, чтобы создать ряд событий кнопок, демонстрирующих принципы поведения локальных и пространственных привязок Azure в приложении.</span><span class="sxs-lookup"><span data-stu-id="d33ef-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="d33ef-163">1. Настройка нажатой кнопки Холо линза 2 (скрипт)</span><span class="sxs-lookup"><span data-stu-id="d33ef-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="d33ef-164">В окне Иерархия разверните объект **буттонпарент** и выберите первый дочерний объект с именем **стартазуресессион**:</span><span class="sxs-lookup"><span data-stu-id="d33ef-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="d33ef-166">В окне инспектора выберите компонент **Холо линз 2 (скрипт)** , который можно нажать, и добавьте новый прослушиватель событий **нажатием кнопки ()** , щелкнув значок **+** :</span><span class="sxs-lookup"><span data-stu-id="d33ef-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="d33ef-168">Когда объект Стартазуресессион все еще выбран в окне Иерархия, щелкните и перетащите объект **парентанчор** из окна Иерархия в пустое поле **None (Object) (пустой объект)** только что добавленного прослушивателя событий, чтобы объект парентанчор прослушивает события нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="d33ef-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="d33ef-170">Щелкните раскрывающийся список **без функций** того же прослушивателя событий, а затем выберите **анчормодулескрипт** > **стартазуресессион ()** , чтобы задать функцию стартазуресессион () в качестве действия, запускаемого при срабатывании события нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="d33ef-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="d33ef-172">2. Настройка компонента, поддерживающего взаимодействие (скрипт)</span><span class="sxs-lookup"><span data-stu-id="d33ef-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="d33ef-173">Если объект Стартазуресессион все еще выбран в окне "иерархия", в окне инспектора выберите компонент " **взаимодействие (скрипт)** " и повторите тот же процесс, что и в шаге 1 выше для события **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="d33ef-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="d33ef-175">3. Настройка оставшихся кнопок</span><span class="sxs-lookup"><span data-stu-id="d33ef-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="d33ef-176">Для каждой из оставшихся кнопок выполните процедуру, описанную в шагах 1 и 2, чтобы назначить функции для событий **нажатия кнопки ()** и **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="d33ef-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="d33ef-177">Для объекта **стопазуресессион** назначьте функцию Анчормодулескрипт > **стопазуресессион ()** .</span><span class="sxs-lookup"><span data-stu-id="d33ef-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="d33ef-178">Для объекта **креатеазуреанчор** назначьте функцию Анчормодулескрипт > **креатеазуреанчор ()** ,</span><span class="sxs-lookup"><span data-stu-id="d33ef-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="d33ef-179">затем перетащите **парентанчор** в пустое поле **None (Game Object)** .</span><span class="sxs-lookup"><span data-stu-id="d33ef-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="d33ef-180">Для объекта **ремовелокаланчор** назначьте функцию Анчормодулескрипт > **ремовелокаланчор ()** ,</span><span class="sxs-lookup"><span data-stu-id="d33ef-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="d33ef-181">затем перетащите **парентанчор** в пустое поле **None (Game Object)** .</span><span class="sxs-lookup"><span data-stu-id="d33ef-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="d33ef-182">Для объекта **финдазуреанчор** назначьте функцию Анчормодулескрипт > **финдазуреанчор ()** .</span><span class="sxs-lookup"><span data-stu-id="d33ef-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="d33ef-183">Для объекта **делетеазуреанчор** назначьте функцию Анчормодулескрипт > **делетеазуреанчор ()** .</span><span class="sxs-lookup"><span data-stu-id="d33ef-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="d33ef-184">4. Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="d33ef-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="d33ef-185">В окне «Иерархия» выберите объект **парентанчор** и в окне инспектора прокрутите вниз до компонента « **Диспетчер пространственных привязок» (script)** .</span><span class="sxs-lookup"><span data-stu-id="d33ef-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="d33ef-186">Затем в разделе **учетные данные** вставьте идентификатор и ключ учетной записи пространственной привязки, созданный в рамках [предварительных требований](mrlearning-asa-ch1.md#prerequisites)этого учебника, в соответствующие поля **идентификатор учетной записи пространственных** привязок и **ключ учетной записи пространственных привязок** .</span><span class="sxs-lookup"><span data-stu-id="d33ef-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="d33ef-188">Попытка базового поведения пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="d33ef-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="d33ef-189">Теперь, когда сцена настроена на демонстрацию основ пространственных привязок Azure, пора развернуть приложение, чтобы вы могли работать с пространственными привязками Azure.</span><span class="sxs-lookup"><span data-stu-id="d33ef-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="d33ef-190">1. Добавьте дополнительные необходимые возможности</span><span class="sxs-lookup"><span data-stu-id="d33ef-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="d33ef-191">В меню Unity выберите **изменить** > **Параметры проекта...** , чтобы открыть окно Параметры проигрывателя:</span><span class="sxs-lookup"><span data-stu-id="d33ef-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="d33ef-193">В окне Параметры проигрывателя выберите **проигрыватель** , а затем **Параметры публикации**.</span><span class="sxs-lookup"><span data-stu-id="d33ef-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="d33ef-195">В разделе " **Параметры публикации**" прокрутите вниз до раздела " **возможности** " и дважды убедитесь, что возможности **InternetClient**, **Microphone**и **спатиалперцептион** , включенные при создании проекта в начале этого руководства, включены.</span><span class="sxs-lookup"><span data-stu-id="d33ef-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="d33ef-196">Затем включите возможности **интернетклиентсервер**, **приватенетворкклиентсервер**, **ремоваблестораже**и веб- **камеры** :</span><span class="sxs-lookup"><span data-stu-id="d33ef-196">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="d33ef-198">2. Развертывание приложения в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d33ef-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="d33ef-199">Пространственные привязки Azure не могут выполняться в Unity, поэтому для тестирования функциональности пространственных привязок Azure необходимо развернуть проект на устройстве.</span><span class="sxs-lookup"><span data-stu-id="d33ef-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="d33ef-200">Напоминание о том, как создать и развернуть проект Unity в HoloLens 2, можно найти в руководстве по [сборке приложения на устройстве](mrlearning-base-ch1.md#build-your-application-to-your-device) .</span><span class="sxs-lookup"><span data-stu-id="d33ef-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="d33ef-201">3. Запустите приложение в HoloLens 2 и следуйте инструкциям в приложении.</span><span class="sxs-lookup"><span data-stu-id="d33ef-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="d33ef-202">Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки, чтобы убедиться, что устройство подключено к Интернету.</span><span class="sxs-lookup"><span data-stu-id="d33ef-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="d33ef-203">Когда приложение запускается на устройстве, следуйте инструкциям на экране на панели инструкции учебника по пространственной точке управления Azure:</span><span class="sxs-lookup"><span data-stu-id="d33ef-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="d33ef-205">Привязка интерфейса</span><span class="sxs-lookup"><span data-stu-id="d33ef-205">Anchoring an experience</span></span>

<span data-ttu-id="d33ef-206">В предыдущих разделах вы узнали основы пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d33ef-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="d33ef-207">Мы использовали куб для представления и визуализации родительского объекта Game с присоединенной привязкой.</span><span class="sxs-lookup"><span data-stu-id="d33ef-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="d33ef-208">В этом разделе вы узнаете, как закрепить весь интерфейс, поместив его в качестве дочернего элемента объекта Парентанчор.</span><span class="sxs-lookup"><span data-stu-id="d33ef-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="d33ef-209">1. Добавьте интерфейс запуска Rocket</span><span class="sxs-lookup"><span data-stu-id="d33ef-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="d33ef-210">В окне проекта перейдите к **ресурсам** > **мртк. Учебник. GettingStarted** > **Prefabs** > **роккетлаунчер** папка и выберите **RocketLauncher_Complete** Prefab:</span><span class="sxs-lookup"><span data-stu-id="d33ef-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="d33ef-212">Выбрав RocketLauncher_Complete prefab, перетащите его поверх объекта **парентанчор** в окне иерархии, чтобы сделать его дочерним элементом объекта парентанчор:</span><span class="sxs-lookup"><span data-stu-id="d33ef-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="d33ef-214">2. изменение расположения процесса запуска Rocket</span><span class="sxs-lookup"><span data-stu-id="d33ef-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="d33ef-215">Размещение, поворот и масштабирование объекта **RocketLauncher_Complete** с учетом подходящего масштаба и ориентации, а также обеспечение того, что объект **парентанчор** по-прежнему предоставляется, например:</span><span class="sxs-lookup"><span data-stu-id="d33ef-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="d33ef-216">**Координата Transform X** = 0, Y = 0, Z = 3,75</span><span class="sxs-lookup"><span data-stu-id="d33ef-216">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="d33ef-217">**Поворот** преобразования X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="d33ef-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="d33ef-218">Преобразование **масштаба** X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="d33ef-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![мрлеарнинг-ASA](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="d33ef-220">В приложении пользователи теперь могут перемещать весь процесс запуска Rocket, перемещая куб.</span><span class="sxs-lookup"><span data-stu-id="d33ef-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="d33ef-221">Существует множество потоков взаимодействия с пользователем для изменения положения, включая использование объекта изменения положения (например, Куба, используемого в этом руководстве), использование кнопки для переключения ограничивающего прямоугольника, окружающего интерфейс, использование положения и вращения. приспособлений и многое другое.</span><span class="sxs-lookup"><span data-stu-id="d33ef-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d33ef-222">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d33ef-222">Congratulations</span></span>

<span data-ttu-id="d33ef-223">В этом руководстве вы узнали основы пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d33ef-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="d33ef-224">В руководстве предоставлено несколько кнопок, позволяющих изучить различные шаги, необходимые для запуска и завершения сеанса пространственных привязок Azure, а также для создания, отправки и скачивания пространственных привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="d33ef-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="d33ef-225">На следующем занятии вы узнаете, как сохранять идентификаторы привязки Azure в HoloLens 2 для получения, даже после перезапуска приложения, а также как передавать идентификаторы привязки между несколькими устройствами для достижения пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="d33ef-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="d33ef-226">Следующее занятие: 2. сохранение, получение и совместное использование пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="d33ef-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
