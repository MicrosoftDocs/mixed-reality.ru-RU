---
title: Руководства по использованию службы "Речь" в Azure, часть 1. Интеграция и использование средств распознавания и транскрибирования речи
description: В рамках этого курса вы узнаете, как реализовать пакет SDK службы "Речь" в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f376ab268e9c2869e48b325fa728672a16ee6d32
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303685"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="a361c-105">1. Интеграция и использование средств распознавания и транскрибирования речи</span><span class="sxs-lookup"><span data-stu-id="a361c-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="a361c-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="a361c-106">Overview</span></span>


<span data-ttu-id="a361c-107">В этой серии руководств вы создадите приложение смешанной реальности и на его примере изучите использование служб распознавания речи Azure с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a361c-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="a361c-108">Изучив эту серию руководств, вы сможете применять микрофон устройства для транскрибирования речи в текст в режиме реального времени, переводить эту речь на другие языки и применять распознавание намерений для анализа голосовых команд с применением искусственного интеллекта.</span><span class="sxs-lookup"><span data-stu-id="a361c-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="a361c-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="a361c-109">Objectives</span></span>

* <span data-ttu-id="a361c-110">Сведения об интеграции службы речи Azure с приложением HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a361c-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="a361c-111">Сведения об использовании функции распознавания речи для транскрибирования текста</span><span class="sxs-lookup"><span data-stu-id="a361c-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a361c-112">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="a361c-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="a361c-113">Если вы еще не прошли руководства из серии, посвященной [началу работы](mr-learning-base-01.md), мы рекомендуем начать знакомство именно с этой серии.</span><span class="sxs-lookup"><span data-stu-id="a361c-113">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="a361c-114">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="a361c-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="a361c-115">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="a361c-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a361c-116">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="a361c-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="a361c-117">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="a361c-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="a361c-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="a361c-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a361c-119">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="a361c-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="a361c-120">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="a361c-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="a361c-121">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="a361c-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="a361c-122">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="a361c-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="a361c-123">Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:</span><span class="sxs-lookup"><span data-stu-id="a361c-123">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="a361c-124">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="a361c-124">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="a361c-125">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="a361c-125">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="a361c-126">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="a361c-126">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="a361c-127">Импорт набора средств для Смешанной реальности (MRTK).</span><span class="sxs-lookup"><span data-stu-id="a361c-127">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="a361c-128">Настройка проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="a361c-128">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="a361c-129">[Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей понятного имени, например *AzureSpeechServices*.</span><span class="sxs-lookup"><span data-stu-id="a361c-129">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="a361c-130">Затем следуйте инструкциям по [изменению параметра отображения для отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), чтобы указать профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** для сцены и значение **Occlusion** (Перекрытие) для параметра отображения сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="a361c-130">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="a361c-131">Настройка поведения для начала речевых команд</span><span class="sxs-lookup"><span data-stu-id="a361c-131">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="a361c-132">Поскольку для распознавания и транскрибирования речи вы будете применять пакет SDK "Речь", вам нужно настроить речевые команды MRTK так, чтобы они не мешали работе пакета SDK "Речь".</span><span class="sxs-lookup"><span data-stu-id="a361c-132">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="a361c-133">Чтобы добиться этого, измените поведение начала речевых команд с Auto Start (Автозапуск) на Manual Start (Запуск вручную).</span><span class="sxs-lookup"><span data-stu-id="a361c-133">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="a361c-134">Выделив объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), выберите в окне Inspector (Инспектор) вкладку **Input** (Ввод), клонируйте профили **DefaultHoloLens2InputSystemProfile** и **DefaultMixedRealitySpeechCommandsProfile**, а затем измените для речевых команд параметр **Start Behavior** (Поведение начала) на **Manual Start** (Старт вручную):</span><span class="sxs-lookup"><span data-stu-id="a361c-134">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="a361c-136">Сведения о том, как правильно клонировать и настраивать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="a361c-136">For a reminder on how to clone and configure MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="a361c-137">Настройка функциональных возможностей</span><span class="sxs-lookup"><span data-stu-id="a361c-137">Configuring the capabilities</span></span>

<span data-ttu-id="a361c-138">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player** >  **Publishing Settings** (Проигрыватель > Параметры публикации).</span><span class="sxs-lookup"><span data-stu-id="a361c-138">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="a361c-140">В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient** (Интернет-клиент), **Microphone** (Микрофон) и **SpatialPerception** (Пространственное восприятие), которые вы включили при создании проекта в начале работы с этим руководством.</span><span class="sxs-lookup"><span data-stu-id="a361c-140">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="a361c-141">Теперь включите возможности **InternetClientServer** (Сервер интернет-клиента) и **PrivateNetworkClientServer** (Сервер клиента частной сети):</span><span class="sxs-lookup"><span data-stu-id="a361c-141">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="a361c-143">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="a361c-143">Importing the tutorial assets</span></span>

<span data-ttu-id="a361c-144">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="a361c-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="a361c-145">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (последняя версия);</span><span class="sxs-lookup"><span data-stu-id="a361c-145">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="a361c-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a361c-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* <span data-ttu-id="a361c-147">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="a361c-147">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)</span></span>

> [!TIP]
> <span data-ttu-id="a361c-148">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт набора средств для Смешанной реальности](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="a361c-148">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="a361c-149">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="a361c-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="a361c-151">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="a361c-151">Preparing the scene</span></span>

<span data-ttu-id="a361c-152">В этом разделе вы подготовите сцену, добавив заготовку для руководства, и настроите компонент Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт) для управления сценой.</span><span class="sxs-lookup"><span data-stu-id="a361c-152">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="a361c-153">В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** и перетащите заготовку **Lunarcom**в окно Hierarchy (Иерархия), чтобы добавить ее в сцену:</span><span class="sxs-lookup"><span data-stu-id="a361c-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="a361c-155">В окне Hierarchy (Иерархия) сохраните выделение объекта **Lunarcom**, а в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Controller (Script)** (Контроллер Lunarcom — скрипт) к объекту Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="a361c-155">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="a361c-157">Компонент Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт) не входит в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="a361c-157">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="a361c-158">Он был предоставлен с активами для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="a361c-158">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="a361c-159">Сохраняя выделение объекта **Lunarcom**, разверните его для просмотра списка дочерних объектов, затем перетащите объект **Terminal** (Терминал) в поле **Terminal** (Терминал) объекта Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт):</span><span class="sxs-lookup"><span data-stu-id="a361c-159">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="a361c-161">Сохраняя выделение объекта **Lunarcom**, разверните объект Terminal (Терминал) для просмотра списка его дочерних объектов, затем перетащите объект **ConnectionLight** (Индикатор подключения) в поле **ConnectionLight** (Индикатор подключения) объекта Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт), а объект **OutputText** (Выходной текст) — в поле **Output Text** (Выходной текст):</span><span class="sxs-lookup"><span data-stu-id="a361c-161">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="a361c-163">Сохраняя выделение объекта **Lunarcom**, разверните объект Buttons (Кнопки), чтобы открыть список его дочерних объектов, а затем в окне "Инспектор" разверните список **Buttons** (Кнопки), установите для его параметра **Size** (Размер) значение 3 и перетащите объекты **MicButton**, **SatelliteButton** и **RocketButton** в поля **Элемент** с номерами 0, 1 и 2, соответственно:</span><span class="sxs-lookup"><span data-stu-id="a361c-163">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="a361c-165">Подключение проекта Unity к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="a361c-165">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="a361c-166">Чтобы использовать службу речи Azure, потребуется создать ресурс Azure и получить ключ API для службы "Речь".</span><span class="sxs-lookup"><span data-stu-id="a361c-166">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="a361c-167">Выполните инструкции [по применению бесплатной версии службы "Речь"](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) и выясните регион (расположение) вашей службы и значение ключа API (это может быть Key1 или Key2).</span><span class="sxs-lookup"><span data-stu-id="a361c-167">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="a361c-168">В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) найдите в компоненте **Lunarcom Controller (Script)** (Контроллер Lunarcom — скрипт) раздел **Speech SDK Credentials** (Учетные данные пакета SDK) и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="a361c-168">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="a361c-169">В поле **Speech Service API Key** (Ключ API службы "Речь") введите значение ключа API (Key1 или Key2).</span><span class="sxs-lookup"><span data-stu-id="a361c-169">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="a361c-170">В поле **Speech Service Region** (Регион службы "Речь") введите значение региона (расположения) службы, переведя все буквы в нижний регистр и удалив пробелы.</span><span class="sxs-lookup"><span data-stu-id="a361c-170">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="a361c-172">Использование функции распознавания речи для транскрибирования речи</span><span class="sxs-lookup"><span data-stu-id="a361c-172">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="a361c-173">В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Speech Recognizer (Script)** (Распознаватель речи Lunarcom — скрипт) к объекту Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="a361c-173">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a361c-175">Компонент Lunarcom Speech Recognizer (Script) (Распознаватель речи Lunarcom — скрипт) не входит в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="a361c-175">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="a361c-176">Он был предоставлен с активами для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="a361c-176">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="a361c-177">Войдя в игровой режим, вы сможете проверить распознавание речи. Для начала нажмите кнопку микрофона.</span><span class="sxs-lookup"><span data-stu-id="a361c-177">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="a361c-179">Теперь, если на компьютере подключен микрофон, любой сказанный вами текст будет выводиться на панели терминала:</span><span class="sxs-lookup"><span data-stu-id="a361c-179">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="a361c-181">Этому приложению требуется подключение к Azure, поэтому не забудьте проверить связь компьютера или устройства с Интернетом.</span><span class="sxs-lookup"><span data-stu-id="a361c-181">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a361c-182">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="a361c-182">Congratulations</span></span>

<span data-ttu-id="a361c-183">Вы успешно реализовали функцию распознавания речи на платформе Azure.</span><span class="sxs-lookup"><span data-stu-id="a361c-183">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="a361c-184">Запустите приложение на устройстве и убедитесь, что все работает правильно.</span><span class="sxs-lookup"><span data-stu-id="a361c-184">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="a361c-185">В следующем учебнике вы узнаете, как выполнять команды с помощью распознавания речи Azure.</span><span class="sxs-lookup"><span data-stu-id="a361c-185">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

[<span data-ttu-id="a361c-186">Следующее руководство: 2. Использование функции распознавания речи для выполнения команд</span><span class="sxs-lookup"><span data-stu-id="a361c-186">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
