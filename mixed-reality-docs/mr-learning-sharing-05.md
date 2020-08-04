---
title: Руководства по многопользовательским возможностям, часть 5. Интеграция Пространственных привязок Azure в общий интерфейс
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: fc8e20a9ddaa595db0a3d59975e7c785d01c0a6d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376586"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="e0602-105">5. Интеграция Пространственных привязок Azure в общий интерфейс</span><span class="sxs-lookup"><span data-stu-id="e0602-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="e0602-106">Из этого учебника вы узнаете, как интегрировать Пространственные привязки Azure в общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="e0602-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="e0602-107">Пространственные привязки Azure позволяют нескольким устройствам в физическом мире использовать общие ориентиры, чтобы пользователи видели друг друга в их реальном физическом расположении и использовали общий интерфейс в одном расположении.</span><span class="sxs-lookup"><span data-stu-id="e0602-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="e0602-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="e0602-108">Objectives</span></span>

* <span data-ttu-id="e0602-109">Интеграция Пространственных привязок Azure в общий интерфейс для согласования среды между устройствами.</span><span class="sxs-lookup"><span data-stu-id="e0602-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="e0602-110">Изучение основных принципов Пространственных привязок Azure в контексте локального общего интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e0602-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="e0602-111">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="e0602-111">Preparing the scene</span></span>

<span data-ttu-id="e0602-112">В окне "Иерархия" разверните объект **SharedPlayground**, затем разверните объект **TableAnchor**, чтобы предоставить его дочерние объекты.</span><span class="sxs-lookup"><span data-stu-id="e0602-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

<span data-ttu-id="e0602-114">В окне Project (Проект) перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Заготовки) и перетащите заготовку **Buttons** (Кнопки) на дочерний объект **TableAnchor**, чтобы добавить ее в сцену в качестве дочернего объекта TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="e0602-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab onto the **TableAnchor** child object to add it to your scene as a child of the TableAnchor object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="e0602-116">Настройка кнопок для управления сценой</span><span class="sxs-lookup"><span data-stu-id="e0602-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="e0602-117">В этом разделе показано, как настроить серию событий кнопок, демонстрирующих базовые приемы использования Пространственных привязок Azure для достижения пространственного выравнивания в общем взаимодействии.</span><span class="sxs-lookup"><span data-stu-id="e0602-117">In this section, you will configure a series of button events demonstrating the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="e0602-118">В окне "Иерархия" разверните объект **Button**. Выберите в нем первый дочерний объект кнопки с именем **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="e0602-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

<span data-ttu-id="e0602-120">В окне "Инспектор" найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** (Щелчок), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="e0602-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="e0602-121">В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="e0602-121">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="e0602-122">В раскрывающемся списке **No Function** (Нет функции) выберите функцию **AnchorModuleScript** > **StartAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="e0602-122">From the **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

<span data-ttu-id="e0602-124">В окне "Иерархия" выберите второй дочерний объект кнопки с именем **CreateAzureAnchor**. Затем в окне "Инспектор" найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** (Щелчок), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="e0602-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="e0602-125">В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="e0602-125">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="e0602-126">В раскрывающемся списке **No Function** (Нет функции) выберите функцию **AnchorModuleScript** > **CreateAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="e0602-126">From the **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="e0602-127">В появившемся поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="e0602-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

<span data-ttu-id="e0602-129">В окне "Иерархия" выберите третий дочерний объект кнопки с именем **ShareAzureAnchor**. Затем в окне "Инспектор" найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** (Щелчок), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="e0602-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="e0602-130">В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="e0602-130">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="e0602-131">В раскрывающемся списке **No Function** (Нет функции) выберите функцию **SharingModuleScript** > **ShareAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="e0602-131">From the **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

<span data-ttu-id="e0602-133">В окне Hierarchy (Иерархия) выберите четвертый дочерний объект кнопки с именем **GetAzureAnchor**. Затем в окне Inspector (Инспектор) найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e0602-133">In the Hierarchy window, select the fourth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="e0602-134">В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="e0602-134">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="e0602-135">В раскрывающемся списке **No Function** (Нет функции) выберите функцию **SharingModuleScript** > **GetAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="e0602-135">From the **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="e0602-137">Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="e0602-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="e0602-138">В окне "Иерархия" разверните объект **SharedPlayground** и выберите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="e0602-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span>

<span data-ttu-id="e0602-139">В окне Inspector (Инспектор) найдите компонент **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт) и укажите в разделе **Credentials** (Учетные данные) данные учетной записи Пространственных привязок Azure, созданной при работе с разделом [предварительных требований](mr-learning-sharing-01.md#prerequisites) для этой серии руководств.</span><span class="sxs-lookup"><span data-stu-id="e0602-139">In the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-sharing-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="e0602-140">В поле **Spatial Anchors Account ID** (Идентификатор учетной записи пространственных привязок) вставьте **идентификатор учетной записи** Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="e0602-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="e0602-141">В поле **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок) вставьте первичный или вторичный **ключ доступа** учетной записи Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="e0602-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="e0602-143">Вы можете задать идентификатор и ключ учетной записи Пространственных привязок не только для сцены, но и для всего проекта, если у вас есть несколько сцен с Пространственными привязками Azure.</span><span class="sxs-lookup"><span data-stu-id="e0602-143">Instead of setting the Spatial Anchors Account ID and Key in the scene, you can set it for your entire project, this can be advantageous if you have multiple scenes using ASA.</span></span> <span data-ttu-id="e0602-144">Для этого в окне Project (Проект) выберите Assets (Активы) > AzureSpatialAnchors.SDK > Resources (Ресурсы) > актив **SpatialAnchorConfig**, а затем задайте значения в окне Inspector (Инспектор).</span><span class="sxs-lookup"><span data-stu-id="e0602-144">To do this, in the Project window, navigate to the Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig** asset, then set the values in the Inspector window.</span></span>

<span data-ttu-id="e0602-145">В окне Hierarchy (Иерархия) выберите объект **TableAnchor**. Затем в окне Inspector (Инспектор) найдите компонент **Anchor Module (Script)** (Модуль привязок — скрипт) и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e0602-145">In the Hierarchy window, select the **TableAnchor** object, then in the Inspector window, locate the **Anchor Module (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="e0602-146">В поле **Public Sharing Pin** (ПИН-код общего доступа) измените несколько цифр, чтобы код стал уникальным для вашего проекта.</span><span class="sxs-lookup"><span data-stu-id="e0602-146">In the **Public Sharing Pin** field, change a few digits, so the pin becomes unique to your project</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

<span data-ttu-id="e0602-148">С выделенным объектом **TableAnchor** убедитесь, что в окне Inspector (Инспектор) **включены** все компоненты скрипта:</span><span class="sxs-lookup"><span data-stu-id="e0602-148">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are **enabled**:</span></span>

* <span data-ttu-id="e0602-149">Установите флажок рядом с компонентами **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт), чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="e0602-149">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="e0602-150">Установите флажок рядом с компонентами **Anchor Module Script (Script)** (Скрипт модуля привязок — скрипт), чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="e0602-150">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="e0602-151">Установите флажок рядом с компонентами **Sharing Module Script (Script)** (Скрипт модуля общего доступа — скрипт), чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="e0602-151">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="e0602-153">Использование возможности пространственного выравнивания</span><span class="sxs-lookup"><span data-stu-id="e0602-153">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="e0602-154">Пространственные привязки Azure не могут работать в Unity.</span><span class="sxs-lookup"><span data-stu-id="e0602-154">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="e0602-155">Поэтому для проверки функциональных возможностей этой службы вам нужно будет развернуть проект как минимум на двух устройствах.</span><span class="sxs-lookup"><span data-stu-id="e0602-155">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two devices.</span></span>

<span data-ttu-id="e0602-156">После создания и развертывания проекта Unity на двух устройствах вы сможете реализовать пространственное выравнивание между ними, используя общий идентификатор привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="e0602-156">If you now build and deploy the Unity project to two devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="e0602-157">Чтобы проверить этот механизм, можно выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e0602-157">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="e0602-158">На устройстве 1: **запустите приложение** (Rover Explorer создается и размещается в таблице).</span><span class="sxs-lookup"><span data-stu-id="e0602-158">On device 1: **Start the app** (the Rover Explorer is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="e0602-159">На устройстве 2: **запустите приложение** (оба пользователя видят таблицу с Rover Explorer, но таблица не отображается в одном расположении, а аватары пользователей не отображаются там, где находятся пользователи).</span><span class="sxs-lookup"><span data-stu-id="e0602-159">On device 2: **Start the app** (both users see the table with the Rover Explorer, but the table does not appear in the same place, and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="e0602-160">На устройстве 1: нажмите кнопку **Start Azure Session** (Запуск сеанса Azure).</span><span class="sxs-lookup"><span data-stu-id="e0602-160">On device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="e0602-161">На устройстве 1: нажмите кнопку **Create Azure Anchor** (Создать привязку Azure) (создается привязка в расположении объекта TableAnchor и сохраняются сведения о ней в ресурсе Azure).</span><span class="sxs-lookup"><span data-stu-id="e0602-161">On device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="e0602-162">На устройстве 1: нажмите кнопку **Share Azure Anchor** (Поделиться привязкой Azure) (предоставляет другим пользователям доступ к идентификатору привязки в режиме реального времени).</span><span class="sxs-lookup"><span data-stu-id="e0602-162">On device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="e0602-163">На устройстве 2: нажмите кнопку **Start Azure Session** (Запуск сеанса Azure).</span><span class="sxs-lookup"><span data-stu-id="e0602-163">On device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="e0602-164">На устройстве 2: нажмите кнопку **Get Azure Anchor** (Получить привязку Azure) (подключается к ресурсу Azure, чтобы получить сведения о привязке для общего идентификатора привязки, затем перемещает объект TableAnchor в расположение, где с помощью устройства 1 была создана привязка).</span><span class="sxs-lookup"><span data-stu-id="e0602-164">On device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the device 1)</span></span>

> [!TIP]
> <span data-ttu-id="e0602-165">Если у вас нет доступа к двум устройствам HoloLens, выполните инструкции из статьи [Создание Пространственных привязок Azure для мобильных устройств](mr-learning-asa-05.md), чтобы развернуть проект на мобильном устройстве.</span><span class="sxs-lookup"><span data-stu-id="e0602-165">If you don't have access to two HoloLens devices, you may follow the [Building Azure Spatial Anchors for mobile devices](mr-learning-asa-05.md) to deploy the project to your mobile device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e0602-166">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="e0602-166">Congratulations</span></span>

<span data-ttu-id="e0602-167">Из этого учебника вы узнали, как интегрировать мощные возможности Пространственных привязок Azure для поддержки согласованного расположения устройств в общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="e0602-167">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span>

<span data-ttu-id="e0602-168">На этом мы завершаем работу с этой серией руководств, из которой вы узнали, как настроить учетную запись Photon, создать приложение PUN, интегрировать PUN в проект Unity, настроить аватары пользователей и общие объекты, а также как согласовать разных участников с помощью Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="e0602-168">This also concludes this tutorial series where you learned how to set up a Photon account, create a PUN app, integrate PUN into the Unity project, configure user avatars and shared objects, and finally align multiple participants using Azure Spatial Anchors.</span></span>
