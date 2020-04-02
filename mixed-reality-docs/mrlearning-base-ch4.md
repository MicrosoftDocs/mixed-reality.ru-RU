---
title: Серия руководств по началу работы, часть 5. Взаимодействие с трехмерными объектами
description: Сведения о базовом содержимом и интерфейсах пользователя в трехмерной среде, в том числе об упорядочении трехмерных объектов и ограничивающих прямоугольниках для простого манипулирования.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 65bcef6a7c10450816d7a928302b0b266b132f0f
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362070"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="34aad-105">5. Взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="34aad-105">5. Interacting with 3D objects</span></span>

<span data-ttu-id="34aad-106">В этом руководстве содержатся базовые сведения о содержимом и взаимодействии с пользователем в трехмерной среде. В частности, вы узнаете, как упорядочивать трехмерные объекты в составе коллекции и использовать ограничивающие рамки для простых манипуляций, а также что такое ближнее и дальнее взаимодействие и как использовать отслеживание рук для жестов касания и захвата.</span><span class="sxs-lookup"><span data-stu-id="34aad-106">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="34aad-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="34aad-107">Objectives</span></span>

* <span data-ttu-id="34aad-108">Создание панели трехмерных объектов, которые будут далее использоваться для других целей обучения</span><span class="sxs-lookup"><span data-stu-id="34aad-108">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="34aad-109">Реализация ограничивающих рамок.</span><span class="sxs-lookup"><span data-stu-id="34aad-109">Implement bounding boxes</span></span>
* <span data-ttu-id="34aad-110">Настройка трехмерных объектов для базовых манипуляций (перемещение, поворот и масштабирование).</span><span class="sxs-lookup"><span data-stu-id="34aad-110">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="34aad-111">Изучение ближнего и дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="34aad-111">Explore near and far interaction</span></span>
* <span data-ttu-id="34aad-112">Освоение дополнительных жестов, таких как захват и касание, при работе с отслеживанием рук.</span><span class="sxs-lookup"><span data-stu-id="34aad-112">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="34aad-113">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="34aad-113">Importing the tutorial assets</span></span>

<span data-ttu-id="34aad-114">Скачайте и импортируйте пользовательский пакет Unity:</span><span class="sxs-lookup"><span data-stu-id="34aad-114">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="34aad-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="34aad-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

<span data-ttu-id="34aad-116">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="34aad-116">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="34aad-118">Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="34aad-118">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="34aad-119">Устранение захламленности представления сцены</span><span class="sxs-lookup"><span data-stu-id="34aad-119">Decluttering the scene view</span></span>

<span data-ttu-id="34aad-120">Чтобы работать со сценой было проще, отключите параметр **Scene Visibility** (Видимость сцены) для объектов **Cube** и **ButtonCollection**. Для этого щелкните значки с изображением **глаза** слева от этих объектов.</span><span class="sxs-lookup"><span data-stu-id="34aad-120">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="34aad-121">Так вы спрячете объект в окне сцены, не изменяя его внутриигровой видимости.</span><span class="sxs-lookup"><span data-stu-id="34aad-121">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="34aad-123">Дополнительные сведения об элементах управления видимостью и их применении для оптимизации представления сцены и рабочего процесса вы можете найти на <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">этой странице</a> документации.</span><span class="sxs-lookup"><span data-stu-id="34aad-123">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="34aad-124">Упорядочение трехмерных объектов в коллекции</span><span class="sxs-lookup"><span data-stu-id="34aad-124">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="34aad-125">В рамках этого раздела вы создадите панель трехмерных объектов, которые при работе со следующими разделами этого руководства примените для изучения разных способов взаимодействия с трехмерными объектами.</span><span class="sxs-lookup"><span data-stu-id="34aad-125">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="34aad-126">В частности, вы разместите трехмерные объекты в сетке 3x3.</span><span class="sxs-lookup"><span data-stu-id="34aad-126">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="34aad-127">Точно так же, как и при [создании панели кнопок](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), необходимо выполнить следующие основные действия:</span><span class="sxs-lookup"><span data-stu-id="34aad-127">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="34aad-128">Присвоение родительского объекта для трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="34aad-128">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="34aad-129">Добавление и настройка компонента Grid Object Collection (Script) (Коллекция объектов сетки — скрипт).</span><span class="sxs-lookup"><span data-stu-id="34aad-129">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="34aad-130">1. Присвоение родительского объекта для трехмерных объектов</span><span class="sxs-lookup"><span data-stu-id="34aad-130">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="34aad-131">В окне "Иерархия" **создайте пустой объект**. Присвойте ему подходящее имя, например **3DObjectCollection**, и разместите его в подходящем расположении, например с координатами X = 0, Y = –0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="34aad-131">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="34aad-132">В окне Project (Проект) перейдите к разделу **Assets** (Активы) > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Заготовки). Затем присвойте значение **родительского объекта** **3DObjectCollection** для следующих заготовок:</span><span class="sxs-lookup"><span data-stu-id="34aad-132">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="34aad-133">Cheese;</span><span class="sxs-lookup"><span data-stu-id="34aad-133">Cheese</span></span>
* <span data-ttu-id="34aad-134">CoffeeCup;</span><span class="sxs-lookup"><span data-stu-id="34aad-134">CoffeeCup</span></span>
* <span data-ttu-id="34aad-135">EarthCore;</span><span class="sxs-lookup"><span data-stu-id="34aad-135">EarthCore</span></span>
* <span data-ttu-id="34aad-136">Octa;</span><span class="sxs-lookup"><span data-stu-id="34aad-136">Octa</span></span>
* <span data-ttu-id="34aad-137">Platonic;</span><span class="sxs-lookup"><span data-stu-id="34aad-137">Platonic</span></span>
* <span data-ttu-id="34aad-138">TheModule.</span><span class="sxs-lookup"><span data-stu-id="34aad-138">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="34aad-140">В окне "Иерархия" **создайте три куба** в качестве дочерних объектов для объекта **3DObjectCollection**. Присвойте значению преобразования **Масштаб** координаты X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="34aad-140">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="34aad-142">Руководство по [созданию пользовательского интерфейса и настройке Набора средств для смешанной реальности](mrlearning-base-ch2.md) поможет освежить знания о выполнении описанных выше действий.</span><span class="sxs-lookup"><span data-stu-id="34aad-142">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="34aad-143">Переместите кубы таким образом, чтобы все они были хорошо видны:</span><span class="sxs-lookup"><span data-stu-id="34aad-143">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="34aad-145">В окне Project (Проект) перейдите к разделу **Assets** (Активы) > **MixedRealityToolkit.SDK** > **StandardAssets** (Стандартные активы) > **Materials** (Материалы), чтобы просмотреть включенные в состав MRTK материалы.</span><span class="sxs-lookup"><span data-stu-id="34aad-145">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="34aad-146">**Щелкните и перетащите** подходящие материалы на свойство **Материалы** для элемента 0 каждого куба в отрисовщике сетки:</span><span class="sxs-lookup"><span data-stu-id="34aad-146">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="34aad-147">MRTK_Standard_GlowingCyan;</span><span class="sxs-lookup"><span data-stu-id="34aad-147">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="34aad-148">MRTK_Standard_GlowingOrange;</span><span class="sxs-lookup"><span data-stu-id="34aad-148">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="34aad-149">MRTK_Standard_Green.</span><span class="sxs-lookup"><span data-stu-id="34aad-149">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="34aad-151">2. Добавление и настройка компонента Grid Object Collection (Script) (Коллекция объектов сетки — скрипт).</span><span class="sxs-lookup"><span data-stu-id="34aad-151">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="34aad-152">Добавьте компонент **Grid Object Collection (Script)** (Коллекция объектов сетки — скрипт) в объект **3DObjectCollection**. Настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34aad-152">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="34aad-153">Для параметра **Sort Type** (Тип сортировки) укажите значение **Child Order** (В порядке дочерних объектов), чтобы отсортировать дочерние объекты в порядке их размещения в родительском объекте.</span><span class="sxs-lookup"><span data-stu-id="34aad-153">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="34aad-154">Нажмите кнопку **Update Collection** (Обновить коллекцию), чтобы применить новую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="34aad-154">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="34aad-156">Работа с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="34aad-156">Manipulating 3D objects</span></span>

<span data-ttu-id="34aad-157">В рамках этого раздела вы добавите возможность манипулировать трехмерными объектами, размещенными на созданной в предыдущем разделе панели.</span><span class="sxs-lookup"><span data-stu-id="34aad-157">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="34aad-158">Кроме того, для заготовок вы настроите возможность трогать и захватывать эти объекты отслеживаемыми руками.</span><span class="sxs-lookup"><span data-stu-id="34aad-158">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="34aad-159">После этого вы изучите некоторые поведения манипуляции, которые можно применить к объектам.</span><span class="sxs-lookup"><span data-stu-id="34aad-159">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="34aad-160">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="34aad-160">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="34aad-161">Добавьте компонент "Manipulation Handler (Script)" (Обработчик манипуляций — скрипт) ко всем объектам.</span><span class="sxs-lookup"><span data-stu-id="34aad-161">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="34aad-162">Добавьте компонент "Near Interaction Grabbable (Script)" (Возможность захвата при близком взаимодействии — скрипт) к объектам заготовок.</span><span class="sxs-lookup"><span data-stu-id="34aad-162">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="34aad-163">Настройте компонент "Manipulation Handler (Script)" (Обработчик манипуляций — скрипт).</span><span class="sxs-lookup"><span data-stu-id="34aad-163">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34aad-164">Чтобы **объект поддерживал манипуляции**, он должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="34aad-164">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="34aad-165">компонент **Collider** (Коллайдер), например Box Collider;</span><span class="sxs-lookup"><span data-stu-id="34aad-165">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="34aad-166">компонент **Manipulation Handler (Script)** (Обработчик манипуляций — скрипт).</span><span class="sxs-lookup"><span data-stu-id="34aad-166">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="34aad-167">Чтобы **объект поддерживал манипуляции** и **захват отслеживаемыми руками**, он должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="34aad-167">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="34aad-168">компонент **Collider** (Коллайдер), например Box Collider;</span><span class="sxs-lookup"><span data-stu-id="34aad-168">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="34aad-169">компонент **Manipulation Handler (Script)** (Обработчик манипуляций — скрипт);</span><span class="sxs-lookup"><span data-stu-id="34aad-169">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="34aad-170">компонент **Near Interaction Grabbable (Script)** (Возможность захвата при близком взаимодействии — скрипт).</span><span class="sxs-lookup"><span data-stu-id="34aad-170">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="34aad-171">1. Добавление компонента "Manipulation Handler (Script)" (Обработчик манипуляций — скрипт) ко всем объектам</span><span class="sxs-lookup"><span data-stu-id="34aad-171">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="34aad-172">В окне "Иерархия" выберите объект **Cheese**. Затем нажмите и удерживайте клавишу **SHIFT**. Выберите объект **Cube () 2** и добавьте ко всем выбранным объектам компонент **Manipulation Handler (Script)** (Обработчик манипуляций —скрипт):</span><span class="sxs-lookup"><span data-stu-id="34aad-172">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="34aad-174">Для выполнения задач этого руководства в заготовки уже добавлены коллайдеры.</span><span class="sxs-lookup"><span data-stu-id="34aad-174">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="34aad-175">В примитивах Unity, например в объектах Cube, компоненты коллайдера добавляются автоматически при создании объекта.</span><span class="sxs-lookup"><span data-stu-id="34aad-175">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="34aad-176">На приведенном выше изображении коллайдеры обведены зелеными контурами.</span><span class="sxs-lookup"><span data-stu-id="34aad-176">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="34aad-177">Чтобы получить дополнительные сведения о коллайдерах, воспользуйтесь <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">этим разделом</a> из документации по Unity.</span><span class="sxs-lookup"><span data-stu-id="34aad-177">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="34aad-178">2. Добавление компонента "Near Interaction Grabbable (Script)" (Возможность захвата при близком взаимодействии — скрипт) к объектам заготовок</span><span class="sxs-lookup"><span data-stu-id="34aad-178">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="34aad-179">В окне "Иерархия" выберите объект **Cheese**. Затем нажмите и удерживайте клавишу **SHIFT**, выберите объект **TheModule**. Добавьте ко всем выбранным объектам компонент **Near Interaction Grabbable (Script)** (Возможность захвата при близком взаимодействии — скрипт):</span><span class="sxs-lookup"><span data-stu-id="34aad-179">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="34aad-181">3. Настройте компонент "Manipulation Handler (Script)" (Обработчик манипуляций — скрипт).</span><span class="sxs-lookup"><span data-stu-id="34aad-181">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="34aad-182">Стандартное манипулирование</span><span class="sxs-lookup"><span data-stu-id="34aad-182">Default manipulation</span></span>

<span data-ttu-id="34aad-183">Для объекта **Cube** сохраните значения всех свойств по умолчанию, чтобы проверить в работе стандартное поведение манипулирования:</span><span class="sxs-lookup"><span data-stu-id="34aad-183">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="34aad-185">Чтобы сбросить настройки компонента на стандартные, щелкните значок "Параметры" этого компонента и выберите действие "Сбросить".</span><span class="sxs-lookup"><span data-stu-id="34aad-185">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="34aad-186">Ограничение манипулирования только масштабированием</span><span class="sxs-lookup"><span data-stu-id="34aad-186">Restrict manipulation to scale only</span></span>

<span data-ttu-id="34aad-187">Для объекта **Cube (1)** измените значение параметра **Two Handed Manipulation Type** (Тип манипулирования двумя руками) на **Scale** (Масштабирование), чтобы пользователь мог изменять у этого объекта только размер:</span><span class="sxs-lookup"><span data-stu-id="34aad-187">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="34aad-189">Ограничение манипулирования фиксированной дистанцией до пользователя</span><span class="sxs-lookup"><span data-stu-id="34aad-189">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="34aad-190">Для объекта **Cube (2)** измените значение параметра **Constraint On Movement** (Ограничения на перемещение) на **Fix Distance From Head** (Фиксированное расстояние до головы), чтобы при любом перемещении объекта он оставался на том же удалении от пользователя:</span><span class="sxs-lookup"><span data-stu-id="34aad-190">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="34aad-192">Стандартное манипулирование с возможностью захвата</span><span class="sxs-lookup"><span data-stu-id="34aad-192">Default grabbable manipulation</span></span>

<span data-ttu-id="34aad-193">Для объектов **Cheese**, **CoffeCup** и **EarthCore** сохраните значения всех свойств по умолчанию, чтобы проверить в работе стандартное поведение манипулирования с возможностью захвата:</span><span class="sxs-lookup"><span data-stu-id="34aad-193">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="34aad-195">Удаление возможности дальнего манипулирования</span><span class="sxs-lookup"><span data-stu-id="34aad-195">Remove the ability of far manipulation</span></span>

<span data-ttu-id="34aad-196">Для объекта **Octa** снимите флажок **Allow Far Manipulation** (Разрешать дальнее манипулирование), чтобы пользователь мог взаимодействовать с этим объектом только при непосредственном контакте отслеживаемых рук:</span><span class="sxs-lookup"><span data-stu-id="34aad-196">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="34aad-198">Настройка поворота объекта вокруг его центральной точки</span><span class="sxs-lookup"><span data-stu-id="34aad-198">Make an object rotate around its center</span></span>

<span data-ttu-id="34aad-199">Для объекта **Platonic** измените значение параметров **One Hand Rotation Mode Near** (Режим вращения одной рукой при ближнем взаимодействии) и **One Hand Rotation Mode Far** (Режим вращения одной рукой при дальнем взаимодействии) на **Rotate About Object Center** (Вращение вокруг центра объекта), чтобы при вращении этого объекта одной рукой он поворачивался вокруг своей центральной точки:</span><span class="sxs-lookup"><span data-stu-id="34aad-199">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="34aad-201">Сохранение движения при отпускании объекта</span><span class="sxs-lookup"><span data-stu-id="34aad-201">Keep movement after object is released</span></span>

<span data-ttu-id="34aad-202">Для объекта **TheModule** добавьте компонент **Rigidbody**, чтобы поддерживать физические законы. Затем удалите флажок **Use Gravity** (Использовать гравитацию), чтобы этот объект не подвергался земному притяжению:</span><span class="sxs-lookup"><span data-stu-id="34aad-202">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="34aad-204">Вернитесь к компоненту "Manipulation Handler (Script)" (Обработчик манипуляций — скрипт) и убедитесь, что для параметра **Release Behavior** (Поведение при отпускании) заданы значения **Keep Velocity** (Сохранять скорость) и **Keep Angular Velocity** (Сохранять угловую скорость), чтобы этот объект продолжал движение при прекращении контакта с рукой пользователя.</span><span class="sxs-lookup"><span data-stu-id="34aad-204">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="34aad-206">Дополнительные сведения о компоненте "Обработчик манипуляции" и его свойствах вы можете получить в [этом руководстве](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="34aad-206">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="34aad-207">Добавление ограничивающих рамок</span><span class="sxs-lookup"><span data-stu-id="34aad-207">Adding bounding boxes</span></span>

<span data-ttu-id="34aad-208">Ограничивающие рамки делают манипулирование объектами одной рукой более простым и интуитивно понятным при ближнем и дальнем взаимодействии, предоставляя маркеры для масштабирования и вращения.</span><span class="sxs-lookup"><span data-stu-id="34aad-208">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="34aad-209">В рамках нашего примера вы добавите ограничивающую рамку к объекту EarthCore, чтобы с этим объектом можно было не только взаимодействовать путем манипулирования, которое вы настроили в предыдущем разделе, но и путем масштабирования, а также вращения с помощью маркеров ограничивающей рамки.</span><span class="sxs-lookup"><span data-stu-id="34aad-209">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34aad-210">Чтобы **использовать ограничивающую рамку**, объект должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="34aad-210">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="34aad-211">компонент **Collider** (Коллайдер), например Box Collider;</span><span class="sxs-lookup"><span data-stu-id="34aad-211">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="34aad-212">компонент **Bounding Box (Script)** (Ограничивающая рамка — скрипт).</span><span class="sxs-lookup"><span data-stu-id="34aad-212">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="34aad-213">1. Добавление компонента Bounding Box (Script) (Ограничивающая рамка — скрипт) к объекту EarthCore</span><span class="sxs-lookup"><span data-stu-id="34aad-213">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="34aad-214">В окне "Инспектор" выберите объект **EarthCore**. Добавьте к нему компонент **Bounding Box (Script)** (Ограничивающая рамка — скрипт).</span><span class="sxs-lookup"><span data-stu-id="34aad-214">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="34aad-216">Визуализация ограничивающей рамки создается во время выполнения. Поэтому вы не увидите ее до входа в игровой режим.</span><span class="sxs-lookup"><span data-stu-id="34aad-216">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="34aad-217">2. Визуализация и тестирование ограничивающей рамки с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="34aad-217">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="34aad-218">Нажмите кнопку Play (Играть), чтобы перейти в игровой режим.</span><span class="sxs-lookup"><span data-stu-id="34aad-218">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="34aad-219">Теперь нажмите и удерживайте клавишу "Пробел", чтобы отобразить руку. С помощью мыши попробуйте взаимодействовать с ограничивающей рамкой.</span><span class="sxs-lookup"><span data-stu-id="34aad-219">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="34aad-221">Дополнительные сведения о компоненте Bounding Box (Ограничивающая рамка) и его свойствах вы можете получить в [этом руководстве](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="34aad-221">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="34aad-222">Добавление поддержки касания</span><span class="sxs-lookup"><span data-stu-id="34aad-222">Adding touch effects</span></span>

<span data-ttu-id="34aad-223">В рамках этого примера мы добавим активацию событий при касании объекта рукой.</span><span class="sxs-lookup"><span data-stu-id="34aad-223">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="34aad-224">В частности, мы настроим для объекта Octa воспроизведение звукового эффекта при касании пользователем.</span><span class="sxs-lookup"><span data-stu-id="34aad-224">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="34aad-225">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="34aad-225">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="34aad-226">Добавление компонента источника звука в объект.</span><span class="sxs-lookup"><span data-stu-id="34aad-226">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="34aad-227">Добавление компонента "Near Interaction Touchable (Script)" (Возможность касания при близком взаимодействии — скрипт) к объекту.</span><span class="sxs-lookup"><span data-stu-id="34aad-227">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="34aad-228">Добавление компонента "Hand Interaction Touch (Script)" (Касание при взаимодействии рукой — скрипт) к объекту.</span><span class="sxs-lookup"><span data-stu-id="34aad-228">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="34aad-229">Реализация события On Touch Started.</span><span class="sxs-lookup"><span data-stu-id="34aad-229">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="34aad-230">Тестирование взаимодействия касанием с помощью имитации в редакторе.</span><span class="sxs-lookup"><span data-stu-id="34aad-230">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34aad-231">Чтобы **запускать события касанием**, объект должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="34aad-231">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="34aad-232">компонент **Collider** (Коллайдер), желательно Box Collider;</span><span class="sxs-lookup"><span data-stu-id="34aad-232">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="34aad-233">компонент **Near Interaction Touchable (Script)** (Возможность касания при ближнем взаимодействии — скрипт);</span><span class="sxs-lookup"><span data-stu-id="34aad-233">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="34aad-234">компонент **Hand Interaction Touch (Script)** (Касание при взаимодействии рукой — скрипт).</span><span class="sxs-lookup"><span data-stu-id="34aad-234">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="34aad-235">Компонент "Hand Interaction Touch (Script)" (Касание при взаимодействии рукой — скрипт) не входит в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="34aad-235">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="34aad-236">Вы импортировали его вместе с другими активами для руководства. Изначально он входил в набор примеров для Набора средств Unity для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="34aad-236">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="34aad-237">1. Добавление компонента источника звука в объект</span><span class="sxs-lookup"><span data-stu-id="34aad-237">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="34aad-238">В окне "Иерархия" выберите объект **Octa**. Добавьте к этому объекту компонент **Audio Source** (Источник звука) и укажите для параметра **Spatial Blend** (Пространственное смешивание) значение 1, чтобы включить пространственный звук.</span><span class="sxs-lookup"><span data-stu-id="34aad-238">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="34aad-240">2. Добавление компонента "Near Interaction Touchable (Script)" (Возможность касания при близком взаимодействии — скрипт) к объекту</span><span class="sxs-lookup"><span data-stu-id="34aad-240">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="34aad-241">Оставляя выделенным объект **Octa**, добавьте компонент **Near Interaction Touchable (Script)** (Возможность касания при ближнем взаимодействии — скрипт). Нажмите кнопки **Fix Bounds** (Зафиксировать границы) и **Fix Center** (Зафиксировать центр) для компонента "Near Interaction Touchable (Script)" (Возможность касания при ближнем взаимодействии — скрипт), чтобы он совпадал с объектом BoxCollider.</span><span class="sxs-lookup"><span data-stu-id="34aad-241">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="34aad-243">3. Добавление компонента "Hand Interaction Touch (Script)" (Касание при взаимодействии рукой — скрипт) к объекту</span><span class="sxs-lookup"><span data-stu-id="34aad-243">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="34aad-244">Сохраняя выделенным объект **Octa**, добавьте компонент **Hand Interaction Touch (Script)** (Касание при взаимодействии рукой — скрипт) к объекту:</span><span class="sxs-lookup"><span data-stu-id="34aad-244">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="34aad-246">4. Реализация события On Touch Started</span><span class="sxs-lookup"><span data-stu-id="34aad-246">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="34aad-247">В компоненте **Hand Interaction Touch (Script)** (Касание при взаимодействии рукой — скрипт) щелкните маленький значок **+** , чтобы создать новое событие **On Touch Started ()** .</span><span class="sxs-lookup"><span data-stu-id="34aad-247">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="34aad-248">Теперь настройте в объекте **Octa** получение события и определите **AudioSource.PlayOneShot** в качестве выполняемого действия:</span><span class="sxs-lookup"><span data-stu-id="34aad-248">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="34aad-250">Перейдите в раздел **Ресурсы** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Audio**, чтобы просмотреть звуковые клипы, предоставленные в комплекте с MRTK. Затем подберите подходящий клип для поля **Звуковой клип**, например MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="34aad-250">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Audio** to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="34aad-252">В разделе об [обработке жестов и нажатий активных кнопок с помощью средства отслеживания руки](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) вы можете освежить свои знания о реализации событий.</span><span class="sxs-lookup"><span data-stu-id="34aad-252">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="34aad-253">5. Тестирование взаимодействия касанием с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="34aad-253">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="34aad-254">Нажмите кнопку Play (Играть), чтобы перейти в игровой режим.</span><span class="sxs-lookup"><span data-stu-id="34aad-254">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="34aad-255">Теперь нажмите и удерживайте клавишу "Пробел", чтобы отобразить руку. С помощью мыши коснитесь объекта Octa для воспроизведения звукового эффекта.</span><span class="sxs-lookup"><span data-stu-id="34aad-255">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="34aad-257">Как вы наблюдали при взаимодействии касанием и как видно на изображении выше, цвет объекта Octa пульсирует при касании.</span><span class="sxs-lookup"><span data-stu-id="34aad-257">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="34aad-258">Этот эффект жестко закодирован в компоненте "Hand Interaction Touch (Script)" (Касание при взаимодействии рукой — скрипт) и не является следствием действий по настройке, которые вы выполняли ранее.</span><span class="sxs-lookup"><span data-stu-id="34aad-258">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="34aad-259">Если вы хотите отключить этот эффект, закомментируйте строку 32 'TargetRenderer = GetComponentInChildren<Renderer>();'. В результате значение TargetRenderer всегда будет NULL и цвет объекта не изменится.</span><span class="sxs-lookup"><span data-stu-id="34aad-259">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="34aad-260">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="34aad-260">Congratulations</span></span>

<span data-ttu-id="34aad-261">Из этого руководства вы узнали, как упорядочить трехмерные объекты в коллекции сетки и манипулировать трехмерными объектами (масштабирование, вращение и перемещение) с помощью близкого взаимодействия (непосредственный захват отслеживаемыми руками) и дальнего взаимодействия (посредством лучей от взгляда или от руки).</span><span class="sxs-lookup"><span data-stu-id="34aad-261">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="34aad-262">Вы также узнали, как разместить ограничивающие рамки вокруг трехмерных объектов, а также использовать и настраивать манипуляторы на этих ограничивающих рамках.</span><span class="sxs-lookup"><span data-stu-id="34aad-262">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="34aad-263">И наконец, вы научились инициировать события при касании объекта.</span><span class="sxs-lookup"><span data-stu-id="34aad-263">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="34aad-264">Следующий урок. 6. Изучение дополнительных входных параметров</span><span class="sxs-lookup"><span data-stu-id="34aad-264">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
