---
title: Учебники по возможностям для нескольких пользователей — 5. Интеграция пространственных привязок Azure в общий интерфейс
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: cb4645d197238d8712719625bf11eac0650a8246
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701873"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="408ab-105">5. Интеграция пространственных привязок Azure в общий интерфейс</span><span class="sxs-lookup"><span data-stu-id="408ab-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="408ab-106">На этом занятии мы Научитесь интегрировать пространственные привязки Azure (ASA) в наши общие возможности.</span><span class="sxs-lookup"><span data-stu-id="408ab-106">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="408ab-107">ASA позволяет нескольким совместно размещенным устройствам иметь общую ссылку, если их физическая среда связана с закреплением виртуальных возможностей таким образом, что все участники видят объекты в одном физическом месте.</span><span class="sxs-lookup"><span data-stu-id="408ab-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="408ab-108">Прежде чем продолжить работу с этим занятием, необходимо выполнить модуль обучения ASA, в котором будут рассмотрены основы ASA, создание учетных записей и ресурсов Azure, а также другие фундаментальные блоки зданий, которые необходимы, прежде чем мы можем интегрировать ASA в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="408ab-108">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="408ab-109">Служит</span><span class="sxs-lookup"><span data-stu-id="408ab-109">Objectives:</span></span>

- <span data-ttu-id="408ab-110">Интегрируйте ASA в общий интерфейс для выравнивания нескольких устройств.</span><span class="sxs-lookup"><span data-stu-id="408ab-110">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="408ab-111">Изучите основные принципы работы ASA в контексте локального совместного использования.</span><span class="sxs-lookup"><span data-stu-id="408ab-111">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="408ab-112">Инструкция</span><span class="sxs-lookup"><span data-stu-id="408ab-112">Instructions</span></span>

1. <span data-ttu-id="408ab-113">Сохраните проект из предыдущего занятия (Control + S) и назовите его "HLSharedProjectMainPart5. Unity", чтобы его было проще найти, когда это необходимо.</span><span class="sxs-lookup"><span data-stu-id="408ab-113">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="408ab-114">Выберите Таблеанчор prefab под родительским объектом Микседреалитиплайспаце и удалите его.</span><span class="sxs-lookup"><span data-stu-id="408ab-114">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="408ab-116">В представлении проекта перейдите к разделу активы-> ресурсы — > Prefabs и перетащите Таблеанчор prefab поверх объекта Шаредплайграунд, чтобы сделать его дочерним.</span><span class="sxs-lookup"><span data-stu-id="408ab-116">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="408ab-117">Разверните объект Микседреалитиплайспаце Parent, Таблеанчор, а также объект Buttons.</span><span class="sxs-lookup"><span data-stu-id="408ab-117">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="408ab-119">Теперь в иерархии выберите Шареазуреанчорбуттон и обратите внимание на панель "аспекты".</span><span class="sxs-lookup"><span data-stu-id="408ab-119">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="408ab-120">Прокрутите вниз до раскрывающегося меню, показанного на рисунке ниже, выберите Анчормодулескрипт и щелкните Шареанчорнетеворк ().</span><span class="sxs-lookup"><span data-stu-id="408ab-120">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="408ab-122">Выберите Жетазуреанчорбуттон (см. шаг 4) и переместите внимание на панель инспектора.</span><span class="sxs-lookup"><span data-stu-id="408ab-122">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="408ab-123">Прокрутите вниз до раскрывающегося меню, показанного на рисунке ниже, выберите Анчормодулескрипт и щелкните Жетшареданчорнетворк () и сохраните.</span><span class="sxs-lookup"><span data-stu-id="408ab-123">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="408ab-125">Чтобы протестировать модуль общего доступа, нажмите кнопку "запустить сеанс Azure ASA", которая запустит сеанс пространственных привязок Azure, а затем создайте привязку Azure, нажав кнопку "создать привязку Azure" и дождитесь создания привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="408ab-125">To test the sharing module, click on the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button and wait for sometime for the azure anchor to get created.</span></span> <span data-ttu-id="408ab-126">После создания привязки Azure нажмите кнопку "поделиться с Azure Anchor", чтобы поделиться созданной привязкой Azure от HoloLens.</span><span class="sxs-lookup"><span data-stu-id="408ab-126">Once the azure anchor is created then click on the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="408ab-127">Чтобы получить общую привязку Azure в другом HoloLens, щелкните "запустить сеанс Azure ASA", чтобы начать и перейти к текущему сеансу ASA, и нажмите кнопку "получить привязку Azure", чтобы получить общую привязку Azure от другого HoloLens.</span><span class="sxs-lookup"><span data-stu-id="408ab-127">To recieve the shared azure anchor in another HoloLens, click on the "Start Azure ASA Session" to start and get in to the current ASA session and click on "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="408ab-128">Примечание. Все сведения о соответствующих действиях с отдельными кнопками будут отображаться в окне отладки.</span><span class="sxs-lookup"><span data-stu-id="408ab-128">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="408ab-129">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="408ab-129">Congratulations</span></span>

<span data-ttu-id="408ab-130">На этом занятии вы узнали, как интегрировать мощные новые пространственные привязки Azure для выравнивания совместно размещенных устройств в общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="408ab-130">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="408ab-131">На этом занятии также завершается модуль общего доступа.</span><span class="sxs-lookup"><span data-stu-id="408ab-131">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="408ab-132">Мы узнали, как настроить новую учетную запись Photon, интегрировать Photon и шутка в новое приложение Unity, настраивать аватары и общие объекты и, наконец, согласовывать нескольких участников с помощью ASA.</span><span class="sxs-lookup"><span data-stu-id="408ab-132">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

