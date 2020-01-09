---
title: Учебники по началу работы — 7. Создание примера приложения Лунный модуль
description: На этом занятии вы объедините несколько концепций, полученных в предыдущих занятиях, для создания уникального примера.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 3127ffceea08202fe9d978ad77f8fddb6fba60a3
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334370"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="d2955-105">7. Создание примера приложения с лунным модулем</span><span class="sxs-lookup"><span data-stu-id="d2955-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="d2955-106">В этом руководстве несколько концепций объединяются из предыдущих уроков для создания уникального примера.</span><span class="sxs-lookup"><span data-stu-id="d2955-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="d2955-107">Вы узнаете, как создать приложение для работы с лунной микромодульной сборкой, в котором пользователь должен использовать отслеживание руки для получения подразделов лунного модуля и попытаться собрать Лунный модуль.</span><span class="sxs-lookup"><span data-stu-id="d2955-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="d2955-108">Мы используем нажатые кнопки, чтобы переключить подсказки о размещении, сбросить наш опыт и запустить наш Лунный модуль в место!</span><span class="sxs-lookup"><span data-stu-id="d2955-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="d2955-109">В следующих учебных курсах мы будем продолжать создавать эти возможности, в том числе эффективные варианты использования в нескольких пользователях, использующие пространственные привязки Azure для пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="d2955-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="d2955-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="d2955-110">Objectives</span></span>

- <span data-ttu-id="d2955-111">Объединить несколько концепций из предыдущих уроков, чтобы выполнить уникальный сценарий.</span><span class="sxs-lookup"><span data-stu-id="d2955-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="d2955-112">Узнать, как переключать объекты.</span><span class="sxs-lookup"><span data-stu-id="d2955-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="d2955-113">Запустить сложные события с помощью нажимаемых кнопок.</span><span class="sxs-lookup"><span data-stu-id="d2955-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="d2955-114">Использовать силы и физику твердых тел.</span><span class="sxs-lookup"><span data-stu-id="d2955-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="d2955-115">Изучить использование всплывающих подсказок.</span><span class="sxs-lookup"><span data-stu-id="d2955-115">Explore the use of tool tips</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="d2955-116">Настройка лунного модуля</span><span class="sxs-lookup"><span data-stu-id="d2955-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="d2955-117">В этом разделе представлены различные компоненты, необходимые для создания нашего примера работы.</span><span class="sxs-lookup"><span data-stu-id="d2955-117">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="d2955-118">Добавьте prefabную сборку модуля в базовую сцену.</span><span class="sxs-lookup"><span data-stu-id="d2955-118">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="d2955-119">Для этого на вкладке проект перейдите к Assets > Басемодулеассетс > Prefabs.</span><span class="sxs-lookup"><span data-stu-id="d2955-119">To do this, in the Project tab navigate to Assets > BaseModuleAssets > Prefabs.</span></span> <span data-ttu-id="d2955-120">Вы увидите два Prefabs средства запуска Rocket, перетащите Rocket Launcher_Tutorial prefab в сцену и выберите нужное расположение.</span><span class="sxs-lookup"><span data-stu-id="d2955-120">You will see two rocket launcher prefabs, drag the Rocket Launcher_Tutorial prefab into your scene, and position as you wish.</span></span>

    >[!NOTE]
    ><span data-ttu-id="d2955-121">Rocket Launcher_Complete prefab — это завершенное средство запуска, предоставленное для справки.</span><span class="sxs-lookup"><span data-stu-id="d2955-121">The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span>

    ![Изображение "Урок 6, раздел 1, шаг 1"](images/Lesson6_Chapter1_step1im.PNG)

    <span data-ttu-id="d2955-123">Если развернуть объект Rocket Launcher_Tutorial Game в иерархии, а затем расширить объект лунного модуля, вы найдете несколько дочерних объектов, имеющих материал «x-ray».</span><span class="sxs-lookup"><span data-stu-id="d2955-123">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="d2955-124">Материал x-Ray позволяет слегка полупрозрачным цветом, который будет использоваться в качестве подсказок размещения для пользователя.</span><span class="sxs-lookup"><span data-stu-id="d2955-124">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span>

    ![Lesson6 Chapter1 Нотеаим](images/Lesson6_Chapter1_noteaim.PNG)

    <span data-ttu-id="d2955-126">В лунном модуле есть пять частей, с которыми взаимодействует пользователь, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="d2955-126">There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

    1. <span data-ttu-id="d2955-127">Корпус лунохода.</span><span class="sxs-lookup"><span data-stu-id="d2955-127">The Rover Enclosure</span></span>
    2. <span data-ttu-id="d2955-128">Топливный бак.</span><span class="sxs-lookup"><span data-stu-id="d2955-128">The Fuel Tank</span></span>
    3. <span data-ttu-id="d2955-129">Топливная камера.</span><span class="sxs-lookup"><span data-stu-id="d2955-129">The Energy Cell</span></span>
    4. <span data-ttu-id="d2955-130">Стыковочный модуль.</span><span class="sxs-lookup"><span data-stu-id="d2955-130">The Docking Portal</span></span>
    5. <span data-ttu-id="d2955-131">Внешний датчик.</span><span class="sxs-lookup"><span data-stu-id="d2955-131">The External sensor</span></span>

    ![Изображение "Урок 6, раздел 1, примечание б"](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    ><span data-ttu-id="d2955-133">Названия игровых объектов, которые вы видите в иерархии базовой сцены, не соответствуют именам объектов в сцене.</span><span class="sxs-lookup"><span data-stu-id="d2955-133">The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

2. <span data-ttu-id="d2955-134">Добавьте источник звука в игровом объекте Лунармодуле.</span><span class="sxs-lookup"><span data-stu-id="d2955-134">Add an audio source to the LunarModule game object.</span></span> <span data-ttu-id="d2955-135">Убедитесь, что в иерархии сцены выбран параметр Лунармодуле, и нажмите кнопку Добавить компонент.</span><span class="sxs-lookup"><span data-stu-id="d2955-135">Make sure the LunarModule is selected in your scene hierarchy and click Add Component.</span></span> <span data-ttu-id="d2955-136">Найдите источник аудио и добавьте его в объект Game.</span><span class="sxs-lookup"><span data-stu-id="d2955-136">Search for Audio Source and add it to the game object.</span></span> <span data-ttu-id="d2955-137">Оставьте поле аудиоклип пустым, но измените особый параметр Blend с 0 на 1, чтобы включить Пространственный звук.</span><span class="sxs-lookup"><span data-stu-id="d2955-137">Leave the AudioClip field blank for now, but change the Special Blend setting from 0 to 1 so to enable spatial audio.</span></span> <span data-ttu-id="d2955-138">Этот источник звука будет использоваться для воспроизведения запуска звука позже.</span><span class="sxs-lookup"><span data-stu-id="d2955-138">You will use this audio source to play the launching sound later.</span></span>

    ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. <span data-ttu-id="d2955-140">Добавьте подсказку для переключения размещения сценария.</span><span class="sxs-lookup"><span data-stu-id="d2955-140">Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="d2955-141">Щелкните Добавить компонент и выполните поиск подсказок по размещению переключателей.</span><span class="sxs-lookup"><span data-stu-id="d2955-141">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="d2955-142">Это пользовательский сценарий, который позволяет включать и отключать полупрозрачные подсказки (объекты с материалом x-ray), как упоминалось ранее.</span><span class="sxs-lookup"><span data-stu-id="d2955-142">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>

    ![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. <span data-ttu-id="d2955-144">Поскольку у нас есть пять объектов, введите "5" для размера массива игрового объекта.</span><span class="sxs-lookup"><span data-stu-id="d2955-144">Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="d2955-145">Вы увидите пять новых элементов.</span><span class="sxs-lookup"><span data-stu-id="d2955-145">You will then see five new elements appear.</span></span>

    ![Изображение "Урок 6, раздел 1, шаг 4б"](images/Lesson6_Chapter1_step4bim.PNG)

    <span data-ttu-id="d2955-147">Перетащите все полупрозрачные объекты в поля имя (игровой объект).</span><span class="sxs-lookup"><span data-stu-id="d2955-147">Drag each of the translucent objects into all the Name (Game Object) boxes.</span></span> <span data-ttu-id="d2955-148">Перетащите следующие объекты из лунного модуля в сцене в поля массива объектов, как показано на рисунке выше:</span><span class="sxs-lookup"><span data-stu-id="d2955-148">Drag the following objects from the lunar module in your scene into the object array fields as shown in the image above:</span></span>

    ![Изображение "Урок 6, раздел 1, шаг 4а"](images/Lesson6_Chapter1_step4aim.PNG)

    <span data-ttu-id="d2955-150">Теперь сценарий включения переключателя для указания размещения настроен, что позволяет включать и отключать подсказки.</span><span class="sxs-lookup"><span data-stu-id="d2955-150">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

5. <span data-ttu-id="d2955-151">Добавьте скрипт запуска Лунный модуль.</span><span class="sxs-lookup"><span data-stu-id="d2955-151">Add the Launch Lunar Module script.</span></span> <span data-ttu-id="d2955-152">Нажмите кнопку Добавить компонент, выполните поиск по запросу "запустить Лунный модуль" и выберите его.</span><span class="sxs-lookup"><span data-stu-id="d2955-152">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="d2955-153">Этот сценарий запускает Лунный модуль.</span><span class="sxs-lookup"><span data-stu-id="d2955-153">This script launches the lunar module.</span></span> <span data-ttu-id="d2955-154">При нажатии настроенной кнопки она добавляет к компоненту внутренний текст в лунном модуле принудительную переправку и заставляет модуль запускаться вверх.</span><span class="sxs-lookup"><span data-stu-id="d2955-154">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="d2955-155">Если вы находитесь в помещении, лунный модуль может разбиться о потолочную сетку.</span><span class="sxs-lookup"><span data-stu-id="d2955-155">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="d2955-156">Если вы находится в области с высоким цеилингс или без цеилингс, Лунный модуль полетает в неограниченное место.</span><span class="sxs-lookup"><span data-stu-id="d2955-156">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span>

    ![Изображение "Урок 6, раздел 1, шаг 5"](images/Lesson6_Chapter1_step5im.PNG)

6. <span data-ttu-id="d2955-158">Отрегулируйте тягу так, чтобы лунный модуль изящно взлетел.</span><span class="sxs-lookup"><span data-stu-id="d2955-158">Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="d2955-159">Попробуйте использовать значение 0,01.</span><span class="sxs-lookup"><span data-stu-id="d2955-159">Try a value of 0.01.</span></span> <span data-ttu-id="d2955-160">Оставьте поле Rb пустым.</span><span class="sxs-lookup"><span data-stu-id="d2955-160">Leave the "Rb" field blank.</span></span> <span data-ttu-id="d2955-161">RB означает жесткое тело, и это поле будет автоматически заполнено во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d2955-161">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

    ![Изображение "Урок 6, раздел 1, шаг 6"](images/Lesson6_Chapter1_step6im.PNG)

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="d2955-163">Обзор компонентов лунного модуля</span><span class="sxs-lookup"><span data-stu-id="d2955-163">Lunar Module Parts overview</span></span>

<span data-ttu-id="d2955-164">Родительский объект частей лунного модуля — это коллекция объектов, с которыми взаимодействует пользователь.</span><span class="sxs-lookup"><span data-stu-id="d2955-164">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="d2955-165">Имена объектов игры с названиями сцен в скобках приведены в списке ниже.</span><span class="sxs-lookup"><span data-stu-id="d2955-165">The Game object names with scene labeled names in parentheses, are provided in the list below:</span></span>

- <span data-ttu-id="d2955-166">Ранец (ячейка энергии)</span><span class="sxs-lookup"><span data-stu-id="d2955-166">Backpack (Energy Cell)</span></span>
- <span data-ttu-id="d2955-167">Гастанк (топливо бак)</span><span class="sxs-lookup"><span data-stu-id="d2955-167">GasTank (Fuel Tank)</span></span>
- <span data-ttu-id="d2955-168">TopLeftBody (корпус лунохода);</span><span class="sxs-lookup"><span data-stu-id="d2955-168">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="d2955-169">Nose (стыковочный модуль);</span><span class="sxs-lookup"><span data-stu-id="d2955-169">Nose (Docking Portal)</span></span>
- <span data-ttu-id="d2955-170">LeftTwirler (внешний датчик).</span><span class="sxs-lookup"><span data-stu-id="d2955-170">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="d2955-171">Обратите внимание, что каждый из этих объектов имеет обработчик манипуляции, как описано в занятии 4.</span><span class="sxs-lookup"><span data-stu-id="d2955-171">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="d2955-172">Эта функция позволяет пользователям захватить и манипулировать объектом.</span><span class="sxs-lookup"><span data-stu-id="d2955-172">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="d2955-173">Кроме того, обратите внимание, что для параметра два типа манипуляции задано значение перемещение и поворот.</span><span class="sxs-lookup"><span data-stu-id="d2955-173">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="d2955-174">Этот параметр позволяет пользователю только перемещать объект и не изменять его размер, что является требуемой функциональностью для приложения сборки.</span><span class="sxs-lookup"><span data-stu-id="d2955-174">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="d2955-175">Кроме того, далеко не установлен флажок, чтобы разрешить только прямое взаимодействие частей модулей.</span><span class="sxs-lookup"><span data-stu-id="d2955-175">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Изображение "Урок 6, раздел 2"](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="d2955-177">Демонстрационный сценарий сборки части (показанный выше) представляет собой сценарий, управляющий объектами, которые пользователь помещает в Лунный модуль пользователем.</span><span class="sxs-lookup"><span data-stu-id="d2955-177">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span>

<span data-ttu-id="d2955-178">Поле "объект для размещения" — это выбранное преобразование, как показано на рисунке выше, ранец/топливо Tank, связанное с объектом, к которому он подключается.</span><span class="sxs-lookup"><span data-stu-id="d2955-178">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span>

<span data-ttu-id="d2955-179">Параметры близкого расстояния и дальнего расстояния определяют сходство, к какому компоненту привязывается, или могут быть освобождены.</span><span class="sxs-lookup"><span data-stu-id="d2955-179">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="d2955-180">Например, ранец или горючее должно быть 0,1 единиц на расстоянии от лунного модуля до того, как будет выполнена привязка.</span><span class="sxs-lookup"><span data-stu-id="d2955-180">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="d2955-181">Параметр дальнего расстояния задает расположение, в котором объект может быть, прежде чем он сможет отсоединиться от лунного модуля.</span><span class="sxs-lookup"><span data-stu-id="d2955-181">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="d2955-182">В этом случае рука пользователя должна захватить backpack (топливный бак) и вытащить его на расстояние 0,2 единицы от лунного модуля, чтобы отсоединить его.</span><span class="sxs-lookup"><span data-stu-id="d2955-182">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="d2955-183">Объект подсказки — это метка подсказки в сцене.</span><span class="sxs-lookup"><span data-stu-id="d2955-183">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="d2955-184">Когда объекты привязываются на месте, метка отключается.</span><span class="sxs-lookup"><span data-stu-id="d2955-184">When the objects are snapped in place, the label is disabled.</span></span>

<span data-ttu-id="d2955-185">Источник звука будет автоматически извлечен.</span><span class="sxs-lookup"><span data-stu-id="d2955-185">The Audio Source is automatically grabbed.</span></span>

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="d2955-186">Настройка кнопки подсказок размещения</span><span class="sxs-lookup"><span data-stu-id="d2955-186">Configuring the Placement Hints button</span></span>

<span data-ttu-id="d2955-187">На [занятии 2](mrlearning-base-ch2.md)вы узнали, как разместить и настроить кнопки для выполнения таких задач, как изменение цвета элемента или воспроизведение звука при отправке.</span><span class="sxs-lookup"><span data-stu-id="d2955-187">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="d2955-188">Мы продолжим использовать эти принципы при настройке наших кнопок для переключения подсказок по размещению.</span><span class="sxs-lookup"><span data-stu-id="d2955-188">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span>

<span data-ttu-id="d2955-189">Целью является настройка нашей кнопки таким образом, чтобы каждый раз, когда пользователь нажимает кнопку подсказок размещения, он переключается на прозрачность подсказок размещения.</span><span class="sxs-lookup"><span data-stu-id="d2955-189">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span>

1. <span data-ttu-id="d2955-190">Переместите Лунный модуль в пустой слот исполняющей среды на панели инспектора, когда объект указания размещения выбран в иерархии базовых сцен.</span><span class="sxs-lookup"><span data-stu-id="d2955-190">Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span>

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. <span data-ttu-id="d2955-192">Щелкните раскрывающийся список нет функции.</span><span class="sxs-lookup"><span data-stu-id="d2955-192">Click the No Function dropdown list.</span></span> <span data-ttu-id="d2955-193">Перейдите к Тогглеплацеменсинтс и выберите Тогглегамеобжектс () в этом меню.</span><span class="sxs-lookup"><span data-stu-id="d2955-193">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="d2955-194">Тогглегамеобжектс () переключает подсказки размещения, чтобы они были видимыми или невидимыми при каждом нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="d2955-194">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="d2955-196">Настройка кнопки сброса</span><span class="sxs-lookup"><span data-stu-id="d2955-196">Configuring the Reset button</span></span>

<span data-ttu-id="d2955-197">Существуют ситуации, когда пользователь создает ошибку, случайно выдает объект из системы или просто хочет сбросить интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d2955-197">There will be situations where the user makes a mistake, accidentally throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="d2955-198">Кнопка Reset (Сброс) добавляет возможность перезапуска процесса.</span><span class="sxs-lookup"><span data-stu-id="d2955-198">The Reset button adds the ability to restart the experience.</span></span>

1. <span data-ttu-id="d2955-199">Нажмите кнопку Сброс.</span><span class="sxs-lookup"><span data-stu-id="d2955-199">Select the Reset button.</span></span> <span data-ttu-id="d2955-200">В основной сцене он называется Ресетраундбуттон.</span><span class="sxs-lookup"><span data-stu-id="d2955-200">In the base scene, it’s named ResetRoundButton.</span></span>

2. <span data-ttu-id="d2955-201">Перетащите Лунный модуль из иерархии базовых сцен в пустой слот под кнопкой, нажатой на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="d2955-201">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. <span data-ttu-id="d2955-203">Выберите раскрывающееся меню без функции и наведите указатель мыши на Лаунчлунармодуле, а затем выберите Ресетмодуле ().</span><span class="sxs-lookup"><span data-stu-id="d2955-203">Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

    ![Изображение "Урок 6, раздел 4, шаг 3"](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="d2955-205">Обратите внимание, что по умолчанию GameObject. Броадкастмессаже настроен на Ресетплацемент.</span><span class="sxs-lookup"><span data-stu-id="d2955-205">Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="d2955-206">Это широковещательная рассылка сообщения с именем Ресетплацемент для каждого дочернего объекта RocketLauncher_Tutorial.</span><span class="sxs-lookup"><span data-stu-id="d2955-206">This broadcasts a message named ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="d2955-207">Любой объект, имеющий метод для Ресетплацемент (), отвечает на это сообщение, передавая его расположение.</span><span class="sxs-lookup"><span data-stu-id="d2955-207">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span>

## <a name="configuring-the-launch-button"></a><span data-ttu-id="d2955-208">Настройка кнопки запуска</span><span class="sxs-lookup"><span data-stu-id="d2955-208">Configuring the Launch button</span></span>

<span data-ttu-id="d2955-209">В этом разделе объясняется, как настроить кнопку запуска, которая позволяет пользователю нажать кнопку и запустить модуль лунного календаря в место.</span><span class="sxs-lookup"><span data-stu-id="d2955-209">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

1. <span data-ttu-id="d2955-210">Нажмите кнопку запустить.</span><span class="sxs-lookup"><span data-stu-id="d2955-210">Select the Launch button.</span></span> <span data-ttu-id="d2955-211">В основной сцене он называется Лаунчраундбуттон.</span><span class="sxs-lookup"><span data-stu-id="d2955-211">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="d2955-212">Перетащите Лунный модуль в пустой слот в разделе сенсорная точка на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="d2955-212">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. <span data-ttu-id="d2955-214">Выберите раскрывающееся меню без функции и наведите указатель мыши на Лаунчлунармодуле и выберите Стопсрустер ().</span><span class="sxs-lookup"><span data-stu-id="d2955-214">Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="d2955-215">Определяет, сколько креативность пользователь хочет предоставить Лунный модуль.</span><span class="sxs-lookup"><span data-stu-id="d2955-215">This controls how much thrust the user wants to give to the lunar module.</span></span>

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. <span data-ttu-id="d2955-217">Перетащите Лунный модуль из иерархии базовых сцен в пустой слот под нажатой кнопкой на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="d2955-217">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed in the inspector panel.</span></span>

4. <span data-ttu-id="d2955-218">Щелкните раскрывающееся меню нет функции, а затем на Лаунчлунармодуле и выберите Стартсрустер ().</span><span class="sxs-lookup"><span data-stu-id="d2955-218">Click the No function dropdown menu and then on LaunchLunarModule and select StartThruster ().</span></span>

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. <span data-ttu-id="d2955-220">Добавьте музыку в Лунный модуль, чтобы музыка воспроизводилась при отключении Rocket.</span><span class="sxs-lookup"><span data-stu-id="d2955-220">Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="d2955-221">Для этого перетащите Лунный модуль в следующий пустой слот под нажатой кнопкой ().</span><span class="sxs-lookup"><span data-stu-id="d2955-221">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

6. <span data-ttu-id="d2955-222">Выберите раскрывающееся меню без функции, наведите указатель мыши на Аудиосаурце и выберите Плайонешот (аудиоклип).</span><span class="sxs-lookup"><span data-stu-id="d2955-222">Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="d2955-223">Вы можете просмотреть все разнообразие звуков, включенных в MRTK.</span><span class="sxs-lookup"><span data-stu-id="d2955-223">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="d2955-224">В этом примере мы будем использовать «MRTK_Gem».</span><span class="sxs-lookup"><span data-stu-id="d2955-224">In this example, we'll use "MRTK_Gem."</span></span>

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

## <a name="congratulations"></a><span data-ttu-id="d2955-226">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d2955-226">Congratulations</span></span>

<span data-ttu-id="d2955-227">Вы полностью настроили это приложение.</span><span class="sxs-lookup"><span data-stu-id="d2955-227">You have fully configured this application.</span></span> <span data-ttu-id="d2955-228">Теперь, когда вы нажмете кнопку Воспроизвести, вы можете полностью собрать Лунный модуль, переключить подсказки, запустить Лунный модуль и сбросить его, чтобы снова запустить.</span><span class="sxs-lookup"><span data-stu-id="d2955-228">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>
