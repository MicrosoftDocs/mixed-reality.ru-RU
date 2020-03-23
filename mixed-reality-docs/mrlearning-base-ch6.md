---
title: Серия руководств по началу работы, часть 7 Создание примера приложения лунного модуля
description: В этом уроке мы объединим несколько концепций, которые узнали из предыдущих уроков, чтобы создать уникальный пример взаимодействия.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031567"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="6f9b5-105">7. Создание примера приложения лунного модуля</span><span class="sxs-lookup"><span data-stu-id="6f9b5-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="6f9b5-106">В этом руководстве несколько концепций, которые вы узнали из предыдущих уроков, объединяются в уникальный пример взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="6f9b5-107">Вы узнаете, как создать приложение для сборки деталей, в котором пользователю потребуется использовать отслеживание рук, чтобы поднять части лунного модуля и попытаться его собрать.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="6f9b5-108">Вы примените нажимаемые кнопки для включения подсказок по размещению, сброса выполненных действий и запуска лунного модуля в космос.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="6f9b5-109">В последующих руководствах мы продолжим развивать этот пример, добавляя мощные многопользовательские сценарии применения, использующие Пространственные привязки Azure для пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="6f9b5-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="6f9b5-110">Objectives</span></span>

* <span data-ttu-id="6f9b5-111">Объединить несколько концепций из предыдущих уроков, чтобы выполнить уникальный сценарий.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="6f9b5-112">Узнать, как переключать объекты.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="6f9b5-113">Запустить сложные события с помощью нажимаемых кнопок.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="6f9b5-114">Использовать силы и физику твердых тел.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="6f9b5-115">Изучить использование всплывающих подсказок.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="6f9b5-116">Общие сведения о сборке лунного модуля</span><span class="sxs-lookup"><span data-stu-id="6f9b5-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="6f9b5-117">В этом разделе объясняется, как создать простую задачу сборки деталей, в которой пользователю предстоит правильно разместить пять деталей лунного модуля, разложенных на столе.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="6f9b5-118">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="6f9b5-119">Добавление в сцену заготовки Rocket Launcher.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="6f9b5-120">Включение манипулирования объектом для всех деталей.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="6f9b5-121">Добавление и настройка компонента "Part Assembly Demo (Script)" (Демонстрация сборки деталей — скрипт).</span><span class="sxs-lookup"><span data-stu-id="6f9b5-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="6f9b5-122">Компонент "Part Assembly Demo (Script)" (Демонстрация сборки деталей — скрипт) не входит в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="6f9b5-123">Он был предоставлен с активами для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="6f9b5-124">1. Добавление в сцену заготовки Rocket Launcher</span><span class="sxs-lookup"><span data-stu-id="6f9b5-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="6f9b5-125">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, перетащите заготовку **RocketLauncher** в окно Hierarchy (Иерархия), чтобы добавить ее в сцену, и поместите ее в приемлемое положение, например так:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="6f9b5-126">для параметра преобразования Position (Положение) укажите значения X = 1.5, Y = -0,4, Z = 0, чтобы деталь размещалась справа от пользователя на уровне груди;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="6f9b5-127">для параметра преобразования Rotation (Поворот) укажите значения X = 0, Y = 180, Z = 0, чтобы основные элементы объекта были направлены в сторону пользователя.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="6f9b5-129">2. Включение манипулирования объектом для всех деталей</span><span class="sxs-lookup"><span data-stu-id="6f9b5-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="6f9b5-130">В окне Hierarchy (Иерархия) найдите объект RocketLauncher > **LunarModuleParts** и выберите все его **дочерние объекты**, затем добавьте компоненты **Manipulation Handler (Script)** (Обработчик манипулирования — скрипт) и **Near Interaction Grabbable (Script)** (Возможность захвата при близком взаимодействии — скрипт) и настройте Manipulation Handler (Script) (Обработчик манипулирования — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="6f9b5-131">снимите флажок **Allow Far Manipulation** (Разрешить дальнее манипулирование), чтобы поддерживать только ближнее взаимодействие;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="6f9b5-132">для параметра **Two Handed Manipulation Type** (Тип манипуляции двумя руками) укажите значение **Move Rotate** (Перемещение и вращение), чтобы отключить масштабирование.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="6f9b5-134">В разделе [Работа с трехмерными объектами](mrlearning-base-ch4.md#manipulating-3d-objects) вы можете освежить свои знания о реализации манипулирования объектами и получить пошаговые инструкции.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="6f9b5-135">3. Добавление и настройка компонента "Part Assembly Demo (Script)" (Демонстрация сборки деталей — скрипт)</span><span class="sxs-lookup"><span data-stu-id="6f9b5-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="6f9b5-136">Выделив все дочерние объекты объекта LunarModuleParts, добавьте компонент **Audio Source** (Источник звука) и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="6f9b5-137">укажите подходящий аудиоклип в поле **AudioClip**, например MRKT_Scale_Start;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="6f9b5-138">снимите флажок **Play On Awake** (Воспроизвести при загрузке), чтобы аудиоклип не включался автоматически при загрузке сцены;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="6f9b5-139">для параметра **Spatial Blend** (Пространственное наложение) укажите значение 1, чтобы включить пространственный звук.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="6f9b5-141">Выделив все дочерние объекты объекта LunarModuleParts, добавьте компонент **Part Assembly Demo (Script)** (Демонстрация сборки деталей — скрипт):</span><span class="sxs-lookup"><span data-stu-id="6f9b5-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="6f9b5-143">В окне Hierarchy (Иерархия) выберите объект **RoverEnclosure** и настройте его компонент **Part Assembly Demo (Script)** (Демонстрация сборки деталей — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="6f9b5-144">в поле **Object To Place** (Объект для размещения) укажите **сам объект**, в нашем примере это RoverEnclosure;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="6f9b5-145">в поле **Location To Place** (Расположение для размещения) сохраните соответствующий объект **PlacementHint**, в нашем примере это RoverEnclosure_PlacementHint;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="6f9b5-146">в поле **Tool Tip Object** (Всплывающая подсказка) сохраните соответствующий объект **ToolTip**, в нашем примере это RoverEnclosure_ToolTip;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="6f9b5-147">в поле **Audio Source** (Источник звука) укажите **сам объект**, в нашем примере это RoverEnclosure.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="6f9b5-149">**Повторите** этот процесс для всех дочерних объектов объекта LunarModuleParts: FuelTank, EnergyCell, DockingPortal и ExternalSensor.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="6f9b5-150">Теперь если вы перейдете в игровой режим и переместите объект для размещения в расположение для размещения, произойдет следующее:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="6f9b5-151">Объект встанет на нужное место и станет дочерним объектом для LunarModule, то есть станет частью лунного модуля.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="6f9b5-152">Компонент Audio Source этого объекта воспроизведет назначенный ему аудиоклип в том расположении, где сейчас находится этот объект.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="6f9b5-153">Скроется соответствующая подсказка.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="6f9b5-155">Чтобы вспомнить, как использовать встроенный имитатор ввода, воспользуйтесь руководством [по использованию имитации ввода с помощью рук в редакторе для тестирования сцены](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene), размещенным на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="6f9b5-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="6f9b5-156">Настройка лунного модуля</span><span class="sxs-lookup"><span data-stu-id="6f9b5-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="6f9b5-157">В этом разделе описывается, как добавить новые возможности в приложение Rocket Launcher, благодаря которым пользователь сможет выполнять следующие действия:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="6f9b5-158">взаимодействие с лунным модулем;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="6f9b5-159">запуск лунного модуля в космос со звуковым сопровождением;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="6f9b5-160">сброс состояния приложения, чтобы вернуть лунный модуль и все его детали на исходные места;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="6f9b5-161">отключение подсказок по размещению, чтобы усложнить задачу сборки деталей.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="6f9b5-162">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="6f9b5-163">Включение манипулирования объектами.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-163">Enable object manipulation</span></span>
2. <span data-ttu-id="6f9b5-164">Включение физических законов.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-164">Enable physics</span></span>
3. <span data-ttu-id="6f9b5-165">Добавление компонента источника звука.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="6f9b5-166">Добавление и настройка компонента "Launch Lunar Module (Script)" (Запуск лунного модуля — скрипт).</span><span class="sxs-lookup"><span data-stu-id="6f9b5-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="6f9b5-167">Добавление и настройка компонента "Toggle Placement Hints (Script)" (Переключение подсказок по размещению — скрипт).</span><span class="sxs-lookup"><span data-stu-id="6f9b5-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="6f9b5-168">Компоненты Launch Lunar Module (Script) (Запуск лунного модуля — скрипт) и Toggle Placement Hints (Script) (Переключение подсказок по размещению — скрипт) не входят в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="6f9b5-169">Он был предоставлен с активами для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="6f9b5-170">1. Включение манипулирования объектами</span><span class="sxs-lookup"><span data-stu-id="6f9b5-170">1. Enable object manipulation</span></span>

<span data-ttu-id="6f9b5-171">В окне Hierarchy (Иерархия) выберите объект RocketLauncher > **LunarModule** и добавьте компоненты **Manipulation Handler (Script)** (Обработчик манипулирования — скрипт) и **Near Interaction Grabbable (Script)** (Возможность захвата при близком взаимодействии — скрипт), а затем настройте Manipulation Handler (Script) (Обработчик манипулирования — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="6f9b5-172">снимите флажок **Allow Far Manipulation** (Разрешить дальнее манипулирование), чтобы поддерживать только ближнее взаимодействие;</span><span class="sxs-lookup"><span data-stu-id="6f9b5-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="6f9b5-173">для параметра **Two Handed Manipulation Type** (Тип манипуляции двумя руками) укажите значение "Move Rotate" (Перемещение и вращение), чтобы отключить масштабирование.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="6f9b5-175">2. Включение физических законов</span><span class="sxs-lookup"><span data-stu-id="6f9b5-175">2. Enable physics</span></span>

<span data-ttu-id="6f9b5-176">Выделив объект RocketLauncher > **LunarModule**, добавьте компонент **RigidBody** и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="6f9b5-177">Снимите флажок **Use Gravity** (Использовать гравитацию), чтобы этот объект не подвергался земному притяжению.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="6f9b5-178">Установите флажок **Is Kinematic** (Кинематические свойства), чтобы этот объект изначально не подвергался влиянию физических законов.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="6f9b5-180">3. Добавление компонента источника звука</span><span class="sxs-lookup"><span data-stu-id="6f9b5-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="6f9b5-181">Сохраняя выделение объекта RocketLauncher > **LunarModule**, добавьте компонент **Audio Source** (Источник звука) и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="6f9b5-182">Для параметра **Spatial Blend** (Пространственное наложение) укажите значение 1, чтобы включить пространственный звук.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="6f9b5-184">4. Добавление и настройка компонента "Launch Lunar Module (Script)" (Запуск лунного модуля — скрипт)</span><span class="sxs-lookup"><span data-stu-id="6f9b5-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="6f9b5-185">Сохраняя выделение объекта RocketLauncher > **LunarModule**, добавьте компонент **Launch Lunar Module (Script)** (Запуск лунного модуля — скрипт) и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="6f9b5-186">Измените значение **Thrust** (Тяга), чтобы лунный модуль при запуске взлетал изящно, например укажите 0,01.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="6f9b5-188">5. Добавление и настройка компонента "Toggle Placement Hints (Script)" (Переключение подсказок по размещению — скрипт)</span><span class="sxs-lookup"><span data-stu-id="6f9b5-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="6f9b5-189">Сохраняя выделение объекта RocketLauncher > **LunarModule**, добавьте компонент **Toggle Placement Hints (Script)** (Переключение подсказок по размещению — скрипт) и настройте его следующим образом.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="6f9b5-190">В массиве игровых объектов для свойства **Size** (Размер) укажите значение 5.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="6f9b5-191">Каждый из **дочерних объектов** объекта RocketLauncher > LunarModule > **PlacementHints** добавьте в поле **Element** (Элемент) в массиве игровых объектов:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="6f9b5-193">Настройка кнопки запуска</span><span class="sxs-lookup"><span data-stu-id="6f9b5-193">Configuring the Launch button</span></span>

<span data-ttu-id="6f9b5-194">В окне Hierarchy (Иерархия) выберите объект RocketLauncher > Buttons > **LaunchButton**, затем для компонента **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) создайте новое событие **Button Pressed ()** (Нажатие кнопки), настройте получение этого события в объекте **LunarModule** и определите **LaunchLunarModule.StartThruster** в качестве активируемого действия:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="6f9b5-196">В разделе об [обработке жестов и нажатий активных кнопок с помощью средства отслеживания руки](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) вы можете освежить свои знания о реализации событий.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="6f9b5-197">Сохраняя выделение объекта RocketLauncher > Buttons > **LaunchButton**, создайте в компоненте **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) новое событие **Button Pressed ()** (Нажатие кнопки), настройте получение этого события в объекте **LunarModule**, определите **AudioSource.PlayOneShot** в качестве действия для запуска и назначьте подходящий звуковой клип в поле **Audio Clip** (Аудиоклип), например MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="6f9b5-199">Сохраняя выделение объекта RocketLauncher > Buttons > **LaunchButton**, затем для компонента **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) создайте событие **Touch End ()** (Касание конца), настройте получение этого события в объекте **LunarModule** и определите **LaunchLunarModule.StopThruster** в качестве активируемого действия:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="6f9b5-201">Теперь, если вы войдете в игровой режим и нажмете кнопку запуска, будет запущен аудиоклип, а если вы будете удерживать эту кнопку примерно секунду или более, лунный модуль улетит в космос:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="6f9b5-203">Настройка кнопки сброса</span><span class="sxs-lookup"><span data-stu-id="6f9b5-203">Configuring the Reset button</span></span>

<span data-ttu-id="6f9b5-204">В окне Hierarchy (Иерархия) выберите объект RocketLauncher > Buttons > **ResetButton**, затем для компонента **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) создайте новое событие **Button Pressed ()** (Нажатие кнопки), настройте получение этого события в объекте **LunarModule** и определите **LaunchLunarModule.ResetModule** в качестве запускаемого действия:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="6f9b5-206">Сохраняя выделение объекта RocketLauncher > Buttons > **ResetButton**, создайте для компонента **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) новое событие **Button Pressed ()** (Нажатие кнопки), настройте получение этого события в объекте **RocketLauncher**, определите **GameObject.BroadcastMessage** в качестве запускаемого действия и укажите **ResetPlacement** в поле сообщения:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="6f9b5-208">Действие GameObject.BroadcastMessage отправляет сообщение ResetPlacement из объекта RocketLauncher всем его дочерним объектам.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="6f9b5-209">Все дочерние объекты, для которых определена функция ResetPlacement из компонента Part Assembly Demo (Script) (Демонстрация сборки деталей — скрипт), добавленного ранее во все дочерние объекты объекта LunarModuleParts, вызовут эту функцию ResetPlacement для сброса расположения соответствующего дочернего объекта.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="6f9b5-210">Теперь, если вы войдете в игровой режим, переместите некоторые детали и (или) запустите лунный модуль, а затем нажмете кнопку сброса, все детали и (или) сам лунный модуль будут возвращены на исходные места.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="6f9b5-212">Настройка кнопки подсказок расположения</span><span class="sxs-lookup"><span data-stu-id="6f9b5-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="6f9b5-213">В окне Hierarchy (Иерархия) выберите объект RocketLauncher > Buttons > **HintsButton**, затем для компонента **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) создайте новое событие **Button Pressed ()** (Нажатие кнопки), настройте получение этого события в объекте **LunarModule** и определите **TogglePlacementHints.ToggleGameObjects** в качестве запускаемого действия:</span><span class="sxs-lookup"><span data-stu-id="6f9b5-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="6f9b5-215">Теперь, если вы войдете в игровой режим, полупрозрачные подсказки расположения не будут отображаться по умолчанию, но вы сможете их включить нажатием соответствующей кнопки.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="6f9b5-217">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="6f9b5-217">Congratulations</span></span>

<span data-ttu-id="6f9b5-218">Вы полностью настроили это приложение.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-218">You have fully configured this application.</span></span> <span data-ttu-id="6f9b5-219">Теперь в этом приложении пользователи могут собрать лунный модуль из отдельных деталей, запустить его в космос, включить или выключить подсказки и сбросить состояние приложения для повторной игры.</span><span class="sxs-lookup"><span data-stu-id="6f9b5-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
