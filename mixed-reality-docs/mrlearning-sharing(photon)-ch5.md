---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327298"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="82980-104">Azure пространственных привязки и отзывов</span><span class="sxs-lookup"><span data-stu-id="82980-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="82980-105">На этом занятии будет рассказано как интегрировать Azure пространственных привязки (ASA) в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="82980-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="82980-106">ASA позволяет иметь общее представление, если их физической среды, чтобы привязать виртуальный таким образом, чтобы все участники см. в разделе объектов находится там же физических несколько совмещенной устройства.</span><span class="sxs-lookup"><span data-stu-id="82980-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="82980-107">Прежде чем продолжить с этого занятия, будет необходимо выполнить модуль ASA обучения, который мы рассмотрим основы ASA, учетная запись Azure и создание ресурсов и других блоков фундаментальные здания, которые необходимы, прежде чем мы можете интегрировать ASA в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="82980-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="82980-108">Цели:</span><span class="sxs-lookup"><span data-stu-id="82980-108">Objectives:</span></span>

- <span data-ttu-id="82980-109">Интеграция ASA в общий интерфейс для нескольких устройств выравнивания</span><span class="sxs-lookup"><span data-stu-id="82980-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="82980-110">Изучение основ работы ASA в контексте локального общего качества</span><span class="sxs-lookup"><span data-stu-id="82980-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="82980-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="82980-111">Instructions</span></span>

1. <span data-ttu-id="82980-112">Сохраните проект на предыдущем занятии (CTRL + S) и назовите его «HLSharedProjectMainPart5.unity», так как это было легко найти, когда она понадобится снова.</span><span class="sxs-lookup"><span data-stu-id="82980-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="82980-113">Выберите prefab TableAnchor под «MixedRealityPlayspace» родительского объекта и удалите его.</span><span class="sxs-lookup"><span data-stu-id="82980-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. <span data-ttu-id="82980-115">Так же, как некоторые из предыдущих занятий, импортировать новый пользовательский пакет, который можно получить [здесь.](placeholderlink)</span><span class="sxs-lookup"><span data-stu-id="82980-115">Just like some of the previous lessons, import a new custom package that you can get [here.](placeholderlink)</span></span>

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. <span data-ttu-id="82980-117">После импорта, захватите привязки обновленного таблицы (из пакета unity, импортированные в предыдущем шаге) в папке «prefabs» в панели «проект» и поместите его в родительский объект «MixedRealityPlayspace.»</span><span class="sxs-lookup"><span data-stu-id="82980-117">Once it's imported, grab the newly updated table anchor (from the unity package imported in the previous step) from the "prefabs" folder in the project panel and drop it into the parent object "MixedRealityPlayspace."</span></span>

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. <span data-ttu-id="82980-119">Разверните родительский объект «MixedRealityPlayspace», то объект «TableAnchor», а также объект «кнопки».</span><span class="sxs-lookup"><span data-stu-id="82980-119">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. <span data-ttu-id="82980-121">Теперь в иерархии, выберите «ShareAzureAnchorButton» и переместите вашего внимания к панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="82980-121">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="82980-122">Прокрутите вниз, чтобы в раскрывающемся меню, показанный на рисунке ниже и выберите «AnchorModuleScript» и щелкните «ShareAnchorNetework().»</span><span class="sxs-lookup"><span data-stu-id="82980-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. <span data-ttu-id="82980-124">Подобно шаг 6 выберите «GetAzureAnchorButton» и переместите вашего внимания, вернитесь к панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="82980-124">Much like step 6, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="82980-125">Прокрутите вниз, чтобы в раскрывающемся меню, показанный на рисунке ниже и выберите «AnchorModuleScript» и щелкните «GetSharedAnchorNetwork().»</span><span class="sxs-lookup"><span data-stu-id="82980-125">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="82980-126">Затем сохраните.</span><span class="sxs-lookup"><span data-stu-id="82980-126">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="82980-128">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="82980-128">Congratulations</span></span>

<span data-ttu-id="82980-129">В этом уроке вы узнали, как интегрировать Azure мощные новые Пространственные привязки для выравнивания совмещенной устройств в общий интерфейс!</span><span class="sxs-lookup"><span data-stu-id="82980-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="82980-130">Этого занятия также завершается работа модуля управления доступом.</span><span class="sxs-lookup"><span data-stu-id="82980-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="82980-131">Мы узнали, как настроить учетную запись Photon, интегрировать Photon и СОВМЕСТНОЙ в новое приложение Unity, Настройка аватары и общих объектов и наконец выравнивание несколькими участниками, используя ASA.</span><span class="sxs-lookup"><span data-stu-id="82980-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

