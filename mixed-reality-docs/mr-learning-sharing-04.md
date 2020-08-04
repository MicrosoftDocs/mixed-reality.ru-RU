---
title: Руководства по многопользовательским возможностям, часть 4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7dbe25cd1b0329e366fcbd567074018025032f9e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376566"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="767e3-105">4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям</span><span class="sxs-lookup"><span data-stu-id="767e3-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="767e3-106">В этом руководстве показано, как совместно использовать перемещения объектов, чтобы все участники общего взаимодействия могли взаимодействовать друг с другом и наблюдать за этими процессами.</span><span class="sxs-lookup"><span data-stu-id="767e3-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each other's interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="767e3-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="767e3-107">Objectives</span></span>

* <span data-ttu-id="767e3-108">Настройка проекта для совместного использования перемещений объектов</span><span class="sxs-lookup"><span data-stu-id="767e3-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="767e3-109">Создать простое многопользовательское приложение для совместной работы.</span><span class="sxs-lookup"><span data-stu-id="767e3-109">Learn how to build a basic multi-user collaborative app</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="767e3-110">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="767e3-110">Preparing the scene</span></span>

<span data-ttu-id="767e3-111">В рамках этого раздела вы подготовите сцену, добавив в нее заготовку для учебника.</span><span class="sxs-lookup"><span data-stu-id="767e3-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="767e3-112">В окне Project (Проект) перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Заготовки) и перетащите заготовку **TableAnchor** на объект **SharedPlayground** в окне Hierarchy (Иерархия), чтобы добавить ее в сцену в качестве дочернего элемента объекта SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="767e3-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab onto the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="767e3-114">Настройка PUN для создания объектов</span><span class="sxs-lookup"><span data-stu-id="767e3-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="767e3-115">С помощью инструкций из этого раздела вы настроите в проекте использование взаимодействия Rover Explorer, созданного с помощью [руководств по началу работы](mr-learning-base-01.md), и определите расположение, в котором буде создан его экземпляр.</span><span class="sxs-lookup"><span data-stu-id="767e3-115">In this section, you will configure the project to use the Rover Explorer experience created during the [Getting started tutorials](mr-learning-base-01.md) and define where it will be instantiated.</span></span>

<span data-ttu-id="767e3-116">В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).</span><span class="sxs-lookup"><span data-stu-id="767e3-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="767e3-117">В окне "Иерархия" разверните объект **NetworkLobby** и выберите дочерний объект **NetworkRoom**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="767e3-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="767e3-118">В поле **Rover Explorer Prefab** (Заготовка Rover Explorer) назначьте заготовку **RoverExplorer_Complete_Variant** из папки Resources (Ресурсы).</span><span class="sxs-lookup"><span data-stu-id="767e3-118">To the **Rover Explorer Prefab** field, assign the **RoverExplorer_Complete_Variant** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

<span data-ttu-id="767e3-120">Сохраняя выделение объекта **NetworkRoom**, в окне "Иерархия" разверните объект **TableAnchor**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="767e3-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="767e3-121">В поле **Rover Explorer Location** (Расположение Rover Explorer) укажите дочерний объект TableAnchor > **Table** из окна Hierarchy (Иерархия).</span><span class="sxs-lookup"><span data-stu-id="767e3-121">To the **Rover Explorer Location** field, assign the TableAnchor > **Table** child object from the Hierarchy window</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="767e3-123">Использование возможности общего перемещения объектов</span><span class="sxs-lookup"><span data-stu-id="767e3-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="767e3-124">Если вы теперь создадите и развернете проект Unity в HoloLens, а затем вернетесь в Unity и во время выполнения приложения на устройстве HoloLens нажмете кнопку Play (Играть), чтобы перейти в игровой режим, вы увидите, как при перемещении объекта в HoloLens перемещается объект в Unity.</span><span class="sxs-lookup"><span data-stu-id="767e3-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the app is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="767e3-126">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="767e3-126">Congratulations</span></span>

<span data-ttu-id="767e3-127">Вы успешно настроили проект. Теперь перемещения объектов синхронизированы и пользователи могут видеть, как перемещаются объекты, когда их перемещают другие пользователи.</span><span class="sxs-lookup"><span data-stu-id="767e3-127">You have successfully configured your project to synchronize object movements so users can see the objects move when other users move them.</span></span> <span data-ttu-id="767e3-128">В следующем руководстве показано, как реализовать функциональность для согласования взаимодействия с физическим миром.</span><span class="sxs-lookup"><span data-stu-id="767e3-128">In the next tutorial, you will implement functionality to align the experience in the physical world.</span></span> <span data-ttu-id="767e3-129">Благодаря этому пользователи будут видеть друг друга в фактическом физическом расположении, а объекты будут отображаться в одном физическом расположении и с одним поворотом для всех пользователей.</span><span class="sxs-lookup"><span data-stu-id="767e3-129">This will ensure the users see each other in their actual physical location, and so the objects appear in the same physical position and rotation for all users.</span></span>

[<span data-ttu-id="767e3-130">Следующее руководство: 5. Интеграция Пространственных привязок Azure в общий интерфейс</span><span class="sxs-lookup"><span data-stu-id="767e3-130">Next Tutorial: 5. Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)
