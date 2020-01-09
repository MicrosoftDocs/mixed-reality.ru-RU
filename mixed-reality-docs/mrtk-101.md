---
title: МРТК 101 — как использовать Unity набора средств Mixed Reality для базовых взаимодействий (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Как использовать Unity набора средств Mixed Reality для базовых взаимодействий (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, МРТК, набор средств для смешанной реальности, Windows Mixed Reality, проектирование, пример приложения, элементы управления
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623499"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="b059b-104">МРТК 101: как использовать Unity набора средств Mixed Reality для базовых взаимодействий (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span><span class="sxs-lookup"><span data-stu-id="b059b-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![мртк](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="b059b-106">Узнайте, как использовать МРТК для достижения некоторых наиболее часто используемых общих шаблонов взаимодействия в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b059b-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="b059b-107">Как имитировать входные взаимодействия в редакторе Unity?</span><span class="sxs-lookup"><span data-stu-id="b059b-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="b059b-108">Как взять и переместить объект?</span><span class="sxs-lookup"><span data-stu-id="b059b-108">How to grab and move an object?</span></span>
- <span data-ttu-id="b059b-109">Как изменить размер объекта?</span><span class="sxs-lookup"><span data-stu-id="b059b-109">How to resize an object?</span></span>
- <span data-ttu-id="b059b-110">Как переместить или повернуть объект с точностью?</span><span class="sxs-lookup"><span data-stu-id="b059b-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="b059b-111">Как сделать объект реакцией на входные события?</span><span class="sxs-lookup"><span data-stu-id="b059b-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="b059b-112">Как добавить визуальную обратную связь?</span><span class="sxs-lookup"><span data-stu-id="b059b-112">How to add visual feedback?</span></span>
- <span data-ttu-id="b059b-113">Как добавить отзыв о звуках?</span><span class="sxs-lookup"><span data-stu-id="b059b-113">How to add audio feedback?</span></span>
- <span data-ttu-id="b059b-114">Как использовать кнопку Prefabs в HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="b059b-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="b059b-115">Как сделать объект следующим?</span><span class="sxs-lookup"><span data-stu-id="b059b-115">How to make an object follow you?</span></span>
- <span data-ttu-id="b059b-116">Как сделать объект лицом к вам?</span><span class="sxs-lookup"><span data-stu-id="b059b-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="b059b-117">Как имитировать входные взаимодействия в редакторе Unity?</span><span class="sxs-lookup"><span data-stu-id="b059b-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="b059b-118">МРТК поддерживает имитацию входных данных в редакторе.</span><span class="sxs-lookup"><span data-stu-id="b059b-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="b059b-119">Просто запустите сцену, нажав кнопку воспроизведения Unity.</span><span class="sxs-lookup"><span data-stu-id="b059b-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="b059b-120">Используйте эти ключи для имитации входных данных.</span><span class="sxs-lookup"><span data-stu-id="b059b-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="b059b-121">Чтобы переместить камеру, нажмите клавиши W, A, S, D.</span><span class="sxs-lookup"><span data-stu-id="b059b-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="b059b-122">Удерживайте правую кнопку мыши и наведите указатель мыши на нужное место.</span><span class="sxs-lookup"><span data-stu-id="b059b-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="b059b-123">Чтобы отобразить смоделированные руки, нажмите клавишу пробела (справа) или клавишу SHIFT слева (слева), чтобы имитировать имитацию руки в представлении, нажмите клавишу «T» или «Y», чтобы повернуть смоделированные руки, нажмите клавишу Q или E (горизонтально)/R или F (вертикально)</span><span class="sxs-lookup"><span data-stu-id="b059b-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="b059b-124">Дополнительные сведения о моделировании ввода см. в документации по МРТК.</span><span class="sxs-lookup"><span data-stu-id="b059b-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="b059b-125">Как взять и переместить объект?</span><span class="sxs-lookup"><span data-stu-id="b059b-125">How to grab and move an object?</span></span>
<span data-ttu-id="b059b-126">Чтобы сделать объект неуправляемым, назначьте следующие два скрипта: ManipulationHandler.cs и Неаринтерактионграббабле. cs (для прямого захвата с помощью входных данных отслеживания) Манипулатионхандлер поддерживает почти и далеко взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="b059b-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="b059b-127">Вы можете захватить и переместить объект с использованием входных данных отслеживания с помощью HoloLens 2 (NEAR), руки (FAR), подвижного контроллера движения (FAR), курсора HoloLens, & воздушного касания (FAR).</span><span class="sxs-lookup"><span data-stu-id="b059b-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="b059b-128">Как изменить размер объекта?</span><span class="sxs-lookup"><span data-stu-id="b059b-128">How to resize an object?</span></span>
<span data-ttu-id="b059b-129">ManipulationHandler.cs поддерживает двустороннюю масштабирование и вращение.</span><span class="sxs-lookup"><span data-stu-id="b059b-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="b059b-130">Это работает с различными типами входных данных, такими как ввод с клавиатуры HoloLens 2, элемент управления "аналитика" HoloLens 1, ввод жеста, а также входные данные контроллера движения в Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b059b-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="b059b-131">Дополнительные сведения о обработчике манипуляций см. в документации по МРТК.</span><span class="sxs-lookup"><span data-stu-id="b059b-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="b059b-132">Как переместить или повернуть объект с точностью?</span><span class="sxs-lookup"><span data-stu-id="b059b-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="b059b-133">Назначьте BoundingBox.cs объекту для использования ограничивающего прямоугольника, который является интерфейсом для масштабирования и поворота объекта.</span><span class="sxs-lookup"><span data-stu-id="b059b-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="b059b-134">По умолчанию он показывает синие маркеры и провода в стиле HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="b059b-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="b059b-135">Чтобы использовать в стиле HoloLens 2 анимированные маркеры на основе расположения, необходимо назначить Prefabs и материалы.</span><span class="sxs-lookup"><span data-stu-id="b059b-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="b059b-136">Сведения о конфигурации см. в [документации по ограничивающему прямоугольнику](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) и в сцене баундингбоксексамплес. Unity.</span><span class="sxs-lookup"><span data-stu-id="b059b-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="b059b-137">Дополнительные сведения о ограничивающем прямоугольнике в документации по МРТК</span><span class="sxs-lookup"><span data-stu-id="b059b-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="b059b-138">Как сделать объект реакцией на входные события?</span><span class="sxs-lookup"><span data-stu-id="b059b-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="b059b-139">Назначьте PointerHandler.cs объекту.</span><span class="sxs-lookup"><span data-stu-id="b059b-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="b059b-140">В Инспекторе вы сможете использовать события Онпоинтердовн (), Онпоинтеруп (), Онпоинтеркликкед (), Онпоинтердрагжед () для использования этих событий в скрипте, реализовать Имикседреалитипоинтерхандлер.</span><span class="sxs-lookup"><span data-stu-id="b059b-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="b059b-141">Дополнительные сведения о системе ввода в документации по МРТК</span><span class="sxs-lookup"><span data-stu-id="b059b-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="b059b-142">Как добавить визуальную обратную связь?</span><span class="sxs-lookup"><span data-stu-id="b059b-142">How to add visual feedback?</span></span>
<span data-ttu-id="b059b-143">Назначьте Interactable.cs объекту.</span><span class="sxs-lookup"><span data-stu-id="b059b-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="b059b-144">В инспекторе создайте новую тему.</span><span class="sxs-lookup"><span data-stu-id="b059b-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="b059b-145">С помощью профилей темы, доступных для взаимодействия, можно легко добавить визуальную обратную связь во все доступные состояния взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="b059b-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="b059b-146">Взаимодействие предоставляет различные типы тем, включая тему шейдера, которая позволяет управлять свойствами шейдера для каждого состояния взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="b059b-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="b059b-147">Дополнительные сведения о взаимодействии в документации по МРТК</span><span class="sxs-lookup"><span data-stu-id="b059b-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="b059b-148">Другим важным стандартным блоком для визуальной обратной связи является стандартный шейдер МРТК.</span><span class="sxs-lookup"><span data-stu-id="b059b-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="b059b-149">С помощью шейдера МРТК Standard можно легко добавлять визуальные эффекты обратной связи, такие как навести указатель на освещение и освещение.</span><span class="sxs-lookup"><span data-stu-id="b059b-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="b059b-150">Так как шейдер МРТК Standard выполняет значительно меньше вычислений, чем стандартный шейдер Unity, вы можете создать среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="b059b-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="b059b-151">Создайте новый материал и выберите шейдер "Mixed Reality Toolkit > Standard".</span><span class="sxs-lookup"><span data-stu-id="b059b-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="b059b-152">Или можно выбрать один из существующих материалов, использующих шейдер МРТК Standard.</span><span class="sxs-lookup"><span data-stu-id="b059b-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="b059b-153">Дополнительные сведения о шейдере МРТК Standard см. в документации по МРТК.</span><span class="sxs-lookup"><span data-stu-id="b059b-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="b059b-154">Как добавить отзыв о звуках?</span><span class="sxs-lookup"><span data-stu-id="b059b-154">How to add audio feedback?</span></span>
<span data-ttu-id="b059b-155">Добавьте Аудиосаурце в объект.</span><span class="sxs-lookup"><span data-stu-id="b059b-155">Add AudioSource to an object.</span></span> <span data-ttu-id="b059b-156">Затем в скриптах, которые предоставляют входные события (например, Interactable.cs или PointerHandler.cs), назначьте объект событию и выберите Аудиосаурце. Плайонешот ().</span><span class="sxs-lookup"><span data-stu-id="b059b-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="b059b-157">Вы можете использовать звуковые клипы или выбрать один из звуковых ресурсов МРТК.</span><span class="sxs-lookup"><span data-stu-id="b059b-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="b059b-158">Как использовать кнопку Prefabs в HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="b059b-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="b059b-159">МРТК предоставляет различные типы кнопок в стиле оболочки HoloLens (ОС).</span><span class="sxs-lookup"><span data-stu-id="b059b-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="b059b-160">Он предоставляет сложные визуальные отзывы, такие как освещение, сжатие и эффекты Ripple на поверхности кнопки.</span><span class="sxs-lookup"><span data-stu-id="b059b-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="b059b-161">Просто перетащите одну из prefab кнопок в стиле HoloLens 2 в сцену.</span><span class="sxs-lookup"><span data-stu-id="b059b-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="b059b-162">Prefab использует Interactable.cs, представленный выше.</span><span class="sxs-lookup"><span data-stu-id="b059b-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="b059b-163">Можно использовать предоставляемые события, такие как onclick (), в взаимодействии, чтобы активировать действия.</span><span class="sxs-lookup"><span data-stu-id="b059b-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="b059b-164">Дополнительные сведения о кнопке Prefabs в документации МРТК</span><span class="sxs-lookup"><span data-stu-id="b059b-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="b059b-165">Как сделать объект следующим?</span><span class="sxs-lookup"><span data-stu-id="b059b-165">How to make an object follow you?</span></span>
<span data-ttu-id="b059b-166">Назначение скрипта RadialView.cs объекту.</span><span class="sxs-lookup"><span data-stu-id="b059b-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="b059b-167">Она является частью серии сценариев поиска решений, которая позволяет создавать различные типы позиционирования объектов в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="b059b-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="b059b-168">SolverHandler.cs будет автоматически добавлен.</span><span class="sxs-lookup"><span data-stu-id="b059b-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="b059b-169">Ниже приведен пример настройки Радиалвиев для выполнения тега "ленивой" функции, как и в меню "Пуск" в оболочке HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b059b-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="b059b-170">Вы можете указать минимальное и максимальное расстояние, а также минимальные и максимальные уровни представления.</span><span class="sxs-lookup"><span data-stu-id="b059b-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="b059b-171">В приведенном ниже примере показано размещение объекта между 0,4 m и 0,8 m диапазоном в 15 °.</span><span class="sxs-lookup"><span data-stu-id="b059b-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="b059b-172">Настройте значения времени Лерп, чтобы обеспечить быстрое или медленное выполнение позиционированного обновления.</span><span class="sxs-lookup"><span data-stu-id="b059b-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="b059b-173">Дополнительные сведения об поисковых решениях см. в документации по МРТК.</span><span class="sxs-lookup"><span data-stu-id="b059b-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="b059b-174">Как сделать объект лицом к вам?</span><span class="sxs-lookup"><span data-stu-id="b059b-174">How to make an object face you?</span></span>
<span data-ttu-id="b059b-175">Назначение скрипта Billboard.cs объекту.</span><span class="sxs-lookup"><span data-stu-id="b059b-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="b059b-176">Она всегда будет лицом, независимо от вашей должности.</span><span class="sxs-lookup"><span data-stu-id="b059b-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="b059b-177">Можно указать параметр оси сведения.</span><span class="sxs-lookup"><span data-stu-id="b059b-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="b059b-178">Готовы к созданию великолепных возможностей для смешанной реальности?</span><span class="sxs-lookup"><span data-stu-id="b059b-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="b059b-179">Посетите страницы ниже и Узнайте больше о МРТК и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b059b-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="b059b-180">Об авторе</span><span class="sxs-lookup"><span data-stu-id="b059b-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="b059b-181"><b>Донг Йоон</b></span><span class="sxs-lookup"><span data-stu-id="b059b-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="b059b-182">@Microsoft конструктора UX</span><span class="sxs-lookup"><span data-stu-id="b059b-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="b059b-183">См. также статью</span><span class="sxs-lookup"><span data-stu-id="b059b-183">See also</span></span>

* [<span data-ttu-id="b059b-184">Набор средств для смешанной реальности — Unity (МРТК) GitHub</span><span class="sxs-lookup"><span data-stu-id="b059b-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="b059b-185">Портал документации по МРТК</span><span class="sxs-lookup"><span data-stu-id="b059b-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="b059b-186">начало работы с МРТК</span><span class="sxs-lookup"><span data-stu-id="b059b-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="b059b-187">Руководство по переносу Холотулкит в МРТК</span><span class="sxs-lookup"><span data-stu-id="b059b-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
