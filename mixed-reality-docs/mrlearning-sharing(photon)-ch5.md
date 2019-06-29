---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465202"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="ea3d2-104">Azure пространственных привязки и отзывов</span><span class="sxs-lookup"><span data-stu-id="ea3d2-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="ea3d2-105">В этом уроке мы узнаем, как интегрировать Azure пространственных привязки (ASA) в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="ea3d2-106">ASA позволяет иметь Справочник по общим, если их физической среды виртуальные компоненты для работы привязки таким образом, чтобы все участники см. в разделе объектов находится там же физических несколько совмещенной устройства.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="ea3d2-107">Прежде чем продолжить с этого занятия, нам потребуется для выполнения модуля обучения ASA, который мы рассмотрим основы ASA, учетная запись Azure и создание ресурсов и других блоков фундаментальные здания, которые необходимы, прежде чем мы можете интегрировать ASA в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="ea3d2-108">Цели:</span><span class="sxs-lookup"><span data-stu-id="ea3d2-108">Objectives:</span></span>

- <span data-ttu-id="ea3d2-109">Интеграция ASA в общий интерфейс для нескольких устройств выравнивания</span><span class="sxs-lookup"><span data-stu-id="ea3d2-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="ea3d2-110">Изучение основ работы ASA в контексте локального общего качества</span><span class="sxs-lookup"><span data-stu-id="ea3d2-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="ea3d2-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="ea3d2-111">Instructions</span></span>

1. <span data-ttu-id="ea3d2-112">Сохраните проект на предыдущем занятии (CTRL + S) и назовите его «HLSharedProjectMainPart5.unity», так как это было легко найти, когда она понадобится снова.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="ea3d2-113">Выберите prefab TableAnchor под MixedRealityPlayspace родительского объекта и удалите его.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="ea3d2-115">В представлении проекта перейти к ресурсам, "->" ресурсы "->" Prefabs, а затем перетащите prefab TableAnchor поверх SharedPlayground объект в качестве дочернего.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-115">In the Project view go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="ea3d2-116">Разверните MixedRealityPlayspace родительский объект, объект TableAnchor, а также объект кнопки.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="ea3d2-118">Теперь в иерархии, выберите ShareAzureAnchorButton и переместите вашего внимания Inaspector панели.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="ea3d2-119">Прокрутите вниз до раскрывающееся меню, показанный на рисунке ниже, выберите AnchorModuleScript и нажмите кнопку ShareAnchorNetework().</span><span class="sxs-lookup"><span data-stu-id="ea3d2-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="ea3d2-121">Выберите GetAzureAnchorButton (см. шаг 4), и переместите вашего внимания, вернитесь к панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="ea3d2-122">Прокрутите вниз до раскрывающееся меню, показанный на рисунке ниже и выберите AnchorModuleScript и нажмите кнопку GetSharedAnchorNetwork() и сохраните.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="ea3d2-124">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="ea3d2-124">Congratulations</span></span>

<span data-ttu-id="ea3d2-125">В этом уроке вы узнали, как интегрировать Azure мощные новые Пространственные привязки для выравнивания совмещенной устройств в общий интерфейс!</span><span class="sxs-lookup"><span data-stu-id="ea3d2-125">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="ea3d2-126">Этого занятия также завершается работа модуля управления доступом.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-126">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="ea3d2-127">Мы узнали, как настроить учетную запись Photon, интегрировать Photon и СОВМЕСТНОЙ в новое приложение Unity, Настройка аватары и общих объектов и наконец выравнивание несколькими участниками, используя ASA.</span><span class="sxs-lookup"><span data-stu-id="ea3d2-127">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

