---
title: Руководства по многопользовательским возможностям, часть 5. Интеграция Пространственных привязок Azure в общий интерфейс
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604975"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="1edeb-105">4. Интеграция Пространственных привязок Azure в общий интерфейс</span><span class="sxs-lookup"><span data-stu-id="1edeb-105">4. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="1edeb-106">Из этого учебника вы узнаете, как интегрировать Пространственные привязки Azure в общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="1edeb-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="1edeb-107">Пространственные привязки Azure позволяют нескольким устройствам в физическом мире использовать общие ориентиры, чтобы пользователи видели друг друга в их реальном физическом расположении и использовали общий интерфейс в одном расположении.</span><span class="sxs-lookup"><span data-stu-id="1edeb-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="1edeb-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="1edeb-108">Objectives</span></span>

* <span data-ttu-id="1edeb-109">Интеграция Пространственных привязок Azure в общий интерфейс для согласования среды между устройствами.</span><span class="sxs-lookup"><span data-stu-id="1edeb-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="1edeb-110">Изучение основных принципов Пространственных привязок Azure в контексте локального общего интерфейса.</span><span class="sxs-lookup"><span data-stu-id="1edeb-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="1edeb-111">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="1edeb-111">Preparing the scene</span></span>

<span data-ttu-id="1edeb-112">В окне "Иерархия" разверните объект **SharedPlayground**, затем разверните объект **TableAnchor**, чтобы предоставить его дочерние объекты.</span><span class="sxs-lookup"><span data-stu-id="1edeb-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

<span data-ttu-id="1edeb-114">В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Заготовки) и перетащите заготовку **Buttons** (Кнопки) поверх дочернего объекта **TableAnchor** в окне "Иерархия", чтобы добавить ее в сцену в качестве дочернего объекта TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="1edeb-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab on top of the **TableAnchor** child object in the Hierarchy window to add it to your scene as a child of the TableAnchor object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="1edeb-116">Настройка кнопок для управления сценой</span><span class="sxs-lookup"><span data-stu-id="1edeb-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="1edeb-117">В рамках этого раздела вы настроите серию событий кнопок, демонстрирующих базовые приемы использования Пространственных привязок Azure для достижения пространственного выравнивания в общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="1edeb-117">In this section, you will configure a series of button events that demonstrate the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="1edeb-118">В окне "Иерархия" разверните объект **Button**. Выберите в нем первый дочерний объект кнопки с именем **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="1edeb-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

<span data-ttu-id="1edeb-120">В окне "Инспектор" найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** (Щелчок), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="1edeb-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="1edeb-121">В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="1edeb-121">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="1edeb-122">В раскрывающемся списке **No Function** (Нет функции) выберите функцию **AnchorModuleScript** > **StartAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="1edeb-122">From **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

<span data-ttu-id="1edeb-124">В окне "Иерархия" выберите второй дочерний объект кнопки с именем **CreateAzureAnchor**. Затем в окне "Инспектор" найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** (Щелчок), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="1edeb-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="1edeb-125">В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="1edeb-125">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="1edeb-126">В раскрывающемся списке **No Function** (Нет функции) выберите функцию **AnchorModuleScript** > **CreateAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="1edeb-126">From **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="1edeb-127">В появившемся поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="1edeb-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

<span data-ttu-id="1edeb-129">В окне "Иерархия" выберите третий дочерний объект кнопки с именем **ShareAzureAnchor**. Затем в окне "Инспектор" найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** (Щелчок), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="1edeb-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="1edeb-130">В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="1edeb-130">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="1edeb-131">В раскрывающемся списке **No Function** (Нет функции) выберите функцию **SharingModuleScript** > **ShareAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="1edeb-131">From **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

<span data-ttu-id="1edeb-133">В окне "Иерархия" выберите четвертый дочерний объект кнопки с именем **GetAzureAnchor**. Затем в окне "Инспектор" найдите компонент **Interactable (Script)** и настройте событие **OnClick ()** , как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="1edeb-133">In the Hierarchy window, select the forth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="1edeb-134">В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="1edeb-134">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="1edeb-135">В раскрывающемся списке **No Function** (Нет функции) выберите функцию **SharingModuleScript** > **GetAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="1edeb-135">From **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="1edeb-137">Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="1edeb-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="1edeb-138">В окне "Иерархия" разверните объект **SharedPlayground** и выберите объект **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="1edeb-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span> <span data-ttu-id="1edeb-139">Затем в окне "Инспектор" найдите компонент **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт) и укажите в разделе **Учетные данные** данные учетной записи Пространственных привязок Azure, созданной в рамках [предварительных требований](mrlearning-sharing(photon)-ch1.md#prerequisites) для этой серии учебников.</span><span class="sxs-lookup"><span data-stu-id="1edeb-139">Then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mrlearning-sharing(photon)-ch1.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="1edeb-140">В поле **Spatial Anchors Account ID** (Идентификатор учетной записи пространственных привязок) вставьте **идентификатор учетной записи** Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="1edeb-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="1edeb-141">В поле **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок) вставьте первичный или вторичный **ключ доступа** учетной записи Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="1edeb-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

<span data-ttu-id="1edeb-143">Сохраняя выделение объекта **TableAnchor**, убедитесь, что в окне "Инспектор" включены все компоненты скрипта.</span><span class="sxs-lookup"><span data-stu-id="1edeb-143">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are enabled:</span></span>

* <span data-ttu-id="1edeb-144">Установите флажок рядом с компонентами **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт), чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="1edeb-144">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="1edeb-145">Установите флажок рядом с компонентами **Anchor Module Script (Script)** (Скрипт модуля привязок — скрипт), чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="1edeb-145">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="1edeb-146">Установите флажок рядом с компонентами **Sharing Module Script (Script)** (Скрипт модуля общего доступа — скрипт), чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="1edeb-146">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="1edeb-148">Использование возможности пространственного выравнивания</span><span class="sxs-lookup"><span data-stu-id="1edeb-148">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="1edeb-149">Пространственные привязки Azure не могут работать в Unity.</span><span class="sxs-lookup"><span data-stu-id="1edeb-149">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="1edeb-150">Поэтому для проверки функциональных возможностей этой службы вам придется развернуть проект как минимум на двух устройствах HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1edeb-150">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two HoloLens devices.</span></span>

<span data-ttu-id="1edeb-151">После создания и развертывания проекта Unity на двух устройствах HoloLens вы сможете поддерживать пространственное выравнивание между ними, используя общий идентификатор привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="1edeb-151">If you now build and deploy the Unity project to two HoloLens devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="1edeb-152">Чтобы проверить этот механизм, можно выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="1edeb-152">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="1edeb-153">На устройстве HoloLens 1: **запустите приложение** (создается Rocket Launcher и размещается в таблице).</span><span class="sxs-lookup"><span data-stu-id="1edeb-153">On HoloLens device 1: **Start the application** (the Rocket Launcher is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="1edeb-154">На устройстве HoloLens 2: **запустите приложение** (оба пользователя видят таблицу с Rocket Launcher, однако таблица не отображается в одном расположении, а аватары пользователей не отображаются там, где находятся пользователи).</span><span class="sxs-lookup"><span data-stu-id="1edeb-154">On HoloLens device 2: **Start the application** (both users see the table with the Rocket Launcher, however, the table does not appear in the same place and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="1edeb-155">На устройстве HoloLens 1: нажмите кнопку **Start Azure Session** (Запуск сеанса Azure).</span><span class="sxs-lookup"><span data-stu-id="1edeb-155">On HoloLens device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="1edeb-156">На устройстве HoloLens 1: нажмите кнопку **Create Azure Anchor** (Создать привязку Azure) (создается привязка в расположении объекта TableAnchor и сохраняются сведения о ней в ресурсе Azure).</span><span class="sxs-lookup"><span data-stu-id="1edeb-156">On HoloLens device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="1edeb-157">На устройстве HoloLens 1: нажмите кнопку **Share Azure Anchor** (Поделиться привязкой Azure) (предоставляет другим пользователям доступ к идентификатору привязки в режиме реального времени).</span><span class="sxs-lookup"><span data-stu-id="1edeb-157">On HoloLens device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="1edeb-158">На устройстве HoloLens 2: нажмите кнопку **Start Azure Session** (Запуск сеанса Azure).</span><span class="sxs-lookup"><span data-stu-id="1edeb-158">On HoloLens device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="1edeb-159">На устройстве HoloLens 2: нажмите кнопку **Get Azure Anchor** (Получить привязку Azure) (подключается к ресурсу Azure для получения сведений о привязке для совместно используемого идентификатора привязки, затем перемещает объект TableAnchor в расположение, где с помощью устройства HoloLens 1 была создана привязка).</span><span class="sxs-lookup"><span data-stu-id="1edeb-159">On HoloLens device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the HoloLens device 1)</span></span>

## <a name="congratulations"></a><span data-ttu-id="1edeb-160">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="1edeb-160">Congratulations</span></span>

<span data-ttu-id="1edeb-161">Из этого учебника вы узнали, как интегрировать мощные возможности Пространственных привязок Azure для поддержки согласованного расположения устройств в общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="1edeb-161">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span> <span data-ttu-id="1edeb-162">На этом мы завершаем работу с этой серией учебников, из которой мы узнали, как настроить учетную запись и приложение Photon, как интегрировать Photon и PUN в приложение Unity, как настроить аватары пользователей и общие объекты, а также как согласовать нескольких участников с помощью Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="1edeb-162">This also concludes this tutorial series where you have learned how to set up a Photon account and application, integrate Photon and PUN into a Unity application, configure user avatars and shared objects, and finally align multiple participants using ASA.</span></span>
