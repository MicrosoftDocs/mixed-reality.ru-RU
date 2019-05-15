---
title: Модуль MR обучения Base - качества образец модуля лунного сборки
description: На этом занятии мы объединит несколько понятий, узнали из предыдущих занятий, для создания уникальных пример взаимодействия.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Смешанная реальность, unity, руководство, hololens
ms.openlocfilehash: 303ed17724ba8799490aa7bca7a60600f6e5349b
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929605"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a><span data-ttu-id="2e74a-104">Модуль MR обучения Base - качества образец модуля лунного сборки</span><span class="sxs-lookup"><span data-stu-id="2e74a-104">MR Learning Base Module - Lunar Module Assembly Sample Experience</span></span>

<span data-ttu-id="2e74a-105">На этом занятии мы объединит несколько понятий, узнали из предыдущих занятий, для создания уникальных пример взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="2e74a-105">In this lesson, we will combine multiple concepts learned from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="2e74a-106">Мы создадим приложение сборки лунного модуля, при котором пользователю будет необходимо использовать отслеживаемые руки для применения модуля лунного частей и попытаться собрать лунного модуля.</span><span class="sxs-lookup"><span data-stu-id="2e74a-106">We will create a lunar module assembly application whereby a user will need to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="2e74a-107">Мы будем использовать pressable кнопки для переключения размещения подсказки, чтобы сбросить опыт и запуск нашего модуля лунного в пространство!</span><span class="sxs-lookup"><span data-stu-id="2e74a-107">We will use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="2e74a-108">В последующих руководствах мы будем продолжать созданы на основе этой работы, включая мощные несколькими пользователями варианты использования, которые использует Azure пространственных привязки для выравнивания пространственных.</span><span class="sxs-lookup"><span data-stu-id="2e74a-108">In future tutorials, we will continue to build upon this experience, including powerful multi-user use-cases that leverages Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="2e74a-109">Цели</span><span class="sxs-lookup"><span data-stu-id="2e74a-109">Objectives</span></span>

- <span data-ttu-id="2e74a-110">Объединение нескольких концепции из предыдущих занятий, чтобы создать уникальное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="2e74a-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="2e74a-111">Узнайте, как переключить объекты</span><span class="sxs-lookup"><span data-stu-id="2e74a-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="2e74a-112">Сложные события триггера с помощью pressable кнопок</span><span class="sxs-lookup"><span data-stu-id="2e74a-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="2e74a-113">Использование элемента rigidbody физики и силы</span><span class="sxs-lookup"><span data-stu-id="2e74a-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="2e74a-114">Изучить использование всплывающих подсказок</span><span class="sxs-lookup"><span data-stu-id="2e74a-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="2e74a-115">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2e74a-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="2e74a-116">Настройка модуля лунного</span><span class="sxs-lookup"><span data-stu-id="2e74a-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="2e74a-117">В этой главе мы будут представлены различные компоненты, необходимые для создания опыт образец.</span><span class="sxs-lookup"><span data-stu-id="2e74a-117">In this chapter, we will be introduced to the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="2e74a-118">Добавление готового блока сборки модуля лунного в сцену базы.</span><span class="sxs-lookup"><span data-stu-id="2e74a-118">Add the lunar module assembly prefab to your Base Scene.</span></span> <span data-ttu-id="2e74a-119">Для этого на вкладке проект, найдите «Launcher_Tutorial Rocket».</span><span class="sxs-lookup"><span data-stu-id="2e74a-119">To do this, in your project tab, search for "Rocket Launcher_Tutorial."</span></span> <span data-ttu-id="2e74a-120">Можно также найти в ресурсах prefab > BaseModuleAssets > Prefabs.</span><span class="sxs-lookup"><span data-stu-id="2e74a-120">You may also find the prefab in Assets>BaseModuleAssets>Prefabs.</span></span> <span data-ttu-id="2e74a-121">Может появиться два prefabs rocket запуска; один с именем «учебник», а другой с именем «выполнено».</span><span class="sxs-lookup"><span data-stu-id="2e74a-121">You may see two rocket launcher prefabs; one with the name "tutorial" and another with the name "complete."</span></span> <span data-ttu-id="2e74a-122">Перетащите «Rocket Launcher_Tutorial» prefab в сцену базы.</span><span class="sxs-lookup"><span data-stu-id="2e74a-122">Drag the "Rocket Launcher_Tutorial" prefab to your Base Scene.</span></span> <span data-ttu-id="2e74a-123">Вы можете разместить размещение prefab в сцене.</span><span class="sxs-lookup"><span data-stu-id="2e74a-123">Feel free to position the placement of the prefab in your scene.</span></span>
   <span data-ttu-id="2e74a-124">Примечание. Prefab «Launcher_Complete Rocket» является завершенной указано средство запуска, для ссылки.</span><span class="sxs-lookup"><span data-stu-id="2e74a-124">Note: The "Rocket Launcher_Complete" prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="2e74a-126">Если развернуть игровому объекту «Rocket Launcher_Tutorial» в иерархии и далее развернуть объект «Лунного модуля», вы увидите несколько дочерних объектов, которые материал, который называется «рентгенограммы».</span><span class="sxs-lookup"><span data-stu-id="2e74a-126">If you expand the "Rocket Launcher_Tutorial" game object in your hierarchy, and further expand the "Lunar Module" object, you will see several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="2e74a-127">Материал «рентгеновский снимок» позволяет немного полупрозрачный цвет, который мы будем использовать в качестве размещения подсказки для пользователя.</span><span class="sxs-lookup"><span data-stu-id="2e74a-127">The "x-ray" material allows for a slightly translucent color which we will use as placement hints for the user.</span></span> 

<span data-ttu-id="2e74a-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) состоит из пяти частей лунного модуль, который пользователь будет взаимодействовать с ними как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="2e74a-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user is going to interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="2e74a-129">Rover корпуса</span><span class="sxs-lookup"><span data-stu-id="2e74a-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="2e74a-130">Топливный бак</span><span class="sxs-lookup"><span data-stu-id="2e74a-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="2e74a-131">Ячейка энергии</span><span class="sxs-lookup"><span data-stu-id="2e74a-131">The Energy Cell</span></span>
4.  <span data-ttu-id="2e74a-132">На портале закрепления</span><span class="sxs-lookup"><span data-stu-id="2e74a-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="2e74a-133">Внешний датчик</span><span class="sxs-lookup"><span data-stu-id="2e74a-133">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="2e74a-135">Примечание. Имена объектов игр, которые вы видите в иерархии базовых сцены не соответствуют имена объектов в сцене.</span><span class="sxs-lookup"><span data-stu-id="2e74a-135">Note: The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="2e74a-136">Шаг 2. Добавьте источник аудио в модуле лунного.</span><span class="sxs-lookup"><span data-stu-id="2e74a-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="2e74a-137">Убедитесь, что модуль лунного выбран в иерархии сцены базового и нажмите кнопку «Добавить компонент».</span><span class="sxs-lookup"><span data-stu-id="2e74a-137">Make sure the lunar module is selected in your base scene hierarchy and click "Add Component."</span></span> <span data-ttu-id="2e74a-138">Найдите «Аудио источник» и добавьте его к объекту.</span><span class="sxs-lookup"><span data-stu-id="2e74a-138">Search for "Audio Source" and add it to the object.</span></span> <span data-ttu-id="2e74a-139">Не указывайте его сейчас.</span><span class="sxs-lookup"><span data-stu-id="2e74a-139">Leave it blank for now.</span></span> <span data-ttu-id="2e74a-140">Мы будем использовать для воспроизведения звука, запускающий позже.</span><span class="sxs-lookup"><span data-stu-id="2e74a-140">We will use this to play the launching sound later.</span></span>
 <span data-ttu-id="2e74a-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) шаг 3: Добавьте скрипт «размещения подсказки переключателя».</span><span class="sxs-lookup"><span data-stu-id="2e74a-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Step 3: Add the script "toggle placement hints."</span></span> <span data-ttu-id="2e74a-142">Нажмите кнопку «Добавить компонент» и выполните поиск «Размещения подсказки переключателя».</span><span class="sxs-lookup"><span data-stu-id="2e74a-142">Click "Add Component" and search for "Toggle Placement Hints."</span></span> <span data-ttu-id="2e74a-143">Это пользовательский скрипт, который позволяет включать и отключать прозрачные упоминалось ранее подсказки (объекты с материалом рентгеновский снимок).</span><span class="sxs-lookup"><span data-stu-id="2e74a-143">This is a custom script that allows you to turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span> 
<span data-ttu-id="2e74a-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) шаг 4: Поскольку мы имеем 5 объектами, введите «5» для подсчета размера массива игровому объекту.</span><span class="sxs-lookup"><span data-stu-id="2e74a-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Step 4: Since we have 5 objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="2e74a-145">Затем вы увидите 5 новых элементов, которые отображаются.</span><span class="sxs-lookup"><span data-stu-id="2e74a-145">Then you should see 5 new elements appear.</span></span> 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="2e74a-147">Перетащите каждый из объектов прозрачным в поля, в которых говорится «None (Game Object)».</span><span class="sxs-lookup"><span data-stu-id="2e74a-147">Drag each of the translucent objects into the boxes that say "None (Game Object)."</span></span> <span data-ttu-id="2e74a-148">Перетащите следующие объекты из модуля лунного в сцене базовый:</span><span class="sxs-lookup"><span data-stu-id="2e74a-148">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="2e74a-149">• Рюкзаке</span><span class="sxs-lookup"><span data-stu-id="2e74a-149">•   Backpack</span></span>

<span data-ttu-id="2e74a-150">• GasTank</span><span class="sxs-lookup"><span data-stu-id="2e74a-150">•   GasTank</span></span>

<span data-ttu-id="2e74a-151">• Topleftbody</span><span class="sxs-lookup"><span data-stu-id="2e74a-151">•   Topleftbody</span></span>

<span data-ttu-id="2e74a-152">• Нос</span><span class="sxs-lookup"><span data-stu-id="2e74a-152">•   Nose</span></span>

<span data-ttu-id="2e74a-153">• LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="2e74a-153">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="2e74a-155">Теперь настройки сценария «переключить размещения подсказки».</span><span class="sxs-lookup"><span data-stu-id="2e74a-155">Now the "toggle placement hints" script is configured.</span></span> <span data-ttu-id="2e74a-156">Это позволит нам включать подсказки и отключать.</span><span class="sxs-lookup"><span data-stu-id="2e74a-156">This will allow us to turn the hints on and off.</span></span>

<span data-ttu-id="2e74a-157">Шаг 5. Добавьте скрипт «запустить модуль лунного».</span><span class="sxs-lookup"><span data-stu-id="2e74a-157">Step 5: Add the "launch lunar module" script.</span></span> <span data-ttu-id="2e74a-158">Нажмите кнопку «Добавить компонент», найдите «модуля лунного запуска» и выберите его.</span><span class="sxs-lookup"><span data-stu-id="2e74a-158">Click the "Add Component" button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="2e74a-159">Этот сценарий будет отвечать за запуск лунного модуля.</span><span class="sxs-lookup"><span data-stu-id="2e74a-159">This script will be responsible for launching the lunar module.</span></span> <span data-ttu-id="2e74a-160">При нажатии кнопки настроенных он добавляет вверх force компонент модуля лунного твердое тело и вызовет модуля для запуска вверх.</span><span class="sxs-lookup"><span data-stu-id="2e74a-160">When we press a configured button, it will add an upward force to the lunar module's rigid body component and will cause the module to launch upwards.</span></span> <span data-ttu-id="2e74a-161">Если вы являетесь улице, может произойти сбой модуля лунного с Live mesh ceiling.</span><span class="sxs-lookup"><span data-stu-id="2e74a-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="2e74a-162">Но если вы являетесь лета, он будет Вылет пространство неограниченное время.</span><span class="sxs-lookup"><span data-stu-id="2e74a-162">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="2e74a-164">Шаг 6. Измените надежность, таким образом, чтобы корректно лунного модуля будут летать вверх.</span><span class="sxs-lookup"><span data-stu-id="2e74a-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="2e74a-165">Попробуйте значение 0,01.</span><span class="sxs-lookup"><span data-stu-id="2e74a-165">Try a value of 0.01.</span></span> <span data-ttu-id="2e74a-166">Оставьте поле «Rb» пустым.</span><span class="sxs-lookup"><span data-stu-id="2e74a-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="2e74a-167">RB означает твердое тело, и это поле заполняется автоматически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="2e74a-167">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="2e74a-169">Общие сведения о частях лунного модуля</span><span class="sxs-lookup"><span data-stu-id="2e74a-169">Lunar Module Parts Overview</span></span>
<span data-ttu-id="2e74a-170">Модуль лунного частей родительского объекта — коллекция объектов, с которыми будет взаимодействовать пользователь.</span><span class="sxs-lookup"><span data-stu-id="2e74a-170">The Lunar Module parts parent object is the collection of the objects that the user will interact with.</span></span> <span data-ttu-id="2e74a-171">В списке ниже приведены имена игровому объекту (с сцены с меткой имена в paretheses):</span><span class="sxs-lookup"><span data-stu-id="2e74a-171">The game object names (with scene labeled names in paretheses) are provided in the list below:</span></span>

- <span data-ttu-id="2e74a-172">Рюкзаке (топливного)</span><span class="sxs-lookup"><span data-stu-id="2e74a-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="2e74a-173">GasTank (ячейка энергии)</span><span class="sxs-lookup"><span data-stu-id="2e74a-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="2e74a-174">TopLeftBody (Rover корпус)</span><span class="sxs-lookup"><span data-stu-id="2e74a-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="2e74a-175">А нос — папы (закрепление портал)</span><span class="sxs-lookup"><span data-stu-id="2e74a-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="2e74a-176">LeftTwirler (внешний датчик)</span><span class="sxs-lookup"><span data-stu-id="2e74a-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="2e74a-177">Обратите внимание на то, что каждый из этих объектов имеет обработчик манипуляции, как обсуждалось на занятии 4.</span><span class="sxs-lookup"><span data-stu-id="2e74a-177">Notice that each of these objects has the manipulation handler, as discussed in lesson 4.</span></span> <span data-ttu-id="2e74a-178">С помощью обработчика манипуляции пользователи могут взять и манипулировать объектом.</span><span class="sxs-lookup"><span data-stu-id="2e74a-178">With the manipulation handler, users are able to grab and manipulate the object.</span></span> <span data-ttu-id="2e74a-179">Также Обратите внимание, что параметр «два типа выдан манипуляции» имеет значение «перемещать и поворачивать.»</span><span class="sxs-lookup"><span data-stu-id="2e74a-179">Also note that the setting "two handed manipulation type" is set to "move and rotate."</span></span> <span data-ttu-id="2e74a-180">Это позволяет пользователю перемещать объект и не изменять свой размер, являющийся нужной функции для сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="2e74a-180">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="2e74a-181">Кроме того дальней манипуляции не установлен, чтобы разрешить только для прямого взаимодействия частей модуля.</span><span class="sxs-lookup"><span data-stu-id="2e74a-181">In addition, far manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="2e74a-183">Демонстрационный сценарий часть сборки (как показано выше) является сценария, который управляет объектами помещается в модуле лунного пользователем.</span><span class="sxs-lookup"><span data-stu-id="2e74a-183">The part assembly demo script (shown above) is the scrip that manages the objects to be placed on to the lunar module by the user.</span></span> 

<span data-ttu-id="2e74a-184">Поле «Объект на месте» является преобразование, которое выбранный (н регистр на рисунке выше, рюкзаки/топливного) с объектом, который он может подключаться к.</span><span class="sxs-lookup"><span data-stu-id="2e74a-184">The "Object To Place" field is the transform that is selected (n the case of the image above, the backpack/fuel tank) with the object that it can connect to.</span></span> 

<span data-ttu-id="2e74a-185">Параметры «Рядом с Distance» и «Далеко Distance» несете ответственность за определение с учетом расположения, к которому частей страничным на месте или выпуск.</span><span class="sxs-lookup"><span data-stu-id="2e74a-185">The "Near Distance" and "Far Distance" settings are responsible for determining the proximity to which parts will snap in place or be released.</span></span> <span data-ttu-id="2e74a-186">Например рюкзаки/топливного потребуется 0,1 единицы от модуля лунного встать на свое место.</span><span class="sxs-lookup"><span data-stu-id="2e74a-186">For example, the backpack/fuel tank would need to be 0.1 units away from the lunar module to snap into place.</span></span> <span data-ttu-id="2e74a-187">«Далеко Distance» задает расположение, где должен быть отсоединиться от модуля лунного объекта.</span><span class="sxs-lookup"><span data-stu-id="2e74a-187">The "Far Distance" sets the location where the object needs to be to detach from the lunar module.</span></span> <span data-ttu-id="2e74a-188">В этом случае руку пользователя необходимо взять рюкзаке/топливного и потяните за нее 0,2 единицы от модуля лунного, чтобы удалить его из обратно к месту.</span><span class="sxs-lookup"><span data-stu-id="2e74a-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="2e74a-189">«Объект подсказки средства» — это метка совет средство в сцене.</span><span class="sxs-lookup"><span data-stu-id="2e74a-189">The "Tool Tip Object" is the tool tip label in the scene.</span></span> <span data-ttu-id="2e74a-190">Если объекты имеют почасовую привязку на месте, метки будут отключены.</span><span class="sxs-lookup"><span data-stu-id="2e74a-190">When the objects are snapped in place, the label will be disabled.</span></span> 

<span data-ttu-id="2e74a-191">Источник аудио будет извлечен автоматически.</span><span class="sxs-lookup"><span data-stu-id="2e74a-191">The Audio Source will be automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="2e74a-192">Размещение указания кнопок</span><span class="sxs-lookup"><span data-stu-id="2e74a-192">Placement Hints Buttons</span></span>
<span data-ttu-id="2e74a-193">В [Урок 2](mrlearning-base-ch2.md), вы узнали, как размещение и настройка кнопки для работы, например изменение цвета элемента или сделать его воспроизведения звука при его отправке.</span><span class="sxs-lookup"><span data-stu-id="2e74a-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="2e74a-194">Мы будем продолжать использовать эти принципы, как мы настроим наши кнопки переключения размещения подсказки.</span><span class="sxs-lookup"><span data-stu-id="2e74a-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="2e74a-195">Целью является настройте кнопку таким образом, чтобы каждый раз при нажатии кнопка Указание размещения, он будет переключать видимость прозрачные размещения подсказок.</span><span class="sxs-lookup"><span data-stu-id="2e74a-195">The goal is to configure our button so that every time the user presses the placement hint button, it will toggle visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="2e74a-196">Шаг 1. Переместите модуль лунного слот пустой «только среда выполнения» на панели инспектора, пока объект размещения подсказки выбран в иерархии базовых сцены.</span><span class="sxs-lookup"><span data-stu-id="2e74a-196">Step 1: Move the Lunar Module to the empty "runtime only" slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="2e74a-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) шаг 2: Теперь щелкните раскрывающийся список, где отображается надпись, «нет функция».</span><span class="sxs-lookup"><span data-stu-id="2e74a-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the dropdown list where it says, "no function."</span></span> <span data-ttu-id="2e74a-198">Перейдите «TogglePlacementHints» и в этом меню выберите «ToggleGameObjects ().»</span><span class="sxs-lookup"><span data-stu-id="2e74a-198">Go down to "TogglePlacementHints," and under that menu select "ToggleGameObjects ()."</span></span> <span data-ttu-id="2e74a-199">ToggleGameObjects() будет включать размещения подсказки и выключать, чтобы они были видимым или невидимым, каждый раз при нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="2e74a-199">ToggleGameObjects() will toggle the placement hints on and off so that they are visible or invisible every time the button is pressed.</span></span>
 <span data-ttu-id="2e74a-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="2e74a-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="2e74a-201">Настройка кнопки сброса</span><span class="sxs-lookup"><span data-stu-id="2e74a-201">Configuring the Reset Button</span></span>

<span data-ttu-id="2e74a-202">Будет существовать ситуации, когда пользователь делает ошибку, или случайно создает исключение, объект немедленно, или просто хочет rest в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="2e74a-202">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to rest the experience.</span></span> <span data-ttu-id="2e74a-203">«Сброс» будет добавлена возможность перезапустить процесс.</span><span class="sxs-lookup"><span data-stu-id="2e74a-203">The reset button will add the ability to restart the experience.</span></span> 

<span data-ttu-id="2e74a-204">Шаг 1. Нажмите кнопку сброса.</span><span class="sxs-lookup"><span data-stu-id="2e74a-204">Step 1: Select the reset button.</span></span> <span data-ttu-id="2e74a-205">В базовый сцены он называется «ResetRoundButton.»</span><span class="sxs-lookup"><span data-stu-id="2e74a-205">In the base scene, it’s named "ResetRoundButton."</span></span> 

<span data-ttu-id="2e74a-206">Шаг 2. Перетащите модуль лунного из иерархии базовых сцены в пустой слот, в разделе «нажата кнопка» на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="2e74a-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under "button pressed" the inspector panel.</span></span>
 <span data-ttu-id="2e74a-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="2e74a-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="2e74a-208">Шаг 3. Выберите в раскрывающемся меню, который говорит: «нет функции» и наведите указатель мыши «LaunchLunarModule.»</span><span class="sxs-lookup"><span data-stu-id="2e74a-208">Step 3: Select the dropdown menu that says, "no function" and hover over "LaunchLunarModule."</span></span> <span data-ttu-id="2e74a-209">Теперь выберите «resetModule ()».</span><span class="sxs-lookup"><span data-stu-id="2e74a-209">Now select "resetModule ()."</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="2e74a-211">Примечание. Обратите внимание, что по умолчанию «GameObject.BroadcastMessage» настроен для «ResetPlacement.»</span><span class="sxs-lookup"><span data-stu-id="2e74a-211">Note: You will notice that by default the "GameObject.BroadcastMessage" is configured to "ResetPlacement."</span></span> <span data-ttu-id="2e74a-212">Это будет широковещательная передача сообщения о вызове «ResetPlacement» для всех дочерних объектов RocketLauncher_Tutorial.</span><span class="sxs-lookup"><span data-stu-id="2e74a-212">This will broadcast a message called "ResetPlacement" for every child object of RocketLauncher_Tutorial.</span></span> <span data-ttu-id="2e74a-213">Любой объект, который содержит метод для «ResetPlacement()» будет отвечать на это сообщение, сбросив его позиции.</span><span class="sxs-lookup"><span data-stu-id="2e74a-213">Any object that has a method for "ResetPlacement()" will respond to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="2e74a-214">Запуск модуля лунного</span><span class="sxs-lookup"><span data-stu-id="2e74a-214">Launching the Lunar Module</span></span>
<span data-ttu-id="2e74a-215">В этой главе мы будет выполняться настройка кнопку запуска.</span><span class="sxs-lookup"><span data-stu-id="2e74a-215">This chapter we will be configuring the launch button.</span></span> <span data-ttu-id="2e74a-216">Это позволит пользователю нажать кнопку и запустить модуль лунного в пространство.</span><span class="sxs-lookup"><span data-stu-id="2e74a-216">This will permit the user to press the button and launch the Lunar Module into space.</span></span>

<span data-ttu-id="2e74a-217">Шаг 1. Выберите кнопку запуска (в базовый сцене он называется «LaunchRoundButton»).</span><span class="sxs-lookup"><span data-stu-id="2e74a-217">Step 1: Select the launch button (in the base scene it’s named "LaunchRoundButton").</span></span> <span data-ttu-id="2e74a-218">Перетащите модуль лунного пустой слот, в разделе «End Touch» на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="2e74a-218">Drag the Lunar Module to the empty slot under "Touch End" in the inspector panel.</span></span>
 <span data-ttu-id="2e74a-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) шаг 2: Выберите в раскрывающемся меню с сообщением «не функция».</span><span class="sxs-lookup"><span data-stu-id="2e74a-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the dropdown menu that says, "no function."</span></span> <span data-ttu-id="2e74a-220">Наведите указатель мыши «LaunchLunarModule» и выберите «StopThruster ()».</span><span class="sxs-lookup"><span data-stu-id="2e74a-220">Hover over "LaunchLunarModule" and select "StopThruster ()."</span></span> <span data-ttu-id="2e74a-221">Это будет контролировать объем Осевая сила, пользователю необходимо передать лунного модуля.</span><span class="sxs-lookup"><span data-stu-id="2e74a-221">This will control how much thrust the user wants to give to the Lunar Module.</span></span> 
 <span data-ttu-id="2e74a-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) шаг 3: В разделе «ButtonPressed()» добавьте модуль лунного (, удержание, перетаскивание) в пустой слот.</span><span class="sxs-lookup"><span data-stu-id="2e74a-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Step 3: Under "ButtonPressed()", add the Lunar Module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="2e74a-223">Шаг 4. Щелкните раскрывающееся меню с сообщением «нет функции» и наведите указатель мыши «LaunchLunarModule» и выберите «StartThruster ()».</span><span class="sxs-lookup"><span data-stu-id="2e74a-223">Step 4: Click the dropdown menu that says, "no function" and hover over "LaunchLunarModule" and select "StartThruster ()."</span></span> 
 <span data-ttu-id="2e74a-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) шаг 5: Добавьте модуль лунного музыки таким образом, чтобы при ракеты набирает обороты, будет воспроизведение музыки.</span><span class="sxs-lookup"><span data-stu-id="2e74a-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Step 5: Add music to the Lunar Module so that when the rocket takes off, the music will play.</span></span> <span data-ttu-id="2e74a-225">Для этого перетащите модуль лунного Далее пустой слот, в разделе «Pressed() кнопка».</span><span class="sxs-lookup"><span data-stu-id="2e74a-225">To do this, drag the Lunar Module to the next empty slot under "Button Pressed()".</span></span>

<span data-ttu-id="2e74a-226">Шаг 6. Выберите в раскрывающемся меню, который говорит: «нет функции» и наведите указатель мыши «AudioSource» и выберите «PlayOneShot (AudioClip)».</span><span class="sxs-lookup"><span data-stu-id="2e74a-226">Step 6: Select the dropdown menu that says, "no function" and hover over "AudioSource" and select "PlayOneShot (AudioClip)."</span></span> <span data-ttu-id="2e74a-227">Вы можете просмотреть все разнообразие звуков, в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="2e74a-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="2e74a-228">В этом примере мы будем придерживаться «MRTK_Gem.»</span><span class="sxs-lookup"><span data-stu-id="2e74a-228">For this example, we are going to stick with "MRTK_Gem."</span></span>
 <span data-ttu-id="2e74a-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="2e74a-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="2e74a-230">Поздравляю</span><span class="sxs-lookup"><span data-stu-id="2e74a-230">Congratulations</span></span> 
<span data-ttu-id="2e74a-231">Это приложение полностью настроили!</span><span class="sxs-lookup"><span data-stu-id="2e74a-231">You have fully configured this application!</span></span> <span data-ttu-id="2e74a-232">Теперь при нажатии кнопки "play" можно полностью объединить лунного модуля, переключить подсказки, запустите модуль лунного и сбросить его, чтобы повторить все еще раз.</span><span class="sxs-lookup"><span data-stu-id="2e74a-232">Now when you press play, you can fully assemble the Lunar Module, toggle hints, launch the Lunar Module, and reset it to do it all over again.</span></span>