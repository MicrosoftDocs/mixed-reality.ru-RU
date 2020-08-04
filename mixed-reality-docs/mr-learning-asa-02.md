---
title: Руководства по Пространственным привязкам Azure — часть 2. Начало работы с Пространственными привязками Azure
description: Пройдите этот курс и узнайте, как реализовать Пространственные привязки Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d117839e51e586f4b905a20510fffc670d34cd4e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376496"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="d4c10-105">2. Начало работы с Пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="d4c10-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="d4c10-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="d4c10-106">Overview</span></span>

<span data-ttu-id="d4c10-107">В этом руководстве показано, как запускать и завершать сеанс Пространственных привязок Azure, а также как создавать, отправлять и скачивать Пространственные привязки Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="d4c10-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="d4c10-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="d4c10-108">Objectives</span></span>

* <span data-ttu-id="d4c10-109">Изучите основы разработки Пространственных привязок Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d4c10-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="d4c10-110">Узнайте, как создавать пространственные привязки и получать их из Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="d4c10-111">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="d4c10-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="d4c10-112">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="d4c10-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="d4c10-113">Для этого сначала выполните инструкции из руководства [Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md) (исключая раздел [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2)), в том числе следующие действия:</span><span class="sxs-lookup"><span data-stu-id="d4c10-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="d4c10-114">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="d4c10-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="d4c10-115">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="d4c10-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="d4c10-116">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="d4c10-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="d4c10-117">Импорт набора средств для Смешанной реальности (MRTK).</span><span class="sxs-lookup"><span data-stu-id="d4c10-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="d4c10-118">Настройка проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="d4c10-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="d4c10-119">[Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей понятного имени, например *AzureSpatialAnchors.*</span><span class="sxs-lookup"><span data-stu-id="d4c10-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="d4c10-120">Затем выполните инструкции из раздела [Изменение параметра отображения отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option):</span><span class="sxs-lookup"><span data-stu-id="d4c10-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="d4c10-121">Измените **профиль конфигурации MRTK** на **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="d4c10-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="d4c10-122">Измените **параметры отображения сетки отслеживания пространственного положения** на **Occlusion** (Загораживание).</span><span class="sxs-lookup"><span data-stu-id="d4c10-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="d4c10-123">Установка встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="d4c10-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="d4c10-124">В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.</span><span class="sxs-lookup"><span data-stu-id="d4c10-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d4c10-126">Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.</span><span class="sxs-lookup"><span data-stu-id="d4c10-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="d4c10-127">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="d4c10-127">Importing the tutorial assets</span></span>

<span data-ttu-id="d4c10-128">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="d4c10-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="d4c10-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (версия 2.2.1);</span><span class="sxs-lookup"><span data-stu-id="d4c10-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* <span data-ttu-id="d4c10-130">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="d4c10-130">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)</span></span>
* <span data-ttu-id="d4c10-131">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="d4c10-131">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)</span></span>

<span data-ttu-id="d4c10-132">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="d4c10-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="d4c10-134">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт набора средств для Смешанной реальности](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="d4c10-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="d4c10-135">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="d4c10-135">Preparing the scene</span></span>

<span data-ttu-id="d4c10-136">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="d4c10-136">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="d4c10-137">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Активы > MRTK.Tutorials.AzureSpatialAnchors > Заготовки), а затем щелкните и перетащите следующие заготовки в окно иерархии, чтобы добавить их в сцену:</span><span class="sxs-lookup"><span data-stu-id="d4c10-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="d4c10-138">**ButtonParent;**</span><span class="sxs-lookup"><span data-stu-id="d4c10-138">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="d4c10-139">**DebugWindow;**</span><span class="sxs-lookup"><span data-stu-id="d4c10-139">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="d4c10-140">**Instructions;**</span><span class="sxs-lookup"><span data-stu-id="d4c10-140">**Instructions** prefabs</span></span>
* <span data-ttu-id="d4c10-141">**ParentAnchor.**</span><span class="sxs-lookup"><span data-stu-id="d4c10-141">**ParentAnchor** prefabs</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="d4c10-143">Если вы считаете, что большие значки в сцене (например, большие значки "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение, как показано на рисунке выше.</span><span class="sxs-lookup"><span data-stu-id="d4c10-143">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="d4c10-144">Настройка кнопок для управления сценой</span><span class="sxs-lookup"><span data-stu-id="d4c10-144">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="d4c10-145">В этом разделе показано, как добавить в сцену скрипты, чтобы создать серию событий кнопок для демонстрации базовых приемов работы, а также поведения локальных привязок и Пространственных привязок Azure в приложении.</span><span class="sxs-lookup"><span data-stu-id="d4c10-145">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="d4c10-146">В окне иерархии разверните объект **ButtonParent** и выберите первый дочерний объект с именем **StartAzureSession**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d4c10-146">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d4c10-147">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="d4c10-147">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d4c10-148">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StartAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="d4c10-148">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="d4c10-150">В окне иерархии выберите следующую кнопку с именем **StopAzureSession**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d4c10-150">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d4c10-151">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="d4c10-151">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d4c10-152">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StopAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="d4c10-152">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="d4c10-154">В окне иерархии выберите следующую кнопку с именем **CreateAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d4c10-154">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d4c10-155">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="d4c10-155">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d4c10-156">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **CreateAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="d4c10-156">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="d4c10-157">В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor**, чтобы сделать его аргументом функции CreateAzureAnchor ().</span><span class="sxs-lookup"><span data-stu-id="d4c10-157">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="d4c10-159">В окне иерархии выберите следующую кнопку с именем **RemoveLocalAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d4c10-159">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d4c10-160">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="d4c10-160">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d4c10-161">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **RemoveLocalAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="d4c10-161">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="d4c10-162">В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor**, чтобы сделать его аргументом функции RemoveLocalAnchor ().</span><span class="sxs-lookup"><span data-stu-id="d4c10-162">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="d4c10-164">В окне иерархии выберите следующую кнопку с именем **FindAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d4c10-164">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d4c10-165">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="d4c10-165">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d4c10-166">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **FindAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="d4c10-166">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="d4c10-168">В окне иерархии выберите следующую кнопку с именем **DeleteAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d4c10-168">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d4c10-169">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="d4c10-169">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d4c10-170">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **DeleteAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="d4c10-170">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="d4c10-172">Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="d4c10-172">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="d4c10-173">В окне иерархии выберите объект **ParentAnchor**. Затем в окне инспектора найдите компонент **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт).</span><span class="sxs-lookup"><span data-stu-id="d4c10-173">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="d4c10-174">Укажите в разделе **Credentials** (Учетные данные) данные учетной записи Пространственных привязок Azure, созданной при работе с разделом [предварительных требований](mr-learning-asa-01.md#prerequisites) для этой серии руководств.</span><span class="sxs-lookup"><span data-stu-id="d4c10-174">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="d4c10-175">В поле **Spatial Anchors Account ID** (Идентификатор учетной записи пространственных привязок) вставьте **идентификатор учетной записи** Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-175">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="d4c10-176">В поле **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок) вставьте первичный или вторичный **ключ доступа** учетной записи Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-176">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="d4c10-178">Изучение базового поведения Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="d4c10-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="d4c10-179">Пространственные привязки Azure не могут работать в Unity. Поэтому для проверки функциональных возможностей этой службы вам нужно создать проект и развернуть приложение на устройстве.</span><span class="sxs-lookup"><span data-stu-id="d4c10-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="d4c10-180">Сведения о том, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="d4c10-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="d4c10-181">Запустив приложение на устройстве, выполните инструкции, отображаемые на панели с инструкциями из руководства по Пространственным привязкам Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="d4c10-182">Переместите куб в другое расположение.</span><span class="sxs-lookup"><span data-stu-id="d4c10-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="d4c10-183">Запустите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-183">Start Azure Session</span></span>
1. <span data-ttu-id="d4c10-184">Создайте привязку Azure (она создается в расположении, где находится куб).</span><span class="sxs-lookup"><span data-stu-id="d4c10-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="d4c10-185">Завершите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-185">Stop Azure Session</span></span>
1. <span data-ttu-id="d4c10-186">Удалите локальную привязку (позволяет пользователю перемещать куб).</span><span class="sxs-lookup"><span data-stu-id="d4c10-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="d4c10-187">Переместите куб в другое место.</span><span class="sxs-lookup"><span data-stu-id="d4c10-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="d4c10-188">Запустите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-188">Start Azure Session</span></span>
1. <span data-ttu-id="d4c10-189">Выполните поиск привязки Azure (размещение куба в расположении, которое мы настроили на шаге 3).</span><span class="sxs-lookup"><span data-stu-id="d4c10-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="d4c10-190">Удалите привязку Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="d4c10-191">Завершите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-191">Stop Azure session</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="d4c10-193">Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки. Поэтому обеспечьте подключение устройства к Интернету.</span><span class="sxs-lookup"><span data-stu-id="d4c10-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="d4c10-194">Привязка к взаимодействию</span><span class="sxs-lookup"><span data-stu-id="d4c10-194">Anchoring an experience</span></span>

<span data-ttu-id="d4c10-195">В предыдущих разделах вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="d4c10-196">С помощью куба мы представили и визуализировали родительский объект игры с прикрепленной привязкой.</span><span class="sxs-lookup"><span data-stu-id="d4c10-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="d4c10-197">Из этого раздела вы узнаете, как привязать взаимодействие целиком, разместив его в дочернем элементе объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="d4c10-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="d4c10-198">В окне иерархии выберите объект **ParentAnchor**. Затем в окне инспектора настройте компонент **Transform** (Преобразование).</span><span class="sxs-lookup"><span data-stu-id="d4c10-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="d4c10-199">Измените значение **Scale X** (Масштаб Х) на 1.1.</span><span class="sxs-lookup"><span data-stu-id="d4c10-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="d4c10-200">Измените значение **Scale Z** (Масштаб Z) на 1.1.</span><span class="sxs-lookup"><span data-stu-id="d4c10-200">Change **Scale Z** to 1.1</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="d4c10-202">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** (Активы > MRTK.Tutorials.GettingStarted > Заготовки > Rover), а затем щелкните и перетащите заготовку **RoverExplorer_Complete** в окно иерархии, чтобы добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="d4c10-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="d4c10-204">Выбрав добавленный объект RoverModule_Complete в окне иерархии, перетащите его в объект **ParentAnchor**, чтобы сделать его дочерним объектом объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="d4c10-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="d4c10-206">Если сейчас вы перестроите проект и развернете приложение на устройстве, вы сможете перемещать все средства взаимодействия с Rover Explorer, передвигая куб измененного размера.</span><span class="sxs-lookup"><span data-stu-id="d4c10-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="d4c10-207">Есть разные виды взаимодействия с пользователем для изменения положения, в том числе: перемещение объекта (например, куба в этом руководстве), включение ограничивающего прямоугольника вокруг средств взаимодействия нажатием кнопки, применение манипуляторов положения и вращения и другие.</span><span class="sxs-lookup"><span data-stu-id="d4c10-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d4c10-208">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d4c10-208">Congratulations</span></span>

<span data-ttu-id="d4c10-209">В рамках этого руководства вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="d4c10-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="d4c10-210">В этом руководстве показано, как использовать разные кнопки для запуска и завершения сеанса Пространственных привязок Azure,</span><span class="sxs-lookup"><span data-stu-id="d4c10-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="d4c10-211">а также создания, отправки и скачивания Пространственных привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="d4c10-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="d4c10-212">В следующем руководстве показано, как сохранить идентификаторы привязок Azure на устройстве HoloLens 2, чтобы их можно было извлечь даже после перезапуска приложения, и как передавать идентификаторы привязок между несколькими устройствами для пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="d4c10-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="d4c10-213">Следующее руководство: 3. Сохранение, получение и совместное использование пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="d4c10-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
