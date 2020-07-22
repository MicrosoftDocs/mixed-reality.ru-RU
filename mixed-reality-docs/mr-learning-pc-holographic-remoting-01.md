---
title: Учебники по голографическому удаленному взаимодействию с ПК, часть 1. Начало работы с голографическим удаленным взаимодействием с ПК
description: Пройдите этот курс, чтобы узнать, как реализовать удаленное взаимодействие в режиме смешанной реальности между вашим компьютером и HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/19/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbbad9548abeb1b8392b99d187b5b051d5b4ddd4
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306735"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="98954-105">1. Начало работы с голографическим удаленным взаимодействием с ПК</span><span class="sxs-lookup"><span data-stu-id="98954-105">1. Getting started with PC Holographic Remoting</span></span>

## <a name="overview"></a><span data-ttu-id="98954-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="98954-106">Overview</span></span>

  <span data-ttu-id="98954-107">Вас приветствует серия учебников по HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="98954-107">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="98954-108">Из этой серии учебников из двух частей вы узнаете, как выполнить демонстрацию взаимодействия со смешанной реальностью и как создать приложение на ПК для голографического удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="98954-108">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

   <span data-ttu-id="98954-109">Вы научитесь создавать взаимодействие со смешанной реальностью, используя сведения из [этого учебника](mr-learning-pc-holographic-remoting-01.md).</span><span class="sxs-lookup"><span data-stu-id="98954-109">In this tutorial, [Create mixed reality experience](mr-learning-pc-holographic-remoting-01.md), you will learn how to create a mixed reality experience.</span></span> <span data-ttu-id="98954-110">Здесь будут продемонстрированы элементы пользовательского интерфейса, функции управления трехмерными моделями, обрезки моделей, а также функции отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="98954-110">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

  <span data-ttu-id="98954-111">Во втором учебнике вы научитесь [создавать приложение на ПК для голографического удаленного взаимодействия](mr-learning-pc-holographic-remoting-02.md)</span><span class="sxs-lookup"><span data-stu-id="98954-111">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="98954-112">и подключаться к HoloLens 2 в любой момент с помощью визуализации трехмерного содержимого в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="98954-112">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="98954-113">Задачи</span><span class="sxs-lookup"><span data-stu-id="98954-113">Objectives</span></span>

* <span data-ttu-id="98954-114">Импорт ресурсов и настройка сцены.</span><span class="sxs-lookup"><span data-stu-id="98954-114">Import assets and set up the scene</span></span>
* <span data-ttu-id="98954-115">Взаимодействие с голограммами через кнопки и элементы пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="98954-115">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="98954-116">Настройка трехмерных объектов для функции обрезки.</span><span class="sxs-lookup"><span data-stu-id="98954-116">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="98954-117">Получение сведений об активации подсказок с помощью отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="98954-117">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="98954-118">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="98954-118">Prerequisites</span></span>

* <span data-ttu-id="98954-119">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="98954-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="98954-120">Базовые навыки работы с C#.</span><span class="sxs-lookup"><span data-stu-id="98954-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="98954-121">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="98954-121">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="98954-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.X и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="98954-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X mounted, and the Universal Windows Platform Build Support module added</span></span>

><span data-ttu-id="98954-123">Настоятельно рекомендуется ознакомиться с серией учебников по началу работы или иметь хотя бы базовый опыт работы с Unity и MRTK.</span><span class="sxs-lookup"><span data-stu-id="98954-123">[!STRONGLY RECOMMENDED] Completed the Getting started tutorials series or some basic prior experience with Unity and MRTK</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98954-124">Рекомендуемая версия Unity для этой серии учебников — Unity 2019.3.X.</span><span class="sxs-lookup"><span data-stu-id="98954-124">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="98954-125">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="98954-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="98954-126">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="98954-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="98954-127">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="98954-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="98954-128">Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:</span><span class="sxs-lookup"><span data-stu-id="98954-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="98954-129">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="98954-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="98954-130">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="98954-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="98954-131">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="98954-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="98954-132">Импорт набора средств для смешанной реальности (MRTK).</span><span class="sxs-lookup"><span data-stu-id="98954-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="98954-133">Настройка проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="98954-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="98954-134">[Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей подходящего имени, например **Голографическое удаленное взаимодействие с ПК**.</span><span class="sxs-lookup"><span data-stu-id="98954-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="98954-135">Затем следуйте инструкциям по [изменению параметра отображения для отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), чтобы указать профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** для сцены.</span><span class="sxs-lookup"><span data-stu-id="98954-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="98954-136">Измените параметры отображения сетки отслеживания в пространстве на **Occlusion** (Загораживание).</span><span class="sxs-lookup"><span data-stu-id="98954-136">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="98954-137">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="98954-137">Importing the tutorial assets</span></span>

<span data-ttu-id="98954-138">Скачайте и **импортируйте** пакет [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="98954-138">Download and **import** the [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span></span>

>[!TIP]
> <span data-ttu-id="98954-139">Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="98954-139">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="98954-140">Когда вы завершите импорт активов для учебника, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="98954-140">After importing the tutorial assets, your Project window should look similar to this:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="98954-142">Настройка и подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="98954-142">Configuring and preparing the scene</span></span>

<span data-ttu-id="98954-143">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="98954-143">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="98954-144">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**.</span><span class="sxs-lookup"><span data-stu-id="98954-144">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="98954-145">Удерживая нажатой клавишу CTRL, щелкните шесть заготовок, перечисленных ниже.</span><span class="sxs-lookup"><span data-stu-id="98954-145">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="98954-146">ButtonParent;</span><span class="sxs-lookup"><span data-stu-id="98954-146">ButtonParent</span></span>
* <span data-ttu-id="98954-147">ClippingObjects;</span><span class="sxs-lookup"><span data-stu-id="98954-147">ClippingObjects</span></span>
* <span data-ttu-id="98954-148">HandSpatialMapButton;</span><span class="sxs-lookup"><span data-stu-id="98954-148">HandSpatialMapButton</span></span>
* <span data-ttu-id="98954-149">Инструкции</span><span class="sxs-lookup"><span data-stu-id="98954-149">Instructions</span></span>
* <span data-ttu-id="98954-150">ModelParent;</span><span class="sxs-lookup"><span data-stu-id="98954-150">ModelParent</span></span>
* <span data-ttu-id="98954-151">Платформа</span><span class="sxs-lookup"><span data-stu-id="98954-151">Platform</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="98954-153">Перетащите эти модели из папки заготовок в окно **Hierarchy** (Иерархия).</span><span class="sxs-lookup"><span data-stu-id="98954-153">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="98954-155">Чтобы перенести фокус на объекты сцены, дважды щелкните объект **ModelParent**, а затем снова немного увеличьте масштаб представления:</span><span class="sxs-lookup"><span data-stu-id="98954-155">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="98954-157">Если вы считаете, что большие значки в сцене (как большие "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение.</span><span class="sxs-lookup"><span data-stu-id="98954-157">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="98954-158">Настройка кнопок для управления сценой</span><span class="sxs-lookup"><span data-stu-id="98954-158">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="98954-159">В этом разделе вы добавите скрипты в сцену, чтобы создать события кнопки, демонстрирующие базовые принципы переключения моделей и функций обрезки.</span><span class="sxs-lookup"><span data-stu-id="98954-159">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="98954-160">1. Настройка компонента Interactable (Script) (Интерактивный — скрипт)</span><span class="sxs-lookup"><span data-stu-id="98954-160">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="98954-161">В окне Hierarchy (Иерархия) разверните объект **ButtonParent** и выберите **NextButton**.</span><span class="sxs-lookup"><span data-stu-id="98954-161">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="98954-162">В окне Inspector (Инспектор) найдите компонент **Interactable (Script)** (Интерактивный — скрипт) и щелкните значок **+** в событии **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="98954-162">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="98954-164">Сохраняя объект **NextButton** выделенным в окне Hierarchy (Иерархия), щелкните и перетащите объект **ButtonParent** из окна (Иерархия) в пустое поле **None (Object)** (Отсутствует (объект)) только что созданного события, чтобы объект ButtonParent ожидал передачи данных о событии нажатия для этой кнопки:</span><span class="sxs-lookup"><span data-stu-id="98954-164">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="98954-166">Откройте раскрывающийся список **No Function** (Нет функции) того же события.</span><span class="sxs-lookup"><span data-stu-id="98954-166">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="98954-167">Затем выберите **ViewButtonControl** > **NextModel ()** , чтобы установить функцию **NextModel ()** в качестве действия, запускаемого при срабатывании события нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="98954-167">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="98954-169">2. Настройка остальных кнопок</span><span class="sxs-lookup"><span data-stu-id="98954-169">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="98954-170">Для всех остальных кнопок повторно выполните процессы, которые описаны выше, чтобы назначить функции событиям **OnClick ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="98954-170">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="98954-171">Для объекта PreviousButton назначьте функцию **ViewButtonContro**l > **PreviousModel ()** .</span><span class="sxs-lookup"><span data-stu-id="98954-171">For PreviousButton object, assign the **ViewButtonContro**l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="98954-172">Для объекта ClippingButton выберите функцию **ToggleButton** > **ToggleClipping ()** .</span><span class="sxs-lookup"><span data-stu-id="98954-172">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="98954-173">3. Настройка компонентов View Button Control (Script) (Элемент управления кнопкой просмотра — скрипт) и Toggle Button (Script) (Выключатель — скрипт)</span><span class="sxs-lookup"><span data-stu-id="98954-173">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="98954-174">Теперь кнопки настроены, чтобы продемонстрировать функции переключения и обрезки модели.</span><span class="sxs-lookup"><span data-stu-id="98954-174">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="98954-175">Время добавить трехмерные модели и объекты обрезки в скрипт.</span><span class="sxs-lookup"><span data-stu-id="98954-175">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="98954-176">Мы предоставили шесть различных трехмерных моделей для демонстрации, разверните ***ModelParentobject***, чтобы предоставить эти трехмерные модели.</span><span class="sxs-lookup"><span data-stu-id="98954-176">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="98954-177">Сохраняя объект ButtonParent выделенным в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) выберите **View Button Control (Script)** (Элемент управления кнопкой просмотра — скрипт) и разверните переменную **Models** (Модели).</span><span class="sxs-lookup"><span data-stu-id="98954-177">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="98954-178">В поле **Size** (Размер) введите число трехмерных моделей, которые будут находиться в сцене.</span><span class="sxs-lookup"><span data-stu-id="98954-178">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="98954-179">В нашем случае — 6.</span><span class="sxs-lookup"><span data-stu-id="98954-179">In this case, it would be six.</span></span> <span data-ttu-id="98954-180">Будет создано поле для добавления новых трехмерных моделей.</span><span class="sxs-lookup"><span data-stu-id="98954-180">It will create fields for adding new 3D models.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="98954-182">Перетащите каждый дочерний объект объекта ModelParent в эти поля.</span><span class="sxs-lookup"><span data-stu-id="98954-182">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="98954-184">Перетащите объект **ClippingObjects** из окна Hierarchy (Иерархия) в компонент **Toggle Button (Script)** (Переключатель — скрипт) поля **Clipping Object** (Обрезаемый объект).</span><span class="sxs-lookup"><span data-stu-id="98954-184">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="98954-185">Старайтесь использовать только родительский объект кнопки.</span><span class="sxs-lookup"><span data-stu-id="98954-185">Stay in button parent object only.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="98954-187">В окне Hierarchy (Иерархия) выберите заготовку **ClippingObjects** и включите ее в окне Inspector (Инспектор), чтобы включить объекты обрезки.</span><span class="sxs-lookup"><span data-stu-id="98954-187">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="98954-188">Настройка объектов обрезки для включения функции обрезки</span><span class="sxs-lookup"><span data-stu-id="98954-188">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="98954-189">В этом разделе вы добавите отрисовщик дочерних объектов MarsCuriosityRover в отдельный объект обрезки, чтобы продемонстрировать обрезку модели MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="98954-189">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="98954-190">В окне Hierarchy (Иерархия) разверните объект **ClippingObjects**, чтобы предоставить три различных объекта обрезки, которые будут использоваться в этом проекте.</span><span class="sxs-lookup"><span data-stu-id="98954-190">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="98954-191">Чтобы настроить объект **ClippingSphere**, щелкните его, а затем в окне Inspector (Инспектор) выберите компонент **Clipping Sphere (Script)** (Обрезка сферы — скрипт).</span><span class="sxs-lookup"><span data-stu-id="98954-191">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="98954-192">Введите количество отрисовщиков в поле размера, которое необходимо добавить для трехмерной модели.</span><span class="sxs-lookup"><span data-stu-id="98954-192">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="98954-193">В этом случае для дочерних объектов MarsCuriosityRover добавьте 10 отрисовщиков.</span><span class="sxs-lookup"><span data-stu-id="98954-193">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="98954-194">Будут созданы поля для добавления отрисовщиков. Перетащите объекты дочерней модели MarsCuriosityRover в эти поля.</span><span class="sxs-lookup"><span data-stu-id="98954-194">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="98954-196">Выполните тот же процесс и добавьте отрисовщики дочерних объектов MarsCuriosityRover в объекты **ClippingBox** и **ClippingPlane**.</span><span class="sxs-lookup"><span data-stu-id="98954-196">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="98954-197">В этом учебнике для демонстрации функции обрезки будет использоваться только модель MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="98954-197">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="98954-198">Функции обрезки были добавлены к большему количеству моделей. В результате этого размер отрисовщика увеличился и были добавлены индивидуальные отрисовщики сетки.</span><span class="sxs-lookup"><span data-stu-id="98954-198">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="98954-199">Настройка отслеживания взгляда для выделения всплывающих подсказок</span><span class="sxs-lookup"><span data-stu-id="98954-199">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="98954-200">Из этого раздела вы узнаете, как включить отслеживание взгляда в нашем демонстрационном проекте.</span><span class="sxs-lookup"><span data-stu-id="98954-200">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="98954-201">Например, вы реализуете функции, чтобы выделить прикрепленные к деталям MarsCuriosityRover подсказки, когда вы на них смотрите, и скрыть их при отводе взгляда.</span><span class="sxs-lookup"><span data-stu-id="98954-201">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="98954-202">1. Определение целевых объектов и связанных с ними подсказок.</span><span class="sxs-lookup"><span data-stu-id="98954-202">1. Identify target objects and associated tooltips.</span></span>

<span data-ttu-id="98954-203">В окне Hierarchy (Иерархия) выберите объект ModelParent.</span><span class="sxs-lookup"><span data-stu-id="98954-203">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="98954-204">Разверните иерархию ***MarsCuriosity -> Rover***, чтобы найти пять основных деталей MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer** и **POI-RUHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="98954-204">Expand the ***MarsCuriosity -> Rover*** to find five main parts of the MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="98954-205">Обратите внимание на пять соответствующих объектов подсказок, связанных с деталями MarsCuriosityRover в окне Hierarchy (Иерархия).</span><span class="sxs-lookup"><span data-stu-id="98954-205">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span> 
* <span data-ttu-id="98954-206">Эти объекты будут настроены, чтобы выделять элементы при просмотре деталей MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="98954-206">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="98954-208">2. Реализация событий While Looking At Target () и On Look Away ()</span><span class="sxs-lookup"><span data-stu-id="98954-208">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="98954-209">В окне Hierarchy (Иерархия) выберите объект ***POI-Camera***.</span><span class="sxs-lookup"><span data-stu-id="98954-209">In the Hierarchy window, select the ***POI-Camera*** object.</span></span> <span data-ttu-id="98954-210">В окне Inspector (Инспектор) найдите компонент**Eye Tracking Target (Script)** и настройте события **While Looking At Target ()**  & **On Look Away ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="98954-210">In the Inspector window, locate the **Eye Tracking Target (Script)** component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="98954-211">В поле **None (Object)** (Отсутствует (объект)) укажите объект **POI-Camera ToolTip**.</span><span class="sxs-lookup"><span data-stu-id="98954-211">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="98954-212">В раскрывающемся списке **No Function** (Без функции) события **While Looking At Target ()** выберите **GameObject** > **SetActive (bool).**</span><span class="sxs-lookup"><span data-stu-id="98954-212">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="98954-213">Установите **флажок**, чтобы выделить всплывающую подсказку в качестве действия, запускаемого при просмотре целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="98954-213">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="98954-215">Выполните тот же процесс и выберите раскрывающийся список **No Function** (Без функции) прослушивателя событий **On Look Away ()** .</span><span class="sxs-lookup"><span data-stu-id="98954-215">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="98954-216">Затем выберите **GameObject** > **SetActive (bool**) и снимите **флажок**, чтобы скрыть всплывающую подсказку как действие, запускаемое при отведении взгляда от целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="98954-216">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="98954-218">Выполните тот же процесс и назначьте соответствующие объекты подсказки тем же деталям **MarsCuriosityRover** событий **While Looking At Target ()**  & **On Look Away ()** .</span><span class="sxs-lookup"><span data-stu-id="98954-218">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="98954-219">Чтобы включить отслеживание взгляда, следуйте приведенным [рекомендациям](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span><span class="sxs-lookup"><span data-stu-id="98954-219">To enable eye tracking, please follow these [guidelines](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="98954-220">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="98954-220">Congratulations</span></span>

<span data-ttu-id="98954-221">Из этого учебника вы узнали, как создать взаимодействие в смешанной реальности с использованием элементов пользовательского интерфейса, управления трехмерными моделями, обрезкой моделей и функции отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="98954-221">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="98954-222">В этом учебнике показано, как использовать объекты NextButton и PreviousButton, позволяющие исследовать возможности средства просмотра трехмерных моделей.</span><span class="sxs-lookup"><span data-stu-id="98954-222">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="98954-223">ClippingObjectButton позволяет включить функцию обрезки объектов и интерфейса.</span><span class="sxs-lookup"><span data-stu-id="98954-223">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="98954-224">Кроме того, в учебнике показано, как использовать элемент отслеживания взгляда, позволяющий выделять всплывающие подсказки в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="98954-224">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="98954-225">На следующем занятии вы узнаете, как создать приложение для голографического удаленного взаимодействия с ПК для подключения к HoloLens 2 в любой момент, позволяя выполнить визуализацию трехмерного содержимого в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="98954-225">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

[<span data-ttu-id="98954-226">Следующий урок. 2. Создание приложения для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="98954-226">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)
