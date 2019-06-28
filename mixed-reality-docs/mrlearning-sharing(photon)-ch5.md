---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 941bdc64ed614d5ce71f58f05585d0dfc86c3bb7
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415935"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="8d402-104">Azure пространственных привязки и отзывов</span><span class="sxs-lookup"><span data-stu-id="8d402-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="8d402-105">На этом занятии будет рассказано как интегрировать Azure пространственных привязки (ASA) в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="8d402-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="8d402-106">ASA позволяет иметь общее представление, если их физической среды, чтобы привязать виртуальный таким образом, чтобы все участники см. в разделе объектов находится там же физических несколько совмещенной устройства.</span><span class="sxs-lookup"><span data-stu-id="8d402-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="8d402-107">Прежде чем продолжить с этого занятия, будет необходимо выполнить модуль ASA обучения, который мы рассмотрим основы ASA, учетная запись Azure и создание ресурсов и других блоков фундаментальные здания, которые необходимы, прежде чем мы можете интегрировать ASA в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="8d402-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="8d402-108">Цели:</span><span class="sxs-lookup"><span data-stu-id="8d402-108">Objectives:</span></span>

- <span data-ttu-id="8d402-109">Интеграция ASA в общий интерфейс для нескольких устройств выравнивания</span><span class="sxs-lookup"><span data-stu-id="8d402-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="8d402-110">Изучение основ работы ASA в контексте локального общего качества</span><span class="sxs-lookup"><span data-stu-id="8d402-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="8d402-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="8d402-111">Instructions</span></span>

1. <span data-ttu-id="8d402-112">Сохраните проект на предыдущем занятии (CTRL + S) и назовите его «HLSharedProjectMainPart5.unity», так как это было легко найти, когда она понадобится снова.</span><span class="sxs-lookup"><span data-stu-id="8d402-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="8d402-113">Выберите prefab TableAnchor под «MixedRealityPlayspace» родительского объекта и удалите его.</span><span class="sxs-lookup"><span data-stu-id="8d402-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="8d402-115">В представлении проекта, перейдите к активам > ресурсы > Prefabs и перетащите TableAnchor prefab поверх SharedPlayground объект в качестве дочернего.</span><span class="sxs-lookup"><span data-stu-id="8d402-115">In the Project view go to Assets > Resources > Prefabs and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="8d402-116">Разверните родительский объект «MixedRealityPlayspace», то объект «TableAnchor», а также объект «кнопки».</span><span class="sxs-lookup"><span data-stu-id="8d402-116">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="8d402-118">Теперь в иерархии, выберите «ShareAzureAnchorButton» и переместите вашего внимания к панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="8d402-118">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="8d402-119">Прокрутите вниз, чтобы в раскрывающемся меню, показанный на рисунке ниже и выберите «AnchorModuleScript» и щелкните «ShareAnchorNetework().»</span><span class="sxs-lookup"><span data-stu-id="8d402-119">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="8d402-121">Подобно шаг 4 выберите «GetAzureAnchorButton» и переместите вашего внимания, вернитесь к панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="8d402-121">Much like step 4, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="8d402-122">Прокрутите вниз, чтобы в раскрывающемся меню, показанный на рисунке ниже и выберите «AnchorModuleScript» и щелкните «GetSharedAnchorNetwork().»</span><span class="sxs-lookup"><span data-stu-id="8d402-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="8d402-123">Затем сохраните.</span><span class="sxs-lookup"><span data-stu-id="8d402-123">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="8d402-125">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="8d402-125">Congratulations</span></span>

<span data-ttu-id="8d402-126">В этом уроке вы узнали, как интегрировать Azure мощные новые Пространственные привязки для выравнивания совмещенной устройств в общий интерфейс!</span><span class="sxs-lookup"><span data-stu-id="8d402-126">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="8d402-127">Этого занятия также завершается работа модуля управления доступом.</span><span class="sxs-lookup"><span data-stu-id="8d402-127">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="8d402-128">Мы узнали, как настроить учетную запись Photon, интегрировать Photon и СОВМЕСТНОЙ в новое приложение Unity, Настройка аватары и общих объектов и наконец выравнивание несколькими участниками, используя ASA.</span><span class="sxs-lookup"><span data-stu-id="8d402-128">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

