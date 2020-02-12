---
title: Учебники по началу работы — 7. Создание примера приложения Лунный модуль
description: На этом занятии вы объедините несколько концепций, полученных в предыдущих занятиях, для создания уникального примера.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b5b1bd0115822449bd6098f78cfc94d909169737
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129454"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="e1c17-105">7. Создание примера приложения с лунным модулем</span><span class="sxs-lookup"><span data-stu-id="e1c17-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="e1c17-106">В этом руководстве несколько концепций объединяются из предыдущих уроков для создания уникального примера.</span><span class="sxs-lookup"><span data-stu-id="e1c17-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="e1c17-107">Вы узнаете, как создать приложение сборки части, которое позволит пользователю использовать отслеживание руки, чтобы выбрать части и попытаться собрать Лунный модуль.</span><span class="sxs-lookup"><span data-stu-id="e1c17-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="e1c17-108">Вы будете использовать нажатые кнопки для включения и отключения подсказок размещения, для сброса интерфейса и запуска лунного модуля в место!</span><span class="sxs-lookup"><span data-stu-id="e1c17-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="e1c17-109">В следующих учебных курсах вы продолжите создавать эти возможности, в том числе эффективные варианты использования в нескольких пользователях, использующие пространственные привязки Azure для пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="e1c17-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="e1c17-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="e1c17-110">Objectives</span></span>

* <span data-ttu-id="e1c17-111">Объединить несколько концепций из предыдущих уроков, чтобы выполнить уникальный сценарий.</span><span class="sxs-lookup"><span data-stu-id="e1c17-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="e1c17-112">Узнать, как переключать объекты.</span><span class="sxs-lookup"><span data-stu-id="e1c17-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="e1c17-113">Запустить сложные события с помощью нажимаемых кнопок.</span><span class="sxs-lookup"><span data-stu-id="e1c17-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="e1c17-114">Использовать силы и физику твердых тел.</span><span class="sxs-lookup"><span data-stu-id="e1c17-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="e1c17-115">Изучить использование всплывающих подсказок.</span><span class="sxs-lookup"><span data-stu-id="e1c17-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="e1c17-116">Обзор компонентов лунного модуля</span><span class="sxs-lookup"><span data-stu-id="e1c17-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="e1c17-117">В этом разделе вы создадите простую задачу сборки, в которой цель пользователя состоит в размещении пяти частей, распределенных по таблице в правильном расположении в лунном модуле.</span><span class="sxs-lookup"><span data-stu-id="e1c17-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="e1c17-118">Ниже приведены основные действия, которые необходимо выполнить для достижения этого результата.</span><span class="sxs-lookup"><span data-stu-id="e1c17-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="e1c17-119">Добавление средства запуска Rocket prefab в сцену</span><span class="sxs-lookup"><span data-stu-id="e1c17-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="e1c17-120">Включить управление объектами для всех частей</span><span class="sxs-lookup"><span data-stu-id="e1c17-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="e1c17-121">Добавление и настройка компонента демонстрации сборки части (скрипта)</span><span class="sxs-lookup"><span data-stu-id="e1c17-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="e1c17-122">Демонстрационный компонент сборки части (скрипт) не является частью МРТК.</span><span class="sxs-lookup"><span data-stu-id="e1c17-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="e1c17-123">Он был предоставлен с ресурсами этого учебника.</span><span class="sxs-lookup"><span data-stu-id="e1c17-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="e1c17-124">1. Добавьте средство запуска Rocket prefab в сцену.</span><span class="sxs-lookup"><span data-stu-id="e1c17-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="e1c17-125">В окне проекта перейдите к **ресурсам** > **мртк. Учебник. GettingStarted** > **Prefabs** > **Роккетлаунчер** папка, перетащите **роккетлаунчер** prefab в окно иерархии, чтобы добавить его в сцену, а затем поместите его в подходящее расположение, например:</span><span class="sxs-lookup"><span data-stu-id="e1c17-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="e1c17-126">Координата Transform X = 1,5, Y =-0,4, Z = 0, поэтому она располагается справа от пользователя на уши высоте.</span><span class="sxs-lookup"><span data-stu-id="e1c17-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="e1c17-127">Поворот преобразования X = 0, Y = 180, Z = 0, поэтому основные возможности интерфейса пользователя</span><span class="sxs-lookup"><span data-stu-id="e1c17-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="e1c17-129">2. Включение управления объектами для всех частей</span><span class="sxs-lookup"><span data-stu-id="e1c17-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="e1c17-130">В окне Иерархия найдите объект Роккетлаунчер > **лунармодулепартс** и выберите все **дочерние объекты**, добавьте компонент **обработчика манипуляции (скрипт)** и компонент, который можно получить **с помощью диалогового окна близкого взаимодействия (** скрипт), а затем настройте обработчик манипуляции (script) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e1c17-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="e1c17-131">Изменить **тип двух типов манипуляции** на перемещение вращения, поэтому масштабирование отключено</span><span class="sxs-lookup"><span data-stu-id="e1c17-131">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="e1c17-132">Снимите флажок " **Разрешить FAR манипуляции** ", чтобы разрешить только близкое взаимодействие</span><span class="sxs-lookup"><span data-stu-id="e1c17-132">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="e1c17-134">Для напоминания с пошаговыми инструкциями о том, как реализовать манипуляции с объектами, можно обратиться к инструкциям по [манипуляции с трехмерными объектами](mrlearning-base-ch4.md#manipulating-3d-objects) .</span><span class="sxs-lookup"><span data-stu-id="e1c17-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="e1c17-135">3. Добавление и настройка компонента демонстрации сборки части (скрипта)</span><span class="sxs-lookup"><span data-stu-id="e1c17-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="e1c17-136">Если все еще выбраны дочерние объекты Лунармодулепартс, добавьте компонент « **аудио-источник** », а затем настройте его следующим образом.</span><span class="sxs-lookup"><span data-stu-id="e1c17-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="e1c17-137">Назначьте подходящий звуковой клип полю **аудиоклип** , например MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="e1c17-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="e1c17-138">Снимите флажок " **воспроизвести при спящем** режиме", чтобы звуковой клип не воспроизводился автоматически при загрузке сцены.</span><span class="sxs-lookup"><span data-stu-id="e1c17-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="e1c17-139">Измените **пространственный переход** на 1, чтобы включить Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="e1c17-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="e1c17-141">После выбора всех дочерних объектов Лунармодулепартс добавьте **демонстрационный компонент сборки части (скрипт)** :</span><span class="sxs-lookup"><span data-stu-id="e1c17-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="e1c17-143">В окне Иерархия выберите объект **роверенклосуре** и настройте его **демонстрационный компонент сборки (script)** , как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="e1c17-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="e1c17-144">В **объект для размещения** поля, назначьте сам объект (в данном случае это объект **роверенклосуре** ).</span><span class="sxs-lookup"><span data-stu-id="e1c17-144">To the **Object To Place** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>
* <span data-ttu-id="e1c17-145">В поле **расположение для размещения** назначьте соответствующий объект плацеменсинтс, в данном случае — объект **RoverEnclosure_PlacementHints**</span><span class="sxs-lookup"><span data-stu-id="e1c17-145">To the **Location To Place** field, assign the corresponding PlacementHints object, in this case, the **RoverEnclosure_PlacementHints** object</span></span>
* <span data-ttu-id="e1c17-146">В поле " **объект подсказки** " назначьте соответствующий тултипобжект (в данном случае это объект **RoverEnclosure_ToolTip**</span><span class="sxs-lookup"><span data-stu-id="e1c17-146">To the **Tool Tip Object** field, assign the corresponding ToolTipObject, in this case, the **RoverEnclosure_ToolTip** object</span></span>
* <span data-ttu-id="e1c17-147">В поле **источник звука** назначьте сам объект (в данном случае — объект **роверенклосуре** ).</span><span class="sxs-lookup"><span data-stu-id="e1c17-147">To the **Audio Source** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="e1c17-149">**Повторите эти действия** для всех других дочерних объектов лунармодулепартс, например Фуелтанк, Енергицелл, Доккингпортал и екстерналсенсор.</span><span class="sxs-lookup"><span data-stu-id="e1c17-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="e1c17-150">Если вы перейдете в режим игры и переместит "объект для размещения", укажите "расположение для размещения", вы увидите следующее:</span><span class="sxs-lookup"><span data-stu-id="e1c17-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="e1c17-151">Объект будет привязан к месту размещения и быть родительским по отношению к объекту Лунармодуле, чтобы он стал частью лунного модуля.</span><span class="sxs-lookup"><span data-stu-id="e1c17-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="e1c17-152">Источник звука для объекта будет воспроизводить назначенный звуковой клип в месте расположения объекта</span><span class="sxs-lookup"><span data-stu-id="e1c17-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="e1c17-153">Соответствующий объект подсказки по инструменту будет скрыт</span><span class="sxs-lookup"><span data-stu-id="e1c17-153">The corresponding Tool Tip object will be hidden</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="e1c17-155">Напоминание о том, как использовать модель входных данных в редакторе, можно найти в разделе [Использование имитации входных данных в редакторе, чтобы протестировать руководство по монтажному кадру](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) на [портале документации мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e1c17-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="e1c17-156">Настройка лунного модуля</span><span class="sxs-lookup"><span data-stu-id="e1c17-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="e1c17-157">В этом разделе вы добавите в приложение Rocket Launcher дополнительные компоненты, чтобы пользователь мог выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="e1c17-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="e1c17-158">Взаимодействие с лунным модулем</span><span class="sxs-lookup"><span data-stu-id="e1c17-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="e1c17-159">Запуск лунного модуля в пространстве и воспроизведение звука при его запуске</span><span class="sxs-lookup"><span data-stu-id="e1c17-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="e1c17-160">Сбросьте приложение таким образом, чтобы Лунный модуль и вся часть были возвращены обратно в исходное расположение.</span><span class="sxs-lookup"><span data-stu-id="e1c17-160">Reset the application so the Lunar Module and all the part are placed back to their original position</span></span>
* <span data-ttu-id="e1c17-161">Скройте подсказки о размещении, чтобы сделать сборку части сложной.</span><span class="sxs-lookup"><span data-stu-id="e1c17-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="e1c17-162">Ниже приведены основные действия, которые необходимо выполнить для достижения этого результата.</span><span class="sxs-lookup"><span data-stu-id="e1c17-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="e1c17-163">Включить управление объектами</span><span class="sxs-lookup"><span data-stu-id="e1c17-163">Enable object manipulation</span></span>
2. <span data-ttu-id="e1c17-164">Включить физику</span><span class="sxs-lookup"><span data-stu-id="e1c17-164">Enable physics</span></span>
3. <span data-ttu-id="e1c17-165">Добавление компонента "источник звука"</span><span class="sxs-lookup"><span data-stu-id="e1c17-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="e1c17-166">Добавление и настройка компонента "запустить Лунный модуль" (скрипт)</span><span class="sxs-lookup"><span data-stu-id="e1c17-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="e1c17-167">Добавление и настройка компонента включения и настройки подсказок размещения (script)</span><span class="sxs-lookup"><span data-stu-id="e1c17-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="e1c17-168">Компонент «Launch Лунный модуль» (script) и компонент переключения размещения (script) не являются частью МРТК.</span><span class="sxs-lookup"><span data-stu-id="e1c17-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="e1c17-169">Они были предоставлены в активы этого учебника.</span><span class="sxs-lookup"><span data-stu-id="e1c17-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="e1c17-170">1. Включение управления объектами</span><span class="sxs-lookup"><span data-stu-id="e1c17-170">1. Enable object manipulation</span></span>

<span data-ttu-id="e1c17-171">В окне Иерархия выберите объект Роккетлаунчер > **лунармодуле** , добавьте компонент **обработчика манипуляций (скрипт)** и компонент, который можно переустановить **(** скрипт), а затем настройте обработчик манипуляции (script) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e1c17-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="e1c17-172">Изменить **тип двух типов манипуляции** на перемещение вращения, поэтому масштабирование отключено</span><span class="sxs-lookup"><span data-stu-id="e1c17-172">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="e1c17-173">Снимите флажок " **Разрешить FAR манипуляции** ", чтобы разрешить только близкое взаимодействие</span><span class="sxs-lookup"><span data-stu-id="e1c17-173">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="e1c17-175">2. Включение физикы</span><span class="sxs-lookup"><span data-stu-id="e1c17-175">2. Enable physics</span></span>

<span data-ttu-id="e1c17-176">Выбрав объект Роккетлаунчер > **лунармодуле** , добавьте компонент RigidBody, а затем настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e1c17-176">With the RocketLauncher > **LunarModule** object still selected, add a Rigidbody component and then configure it as follows:</span></span>

* <span data-ttu-id="e1c17-177">Снимите флажок использовать параметр " **сила притяжения** ", чтобы на лунном модуле не влияла сила притяжения.</span><span class="sxs-lookup"><span data-stu-id="e1c17-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="e1c17-178">Установите флажок **не** превышено, чтобы на лунном модуле не влияли принудительные фисик</span><span class="sxs-lookup"><span data-stu-id="e1c17-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="e1c17-180">3. Добавление компонента "источник звука"</span><span class="sxs-lookup"><span data-stu-id="e1c17-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="e1c17-181">Выбрав объект Роккетлаунчер > **лунармодуле** , добавьте компонент " **источник звука** ", а затем настройте его следующим образом.</span><span class="sxs-lookup"><span data-stu-id="e1c17-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="e1c17-182">Измените **пространственный переход** на 1, чтобы включить Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="e1c17-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="e1c17-184">4. Добавление и настройка компонента "запустить Лунный модуль" (скрипт)</span><span class="sxs-lookup"><span data-stu-id="e1c17-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="e1c17-185">Выбрав объект Роккетлаунчер > **лунармодуле** , добавьте компонент **Launch Лунный модуль (script)** , а затем настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e1c17-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="e1c17-186">Измените значение **креативность** , чтобы при запуске Лунный модуль был корректно запущен, например, в 0,01</span><span class="sxs-lookup"><span data-stu-id="e1c17-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="e1c17-188">5. Добавление и настройка компонента включения и настройки подсказок размещения (script)</span><span class="sxs-lookup"><span data-stu-id="e1c17-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="e1c17-189">Выбрав объект Роккетлаунчер > **лунармодуле** , добавьте компонент **Переключить подсказки (Scripting Placement)** и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e1c17-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="e1c17-190">Задайте для свойства **Размер** массива игрового объекта значение 5.</span><span class="sxs-lookup"><span data-stu-id="e1c17-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="e1c17-191">Назначьте каждый из **дочерних объектов** объекта **плацеменсинтс** полю **element** в массиве объектов Game:</span><span class="sxs-lookup"><span data-stu-id="e1c17-191">Assign each of the **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="e1c17-193">Настройка кнопки запуска</span><span class="sxs-lookup"><span data-stu-id="e1c17-193">Configuring the Launch button</span></span>

<span data-ttu-id="e1c17-194">В окне Иерархия выберите кнопки Роккетлаунчер > > объект **лаунчбуттон** , затем в компоненте, **поддерживающем нажатие кнопки (скрипт)** , создайте новое событие **нажатия кнопки ()** , настройте объект **лунармодуле** для получения события и определите **лаунчлунармодуле. стартсрустер** в качестве действия для запуска:</span><span class="sxs-lookup"><span data-stu-id="e1c17-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="e1c17-196">Напоминание о том, как реализовать события, можно найти в разделе [жесты отслеживания руки и инструкции по взаимодействию с управляемыми кнопками](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .</span><span class="sxs-lookup"><span data-stu-id="e1c17-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="e1c17-197">Выполнив кнопки Роккетлаунчер > > объект **лаунчбуттон** , на элементе, **поддерживающем нажатие кнопки (скрипт)** , создайте новое событие **нажатия кнопки ()** , настройте объект **лунармодуле** для получения события, определите **аудиосаурце. плайонешот** в качестве действия для запуска и назначьте подходящее звуковое поле **аудиоклипу** , например MRTK_Gem аудиоклип:</span><span class="sxs-lookup"><span data-stu-id="e1c17-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="e1c17-199">Выполнив кнопки Роккетлаунчер > > объект **лаунчбуттон** , на элементе, **поддерживающем нажатие кнопки (скрипт)** , создайте новое событие **касания ()** , настройте объект **лунармодуле** для получения события и определите **лаунчлунармодуле. стопсрустер** в качестве действия для запуска:</span><span class="sxs-lookup"><span data-stu-id="e1c17-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch Ended ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="e1c17-201">Если вы перейдете в режим игры и нажмете кнопку Launch (запустить), начнется воспроизведение аудиоклипа, и если нажать кнопку запустить в течение секунды или более, вы увидите, что Лунный модуль откроется в пространстве:</span><span class="sxs-lookup"><span data-stu-id="e1c17-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="e1c17-203">Настройка кнопки сброса</span><span class="sxs-lookup"><span data-stu-id="e1c17-203">Configuring the Reset button</span></span>

<span data-ttu-id="e1c17-204">В окне Иерархия выберите кнопки Роккетлаунчер > > объект **ресетбуттон** , затем в компоненте, **поддерживающем нажатие кнопки (скрипт)** , создайте новое событие **нажатия кнопки ()** , настройте объект **лунармодуле** для получения события и определите **лаунчлунармодуле. ресетмодуле** в качестве действия для запуска:</span><span class="sxs-lookup"><span data-stu-id="e1c17-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="e1c17-206">Выполнив кнопки Роккетлаунчер > > объект **ресетбуттон** , на элементе, **поддерживающем нажатие кнопки (скрипт)** , создайте новое событие **нажатия кнопки ()** , настройте объект **роккетлаунчер** для получения события, определите **GameObject. броадкастмессаже** как действие для запуска и введите **ресетплацемент** в поле сообщения:</span><span class="sxs-lookup"><span data-stu-id="e1c17-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="e1c17-208">Действие GameObject. Броадкастмессаже отправляет сообщение Ресетплацемент из объекта Роккетлаунчер во все его дочерние объекты.</span><span class="sxs-lookup"><span data-stu-id="e1c17-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="e1c17-209">Любой дочерний объект, имеющий функцию Ресетплацемент, которая определена в демонстрационном компоненте (скрипте), который был добавлен во все дочерние объекты Лунармодулепартс, вызовет функцию Ресетплацемент, которая сбрасывает размещение дочернего объекта.</span><span class="sxs-lookup"><span data-stu-id="e1c17-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="e1c17-210">Если теперь вы перейдете в режим игры и нажмете кнопку Reset (Сброс), вы услышите воспроизводимый звуковой клип и увидите, как запустился Лунный модуль:</span><span class="sxs-lookup"><span data-stu-id="e1c17-210">If you now enter Game mode and press the Reset button you will hear the audio clip being played and see the Lunar Module being launched into space:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="e1c17-212">Настройка кнопки подсказок размещения</span><span class="sxs-lookup"><span data-stu-id="e1c17-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="e1c17-213">В окне Иерархия выберите кнопки Роккетлаунчер > > объект **хинтсбуттон** , затем в компоненте, **поддерживающем нажатие кнопки (скрипт)** , создайте новое событие **нажатия кнопки ()** , настройте объект **лунармодуле** для получения события и определите **тогглеплацеменсинтс. тогглегамеобжектс** действие, которое необходимо запустить:</span><span class="sxs-lookup"><span data-stu-id="e1c17-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** the action to be triggered:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="e1c17-215">Если теперь вы вводите режим игры, вы заметите, что непрозрачные подсказки размещения отключены по умолчанию, но их можно включить и отключить, нажав кнопку указания.</span><span class="sxs-lookup"><span data-stu-id="e1c17-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![мрлеарнинг — базовый](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="e1c17-217">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="e1c17-217">Congratulations</span></span>

<span data-ttu-id="e1c17-218">Вы полностью настроили это приложение.</span><span class="sxs-lookup"><span data-stu-id="e1c17-218">You have fully configured this application.</span></span> <span data-ttu-id="e1c17-219">Теперь приложение позволяет пользователям полностью собирать Лунный модуль, запускать Лунный модуль, переключать подсказки и сбрасывать приложение для повторного запуска.</span><span class="sxs-lookup"><span data-stu-id="e1c17-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
