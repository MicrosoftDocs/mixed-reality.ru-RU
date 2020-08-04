---
title: Серия руководств по началу работы, часть 7 Взаимодействие с трехмерными объектами
description: Из этого курса вы узнаете, как с помощью набора средств для смешанной реальности (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f02780a1b9421b814242727ce92311d62b5e3461
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376426"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="df97d-105">7. Взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="df97d-105">7. Interacting with 3D objects</span></span>

<span data-ttu-id="df97d-106">В этом учебнике вы узнаете, как включить манипулирование дальними и ближними трехмерными объектами и ограничить допустимые типы манипуляций.</span><span class="sxs-lookup"><span data-stu-id="df97d-106">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="df97d-107">Вы также узнаете, как добавлять ограничивающие рамки вокруг трехмерных объектов, чтобы упростить управление манипулированием объектов.</span><span class="sxs-lookup"><span data-stu-id="df97d-107">You will also learn how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="df97d-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="df97d-108">Objectives</span></span>

* <span data-ttu-id="df97d-109">Узнайте, как настроить трехмерные объекты, чтобы с ними можно было взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="df97d-109">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="df97d-110">Узнайте, как добавить ограничивающие рамки для трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="df97d-110">Learn how to add bounding boxes to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="df97d-111">Работа с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="df97d-111">Manipulating 3D objects</span></span>

<span data-ttu-id="df97d-112">В этом разделе вы добавите возможность манипулирования всеми деталями лунохода, упорядоченными в таблице, во время работы с [учебником по размещению объектов в сцене](mr-learning-base-04.md).</span><span class="sxs-lookup"><span data-stu-id="df97d-112">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="df97d-113">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="df97d-113">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="df97d-114">Добавить компонент Object Manipulator (Script) (Манипулятор объектами — скрипт) ко всем объектам деталей.</span><span class="sxs-lookup"><span data-stu-id="df97d-114">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="df97d-115">Добавить компонент NearInteractionGrabbable ко всем объектам деталей.</span><span class="sxs-lookup"><span data-stu-id="df97d-115">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="df97d-116">Настройте компонент Object Manipulator (Script) (Манипулятор объектами — скрипт).</span><span class="sxs-lookup"><span data-stu-id="df97d-116">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="df97d-117">Чтобы **объект поддерживал манипуляции**, он должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="df97d-117">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="df97d-118">компонент **Collider** (Коллайдер), например Box Collider;</span><span class="sxs-lookup"><span data-stu-id="df97d-118">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="df97d-119">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт).</span><span class="sxs-lookup"><span data-stu-id="df97d-119">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="df97d-120">Чтобы **объект поддерживал манипуляции** и **захват отслеживаемыми руками**, он должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="df97d-120">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="df97d-121">компонент **Collider** (Коллайдер), например Box Collider;</span><span class="sxs-lookup"><span data-stu-id="df97d-121">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="df97d-122">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт);</span><span class="sxs-lookup"><span data-stu-id="df97d-122">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="df97d-123">компонент **NearInteractionGrabbable**.</span><span class="sxs-lookup"><span data-stu-id="df97d-123">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="df97d-124">Кроме того, необходимо настроить обозреватель лунохода, чтобы можно было разместить детали лунохода и выполнить его полноценную сборку.</span><span class="sxs-lookup"><span data-stu-id="df97d-124">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="df97d-125">В окне Hierarchy (Иерархия) разверните объект RoverExplorer > **RoverParts** и выберите все дочерние объекты деталей лунохода и **RoverAssembly**, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить следующие компоненты ко всем выбранным объектам:</span><span class="sxs-lookup"><span data-stu-id="df97d-125">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="df97d-126">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт);</span><span class="sxs-lookup"><span data-stu-id="df97d-126">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="df97d-127">компонент **NearInteractionGrabbable**;</span><span class="sxs-lookup"><span data-stu-id="df97d-127">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="df97d-128">компонент **Part Assembly Controller (Script)** (Элемент управления сборкой деталей — скрипт).</span><span class="sxs-lookup"><span data-stu-id="df97d-128">**Part Assembly Controller (Script)** component</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="df97d-130">Чтобы выбрать несколько объектов, которые не расположены рядом, нажмите и удерживайте клавишу CTRL и выберите любой объект с помощью кнопки мыши.</span><span class="sxs-lookup"><span data-stu-id="df97d-130">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="df97d-131">Для выполнения задач этого учебника к деталям лунохода уже добавлены коллайдеры.</span><span class="sxs-lookup"><span data-stu-id="df97d-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="df97d-132">Чтобы получить дополнительные сведения о коллайдерах, воспользуйтесь <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">этим разделом</a> из документации по Unity.</span><span class="sxs-lookup"><span data-stu-id="df97d-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="df97d-133">Элемент управления сборкой деталей (скрипт) не является частью МRТК, но включен в активы учебника.</span><span class="sxs-lookup"><span data-stu-id="df97d-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="df97d-134">Выбрав все объекты деталей лунохода и объект RoverAssembly, в окне Inspector (Инспектор) настройте компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="df97d-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="df97d-135">В раскрывающемся списке **Two Handed Manipulation Type** (Тип манипуляции двумя руками), снимите флажок Scale (Масштаб), чтобы были выбраны только параметры **Move** (Перемещение) и **Rotate** (Поворот).</span><span class="sxs-lookup"><span data-stu-id="df97d-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="df97d-137">На этом этапе вы включили манипулирование объектами для всех объектов деталей лунохода и объекта RoverAssembly.</span><span class="sxs-lookup"><span data-stu-id="df97d-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="df97d-138">В окне проекта перейдите к папке **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio**, чтобы найти аудиоклипы:</span><span class="sxs-lookup"><span data-stu-id="df97d-138">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** folder to locate the audio clips:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="df97d-140">В окне Hierarchy (Иерархия) выберите все **объекты деталей лунохода**, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **Audio Sources** (Источники аудио) и настроить его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="df97d-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="df97d-141">В поле **AudioClip** укажите аудиоклип **MRTK_Scale_Start**.</span><span class="sxs-lookup"><span data-stu-id="df97d-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="df97d-142">Снимите флажок **Play On Awake** (Воспроизвести при загрузке).</span><span class="sxs-lookup"><span data-stu-id="df97d-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="df97d-143">Для параметра **Spatial Blend** (Пространственное наложение) установите значение 1.</span><span class="sxs-lookup"><span data-stu-id="df97d-143">Change **Spatial Blend** to 1</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="df97d-145">В окне Hierarchy (Иерархия) разверните объект RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints**, чтобы отобразить все объекты указания расположения, а затем выберите первую деталь лунохода, RoverParts > **Camera_Part** и настройте компонент **Part Assembly Controller (Script)** (Элемент управления сборкой деталей — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="df97d-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="df97d-146">В поле **Location To Place** (Расположение для размещения) укажите объект **Camera_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="df97d-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="df97d-148">**Повторите** это действие для каждого из оставшихся объектов деталей лунохода и объекта RoverAssembly, чтобы настроить компонент **Part Assembly Controller (Script)** (Элемент управления сборкой деталей — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="df97d-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="df97d-149">Для **Generator_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **Generator_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="df97d-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="df97d-150">Для **Lights_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **Lights_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="df97d-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="df97d-151">Для **UHFAntenna_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **UHFAntenna_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="df97d-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="df97d-152">Для **Spectrometer_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **Spectrometer_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="df97d-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="df97d-153">Для **RoverAssembly** укажите сам объект, т. е. тот же объект **RoverAssembly** в поле **Location To Place** (Расположение для размещения).</span><span class="sxs-lookup"><span data-stu-id="df97d-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="df97d-154">В окне Hierarchy (Иерархия) выберите RoverExplorer > Buttons (Кнопки) > объект кнопки **Reset** (Сброс), затем в окне Inspector (Инспектор) настройте интерактивное событие **OnClick ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="df97d-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="df97d-155">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="df97d-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="df97d-156">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **PartAssemblyController** > **ResetPlacement ()** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="df97d-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="df97d-158">Теперь, войдя в игровой режим, вы сможете поместить детали на луноход в режиме ближнего или дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="df97d-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="df97d-159">Когда деталь будет близка к соответствующей подсказке о размещении, она автоматически закрепится в нужном месте и станет деталью лунохода.</span><span class="sxs-lookup"><span data-stu-id="df97d-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="df97d-160">Чтобы сбросить параметры размещения, нажмите кнопку Reset (Сброс):</span><span class="sxs-lookup"><span data-stu-id="df97d-160">To reset the placements, you can press the Reset button:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="df97d-162">Дополнительные сведения о компоненте Object Manipulator (Манипулятор объектами) и его свойствах вы можете получить в [этом учебнике](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="df97d-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="df97d-163">Добавление ограничивающих рамок</span><span class="sxs-lookup"><span data-stu-id="df97d-163">Adding bounding boxes</span></span>

<span data-ttu-id="df97d-164">Ограничивающие рамки делают манипулирование объектами одной рукой более простым и интуитивно понятным при ближнем и дальнем взаимодействии, предоставляя маркеры для масштабирования и вращения.</span><span class="sxs-lookup"><span data-stu-id="df97d-164">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="df97d-165">В этом примере в объект RoverExplorer будет добавлена ограничивающая рамка, чтобы можно было легко использовать все возможности для перемещения, вращения и масштабирования деталей.</span><span class="sxs-lookup"><span data-stu-id="df97d-165">In this example, you will add a bounding box to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="df97d-166">Кроме того, вы настроите параметры меню, чтобы можно было включить и отключить ограничивающую рамку.</span><span class="sxs-lookup"><span data-stu-id="df97d-166">Additionally, you will configure the Menu so you can turn the Bounding Box on and off.</span></span>

<span data-ttu-id="df97d-167">В окне Hierarchy (Иерархия) выберите объект **RoverExplorer**, а затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="df97d-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="df97d-168">компонент **BoundingBox**;</span><span class="sxs-lookup"><span data-stu-id="df97d-168">**BoundingBox** component</span></span>
* <span data-ttu-id="df97d-169">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт).</span><span class="sxs-lookup"><span data-stu-id="df97d-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="df97d-170">Затем **снимите флажок** рядом с компонентами, чтобы **отключить** их по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="df97d-170">Then **uncheck** the checkbox next to both components to make them **disabled** by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="df97d-172">Визуализация ограничивающей рамки создается во время выполнения. Поэтому вы не увидите ее до входа в игровой режим.</span><span class="sxs-lookup"><span data-stu-id="df97d-172">The Bounding Box visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="df97d-173">Компонент BoundingBox будет автоматически добавлять компонент NearInteractionGrabbable во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="df97d-173">The BoundingBox component will automatically add the NearInteractionGrabbable component at runtime.</span></span> <span data-ttu-id="df97d-174">Поэтому не нужно добавлять этот компонент для захвата вложенных объектов с помощью отслеживаемых рук.</span><span class="sxs-lookup"><span data-stu-id="df97d-174">Therefore, we do not need to add this component to grab the enclosed objects with tracked hands.</span></span>

<span data-ttu-id="df97d-175">В окне Hierarchy (Иерархия) разверните в меню объект **ButtonCollection**, чтобы отобразить четыре кнопки и переименовать третью кнопку на **BoundingBox_Enable**. Затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Помощник настройки кнопки — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="df97d-175">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundingBox_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="df97d-176">Установите для параметра **Main Label Text** (Текст основной метки) значение **Enable** (Включить).</span><span class="sxs-lookup"><span data-stu-id="df97d-176">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="df97d-177">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="df97d-177">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="df97d-178">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **BoundingBox** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="df97d-178">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="df97d-179">Убедитесь, что флажок аргумента **установлен**.</span><span class="sxs-lookup"><span data-stu-id="df97d-179">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="df97d-180">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="df97d-180">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="df97d-181">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="df97d-181">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="df97d-182">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ObjectManipulator** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="df97d-182">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="df97d-183">Убедитесь, что флажок аргумента **установлен**.</span><span class="sxs-lookup"><span data-stu-id="df97d-183">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="df97d-184">Оставьте **значок** куба с ограничивающей рамкой.</span><span class="sxs-lookup"><span data-stu-id="df97d-184">Leave the **Icon** as the 'cube with bounding box' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="df97d-186">Переименуйте четвертую и последнюю кнопку на **BoundingBox_Disable**, затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Помощник настройки кнопки — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="df97d-186">Rename the forth and last button to **BoundingBox_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="df97d-187">Установите для параметра **Main Label Text** (Текст основной метки) значение **Disable** (Отключить).</span><span class="sxs-lookup"><span data-stu-id="df97d-187">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="df97d-188">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="df97d-188">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="df97d-189">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **BoundingBox** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="df97d-189">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="df97d-190">Убедитесь, что флажок аргумента **снят**.</span><span class="sxs-lookup"><span data-stu-id="df97d-190">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="df97d-191">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="df97d-191">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="df97d-192">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="df97d-192">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="df97d-193">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ObjectManipulator** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="df97d-193">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="df97d-194">Убедитесь, что флажок аргумента **снят**.</span><span class="sxs-lookup"><span data-stu-id="df97d-194">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="df97d-195">Измените **значок** на значок куба с ограничивающей рамкой.</span><span class="sxs-lookup"><span data-stu-id="df97d-195">Change the **Icon** to the 'cube with bounding box" icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="df97d-197">Теперь, войдя в игровой режим и включив ограничивающую рамку, нажав кнопку Enable (Включить), вы можете использовать режим ближнего или дальнего взаимодействия для перемещения, вращения и масштабирования ограничивающей рамки. Чтобы повторно отключить ограничивающую рамку, нажмите кнопку Disable (Отключить):</span><span class="sxs-lookup"><span data-stu-id="df97d-197">If you now enter Game mode and enable the Bounding Box by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounding Box, and use the Disable button to disable the Bounding Box again:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="df97d-199">Дополнительные сведения о компоненте Bounding Box (Ограничивающая рамка) и его свойствах вы можете получить в [этом руководстве](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="df97d-199">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="df97d-200">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="df97d-200">Congratulations</span></span>

<span data-ttu-id="df97d-201">В этом учебнике вы узнали, как включить манипулирование дальними и ближними трехмерными объектами и ограничить допустимые типы манипуляций.</span><span class="sxs-lookup"><span data-stu-id="df97d-201">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="df97d-202">Вы также узнали, как добавлять ограничивающие рамки вокруг трехмерных объектов, чтобы упростить управление манипулированием объектов.</span><span class="sxs-lookup"><span data-stu-id="df97d-202">You also learned how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

[<span data-ttu-id="df97d-203">Следующее руководство: 8. Использование отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="df97d-203">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
