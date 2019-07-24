---
title: Начало работы с МРТК версии 2
description: Для новых разработчиков, заинтересованных в использовании МРТК
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, тестирование, набор средств для смешанной реальности, МРТК версии 2, МРТК, средства, пакет SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750364"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="257cc-104">Начало работы с МРТК v2</span><span class="sxs-lookup"><span data-stu-id="257cc-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="257cc-105">МРТК начало работы</span><span class="sxs-lookup"><span data-stu-id="257cc-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="257cc-106">Сведения о начале работы с МРТК v2 см. в разделе [руководство по началу работы с мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) .</span><span class="sxs-lookup"><span data-stu-id="257cc-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="257cc-107">Что такое набор средств для смешанной реальности (МРТК)?</span><span class="sxs-lookup"><span data-stu-id="257cc-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="257cc-108">МРТК — это чудесный набор средств с открытым исходным кодом, с момента первого выпуска HoloLens, который не был в настоящее время без жесткой работы нашего сообщества разработчиков, который участвовал в этом.</span><span class="sxs-lookup"><span data-stu-id="257cc-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="257cc-109">За последние 3 года мы прослушались на отзыве сообщества разработчиков и создали МРТК v2, чтобы принять во внимание самые существенные проблемы.</span><span class="sxs-lookup"><span data-stu-id="257cc-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="257cc-110">МРТК v2 с Unity — это набор средств межплатформенного развертывания с открытым исходным кодом для приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="257cc-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="257cc-111">МРТК версии 2 предназначена для ускорения разработки приложений, предназначенных для головных телефонов Microsoft HoloLens, Windows Mixed Reality (VR) и платформы Опенвр.</span><span class="sxs-lookup"><span data-stu-id="257cc-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="257cc-112">Целью проекта является снижение барьеров для создания приложений смешанной реальности и внесение вклада в развитие сообщества по мере расширения личного опыта.</span><span class="sxs-lookup"><span data-stu-id="257cc-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="257cc-113">Дополнительные сведения см. на [портале документации по мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) .</span><span class="sxs-lookup"><span data-stu-id="257cc-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="257cc-114">Функциональные области</span><span class="sxs-lookup"><span data-stu-id="257cc-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Входная система" width="105"> <span data-ttu-id="257cc-116">Входная система</span><span class="sxs-lookup"><span data-stu-id="257cc-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Отслеживание вручную (HoloLens 2)" width="105"> <span data-ttu-id="257cc-118">Отслеживание вручную (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="257cc-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Отслеживание взгляда (HoloLens 2)" width="105">
    <span data-ttu-id="257cc-120">Отслеживание взгляда (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="257cc-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Голосовое Командое" width="105"> <span data-ttu-id="257cc-122">Голосовое Командое</span><span class="sxs-lookup"><span data-stu-id="257cc-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Взгляните + SELECT (HoloLens (1-й общий))" width="105">
    <span data-ttu-id="257cc-124">Взгляните + SELECT (HoloLens (1-й общий))</span><span class="sxs-lookup"><span data-stu-id="257cc-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Пропорции" width="105"> <span data-ttu-id="257cc-126">Пропорции</span><span class="sxs-lookup"><span data-stu-id="257cc-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Элементы управления пользовательским интерфейсом" width="105"> <span data-ttu-id="257cc-128">Элементы управления пользовательским интерфейсом</span><span class="sxs-lookup"><span data-stu-id="257cc-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Поиск и взаимодействие" width="105"> <span data-ttu-id="257cc-130">Поиск и взаимодействие</span><span class="sxs-lookup"><span data-stu-id="257cc-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Визуализация контроллера" width="105"> <span data-ttu-id="257cc-132">Визуализация контроллера</span><span class="sxs-lookup"><span data-stu-id="257cc-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Пространственное понимание" width="105"> <span data-ttu-id="257cc-134">Пространственное понимание</span><span class="sxs-lookup"><span data-stu-id="257cc-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Средство диагностики" width="105"> <span data-ttu-id="257cc-136">Средство диагностики</span><span class="sxs-lookup"><span data-stu-id="257cc-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Стандартный шейдер МРТК" width="105"> <span data-ttu-id="257cc-138">Стандартный шейдер МРТК</span><span class="sxs-lookup"><span data-stu-id="257cc-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="257cc-139">Стандартные блоки пользовательского интерфейса и взаимодействия</span><span class="sxs-lookup"><span data-stu-id="257cc-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Кнопка" width="250"><br>
    <span data-ttu-id="257cc-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="257cc-141">**Button**</span></span><br>
    <span data-ttu-id="257cc-142">Элемент управления "Кнопка", поддерживающий различные методы ввода, включая наладонный объект HoloLens 2<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Ограничивающий прямоугольник" width="250"><br>
    <span data-ttu-id="257cc-144">**Ограничивающий прямоугольник**</span><span class="sxs-lookup"><span data-stu-id="257cc-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="257cc-145">Стандартный пользовательский интерфейс для манипулирования объектами в трехмерном пространстве<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Обработчик манипуляции" width="250"><br>
    <span data-ttu-id="257cc-147">**Обработчик манипуляции**</span><span class="sxs-lookup"><span data-stu-id="257cc-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="257cc-148">Скрипт для манипулирования объектами с одной или двумя руки<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Рекламы" width="250"><br>
    <span data-ttu-id="257cc-150">**Рекламы**</span><span class="sxs-lookup"><span data-stu-id="257cc-150">**Slate**</span></span> <br>
    <span data-ttu-id="257cc-151">плоскость двумерных стилей, которая поддерживает прокрутку с помощью клавиатуры с вытеканием руки<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Системная клавиатура" width="250"><br>
    <span data-ttu-id="257cc-153">**Системная клавиатура**</span><span class="sxs-lookup"><span data-stu-id="257cc-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="257cc-154">Пример сценария использования системной клавиатуры в Unity<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Элементом" width="250"><br>
     <span data-ttu-id="257cc-156">**Элементом**</span><span class="sxs-lookup"><span data-stu-id="257cc-156">**Interactable**</span></span> <br>
     <span data-ttu-id="257cc-157">Скрипт, обеспечивающий взаимодействие объектов с визуальными состояниями и поддержкой тем<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Найден" width="250"><br>
    <span data-ttu-id="257cc-159">**Найден**</span><span class="sxs-lookup"><span data-stu-id="257cc-159">**Solver**</span></span> <br>
    <span data-ttu-id="257cc-160">Различные поведения позиционирования объектов, такие как тег, блокировка тела, размер представления константы и магнит поверхностей поверхности<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Коллекция объектов" width="250"><br>
    <span data-ttu-id="257cc-162">**Коллекция объектов**</span><span class="sxs-lookup"><span data-stu-id="257cc-162">**Object Collection**</span></span><br>
    <span data-ttu-id="257cc-163">Скрипт для размещения массива объектов в трехмерной фигуре<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Всплывающая подсказка" width="250">  <br>
    <span data-ttu-id="257cc-165">**Сказок**</span><span class="sxs-lookup"><span data-stu-id="257cc-165">**Tooltip**</span></span><br>
    <span data-ttu-id="257cc-166">Пользовательский интерфейс заметки с гибкой системой привязки и сведениями, который можно использовать для создания меток для контроллеров движения и объектов<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Панель приложения" width="250"><br>
    <span data-ttu-id="257cc-168">**Панель приложения**</span><span class="sxs-lookup"><span data-stu-id="257cc-168">**App Bar**</span></span><br>
    <span data-ttu-id="257cc-169">Пользовательский интерфейс для активации ограничивающего прямоугольника вручную<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Указатели" width="250"><br>
    <span data-ttu-id="257cc-171">**Указател**</span><span class="sxs-lookup"><span data-stu-id="257cc-171">**Pointers**</span></span><br>
    <span data-ttu-id="257cc-172">Дополнительные сведения о различных типах указателей<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Удобное графическое представление" width="250"><br>
     <span data-ttu-id="257cc-174">**Удобное графическое представление**</span><span class="sxs-lookup"><span data-stu-id="257cc-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="257cc-175">Визуальное взаимодействие с учетом того, что повышает уверенность в прямом взаимодействии<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    <span data-ttu-id="257cc-177">**Slider**</span><span class="sxs-lookup"><span data-stu-id="257cc-177">**Slider**</span></span><br>
    <span data-ttu-id="257cc-178">Пользовательский интерфейс ползунка для настройки значений, поддерживающих взаимодействие с отслеживанием прямого отслеживания<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Стандартный шейдер МРТК" width="250"><br>
    <span data-ttu-id="257cc-180">**Стандартный шейдер МРТК**</span><span class="sxs-lookup"><span data-stu-id="257cc-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="257cc-181">Стандартный шейдер МРТК поддерживает различные элементы проектирования Fluent с производительностью<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Часер муфта" width="250"><br>
     <span data-ttu-id="257cc-183">**Часер муфта**</span><span class="sxs-lookup"><span data-stu-id="257cc-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="257cc-184">Демонстрирует использование решателя для присоединения объектов к рукой<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Отслеживание взгляда: Выбор целевого объекта" width="250"><br>
    <span data-ttu-id="257cc-186">**Отслеживание взгляда: Выбор целевого объекта**</span><span class="sxs-lookup"><span data-stu-id="257cc-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="257cc-187">Объедините глаза, голоса и руки, чтобы быстро и легко выбирать голограммы в сцене.<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Отслеживание взгляда: Навигация" width="250"><br>
    <span data-ttu-id="257cc-189">**Отслеживание взгляда: Месяца**</span><span class="sxs-lookup"><span data-stu-id="257cc-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="257cc-190">Узнайте, как выполнять автоматическую прокрутку текста или свободно изменять содержимое в зависимости от того, что вы ищете.<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Отслеживание взгляда: Тепловая схема" width="250"><br>
    <span data-ttu-id="257cc-192">**Отслеживание взгляда: Тепловая схема**</span><span class="sxs-lookup"><span data-stu-id="257cc-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="257cc-193">Примеры ведения журнала, загрузки и визуализации того, что пользователи просматривают в приложении<a/></span><span class="sxs-lookup"><span data-stu-id="257cc-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="257cc-194">Минимальные требования для МРТК v2</span><span class="sxs-lookup"><span data-stu-id="257cc-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="257cc-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="257cc-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="257cc-196">Microsoft Visual Studio 2017 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="257cc-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="257cc-197">Windows SDK 18362 +</span><span class="sxs-lookup"><span data-stu-id="257cc-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="257cc-198">Windows 10 1803 или более поздняя версия</span><span class="sxs-lookup"><span data-stu-id="257cc-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="257cc-199">Новые с МРТК v2</span><span class="sxs-lookup"><span data-stu-id="257cc-199">New with MRTK v2</span></span>
<span data-ttu-id="257cc-200">Мы хотим нагрузить наши обязательства на эти средства платформы.</span><span class="sxs-lookup"><span data-stu-id="257cc-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="257cc-201">На самом деле мы воспользуемся МРТК версии 2 для разработки нашего процесса входящих сообщений, таких как программа установки (OOBE) и приложение для обучения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="257cc-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="257cc-202">Вы также можете увидеть новые возможности HoloLens 2, впервые предоставляемые через МРТК, так как мы считаем, что это лучший способ разработки на нашей платформе.</span><span class="sxs-lookup"><span data-stu-id="257cc-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="257cc-203">Полк</span><span class="sxs-lookup"><span data-stu-id="257cc-203">Modular</span></span>
<span data-ttu-id="257cc-204">Мы создали модульный подход, так что вам не нужно брать каждый из них в свой проект.</span><span class="sxs-lookup"><span data-stu-id="257cc-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="257cc-205">Для этого есть несколько преимуществ.</span><span class="sxs-lookup"><span data-stu-id="257cc-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="257cc-206">Это позволяет уменьшить размер проекта, а также упростить управление.</span><span class="sxs-lookup"><span data-stu-id="257cc-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="257cc-207">Поверх этого, поскольку он построен с помощью объектов с поддержкой сценариев и является управляемым интерфейсом, можно также заменить компоненты, включенные в собственный, для поддержки других служб, систем и платформ.</span><span class="sxs-lookup"><span data-stu-id="257cc-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="257cc-208">Поддержка разных платформ</span><span class="sxs-lookup"><span data-stu-id="257cc-208">Cross-platform</span></span>
<span data-ttu-id="257cc-209">Говоря о других платформах, она поддерживает кросс-платформенную поддержку.</span><span class="sxs-lookup"><span data-stu-id="257cc-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="257cc-210">И хотя это и не означает, что каждая отдельная платформа поддерживается не всегда, мы сделали так, что ни один из программных средств не будет нарушен при переключении цели сборки на другие платформы.</span><span class="sxs-lookup"><span data-stu-id="257cc-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="257cc-211">Надежность и расширяемость с модульным проектированием устанавливаются с учетом хорошего пути для поддержки нескольких платформ, таких как Аркоре, ARKit и Опенвр.</span><span class="sxs-lookup"><span data-stu-id="257cc-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="257cc-212">Высокопроизводительных</span><span class="sxs-lookup"><span data-stu-id="257cc-212">Performant</span></span>
<span data-ttu-id="257cc-213">Работая с мобильными платформами, мы составили его с учетом производительности.</span><span class="sxs-lookup"><span data-stu-id="257cc-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="257cc-214">Это очень важно, и мы хотим убедиться, что средства не будут работать с вами.</span><span class="sxs-lookup"><span data-stu-id="257cc-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="257cc-215">См. также</span><span class="sxs-lookup"><span data-stu-id="257cc-215">See also</span></span>
* [<span data-ttu-id="257cc-216">Руководство по началу работы с МРТК</span><span class="sxs-lookup"><span data-stu-id="257cc-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="257cc-217">Домашняя страница документации по МРТК</span><span class="sxs-lookup"><span data-stu-id="257cc-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="257cc-218">Установка средств</span><span class="sxs-lookup"><span data-stu-id="257cc-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="257cc-219">Перенос из ХТК/МРТК в МРТК версии 2</span><span class="sxs-lookup"><span data-stu-id="257cc-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
