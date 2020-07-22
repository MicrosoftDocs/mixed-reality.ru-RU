---
title: Учебники по облачным службам Azure — 1. Облачные службы Azure для HoloLens 2
description: В рамках этого курса вы узнаете, как реализовать различные службы Azure в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: azure, смешанная реальность, unity, учебник, hololens, hololens 2, хранилище blob-объектов azure, табличное хранилище azure, пространственные привязки azure, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306004"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="cc2d4-105">1. Облачные службы Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cc2d4-105">1. Azure Cloud Services for HoloLens 2</span></span>

## <a name="overview"></a><span data-ttu-id="cc2d4-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="cc2d4-106">Overview</span></span>

<span data-ttu-id="cc2d4-107">Представляем вашему вниманию серию учебников, посвященных переносу **облачных служб Azure** в приложение **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-107">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="cc2d4-108">Из этой серии учебников в пяти частях вы узнаете, как интегрировать несколько **облачных служб Azure** в проект **Unity** для **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-108">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="cc2d4-109">В каждой из последующих глав будут добавляться новые **облачные службы Azure** для расширения возможностей приложений и взаимодействий с пользователем. Кроме того, вы узнаете об основных принципах роботы **облачной службы Azure**.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-109">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="cc2d4-110">В этой серии учебников основное внимание уделяется **HoloLens 2**, но из-за межплатформенного характера Unity большая часть материалов будет также применяться для классических приложений и смартфонов.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-110">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="cc2d4-111">В этом первом учебнике [Знакомство с облачными службами Azure для HoloLens 2](mr-learning-azure-01.md) разъясняются цели приложения, а также приведено краткое описание каждой облачной службы Azure и настройки проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-111">In this first tutorial, [Introducing Azure Cloud Services for HoloLens 2](mr-learning-azure-01.md), you begin by explaining the goals of the application, briefly introduce you to each Azure Cloud service and set up the unity project.</span></span>

<span data-ttu-id="cc2d4-112">Во втором учебнике [Интеграция службы хранилища Azure](mr-learning-azure-02.md) вы выполните интеграцию службы хранилища Azure в качестве решения сохраняемости для демонстрационного приложения, узнаете о различиях между Хранилищем BLOB-объектов и хранилищем таблиц, подготовите необходимые ресурсы проекта, настроите сцену и проверите операции чтения, обновления и удаления данных.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-112">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you start off by integrating Azure Storage as the persistence solution for the demo application, learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene and verify the read, update and delete data operations.</span></span>

<span data-ttu-id="cc2d4-113">Продолжая работу с третьим учебником [Интеграция Пользовательского визуального распознавания Azure](mr-learning-azure-03.md), вы будете использовать Пользовательское визуальное распознавание Azure для обучения и обнаружения изображений в приложении HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-113">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="cc2d4-114">В начале главы приведены сведения о настройке ресурса "Пользовательское визуальное распознавание Azure", подготовке компонентов сцены и действия для обучения и обнаружения изображений в приложении.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-114">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="cc2d4-115">Далее в четвертом учебнике [Интеграция пространственных привязок Azure](mr-learning-azure-04.md) вы изучите службы пространственных привязок Azure для сохранения и поиска расположений, а также основные концепции, подготовите необходимые ресурсы, настроите сцены и приступите к использованию новой функции в приложении.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-115">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="cc2d4-116">С помощью пятого руководства [Интеграция службы Azure Bot с LUIS](mr-learning-azure-05.md) вы завершите обучение, предоставляя приложению новый метод взаимодействия с пользователем с использованием естественного языка.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-116">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="cc2d4-117">Эта функция будет реализована с помощью платформы Azure Bot Framework, а также службы "Распознавания речи" (LUIS).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-117">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="cc2d4-118">В этой заключительной главе рассказывается о принципах работы службы Azure Bot и ускорении процесса, который вы будете использовать в качестве решения с нулевым кодом с помощью Bot Framework Composer.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-118">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="cc2d4-119">После создания бота вы интегрируете его в сцену и запустите его на завершающем этапе приложения HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-119">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="cc2d4-120">Цели приложения</span><span class="sxs-lookup"><span data-stu-id="cc2d4-120">Application goals</span></span>

<span data-ttu-id="cc2d4-121">В этой серии учебников вы создадите приложение **HoloLens 2**, которое может обнаруживать объекты на изображениях и находить их пространственное положение.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-121">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="cc2d4-122">Чтобы установить язык домена, необходимо вызвать такие сущности из **отслеживаемого объекта**.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-122">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="cc2d4-123">Пользователь может создать **отслеживаемый объект**, чтобы связать набор изображений с помощью компьютерного зрения или пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-123">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="cc2d4-124">Все данные должны быть сохранены в облаке.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-124">All data must be persisted into the cloud.</span></span> <span data-ttu-id="cc2d4-125">Кроме того, некоторые аспекты приложения будут дополнительно контролироваться естественным языком с помощью бота.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-125">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="cc2d4-126">Возможности</span><span class="sxs-lookup"><span data-stu-id="cc2d4-126">Features</span></span>

* <span data-ttu-id="cc2d4-127">Базовое управление данными и изображениями.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-127">Basic managing of data and images</span></span>
* <span data-ttu-id="cc2d4-128">Обучение и обнаружение изображений.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-128">Image training and detection</span></span>
* <span data-ttu-id="cc2d4-129">Хранение пространственного положения и инструкций.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-129">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="cc2d4-130">Бот-помощник для использования некоторых возможностей с помощью естественного языка.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-130">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="cc2d4-131">Облачные службы Azure</span><span class="sxs-lookup"><span data-stu-id="cc2d4-131">Azure Cloud services</span></span>

<span data-ttu-id="cc2d4-132">Чтобы разрешить необходимые функции для приложения, вы будете использовать указанные ниже **облачные службы Azure**.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-132">To solve the required features for the application, you will use these **Azure Cloud** services:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="cc2d4-133">Служба хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="cc2d4-133">Azure Storage</span></span>

<span data-ttu-id="cc2d4-134">Для решения сохраняемости будет использоваться [служба хранилища Azure](https://azure.microsoft.com/services/storage/).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-134">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="cc2d4-135">Она позволяет хранить данные в таблице и отправлять большие двоичные файлы, например изображения.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-135">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="cc2d4-136">Пользовательское визуальное распознавание Azure</span><span class="sxs-lookup"><span data-stu-id="cc2d4-136">Azure Custom Vision</span></span>

<span data-ttu-id="cc2d4-137">С помощью [Пользовательского визуального распознавания Azure](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (в составе [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) можно связать с *отслеживаемыми объектами* набор изображений, обучить модель машинного обучения в наборе и определить *отслеживаемый объект*.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-137">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="cc2d4-138">Пространственные привязки Azure</span><span class="sxs-lookup"><span data-stu-id="cc2d4-138">Azure Spatial Anchors</span></span>

<span data-ttu-id="cc2d4-139">Чтобы сохранить расположение *отслеживаемого объекта* и предоставить инструкции по его поиску, используйте [Пространственные привязки Azure](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-139">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="cc2d4-140">Служба Azure Bot</span><span class="sxs-lookup"><span data-stu-id="cc2d4-140">Azure Bot Service</span></span>

<span data-ttu-id="cc2d4-141">Приложение в основном управляется через традиционный пользовательский интерфейс, поэтому вы используете [службу Azure Bot](https://azure.microsoft.com/services/bot-service/), чтобы добавить некоторую индивидуальность и использовать новый метод взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-141">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc2d4-142">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="cc2d4-142">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="cc2d4-143">Если вы еще не прошли руководства из серии, посвященной [началу работы](mr-learning-base-01.md), мы рекомендуем начать знакомство именно с этой серии.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-143">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="cc2d4-144">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-144">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="cc2d4-145">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-145">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="cc2d4-146">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-146">Some basic C# programming ability</span></span>
* <span data-ttu-id="cc2d4-147">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-147">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="cc2d4-148">Подключенная веб-камера, если вы хотите выполнить тестирование из редактора Unity.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-148">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="cc2d4-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.X и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="cc2d4-150">Рекомендуемая версия Unity для этой серии учебников — Unity 2019.3.X.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-150">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="cc2d4-151">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-151">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="cc2d4-152">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="cc2d4-152">Creating and preparing the Unity project</span></span>

<span data-ttu-id="cc2d4-153">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-153">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="cc2d4-154">Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:</span><span class="sxs-lookup"><span data-stu-id="cc2d4-154">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="cc2d4-155">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *Azure Cloud Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-155">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="cc2d4-156">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-156">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="cc2d4-157">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-157">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="cc2d4-158">Импорт набора средств для смешанной реальности (MRTK).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-158">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="cc2d4-159">Настройка проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-159">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="cc2d4-160">[Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и назначение ей понятного имени, например *AzureCloudServices.*</span><span class="sxs-lookup"><span data-stu-id="cc2d4-160">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="cc2d4-161">Затем следуйте инструкциям по [изменению параметра отображения для отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), чтобы указать профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** для сцены и значение **Occlusion** (Перекрытие) для параметра отображения сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-161">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="cc2d4-162">Установка встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="cc2d4-162">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="cc2d4-163">В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-163">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="cc2d4-165">Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-165">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="cc2d4-166">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="cc2d4-166">Importing the tutorial assets</span></span>

<span data-ttu-id="cc2d4-167">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="cc2d4-167">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="cc2d4-168">[Хранилище Azure для Unity](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-168">[Azure storage for Unity](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)</span></span>
* [<span data-ttu-id="cc2d4-169">Пространственные привязки Azure</span><span class="sxs-lookup"><span data-stu-id="cc2d4-169">Azure Spatial Anchors</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [<span data-ttu-id="cc2d4-170">MRTK.Tutorials.AzureCloudServices</span><span class="sxs-lookup"><span data-stu-id="cc2d4-170">MRTK.Tutorials.AzureCloudServices</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> <span data-ttu-id="cc2d4-171">Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-171">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="cc2d4-172">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="cc2d4-172">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="cc2d4-174">Создание и подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="cc2d4-174">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="cc2d4-175">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-175">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="cc2d4-176">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-176">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="cc2d4-177">Удерживая нажатой клавишу CTRL, щелкните заготовки **SceneController**, **RootMenu** и **DataManager**, чтобы выбрать их:</span><span class="sxs-lookup"><span data-stu-id="cc2d4-177">While holding down the CTRL button, click on **SceneController**, **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="cc2d4-179">**SceneController (prefab)** (SceneController — заготовка) содержит два скрипта: **SceneController (script)** (SceneController — скрипт) и **UnityDispatcher (script)** (UnityDispatcher — скрипт).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-179">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **UnityDispatcher (script)**.</span></span> <span data-ttu-id="cc2d4-180">Компонент скрипта **SceneController** содержит несколько функций взаимодействия с пользователем и упрощает использование функции фотозахвата. **UnityDispatcher** является вспомогательным классом, позволяющим выполнять действия в основном потоке Unity.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-180">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **UnityDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="cc2d4-181">**RootMenu (prefab)** (RootMenu — заготовка) является основной заготовкой пользовательского интерфейса, которая содержит все окна пользовательского интерфейса, подключенные друг к другу через различные небольшие компоненты скрипта и управляющие общим потоком интерфейса приложения.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-181">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="cc2d4-182">**DataManager (prefab)** (DataManager — заготовка) отвечает за взаимодействие с хранилищем Azure. Она будет описана в следующем учебнике.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-182">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="cc2d4-183">Теперь, когда все три заготовки будут выбраны, перетащите их вместе в окно "Иерархия", чтобы добавить в сцену:</span><span class="sxs-lookup"><span data-stu-id="cc2d4-183">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="cc2d4-185">Чтобы перенести фокус на объекты сцены, дважды щелкните объект **RootMenu** и немного уменьшите масштаб представления:</span><span class="sxs-lookup"><span data-stu-id="cc2d4-185">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="cc2d4-187">Если вы считаете, что большие значки в сцене (как большие "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-187">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="cc2d4-188">Настройка сцены</span><span class="sxs-lookup"><span data-stu-id="cc2d4-188">Configuring the scene</span></span>

<span data-ttu-id="cc2d4-189">В этом разделе вы будете вместе соединять объекты *SceneManager*, *DataManager* и *RootMenu*, чтобы подготовить рабочую сцену к работе со следующим учебником по [интеграции службы хранилища Azure](mr-learning-azure-01.md).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-189">In this section, you will connect *SceneManager*, *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="cc2d4-190">Соединение объектов</span><span class="sxs-lookup"><span data-stu-id="cc2d4-190">Connect the objects</span></span>

<span data-ttu-id="cc2d4-191">В окне Hierarchy (Иерархия) выберите объект **DataManager**:</span><span class="sxs-lookup"><span data-stu-id="cc2d4-191">In the Hierarchy window, select the **DataManager** object:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="cc2d4-193">В окне Inspector (Инспектор) найдите компонент **DataManager (Script)** (DataManager — скрипт), вы увидите пустой слот в событии **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="cc2d4-193">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="cc2d4-194">Теперь в окне Hierarchy (Иерархия) перетащите объект **SceneController** в событие **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="cc2d4-194">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="cc2d4-196">Вы увидите, что раскрывающееся меню события стало активным, щелкните его и перейдите к **SceneController**. В подменю выберите параметр **init ()** :</span><span class="sxs-lookup"><span data-stu-id="cc2d4-196">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="cc2d4-198">В окне Hierarchy (Иерархия) выберите объект **SceneController**. В окне Inspector (Инспектор) вы найдете компонент **SceneController (script)** (SceneController — скрипт).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-198">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="cc2d4-200">Отобразятся несколько незаполненных полей. Заполните их.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-200">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="cc2d4-201">Переместите объект **DataManager** из окна Hierarchy (Иерархия) в поле *Data Manager* (Диспетчер данных) и переместите GameObject **RootMenu** из окна Hierarchy (Иерархия) в поле *Main Menu* (Главное меню).</span><span class="sxs-lookup"><span data-stu-id="cc2d4-201">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="cc2d4-203">Теперь сцена подготовлена для работы со следующими учебниками.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-203">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="cc2d4-204">Не забудьте сохранить ее в проекте.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-204">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="cc2d4-205">Подготовка конвейера сборки проекта</span><span class="sxs-lookup"><span data-stu-id="cc2d4-205">Prepare project build pipeline</span></span>

<span data-ttu-id="cc2d4-206">Хотя в проект еще нужно добавлять содержимое, выполните несколько действий, чтобы проект был готов к созданию **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-206">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="cc2d4-207">1. Добавление дополнительных требуемых возможностей</span><span class="sxs-lookup"><span data-stu-id="cc2d4-207">1. Add additional required capabilities</span></span>

<span data-ttu-id="cc2d4-208">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:</span><span class="sxs-lookup"><span data-stu-id="cc2d4-208">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="cc2d4-210">В окне параметров проекта выберите элемент **Player** (Проигрыватель), а затем — **Publishing Settings** (Параметры публикации):</span><span class="sxs-lookup"><span data-stu-id="cc2d4-210">In the Project Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="cc2d4-212">В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient** (Интернет-клиент), **Microphone** (Микрофон) и **SpatialPerception** (Пространственное восприятие), которые вы включили при создании проекта в начале работы с этим учебником.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-212">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="cc2d4-213">Теперь включите возможности **InternetClientServer** (Сервер интернет-клиента), **PrivateNetworkClientServer** (Сервер клиента частной сети) и **Webcam** (Веб-камера):</span><span class="sxs-lookup"><span data-stu-id="cc2d4-213">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **Webcam** capabilities:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="cc2d4-215">2. Разверните приложение на устройстве HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cc2d4-215">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="cc2d4-216">Не все функции, которые будут использоваться в этой серии учебников, можно выполнять внутри редактора Unity. Это означает, что вам необходимо получить сведения о развертывании приложения на устройстве HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-216">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="cc2d4-217">Чтобы вспомнить, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, воспользуйтесь инструкциями из раздела о [разработке приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2) в учебнике по началу работы.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-217">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="cc2d4-218">3. Запустите приложение на HoloLens 2 и следуйте предоставленным инструкциям</span><span class="sxs-lookup"><span data-stu-id="cc2d4-218">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="cc2d4-219">Все службы Azure используют Интернет, поэтому обеспечьте подключение устройства к Интернету.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-219">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="cc2d4-220">Когда приложение запускается на устройстве, предоставьте доступ к следующим запрошенным возможностям:</span><span class="sxs-lookup"><span data-stu-id="cc2d4-220">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="cc2d4-221">микрофон</span><span class="sxs-lookup"><span data-stu-id="cc2d4-221">Microphone</span></span>
* <span data-ttu-id="cc2d4-222">Камера</span><span class="sxs-lookup"><span data-stu-id="cc2d4-222">Camera</span></span>

<span data-ttu-id="cc2d4-223">Эти функции необходимы для правильной работы таких служб, как *чат-бот* и *Пользовательское визуальное распознавание*.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-223">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="cc2d4-224">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="cc2d4-224">Congratulations</span></span>

<span data-ttu-id="cc2d4-225">Здесь вы ознакомились с серией учебников, узнали о функциях, которые будете реализовывать, и о том, как согласовывать **облачные службы Azure**, чтобы реализовать приложение *HoloLens 2*.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-225">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="cc2d4-226">Вы добавили необходимые компоненты в проект и подготовили сцену для работы с этой серией учебников.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-226">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="cc2d4-227">На следующем уроке вы будете использовать хранилище Azure в качестве облачного решения для сохранения данных и изображений.</span><span class="sxs-lookup"><span data-stu-id="cc2d4-227">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

[<span data-ttu-id="cc2d4-228">Следующее руководство: 2. Интеграция службы хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="cc2d4-228">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)
