---
title: Руководства по многопользовательским возможностям, часть 5. Интеграция Пространственных привязок Azure в общий интерфейс
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031698"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="4c77e-105">5. Интеграция Пространственных привязок Azure в общий интерфейс</span><span class="sxs-lookup"><span data-stu-id="4c77e-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="4c77e-106">В этом уроке вы узнаете, как интегрировать Пространственные привязки Azure в совместное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="4c77e-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="4c77e-107">Пространственные привязки Azure позволяют нескольким устройствам в одном физическом расположении использовать общие ориентиры, сопоставляя с ними виртуальные взаимодействия так, что все участники видят игровые объекты в одном физическом месте.</span><span class="sxs-lookup"><span data-stu-id="4c77e-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="4c77e-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="4c77e-108">Objectives</span></span>

* <span data-ttu-id="4c77e-109">Интеграция Пространственных привязок Azure в совместное взаимодействие для согласования среды между устройствами</span><span class="sxs-lookup"><span data-stu-id="4c77e-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="4c77e-110">Изучение основных принципов Пространственных привязок Azure в контексте локального совместного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="4c77e-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="4c77e-111">Инструкции</span><span class="sxs-lookup"><span data-stu-id="4c77e-111">Instructions</span></span>

1. <span data-ttu-id="4c77e-112">Выберите заготовку TableAnchor, которая является дочерним объектом для MixedRealityPlayspace, и удалите ее.</span><span class="sxs-lookup"><span data-stu-id="4c77e-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="4c77e-114">В представлении проекта перейдите к разделу Assets (Активы) -> Resources (Ресурсы) -> Prefabs (Заготовки) и перетащите заготовку TableAnchor поверх объекта SharedPlayground, чтобы сделать его дочерним.</span><span class="sxs-lookup"><span data-stu-id="4c77e-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="4c77e-115">Разверните родительский объект MixedRealityPlayspace, затем объект TableAnchor и объект Buttons.</span><span class="sxs-lookup"><span data-stu-id="4c77e-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="4c77e-117">Теперь выберите в иерархии ShareAzureAnchorButton и перейдите на панель Inspector (Инспектор).</span><span class="sxs-lookup"><span data-stu-id="4c77e-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="4c77e-118">Прокрутите ее вниз до раскрывающегося меню, которое представлено на рисунке ниже, выберите AnchorModuleScript и щелкните ShareAnchorNetwork().</span><span class="sxs-lookup"><span data-stu-id="4c77e-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="4c77e-120">Выберите GetAzureAnchorButton (как на шаге 4) и снова перейдите на панель Inspector (Инспектор).</span><span class="sxs-lookup"><span data-stu-id="4c77e-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="4c77e-121">Прокрутите ее вниз до раскрывающегося меню, которое представлено на рисунке ниже, выберите AnchorModuleScript и щелкните GetSharedAnchorNetwork().</span><span class="sxs-lookup"><span data-stu-id="4c77e-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="4c77e-123">Повторите шаг 4, чтобы подключить функцию StartAzureSession() к кнопке StartAzureSessionButton.</span><span class="sxs-lookup"><span data-stu-id="4c77e-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="4c77e-124">Повторите шаг 4, чтобы подключить функцию CreateAzureAnchor() к кнопке CreateAzureAnchorButton, и убедитесь, что объект TableAnchor присвоен полю Game Object (Игровой объект) в качестве параметра этой функции.</span><span class="sxs-lookup"><span data-stu-id="4c77e-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="4c77e-125">Выполните инструкции [Подключение сцены к ресурсу Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource), чтобы подключить учетные данные службы пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="4c77e-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="4c77e-126">Чтобы протестировать модуль общего доступа, нажмите кнопку Start Azure ASA Session (Запустить сеанс пространственных привязок Azure) и создайте привязку Azure, нажав кнопку Create Azure Anchor (Создать привязку Azure).</span><span class="sxs-lookup"><span data-stu-id="4c77e-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="4c77e-127">Дождитесь создания привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="4c77e-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="4c77e-128">Когда создание привязки Azure завершится, нажмите кнопку Share Azure Anchor (Поделиться привязкой Azure), чтобы передать созданную привязку Azure из HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4c77e-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="4c77e-129">Чтобы получить переданную привязку Azure в другом устройстве HoloLens, щелкните Start Azure ASA Session (Запустить сеанс пространственных привязок Azure), чтобы подключиться к текущему сеансу.</span><span class="sxs-lookup"><span data-stu-id="4c77e-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="4c77e-130">Нажмите кнопку Get Azure Anchor (Получить привязку Azure), чтобы получить общую привязку Azure от другого устройства HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4c77e-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4c77e-131">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="4c77e-131">Congratulations</span></span>

<span data-ttu-id="4c77e-132">На этом занятии вы узнали, как интегрировать мощные новые возможности пространственных привязок Azure для поддержки согласованного расположения устройств в совместном взаимодействии.</span><span class="sxs-lookup"><span data-stu-id="4c77e-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="4c77e-133">На этом мы завершаем работу с модулем общего доступа.</span><span class="sxs-lookup"><span data-stu-id="4c77e-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="4c77e-134">Мы узнали в нем, как настроить новую учетную запись Photon, как интегрировать Photon и PUN в новое приложение Unity, как настроить аватары и общие объекты и, наконец, как согласовать нескольких участников с помощью пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="4c77e-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
