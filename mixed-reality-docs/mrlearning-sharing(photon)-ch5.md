---
title: Учебники по возможностям для нескольких пользователей — 5. Интеграция пространственных привязок Azure в общий интерфейс
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: a3b136023b0beea7cf6eecd52a9a21447576d482
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901470"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="da4b9-105">5. Интеграция пространственных привязок Azure в общий интерфейс</span><span class="sxs-lookup"><span data-stu-id="da4b9-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="da4b9-106">На этом занятии вы узнаете, как интегрировать пространственные привязки Azure (ASA) в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="da4b9-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="da4b9-107">ASA позволяет нескольким совместно размещенным устройствам иметь общую ссылку, если их физическая среда связана с закреплением виртуальных возможностей таким образом, что все участники видят объекты в одном физическом месте.</span><span class="sxs-lookup"><span data-stu-id="da4b9-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="da4b9-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="da4b9-108">Objectives</span></span>

* <span data-ttu-id="da4b9-109">Интегрируйте ASA в общий интерфейс для выравнивания нескольких устройств.</span><span class="sxs-lookup"><span data-stu-id="da4b9-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="da4b9-110">Изучите основные принципы работы ASA в контексте локального совместного использования.</span><span class="sxs-lookup"><span data-stu-id="da4b9-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="da4b9-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="da4b9-111">Instructions</span></span>

1. <span data-ttu-id="da4b9-112">Выберите Таблеанчор prefab под родительским объектом Микседреалитиплайспаце и удалите его.</span><span class="sxs-lookup"><span data-stu-id="da4b9-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="da4b9-114">В представлении проекта перейдите к разделу активы-> ресурсы — > Prefabs и перетащите Таблеанчор prefab поверх объекта Шаредплайграунд, чтобы сделать его дочерним.</span><span class="sxs-lookup"><span data-stu-id="da4b9-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="da4b9-115">Разверните объект Микседреалитиплайспаце Parent, Таблеанчор, а также объект Buttons.</span><span class="sxs-lookup"><span data-stu-id="da4b9-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="da4b9-117">Теперь в иерархии выберите Шареазуреанчорбуттон и переместите внимание на панель инспектора.</span><span class="sxs-lookup"><span data-stu-id="da4b9-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="da4b9-118">Прокрутите вниз до раскрывающегося меню, показанного на рисунке ниже, выберите Анчормодулескрипт и щелкните Шареанчорнетворк ().</span><span class="sxs-lookup"><span data-stu-id="da4b9-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="da4b9-120">Выберите Жетазуреанчорбуттон (см. шаг 4) и переместите внимание на панель инспектора.</span><span class="sxs-lookup"><span data-stu-id="da4b9-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="da4b9-121">Прокрутите вниз до раскрывающегося меню, показанного на рисунке ниже, выберите Анчормодулескрипт, щелкните Жетшареданчорнетворк () и сохраните.</span><span class="sxs-lookup"><span data-stu-id="da4b9-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="da4b9-123">Чтобы протестировать модуль общего доступа, нажмите кнопку "запустить сеанс Azure ASA", которая запустит сеанс пространственных привязок Azure, а затем создайте привязку Azure, нажав кнопку "создать привязку Azure".</span><span class="sxs-lookup"><span data-stu-id="da4b9-123">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="da4b9-124">Дождитесь создания привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="da4b9-124">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="da4b9-125">После создания привязки Azure нажмите кнопку "поделиться с Azure Anchor", чтобы поделиться созданной привязкой Azure от HoloLens.</span><span class="sxs-lookup"><span data-stu-id="da4b9-125">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="da4b9-126">Чтобы получить общую привязку Azure в другом HoloLens, щелкните "запустить сеанс Azure ASA", чтобы начать и перейти к текущему сеансу ASA.</span><span class="sxs-lookup"><span data-stu-id="da4b9-126">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

8. <span data-ttu-id="da4b9-127">Нажмите кнопку "получить привязку Azure", чтобы получить общую привязку Azure от другого HoloLens.</span><span class="sxs-lookup"><span data-stu-id="da4b9-127">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="da4b9-128">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="da4b9-128">Congratulations</span></span>

<span data-ttu-id="da4b9-129">На этом занятии вы узнали, как интегрировать мощные новые пространственные привязки Azure для выравнивания совместно используемых устройств в общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="da4b9-129">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="da4b9-130">Это также завершает модуль общего доступа.</span><span class="sxs-lookup"><span data-stu-id="da4b9-130">This also concludes the Sharing Module.</span></span> <span data-ttu-id="da4b9-131">Мы узнали, как настроить новую учетную запись Photon, интегрировать Photon и шутка в новое приложение Unity, настроить аватары и общие объекты и, наконец, согласовать нескольких участников с помощью ASA.</span><span class="sxs-lookup"><span data-stu-id="da4b9-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
