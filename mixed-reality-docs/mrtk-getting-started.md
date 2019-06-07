---
title: Приступая к работе с MRTK версии 2
description: Для новых разработчиков, заинтересованных в применении MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, протестировать, смешанной реальности Toolkit, MRTK версии 2, MRTK, средства SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750364"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="28326-104">Приступая к работе с MRTK v2</span><span class="sxs-lookup"><span data-stu-id="28326-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="28326-105">Руководство по началу MRTK работы</span><span class="sxs-lookup"><span data-stu-id="28326-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="28326-106">См. в разделе [MRTK руководство по началу](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) сведения по началу работы с MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="28326-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="28326-107">Что такое набор средств смешанной реальности (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="28326-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="28326-108">MRTK является набор с удивительные открытым кодом, что существовало с момента первого выпуска HoloLens и не будет там, где это сегодня без изнурительной работы по наше сообщество разработчиков, предоставили к нему.</span><span class="sxs-lookup"><span data-stu-id="28326-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="28326-109">За последние 3 лет мы проанализировали отзывы наше сообщество разработчиков, а также построение v2 MRTK учитывать главных задач.</span><span class="sxs-lookup"><span data-stu-id="28326-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="28326-110">V2 MRTK с помощью Unity — это пакету средств разработки кросс платформенных открытым исходным кодом для смешанной реальности приложений.</span><span class="sxs-lookup"><span data-stu-id="28326-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="28326-111">MRTK версии 2 предназначен для ускорения разработки приложений, предназначенных для Microsoft HoloLens, Windows Mixed Reality иммерсивную (VR) и OpenVR платформы.</span><span class="sxs-lookup"><span data-stu-id="28326-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="28326-112">Проект является, предназначенные для снижения барьеры операции для создания приложения смешанной реальности и внести свой вклад сообщества по мере мы все роста.</span><span class="sxs-lookup"><span data-stu-id="28326-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="28326-113">См. в разделе [портале документации MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) для получения дополнительных сведений.</span><span class="sxs-lookup"><span data-stu-id="28326-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="28326-114">Функциональные области</span><span class="sxs-lookup"><span data-stu-id="28326-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Система ввода" width="105"> <span data-ttu-id="28326-116">Система ввода</span><span class="sxs-lookup"><span data-stu-id="28326-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Рука отслеживания (HoloLens 2)" width="105"> <span data-ttu-id="28326-118">Рука отслеживания (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="28326-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Отслеживания (HoloLens 2)" width="105">
    <span data-ttu-id="28326-120">Отслеживания (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="28326-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Голосовые команды" width="105"> <span data-ttu-id="28326-122">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="28326-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Помощи + Выбор (HoloLens (1-го поколения))" width="105">
    <span data-ttu-id="28326-124">Помощи + Выбор (HoloLens (1-го поколения))</span><span class="sxs-lookup"><span data-stu-id="28326-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> <span data-ttu-id="28326-126">Teleportation</span><span class="sxs-lookup"><span data-stu-id="28326-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Элементы управления пользовательским интерфейсом" width="105"> <span data-ttu-id="28326-128">Элементы управления пользовательским интерфейсом</span><span class="sxs-lookup"><span data-stu-id="28326-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Средства поиска решения и взаимодействия" width="105"> <span data-ttu-id="28326-130">Средства поиска решения и взаимодействия</span><span class="sxs-lookup"><span data-stu-id="28326-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Контроллер визуализации" width="105"> <span data-ttu-id="28326-132">Контроллер визуализации</span><span class="sxs-lookup"><span data-stu-id="28326-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Пространственные понимание" width="105"> <span data-ttu-id="28326-134">Пространственные понимание</span><span class="sxs-lookup"><span data-stu-id="28326-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Средство диагностики" width="105"> <span data-ttu-id="28326-136">Средство диагностики</span><span class="sxs-lookup"><span data-stu-id="28326-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Стандартный шейдера MRTK" width="105"> <span data-ttu-id="28326-138">Стандартный шейдера MRTK</span><span class="sxs-lookup"><span data-stu-id="28326-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="28326-139">Пользовательский Интерфейс и взаимодействие стандартных блоков</span><span class="sxs-lookup"><span data-stu-id="28326-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Кнопка" width="250"><br>
    <span data-ttu-id="28326-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="28326-141">**Button**</span></span><br>
    <span data-ttu-id="28326-142">Элемент управления button, который поддерживает различные методы ввода, включая HoloLens 2 ясно сформулированные вручную <a/></span><span class="sxs-lookup"><span data-stu-id="28326-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Ограничивающий прямоугольник" width="250"><br>
    <span data-ttu-id="28326-144">**Ограничивающий прямоугольник**</span><span class="sxs-lookup"><span data-stu-id="28326-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="28326-145">Стандартный пользовательский Интерфейс для управления объектами в трехмерном пространстве <a/></span><span class="sxs-lookup"><span data-stu-id="28326-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Обработчик манипуляции" width="250"><br>
    <span data-ttu-id="28326-147">**Обработчик манипуляции**</span><span class="sxs-lookup"><span data-stu-id="28326-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="28326-148">Скрипт для управления объектами с помощью одного или двух рук <a/></span><span class="sxs-lookup"><span data-stu-id="28326-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Содержание рекламы" width="250"><br>
    <span data-ttu-id="28326-150">**Содержание рекламы**</span><span class="sxs-lookup"><span data-stu-id="28326-150">**Slate**</span></span> <br>
    <span data-ttu-id="28326-151">2D стиля плоскости, которая поддерживает прокрутку с входными данными ясно сформулированные вручную <a/></span><span class="sxs-lookup"><span data-stu-id="28326-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Системную клавиатуру" width="250"><br>
    <span data-ttu-id="28326-153">**Системную клавиатуру**</span><span class="sxs-lookup"><span data-stu-id="28326-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="28326-154">Пример сценария использования клавиатуры системы в Unity <a/></span><span class="sxs-lookup"><span data-stu-id="28326-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Элементом" width="250"><br>
     <span data-ttu-id="28326-156">**Элементом**</span><span class="sxs-lookup"><span data-stu-id="28326-156">**Interactable**</span></span> <br>
     <span data-ttu-id="28326-157">Скрипт для создания объектов элементом с помощью визуальных состояний и поддержка тем <a/></span><span class="sxs-lookup"><span data-stu-id="28326-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Поиск решения" width="250"><br>
    <span data-ttu-id="28326-159">**Поиск решения**</span><span class="sxs-lookup"><span data-stu-id="28326-159">**Solver**</span></span> <br>
    <span data-ttu-id="28326-160">Различные объекта позиционирования особенности поведения, такие как tag-along, текст с блокировкой, размера представления константы и поверхности магнитного <a/></span><span class="sxs-lookup"><span data-stu-id="28326-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Коллекция объектов" width="250"><br>
    <span data-ttu-id="28326-162">**Коллекция объектов**</span><span class="sxs-lookup"><span data-stu-id="28326-162">**Object Collection**</span></span><br>
    <span data-ttu-id="28326-163">Скрипт для размещать массив объектов в трехмерной фигуры <a/></span><span class="sxs-lookup"><span data-stu-id="28326-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Всплывающая подсказка" width="250">  <br>
    <span data-ttu-id="28326-165">**Подсказка**</span><span class="sxs-lookup"><span data-stu-id="28326-165">**Tooltip**</span></span><br>
    <span data-ttu-id="28326-166">Заметка пользовательского интерфейса с гибкой привязки/pivot системы, который может использоваться для работы с метками контроллеров движения и объекта <a/></span><span class="sxs-lookup"><span data-stu-id="28326-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Панель приложения" width="250"><br>
    <span data-ttu-id="28326-168">**Панель приложения**</span><span class="sxs-lookup"><span data-stu-id="28326-168">**App Bar**</span></span><br>
    <span data-ttu-id="28326-169">Пользовательский Интерфейс для ручной активации ограничивающий прямоугольник <a/></span><span class="sxs-lookup"><span data-stu-id="28326-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Указатели" width="250"><br>
    <span data-ttu-id="28326-171">**Указатели**</span><span class="sxs-lookup"><span data-stu-id="28326-171">**Pointers**</span></span><br>
    <span data-ttu-id="28326-172">Дополнительные сведения о различных типов указателей <a/></span><span class="sxs-lookup"><span data-stu-id="28326-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Срезах визуализации" width="250"><br>
     <span data-ttu-id="28326-174">**Срезах визуализации**</span><span class="sxs-lookup"><span data-stu-id="28326-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="28326-175">Visual affordance в срезах, облегчающее достоверности для прямого взаимодействия <a/></span><span class="sxs-lookup"><span data-stu-id="28326-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    <span data-ttu-id="28326-177">**Slider**</span><span class="sxs-lookup"><span data-stu-id="28326-177">**Slider**</span></span><br>
    <span data-ttu-id="28326-178">Ползунок пользовательского интерфейса для изменения значения поддержки прямой вручную отслеживания взаимодействия <a/></span><span class="sxs-lookup"><span data-stu-id="28326-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Стандартный шейдера MRTK" width="250"><br>
    <span data-ttu-id="28326-180">**Стандартный шейдера MRTK**</span><span class="sxs-lookup"><span data-stu-id="28326-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="28326-181">Стандартный шейдера MRTK поддерживает различные элементы проектирования Fluent с производительностью <a/></span><span class="sxs-lookup"><span data-stu-id="28326-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Вручную сертификационного Chaser" width="250"><br>
     <span data-ttu-id="28326-183">**Вручную сертификационного Chaser**</span><span class="sxs-lookup"><span data-stu-id="28326-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="28326-184">Демонстрирует использование средства поиска решения для присоединения объектов к соединений вручную <a/></span><span class="sxs-lookup"><span data-stu-id="28326-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Отслеживание глаза: Выбор назначения" width="250"><br>
    <span data-ttu-id="28326-186">**Отслеживание глаза: Выбор назначения**</span><span class="sxs-lookup"><span data-stu-id="28326-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="28326-187">Объединить глаза, голоса и наличии входные данные быстро и легко выбирать голограммы в сценах <a/></span><span class="sxs-lookup"><span data-stu-id="28326-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Отслеживание глаза: Навигация" width="250"><br>
    <span data-ttu-id="28326-189">**Отслеживание глаза: Навигации**</span><span class="sxs-lookup"><span data-stu-id="28326-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="28326-190">Узнайте, как auto прокрутить текст или меньшим числом запинок масштабирования в конкретное содержимое, в зависимости от того, что вы видите <a/></span><span class="sxs-lookup"><span data-stu-id="28326-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Отслеживание глаза: Тепловая карта" width="250"><br>
    <span data-ttu-id="28326-192">**Отслеживание глаза: Тепловая карта**</span><span class="sxs-lookup"><span data-stu-id="28326-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="28326-193">Примеры для ведения журнала, загрузки и визуализация какие пользователи нуждались в в приложении <a/></span><span class="sxs-lookup"><span data-stu-id="28326-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="28326-194">Минимальным требованием для MRTK v2</span><span class="sxs-lookup"><span data-stu-id="28326-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="28326-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="28326-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="28326-196">Microsoft Visual Studio 2017 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="28326-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="28326-197">Windows SDK 18362 +</span><span class="sxs-lookup"><span data-stu-id="28326-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="28326-198">Windows 10 версии 1803 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="28326-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="28326-199">Новые возможности MRTK v2</span><span class="sxs-lookup"><span data-stu-id="28326-199">New with MRTK v2</span></span>
<span data-ttu-id="28326-200">Мы хотим стремлении к этим средствам платформы с нагрузкой.</span><span class="sxs-lookup"><span data-stu-id="28326-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="28326-201">На самом деле использовались MRTK версии 2 для разработки на нашем опыте работы папки "Входящие", такие как программа установки experience (OOBE) и наше приложение смешанной реальности обучения.</span><span class="sxs-lookup"><span data-stu-id="28326-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="28326-202">Кроме того, можно ожидать новые возможности HoloLens 2, сначала отображенном MRTK, так как мы считаем, что это лучший способ разработки на нашей платформе.</span><span class="sxs-lookup"><span data-stu-id="28326-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="28326-203">Модульная</span><span class="sxs-lookup"><span data-stu-id="28326-203">Modular</span></span>
<span data-ttu-id="28326-204">Мы предусмотрели его модульной способом, таким образом, чтобы вам не нужно отключать каждый бит набора средств в проект.</span><span class="sxs-lookup"><span data-stu-id="28326-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="28326-205">Существует фактически дает несколько преимуществ это.</span><span class="sxs-lookup"><span data-stu-id="28326-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="28326-206">Она обеспечивает меньший размер вашего проекта, а также упрощает управление.</span><span class="sxs-lookup"><span data-stu-id="28326-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="28326-207">Поверх всего этого так как она основана на объекты сценариев и определяется интерфейс, можно также заменить компоненты, которые входят в состав собственным, для поддержки других служб, систем и платформ.</span><span class="sxs-lookup"><span data-stu-id="28326-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="28326-208">Поддержка разных платформ</span><span class="sxs-lookup"><span data-stu-id="28326-208">Cross-platform</span></span>
<span data-ttu-id="28326-209">Говоря о других платформах, он имеет Поддержка разных платформ.</span><span class="sxs-lookup"><span data-stu-id="28326-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="28326-210">И хотя это не означает, что каждый единую платформу поддерживается без дополнительной настройки, мы внесли в том, что никакой код toolkit нарушит работу при переходе целевой сборки с другими платформами.</span><span class="sxs-lookup"><span data-stu-id="28326-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="28326-211">Надежность и расширяемость с помощью модульную структуру настраивает по контуру хорошо иметь возможность обеспечить поддержку нескольких платформ, таких как ARCore, ARKit и OpenVR.</span><span class="sxs-lookup"><span data-stu-id="28326-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="28326-212">Высокопроизводительные</span><span class="sxs-lookup"><span data-stu-id="28326-212">Performant</span></span>
<span data-ttu-id="28326-213">Работа с мобильных платформ, мы составили его с учетом производительности.</span><span class="sxs-lookup"><span data-stu-id="28326-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="28326-214">Это крайне важно выверить, и мы хотели бы убедиться, что средства не будут работать для вас.</span><span class="sxs-lookup"><span data-stu-id="28326-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="28326-215">См. также</span><span class="sxs-lookup"><span data-stu-id="28326-215">See also</span></span>
* [<span data-ttu-id="28326-216">Руководство по началу работы MRTK</span><span class="sxs-lookup"><span data-stu-id="28326-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="28326-217">Домашняя страница документации по MRTK</span><span class="sxs-lookup"><span data-stu-id="28326-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="28326-218">Установка средств</span><span class="sxs-lookup"><span data-stu-id="28326-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="28326-219">Перенос приложений из HTK/MRTK в MRTK версии 2</span><span class="sxs-lookup"><span data-stu-id="28326-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
