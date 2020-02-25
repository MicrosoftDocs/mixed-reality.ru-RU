---
title: Учебники по возможностям для нескольких пользователей — 5. Интеграция пространственных привязок Azure в общий интерфейс
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: c1b64b9d32409d61284f21ca216417ece4767d1b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553812"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="2424e-105">5. Интеграция пространственных привязок Azure в общий интерфейс</span><span class="sxs-lookup"><span data-stu-id="2424e-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="2424e-106">На этом занятии вы узнаете, как интегрировать пространственные привязки Azure (ASA) в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="2424e-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="2424e-107">ASA позволяет нескольким совместно размещенным устройствам иметь общую ссылку, если их физическая среда связана с закреплением виртуальных возможностей таким образом, что все участники видят объекты в одном физическом месте.</span><span class="sxs-lookup"><span data-stu-id="2424e-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="2424e-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="2424e-108">Objectives</span></span>

* <span data-ttu-id="2424e-109">Интегрируйте ASA в общий интерфейс для выравнивания нескольких устройств.</span><span class="sxs-lookup"><span data-stu-id="2424e-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="2424e-110">Изучите основные принципы работы ASA в контексте локального совместного использования.</span><span class="sxs-lookup"><span data-stu-id="2424e-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="2424e-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2424e-111">Instructions</span></span>

1. <span data-ttu-id="2424e-112">Выберите Таблеанчор prefab под родительским объектом Микседреалитиплайспаце и удалите его.</span><span class="sxs-lookup"><span data-stu-id="2424e-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="2424e-114">В представлении проекта перейдите к разделу активы-> ресурсы — > Prefabs и перетащите Таблеанчор prefab поверх объекта Шаредплайграунд, чтобы сделать его дочерним.</span><span class="sxs-lookup"><span data-stu-id="2424e-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="2424e-115">Разверните объект Микседреалитиплайспаце Parent, Таблеанчор, а также объект Buttons.</span><span class="sxs-lookup"><span data-stu-id="2424e-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="2424e-117">Теперь в иерархии выберите Шареазуреанчорбуттон и переместите внимание на панель инспектора.</span><span class="sxs-lookup"><span data-stu-id="2424e-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="2424e-118">Прокрутите вниз до раскрывающегося меню, показанного на рисунке ниже, выберите Анчормодулескрипт и щелкните Шареанчорнетворк ().</span><span class="sxs-lookup"><span data-stu-id="2424e-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="2424e-120">Выберите Жетазуреанчорбуттон (см. шаг 4) и переместите внимание на панель инспектора.</span><span class="sxs-lookup"><span data-stu-id="2424e-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="2424e-121">Прокрутите вниз до раскрывающегося меню, показанного на рисунке ниже, выберите Анчормодулескрипт, щелкните Жетшареданчорнетворк () и сохраните.</span><span class="sxs-lookup"><span data-stu-id="2424e-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="2424e-123">Повторите шаг 4, чтобы подключить функцию Стартазуресессион () к Стартазуресессионбуттон.</span><span class="sxs-lookup"><span data-stu-id="2424e-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="2424e-124">Повторите шаг 4 для подключения функции Креатеазуреанчор () к Креатеазуреанчорбуттон и убедитесь, что объект Таблеанчор назначен в поле "Game Object" для параметра функции.</span><span class="sxs-lookup"><span data-stu-id="2424e-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="2424e-125">Чтобы добавить учетные данные службы пространственных привязок Azure, следуйте инструкциям в статье [Подключение сцены к Azure Resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) .</span><span class="sxs-lookup"><span data-stu-id="2424e-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="2424e-126">Чтобы протестировать модуль общего доступа, нажмите кнопку "запустить сеанс Azure ASA", которая запустит сеанс пространственных привязок Azure, а затем создайте привязку Azure, нажав кнопку "создать привязку Azure".</span><span class="sxs-lookup"><span data-stu-id="2424e-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="2424e-127">Дождитесь создания привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="2424e-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="2424e-128">После создания привязки Azure нажмите кнопку "поделиться с Azure Anchor", чтобы поделиться созданной привязкой Azure от HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2424e-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="2424e-129">Чтобы получить общую привязку Azure в другом HoloLens, щелкните "запустить сеанс Azure ASA", чтобы начать и перейти к текущему сеансу ASA.</span><span class="sxs-lookup"><span data-stu-id="2424e-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="2424e-130">Нажмите кнопку "получить привязку Azure", чтобы получить общую привязку Azure от другого HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2424e-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2424e-131">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="2424e-131">Congratulations</span></span>

<span data-ttu-id="2424e-132">На этом занятии вы узнали, как интегрировать мощные новые пространственные привязки Azure для выравнивания совместно используемых устройств в общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="2424e-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="2424e-133">Это также завершает модуль общего доступа.</span><span class="sxs-lookup"><span data-stu-id="2424e-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="2424e-134">Мы узнали, как настроить новую учетную запись Photon, интегрировать Photon и шутка в новое приложение Unity, настроить аватары и общие объекты и, наконец, согласовать нескольких участников с помощью ASA.</span><span class="sxs-lookup"><span data-stu-id="2424e-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
