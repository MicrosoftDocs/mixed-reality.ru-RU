---
title: Учебники по началу работы — 5. Взаимодействие с трехмерными объектами
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 7eb38e205237257e400550299fdeebb73ba746f1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555497"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="e6808-104">5. взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="e6808-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="e6808-105">В этом учебнике вы узнаете о базовом трехмерном содержимом и взаимодействии с пользователем, например о том, как организовать трехмерные объекты как часть коллекции, ограничивающие рамки для базовой манипуляции, практически и намного взаимодействие, а также жесты касания и захвата с отслеживанием руки.</span><span class="sxs-lookup"><span data-stu-id="e6808-105">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="e6808-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="e6808-106">Objectives</span></span>

* <span data-ttu-id="e6808-107">Создание панели трехмерных объектов, которые будут использоваться для других целей обучения</span><span class="sxs-lookup"><span data-stu-id="e6808-107">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="e6808-108">Реализация ограничивающих рамок.</span><span class="sxs-lookup"><span data-stu-id="e6808-108">Implement bounding boxes</span></span>
* <span data-ttu-id="e6808-109">Настройка трехмерных объектов для базовых манипуляций, таких как перемещение, вращение и масштабирование</span><span class="sxs-lookup"><span data-stu-id="e6808-109">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="e6808-110">Изучение ближнего и дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="e6808-110">Explore near and far interaction</span></span>
* <span data-ttu-id="e6808-111">Дополнительные сведения о жестах отслеживания, таких как захват и сенсорный ввод</span><span class="sxs-lookup"><span data-stu-id="e6808-111">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="e6808-112">Импорт ресурсов учебника</span><span class="sxs-lookup"><span data-stu-id="e6808-112">Importing the tutorial assets</span></span>

<span data-ttu-id="e6808-113">Скачайте и импортируйте пользовательский пакет Unity:</span><span class="sxs-lookup"><span data-stu-id="e6808-113">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="e6808-114">МРТК. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.3.0.2. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="e6808-114">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

<span data-ttu-id="e6808-115">После импорта ресурсов учебника окно проекта должно выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e6808-115">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="e6808-117">Напоминание о том, как импортировать пользовательский пакет Unity, можно найти в разделе Импорт инструкций по [набору средств для смешанной реальности](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .</span><span class="sxs-lookup"><span data-stu-id="e6808-117">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="e6808-118">Раззагромождения представления сцены</span><span class="sxs-lookup"><span data-stu-id="e6808-118">Decluttering the scene view</span></span>

<span data-ttu-id="e6808-119">Чтобы упростить работу с сценой, установите **видимость сцены** для объектов **Cube** и **буттонколлектион** , щелкнув значок **глаза** слева от объектов.</span><span class="sxs-lookup"><span data-stu-id="e6808-119">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="e6808-120">Это скрывает объект в окне сцены, не изменяя его видимость в игре:</span><span class="sxs-lookup"><span data-stu-id="e6808-120">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="e6808-122">Дополнительные сведения об элементах управления видимостью сцены и их использовании для оптимизации представления сцены и рабочего процесса см. в документации по <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">видимости сцены</a> Unity.</span><span class="sxs-lookup"><span data-stu-id="e6808-122">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="e6808-123">Упорядочение трехмерных объектов в коллекции</span><span class="sxs-lookup"><span data-stu-id="e6808-123">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="e6808-124">В этом разделе вы создадите панель трехмерных объектов, которая будет использоваться при изучении различных способов взаимодействия с трехмерными объектами в следующих разделах этого руководства.</span><span class="sxs-lookup"><span data-stu-id="e6808-124">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="e6808-125">В частности, вы настроите трехмерные объекты для размещения в сетке 3 x 3.</span><span class="sxs-lookup"><span data-stu-id="e6808-125">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="e6808-126">Точно так же, как и при [создании панели кнопок](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), необходимо выполнить следующие основные действия.</span><span class="sxs-lookup"><span data-stu-id="e6808-126">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="e6808-127">Родительские трехмерные объекты с родительским объектом</span><span class="sxs-lookup"><span data-stu-id="e6808-127">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="e6808-128">Добавление и настройка компонента "Коллекция объектов сетки" (скрипт)</span><span class="sxs-lookup"><span data-stu-id="e6808-128">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="e6808-129">1. Отображение трехмерных объектов в родительский объект</span><span class="sxs-lookup"><span data-stu-id="e6808-129">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="e6808-130">В окне Иерархия **Создайте пустой объект**, присвойте ему подходящее имя, например **3DObjectCollection**, и поместите его в подходящее расположение, например X = 0, Y =-0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="e6808-130">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="e6808-131">В окне проекта перейдите к разделу **активы** > **мртк. Учебники. GettingStarted** > **Prefabs**, а затем **родительский** элемент Prefabs в **3DObjectCollection**:</span><span class="sxs-lookup"><span data-stu-id="e6808-131">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="e6808-132">Мак</span><span class="sxs-lookup"><span data-stu-id="e6808-132">Cheese</span></span>
* <span data-ttu-id="e6808-133">коффикуп</span><span class="sxs-lookup"><span data-stu-id="e6808-133">CoffeeCup</span></span>
* <span data-ttu-id="e6808-134">еарскоре</span><span class="sxs-lookup"><span data-stu-id="e6808-134">EarthCore</span></span>
* <span data-ttu-id="e6808-135">Восьмиядерными</span><span class="sxs-lookup"><span data-stu-id="e6808-135">Octa</span></span>
* <span data-ttu-id="e6808-136">Платоновыми</span><span class="sxs-lookup"><span data-stu-id="e6808-136">Platonic</span></span>
* <span data-ttu-id="e6808-137">семодуле</span><span class="sxs-lookup"><span data-stu-id="e6808-137">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="e6808-139">В окне Иерархия **Создайте три Куба** в качестве дочерних объектов **3DObjectCollection** и задайте для их **шкалы** преобразования значение X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="e6808-139">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="e6808-141">Напоминание о том, как выполнить перечисленные выше действия, можно найти в руководстве [Создание пользовательского интерфейса и настройка набора средств смешанной реальности](mrlearning-base-ch2.md) .</span><span class="sxs-lookup"><span data-stu-id="e6808-141">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="e6808-142">Перемещайте Кубы, чтобы можно было увидеть каждый куб:</span><span class="sxs-lookup"><span data-stu-id="e6808-142">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="e6808-144">В окне проекта перейдите к разделу **активы** > **микседреалититулкит. SDK** > **стандардассетс** > **материалы** , чтобы просмотреть материалы, предоставленные в мртк.</span><span class="sxs-lookup"><span data-stu-id="e6808-144">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="e6808-145">**Щелкните и перетащите** подходящий материал для каждого из свойств элемент " **материалы** " для модуля подготовки сетки Куба, например:</span><span class="sxs-lookup"><span data-stu-id="e6808-145">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="e6808-146">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="e6808-146">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="e6808-147">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="e6808-147">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="e6808-148">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="e6808-148">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="e6808-150">2. Добавление и настройка компонента "Коллекция объектов сетки" (скрипт)</span><span class="sxs-lookup"><span data-stu-id="e6808-150">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="e6808-151">Добавьте компонент **коллекции объектов Grid (скрипт)** в объект **3DObjectCollection** и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e6808-151">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="e6808-152">Измените **Тип сортировки** на **дочерний порядок** , чтобы обеспечить сортировку дочерних объектов в том порядке, в котором они были помещены в родительский объект.</span><span class="sxs-lookup"><span data-stu-id="e6808-152">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="e6808-153">Затем нажмите кнопку **Update Collection (обновить коллекцию** ), чтобы применить новую конфигурацию:</span><span class="sxs-lookup"><span data-stu-id="e6808-153">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="e6808-155">Обработка трехмерных объектов</span><span class="sxs-lookup"><span data-stu-id="e6808-155">Manipulating 3D objects</span></span>

<span data-ttu-id="e6808-156">В этом разделе вы добавите возможность манипулировать всеми трехмерными объектами на панели, созданной в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="e6808-156">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="e6808-157">Кроме того, для объектов prefab вы сможете предоставить пользователям возможность обращаться к этим объектам с помощью отслеживания руки.</span><span class="sxs-lookup"><span data-stu-id="e6808-157">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="e6808-158">Затем будет рассмотрено несколько поведений манипуляций, которые можно применить к объектам.</span><span class="sxs-lookup"><span data-stu-id="e6808-158">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="e6808-159">Ниже приведены основные действия, которые необходимо выполнить для достижения этого результата.</span><span class="sxs-lookup"><span data-stu-id="e6808-159">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="e6808-160">Добавление компонента обработчика манипуляций (скрипт) для всех объектов</span><span class="sxs-lookup"><span data-stu-id="e6808-160">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="e6808-161">Добавление компонента, который можно получить с помощью диалогового окна близкого взаимодействия (скрипт), к объектам prefab</span><span class="sxs-lookup"><span data-stu-id="e6808-161">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="e6808-162">Настройка компонента обработчика манипуляции (скрипт)</span><span class="sxs-lookup"><span data-stu-id="e6808-162">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6808-163">Чтобы иметь возможность **манипулировать объектом**, объект должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="e6808-163">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="e6808-164">**Компонент,** например, элемент списка конфликтующих</span><span class="sxs-lookup"><span data-stu-id="e6808-164">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="e6808-165">Компонент **обработчика манипуляций (скрипт)**</span><span class="sxs-lookup"><span data-stu-id="e6808-165">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="e6808-166">Чтобы иметь возможность **манипулировать** и **захватить объект с отслеживающими**действиями, объект должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="e6808-166">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="e6808-167">**Компонент,** например, элемент списка конфликтующих</span><span class="sxs-lookup"><span data-stu-id="e6808-167">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="e6808-168">Компонент **обработчика манипуляций (скрипт)**</span><span class="sxs-lookup"><span data-stu-id="e6808-168">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="e6808-169">Компонент, который **приближается к взаимодействию (скрипт)**</span><span class="sxs-lookup"><span data-stu-id="e6808-169">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="e6808-170">1. Добавьте компонент обработчика манипуляций (скрипт) для всех объектов.</span><span class="sxs-lookup"><span data-stu-id="e6808-170">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="e6808-171">В окне Иерархия выберите объект **Мак** , нажмите и удерживайте клавишу **SHIFT** , а затем выберите объект **Cube () 2** и добавьте компонент **обработчика манипуляций (script)** для всех объектов:</span><span class="sxs-lookup"><span data-stu-id="e6808-171">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e6808-173">В рамках этого руководства в Prefabs уже добавлены конфликты.</span><span class="sxs-lookup"><span data-stu-id="e6808-173">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="e6808-174">Для примитивов Unity, таких как объекты куба, автоматически добавляется компонент "конфликты" при создании объекта.</span><span class="sxs-lookup"><span data-stu-id="e6808-174">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="e6808-175">На приведенном выше рисунке конфликты представлены зелеными контурами.</span><span class="sxs-lookup"><span data-stu-id="e6808-175">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="e6808-176">Дополнительные сведения о конфликтах см. <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">в документации по средству для Unity</a> .</span><span class="sxs-lookup"><span data-stu-id="e6808-176">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="e6808-177">2. Добавьте компонент "близкое к взаимодействию" (скрипт) для объектов prefab</span><span class="sxs-lookup"><span data-stu-id="e6808-177">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="e6808-178">В окне Иерархия выберите объект **Мак** , нажмите и удерживайте клавишу **SHIFT** , а затем выберите объект **Семодуле** и добавьте компонент " **ближайший к взаимодействию" (скрипт)** для всех объектов:</span><span class="sxs-lookup"><span data-stu-id="e6808-178">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="e6808-180">3. Настройка компонента обработчика манипуляции (скрипт)</span><span class="sxs-lookup"><span data-stu-id="e6808-180">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="e6808-181">Обработка по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e6808-181">Default manipulation</span></span>

<span data-ttu-id="e6808-182">Для объекта **куба** оставьте все свойства по умолчанию, чтобы работать с поведением по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="e6808-182">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="e6808-184">Чтобы сбросить компонент до значений по умолчанию, можно выбрать значок параметров компонента и нажать кнопку Сбросить.</span><span class="sxs-lookup"><span data-stu-id="e6808-184">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="e6808-185">Ограничить манипуляцию только масштабированием</span><span class="sxs-lookup"><span data-stu-id="e6808-185">Restrict manipulation to scale only</span></span>

<span data-ttu-id="e6808-186">Для объекта **Cube (1)** измените значение **двух типов манипуляции** на **масштабирование** , чтобы разрешить пользователю изменять размер объекта:</span><span class="sxs-lookup"><span data-stu-id="e6808-186">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="e6808-188">Ограничение перемещения до фиксированного расстояния от пользователя</span><span class="sxs-lookup"><span data-stu-id="e6808-188">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="e6808-189">Для объекта **Cube (2)** измените **Ограничение перемещения** , чтобы **исправить расстояние от заголовка** , чтобы при перемещении объекта оно оставалось на том же расстоянии от пользователя:</span><span class="sxs-lookup"><span data-stu-id="e6808-189">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="e6808-191">Манипуляция, используемая по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e6808-191">Default grabbable manipulation</span></span>

<span data-ttu-id="e6808-192">Для объектов **Мак**, **коффекуп**и **еарскоре** оставьте все свойства по умолчанию, чтобы можно было задействовать поведение манипуляции по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e6808-192">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="e6808-194">Удаление возможности выполнения манипуляций</span><span class="sxs-lookup"><span data-stu-id="e6808-194">Remove the ability of far manipulation</span></span>

<span data-ttu-id="e6808-195">Для объекта **восьмиядерными** снимите флажок **Разрешить манипуляцию** , чтобы сделать его возможным, чтобы пользователь мог взаимодействовать с объектом напрямую, используя записанные руки:</span><span class="sxs-lookup"><span data-stu-id="e6808-195">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="e6808-197">Вращение объекта вокруг его центра</span><span class="sxs-lookup"><span data-stu-id="e6808-197">Make an object rotate around its center</span></span>

<span data-ttu-id="e6808-198">Для объекта **Платоновыми** измените **режим поворота руки рядом** с **одним режимом поворота** , который можно повернуть на « **центр объектов** », чтобы сделать так, что когда пользователь поворачивает объект с одной стороны, он поворачивается вокруг центра объекта:</span><span class="sxs-lookup"><span data-stu-id="e6808-198">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="e6808-200">Удерживать перемещение после освобождения объекта</span><span class="sxs-lookup"><span data-stu-id="e6808-200">Keep movement after object is released</span></span>

<span data-ttu-id="e6808-201">Для объекта **семодуле** добавьте компонент **RigidBody** , чтобы включить функцию "физика", а затем снимите флажок " **использовать** задолженность", чтобы на объект не влияла сила притяжения:</span><span class="sxs-lookup"><span data-stu-id="e6808-201">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="e6808-203">Вернитесь к компоненту обработчика манипуляции (скрипт), убедитесь, что для **поведения выпуска** задано значение " **поддерживать скорость** " и " **удерживать угловую скорость** ", чтобы после того, как объект был освобожден от руки пользователя, он продолжает перемещаться:</span><span class="sxs-lookup"><span data-stu-id="e6808-203">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="e6808-205">Дополнительные сведения о компоненте обработчика манипуляции и связанных с ним свойствах см. в руководстве по [обработчику манипуляции](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) на [портале документации мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e6808-205">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="e6808-206">Добавление ограничивающих прямоугольников</span><span class="sxs-lookup"><span data-stu-id="e6808-206">Adding bounding boxes</span></span>

<span data-ttu-id="e6808-207">Ограничивающие прямоугольники упрощают и интуитивно обрабатывают объекты с одной стороны как для почти, так и для дальнего взаимодействия, предоставляя маркеры, которые можно использовать для масштабирования и поворота.</span><span class="sxs-lookup"><span data-stu-id="e6808-207">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="e6808-208">В этом примере вы добавите ограничивающий прямоугольник к объекту Еарскоре, чтобы теперь этот объект мог взаимодействовать с помощью манипуляции с объектами, настроенными в предыдущем разделе, а также масштабированием и поворотом с помощью маркеров ограничивающего прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="e6808-208">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6808-209">Чтобы иметь возможность использовать **ограничивающий прямоугольник**, объект должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="e6808-209">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="e6808-210">**Компонент,** например, элемент списка конфликтующих</span><span class="sxs-lookup"><span data-stu-id="e6808-210">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="e6808-211">Компонент **ограничивающего прямоугольника (скрипт)**</span><span class="sxs-lookup"><span data-stu-id="e6808-211">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="e6808-212">1. Добавьте компонент ограничивающего прямоугольника (script) в объект Еарскоре</span><span class="sxs-lookup"><span data-stu-id="e6808-212">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="e6808-213">В окне инспектора выберите объект **еарскоре** и добавьте компонент **ограничивающего прямоугольника (script)** в объект еарскоре:</span><span class="sxs-lookup"><span data-stu-id="e6808-213">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e6808-215">Визуализация ограничивающего прямоугольника создается во время выполнения и, следовательно, не отображается перед переходом в режим игры.</span><span class="sxs-lookup"><span data-stu-id="e6808-215">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="e6808-216">2. Визуализация и тестирование ограничивающего прямоугольника с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="e6808-216">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="e6808-217">Нажмите кнопку "Воспроизведение", чтобы перейти в режим игры.</span><span class="sxs-lookup"><span data-stu-id="e6808-217">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="e6808-218">Затем нажмите и удерживайте клавишу пробел, чтобы открыть руку и использовать мышь для взаимодействия с ограничивающим прямоугольником:</span><span class="sxs-lookup"><span data-stu-id="e6808-218">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="e6808-220">Дополнительные сведения о компоненте ограничивающего прямоугольника и связанных с ним свойствах см. в руководстве по использованию [ограничивающего прямоугольника](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) на [портале документации мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e6808-220">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="e6808-221">Добавление эффектов касания</span><span class="sxs-lookup"><span data-stu-id="e6808-221">Adding touch effects</span></span>

<span data-ttu-id="e6808-222">В этом примере вы включите события, которые будут запускаться при касании объекта рукой.</span><span class="sxs-lookup"><span data-stu-id="e6808-222">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="e6808-223">В частности, вы настраиваете объект восьмиядерными для воспроизведения звукового эффекта, когда пользователь обращается к нему.</span><span class="sxs-lookup"><span data-stu-id="e6808-223">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="e6808-224">Ниже приведены основные действия, которые необходимо выполнить для достижения этого результата.</span><span class="sxs-lookup"><span data-stu-id="e6808-224">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="e6808-225">Добавление компонента "источник звука" в объект</span><span class="sxs-lookup"><span data-stu-id="e6808-225">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="e6808-226">Добавление в объект компонента с сенсорным взаимодействием (script)</span><span class="sxs-lookup"><span data-stu-id="e6808-226">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="e6808-227">Добавление компонента взаимодействия руки (script) в объект</span><span class="sxs-lookup"><span data-stu-id="e6808-227">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="e6808-228">Реализовать событие on Touch Started</span><span class="sxs-lookup"><span data-stu-id="e6808-228">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="e6808-229">Тестирование взаимодействия касания с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="e6808-229">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6808-230">Чтобы **активировать события касания**, объект должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="e6808-230">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="e6808-231">**Компоненту** , лучше всего, конфликтующему рамку</span><span class="sxs-lookup"><span data-stu-id="e6808-231">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="e6808-232">Компонент для **сенсорного взаимодействия ближнего действия (скрипт)**</span><span class="sxs-lookup"><span data-stu-id="e6808-232">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="e6808-233">Компонент **взаимодействия руки (сценарий)**</span><span class="sxs-lookup"><span data-stu-id="e6808-233">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="e6808-234">Компонент взаимодействия руки (script) не является частью МРТК.</span><span class="sxs-lookup"><span data-stu-id="e6808-234">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="e6808-235">Она была импортирована в активы этого учебника и изначально входит в примеры Unity Toolkit Микседреалити.</span><span class="sxs-lookup"><span data-stu-id="e6808-235">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="e6808-236">1. Добавление компонента "источник звука" в объект</span><span class="sxs-lookup"><span data-stu-id="e6808-236">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="e6808-237">В окне Иерархия выберите объект **восьмиядерными** , добавьте компонент " **источник звука** " в объект восьмиядерными, а затем измените **пространственный Blend** на 1, чтобы включить Пространственный звук:</span><span class="sxs-lookup"><span data-stu-id="e6808-237">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="e6808-239">2. Добавьте в объект компонент с сенсорным взаимодействием (script).</span><span class="sxs-lookup"><span data-stu-id="e6808-239">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="e6808-240">Выбрав объект **восьмиядерными** , добавьте в объект восьмиядерными элемент с **сенсорным взаимодействием (script)** , а затем щелкните кнопки **исправить границы** и **центр исправлений** , чтобы обновить локальные свойства центра и границ близкого взаимодействия (скрипт), чтобы они соответствовали боксколлидер:</span><span class="sxs-lookup"><span data-stu-id="e6808-240">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="e6808-242">3. Добавление компонента взаимодействия руки (script) в объект</span><span class="sxs-lookup"><span data-stu-id="e6808-242">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="e6808-243">Если объект **восьмиядерными** все еще выбран, добавьте компонент **взаимодействия с руки (script)** в объект восьмиядерными:</span><span class="sxs-lookup"><span data-stu-id="e6808-243">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="e6808-245">4. Реализуйте событие on Touch Started</span><span class="sxs-lookup"><span data-stu-id="e6808-245">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="e6808-246">В компоненте **взаимодействия руки (скрипт)** щелкните маленький значок **+** , чтобы создать событие **при запуске касания ()** .</span><span class="sxs-lookup"><span data-stu-id="e6808-246">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="e6808-247">Затем настройте объект **восьмиядерными** для получения события и определите **аудиосаурце. плайонешот** в качестве запускаемого действия:</span><span class="sxs-lookup"><span data-stu-id="e6808-247">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="e6808-249">Перейдите к разделу **активы** > **микседреалититулкит. SDK** > **стандардассетс** > материалы, чтобы просмотреть аудиоклипы, предоставленные мртк, а затем назначьте подходящий звуковой клип полю **аудиоклипа** , например, MRTK_Gem аудиоклип:</span><span class="sxs-lookup"><span data-stu-id="e6808-249">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="e6808-251">Напоминание о том, как реализовать события, можно найти в разделе [жесты отслеживания руки и инструкции по взаимодействию с управляемыми кнопками](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .</span><span class="sxs-lookup"><span data-stu-id="e6808-251">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="e6808-252">5. Тестирование взаимодействия касания с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="e6808-252">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="e6808-253">Нажмите кнопку "Воспроизведение", чтобы перейти в режим игры.</span><span class="sxs-lookup"><span data-stu-id="e6808-253">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="e6808-254">Затем нажмите и удерживайте клавишу пробел, чтобы вывести руку и использовать мышь для касания объекта восьмиядерными и запуска звукового эффекта:</span><span class="sxs-lookup"><span data-stu-id="e6808-254">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="e6808-256">Как вы видели при тестировании сенсорного взаимодействия, как показано на рисунке выше, объект восьмиядерными Color пулсатед, когда он был затронут.</span><span class="sxs-lookup"><span data-stu-id="e6808-256">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="e6808-257">Этот результат жестко закодирован в компоненте взаимодействия руки (script), а не в результате настройки события, выполненной в предыдущих шагах.</span><span class="sxs-lookup"><span data-stu-id="e6808-257">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="e6808-258">Если вы хотите отключить этот результат, можно, например, закомментировать или строку 32 ' Таржетрендерер = Жеткомпонентинчилдрен<Renderer>(); ', что приведет к тому, что Таржетрендерер будет иметь значение NULL и цвет не пулсатинг.</span><span class="sxs-lookup"><span data-stu-id="e6808-258">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e6808-259">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="e6808-259">Congratulations</span></span>

<span data-ttu-id="e6808-260">В этом учебнике вы узнали, как упорядочивать трехмерные объекты в коллекции Grid и как управлять этими объектами (масштабирование, вращение и перемещение) с помощью ближнего взаимодействия (с отслеживанием руки) и намного взаимодействием (с использованием лучей или лучей).</span><span class="sxs-lookup"><span data-stu-id="e6808-260">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="e6808-261">Вы также узнали, как разместить ограничивающие прямоугольники вокруг трехмерных объектов и как использовать и настраивать маркеры в ограничивающих прямоугольниках.</span><span class="sxs-lookup"><span data-stu-id="e6808-261">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="e6808-262">И наконец, вы научились инициировать события при касании объекта.</span><span class="sxs-lookup"><span data-stu-id="e6808-262">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="e6808-263">Следующее занятие: 6. Просмотр дополнительных параметров ввода</span><span class="sxs-lookup"><span data-stu-id="e6808-263">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
