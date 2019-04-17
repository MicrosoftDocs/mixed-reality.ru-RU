---
title: Взглядом, жесты и контроллеры движения в DirectX
description: Объединение информации, поступающей от взглядом, жесты и контроллеры движения, вы можете включить пользователь не загрузит голограмма в вашем приложении.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: взглядом, жесты, движения контроллеры, directx, входные данные, голограммы
ms.openlocfilehash: 7cee3d3d7fbcd903eae0376e205034b9cc4ead3b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605093"
---
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a><span data-ttu-id="aa611-104">Взглядом, жесты и контроллеры движения в DirectX</span><span class="sxs-lookup"><span data-stu-id="aa611-104">Gaze, gestures, and motion controllers in DirectX</span></span>

<span data-ttu-id="aa611-105">Если вы собираетесь создать непосредственно на базе платформы, необходимо обрабатывать информации, поступающей от пользователя — например, где пользователь смотрит через [головного взглядом](gaze.md) и что пользователь выбрал с [жесты](gestures.md) или [движения контроллеров](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="aa611-105">If you're going to build directly on top of the platform, you will have to handle input coming from the user - such as where the user is looking via [head gaze](gaze.md) and what the user has selected with [gestures](gestures.md) or [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="aa611-106">Объединение этих форм ввода данных, вы можете включить пользователь не загрузит [голограмма](hologram.md) в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="aa611-106">Combining these forms of input, you can enable a user to place a [hologram](hologram.md) in your app.</span></span> <span data-ttu-id="aa611-107">[Шаблон holographic приложения](creating-a-holographic-directx-project.md) содержит пример прост в использовании.</span><span class="sxs-lookup"><span data-stu-id="aa611-107">The [holographic app template](creating-a-holographic-directx-project.md) has an easy to use example.</span></span>

>[!NOTE]
><span data-ttu-id="aa611-108">Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="aa611-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="aa611-109">Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.</span><span class="sxs-lookup"><span data-stu-id="aa611-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="gaze-input"></a><span data-ttu-id="aa611-110">Ввод взглядом</span><span class="sxs-lookup"><span data-stu-id="aa611-110">Gaze input</span></span>

<span data-ttu-id="aa611-111">Для доступа к пользователя [головного взглядом](gaze.md), использовании [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) типа.</span><span class="sxs-lookup"><span data-stu-id="aa611-111">To access the user's [head gaze](gaze.md), you use the [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) type.</span></span> <span data-ttu-id="aa611-112">Шаблон holographic приложения включает в себя базовый код для понимания взглядом.</span><span class="sxs-lookup"><span data-stu-id="aa611-112">The holographic app template includes basic code for understanding gaze.</span></span> <span data-ttu-id="aa611-113">Этот код предоставляет вектор, указывающий вперед между пользователя глаза, принимая во внимание устройства положение и ориентацию в заданной [системы координат](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="aa611-113">This code provides a vector pointing forward from between the user's eyes, taking into account the device's position and orientation in a given [coordinate system](coordinate-systems-in-directx.md).</span></span>




```cpp
void SpinningCubeRenderer::PositionHologram(SpatialPointerPose^ pointerPose)
{
    if (pointerPose != nullptr)
    {
        // Get the gaze direction relative to the given coordinate system.
        const float3 headPosition    = pointerPose->Head->Position;
        const float3 headDirection   = pointerPose->Head->ForwardDirection;
    
        // The hologram is positioned two meters along the user's gaze direction.
        static const float distanceFromUser = 2.0f; // meters
        const float3 gazeAtTwoMeters        = headPosition + (distanceFromUser * headDirection);
    
        // This will be used as the translation component of the hologram's
        // model transform.
        SetPosition(gazeAtTwoMeters);
    }
}
```

<span data-ttu-id="aa611-114">Возможно, вам вопрос о: «Но где система координат взять?»</span><span class="sxs-lookup"><span data-stu-id="aa611-114">You may find yourself asking: "But where does the coordinate system come from?"</span></span>

<span data-ttu-id="aa611-115">Давайте ответить на этот вопрос.</span><span class="sxs-lookup"><span data-stu-id="aa611-115">Let's answer that question.</span></span> <span data-ttu-id="aa611-116">В нашем AppMain **обновления** функции, мы обрабатываемых пространственных события ввода его приобретения для наших StationaryFrameOfReference относительно координат.</span><span class="sxs-lookup"><span data-stu-id="aa611-116">In our AppMain's **Update** function, we processed a spatial input event by acquiring it relative to the coordinate system for our StationaryFrameOfReference.</span></span> <span data-ttu-id="aa611-117">Помните, что StationaryFrameOfReference создан при настройке [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), и система координат была получена в начале [обновления](rendering-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="aa611-117">Recall that the StationaryFrameOfReference was created when we set up the [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), and the coordinate system was acquired at the start of [Update](rendering-in-directx.md).</span></span>




```cpp
// Check for new input state since the last frame.
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
if (pointerState != nullptr)
{
    // When a Pressed gesture is detected, the sample hologram will be repositioned
    // two meters in front of the user.
    m_spinningCubeRenderer->PositionHologram(
        pointerState->TryGetPointerPose(currentCoordinateSystem)
        );
}
```

<span data-ttu-id="aa611-118">Обратите внимание на то, что данные привязан к указатель состояние какой-либо.</span><span class="sxs-lookup"><span data-stu-id="aa611-118">Note that the data is tied to a pointer state of some kind.</span></span> <span data-ttu-id="aa611-119">Мы получаем от пространственных входного события.</span><span class="sxs-lookup"><span data-stu-id="aa611-119">We get this from a spatial input event.</span></span> <span data-ttu-id="aa611-120">Объект данных события включают в системе координат, позволяющий всегда можно связать направление взглядом во время события независимо от пространственных систему координат, вам потребуется.</span><span class="sxs-lookup"><span data-stu-id="aa611-120">The event data object includes a coordinate system, so that you can always relate the gaze direction at the time of the event to whatever spatial coordinate system you need.</span></span> <span data-ttu-id="aa611-121">На самом деле это необходимо сделать для получения поза указатель.</span><span class="sxs-lookup"><span data-stu-id="aa611-121">In fact, you must do so in order to get the pointer pose.</span></span>

> [!NOTE]
> <span data-ttu-id="aa611-122">Дополнительные рекомендации, относящиеся к HoloLens 2 [ожидается в ближайшее время](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="aa611-122">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gesture-and-motion-controller-input"></a><span data-ttu-id="aa611-123">Жест движения контроллер и входных данных</span><span class="sxs-lookup"><span data-stu-id="aa611-123">Gesture and motion controller input</span></span>

<span data-ttu-id="aa611-124">В Windows Mixed Reality, обе стороны [жесты](gestures.md) и [движения контроллеров](motion-controllers.md) обрабатываются с помощью того же пространственных входа API-интерфейсы, в [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) пространство имен.</span><span class="sxs-lookup"><span data-stu-id="aa611-124">In Windows Mixed Reality, both hand [gestures](gestures.md) and [motion controllers](motion-controllers.md) are handled through the same spatial input APIs, found in the [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace.</span></span> <span data-ttu-id="aa611-125">Это позволяет с легкостью выполнить общие действия, такие как **выберите** нажимает так же, как в руки и контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="aa611-125">This enables you to easily handle common actions like **Select** presses the same way across both hands and motion controllers.</span></span>

<span data-ttu-id="aa611-126">Существует два уровня API-интерфейса можно ориентироваться при обработке жестов или движения контроллеров в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="aa611-126">There are two levels of API you can target when handling gestures or motion controllers in mixed reality:</span></span>
* <span data-ttu-id="aa611-127">[Взаимодействие](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) и [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), доступный с помощью [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span><span class="sxs-lookup"><span data-stu-id="aa611-127">[Interactions](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) and [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), accessed using a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span></span>
* <span data-ttu-id="aa611-128">[Составные жесты](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), хранения, обработки, навигации), доступный с помощью [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span><span class="sxs-lookup"><span data-stu-id="aa611-128">[Composite gestures](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), Hold, Manipulation, Navigation), accessed using a [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span></span>

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a><span data-ttu-id="aa611-129">Выберите/меню/коммерческих тайн/сенсорной панели/джойстик взаимодействия: SpatialInteractionManager</span><span class="sxs-lookup"><span data-stu-id="aa611-129">Select/Menu/Grasp/Touchpad/Thumbstick interactions: SpatialInteractionManager</span></span>

<span data-ttu-id="aa611-130">Чтобы обнаружить нажатие низкого уровня, выпусках и обновлениях в руки и устройств ввода в Windows Mixed Reality, запустите в [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="aa611-130">To detect low-level presses, releases and updates across hands and input devices in Windows Mixed Reality, you start from a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span></span> <span data-ttu-id="aa611-131">SpatialInteractionManager имеет событие, которое информирует приложения при наличии или движения контроллер обнаружил входных данных.</span><span class="sxs-lookup"><span data-stu-id="aa611-131">The SpatialInteractionManager has an event that informs the app when a hand or motion controller has detected input.</span></span>

<span data-ttu-id="aa611-132">Существуют три основные вида SpatialInteractionSource, каждый из которых представлен по другому значению SpatialInteractionSourceKind:</span><span class="sxs-lookup"><span data-stu-id="aa611-132">There are three key kinds of SpatialInteractionSource, each represented by a different SpatialInteractionSourceKind value:</span></span>
* <span data-ttu-id="aa611-133">**Рука** представляет обнаруженных руку пользователя.</span><span class="sxs-lookup"><span data-stu-id="aa611-133">**Hand** represents a user's detected hand.</span></span> <span data-ttu-id="aa611-134">Рука источники доступны только для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aa611-134">Hand sources are available only on HoloLens.</span></span>
* <span data-ttu-id="aa611-135">**Контроллер** представляет контроллер парных движения.</span><span class="sxs-lookup"><span data-stu-id="aa611-135">**Controller** represents a paired motion controller.</span></span> <span data-ttu-id="aa611-136">Контроллеры движения может предложить широкий набор возможностей, например: Выберите триггеры, кнопки меню, кнопки коммерческих тайн, сенсорные панели и thumbsticks.</span><span class="sxs-lookup"><span data-stu-id="aa611-136">Motion controllers can offer a variety of capabilities, for example: Select triggers, Menu buttons, Grasp buttons, touchpads and thumbsticks.</span></span>
* <span data-ttu-id="aa611-137">**Голосовые** представляет голос пользователя, говоря система обнаружила ключевые слова.</span><span class="sxs-lookup"><span data-stu-id="aa611-137">**Voice** represents the user's voice speaking system-detected keywords.</span></span> <span data-ttu-id="aa611-138">Это будет внедрить выберите press и выпуска всякий раз, когда пользователь скажет: «Выбрать».</span><span class="sxs-lookup"><span data-stu-id="aa611-138">This will inject a Select press and release whenever the user says "Select".</span></span>

<span data-ttu-id="aa611-139">Чтобы обнаружить нажатие во всех этих источниках взаимодействия, можно обрабатывать события SourcePressed SpatialInteractionManager в SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="aa611-139">To detect presses across any of these interaction sources, you can handle the SourcePressed event on SpatialInteractionManager in SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

<span data-ttu-id="aa611-140">Это событие нажатия отправляется в приложение асинхронно.</span><span class="sxs-lookup"><span data-stu-id="aa611-140">This pressed event is sent to your app asynchronously.</span></span> <span data-ttu-id="aa611-141">Ваше приложение или игровое ядро может потребоваться выполнить некоторые задачи обработки прямо сейчас или требуется поставить данные событий в подпрограмму обработки входных данных.</span><span class="sxs-lookup"><span data-stu-id="aa611-141">Your app or game engine may want to perform some processing right away or you may want to queue up the event data in your input processing routine.</span></span>

<span data-ttu-id="aa611-142">В шаблоне есть вспомогательный класс, чтобы приступить к работе.</span><span class="sxs-lookup"><span data-stu-id="aa611-142">The template includes a helper class to get you started.</span></span> <span data-ttu-id="aa611-143">Этот шаблон сложнее, чем обработку для простоты разработки.</span><span class="sxs-lookup"><span data-stu-id="aa611-143">This template forgoes any processing for simplicity of design.</span></span> <span data-ttu-id="aa611-144">Вспомогательный класс следит за ли, что один или несколько **Pressed** события, которые возникли с момента последнего **обновления** вызова.</span><span class="sxs-lookup"><span data-stu-id="aa611-144">The helper class keeps track of whether one or more **Pressed** events occurred since the last **Update** call.</span></span> <span data-ttu-id="aa611-145">Из SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="aa611-145">From SpatialInputHandler.cpp:</span></span>




```cpp
void SpatialInputHandler::OnSourcePressed(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    m_sourceState = args->State;
    
    //
    // TODO: In your app or game engine, rewrite this method to queue
    //       input events in your input class or event handler.
    //
}
```

<span data-ttu-id="aa611-146">Если так, он возвращает [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) самые последние события ввода, во время следующего обновления.</span><span class="sxs-lookup"><span data-stu-id="aa611-146">If so, it returns the [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) for the most recent input event during the next Update.</span></span> <span data-ttu-id="aa611-147">Из SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="aa611-147">From SpatialInputHandler.cpp:</span></span>




```cpp
// Checks if the user performed an input gesture since the last call to this method.
// Allows the main update loop to check for asynchronous changes to the user
// input state.
SpatialInteractionSourceState^ SpatialInputHandler::CheckForInput()
{
    SpatialInteractionSourceState^ sourceState = m_sourceState;
    m_sourceState = nullptr;
    return sourceState;
}
```

<span data-ttu-id="aa611-148">Обратите внимание, что приведенный выше код будет рассматривать все нажимает так же ли пользователь выполняет первичную **выберите** press, ни вторичными **меню** или **осознавать** клавишу.</span><span class="sxs-lookup"><span data-stu-id="aa611-148">Note that the code above will treat all presses the same way, whether the user is performing a primary **Select** press or a secondary **Menu** or **Grasp** press.</span></span> <span data-ttu-id="aa611-149">**Выберите** press представляет собой основной форму взаимодействия поддерживаются в разных руки, контроллеры и голоса, активации, либо вручную, выполнение жест касания, контроллер движения с помощью его основного триггера или кнопки нажата, путем перемещения или пользователя Голосовая связь говорим: «Select».</span><span class="sxs-lookup"><span data-stu-id="aa611-149">The **Select** press is a primary form of interaction supported across hands, motion controllers and voice, triggered either by a hand performing an air-tap, a motion controller with its primary trigger/button pressed, or the user's voice saying "Select".</span></span> <span data-ttu-id="aa611-150">Выберите нажатия представляют намерение пользователя активировать голограмма, который их используете.</span><span class="sxs-lookup"><span data-stu-id="aa611-150">Select presses represent the user's intention to activate the hologram they are targeting.</span></span>

<span data-ttu-id="aa611-151">Происходит вопросов типа press, мы будем изменять обработчик событий SpatialInteractionManager::SourceUpdated.</span><span class="sxs-lookup"><span data-stu-id="aa611-151">To reason about which kind of press is occurring, we will modify the SpatialInteractionManager::SourceUpdated event handler.</span></span> <span data-ttu-id="aa611-152">Наш код обнаружит нажатия коммерческих тайн (при наличии) и использовать их для изменения положения куба.</span><span class="sxs-lookup"><span data-stu-id="aa611-152">Our code will detect Grasp presses (where available) and use them to reposition the cube.</span></span> <span data-ttu-id="aa611-153">Если коммерческих тайн недоступен, мы используем выберите нажатия.</span><span class="sxs-lookup"><span data-stu-id="aa611-153">If Grasp is not available, we will use Select presses instead.</span></span>

<span data-ttu-id="aa611-154">Добавьте следующие объявления закрытого члена SpatialInputHandler.h:</span><span class="sxs-lookup"><span data-stu-id="aa611-154">Add the following private member declarations to SpatialInputHandler.h:</span></span> 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

<span data-ttu-id="aa611-155">Откройте SpatialInputHandler.cpp.</span><span class="sxs-lookup"><span data-stu-id="aa611-155">Open SpatialInputHandler.cpp.</span></span> <span data-ttu-id="aa611-156">Добавьте следующую регистрацию событий в конструктор:</span><span class="sxs-lookup"><span data-stu-id="aa611-156">Add the following event registration to the constructor:</span></span> 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

<span data-ttu-id="aa611-157">Это код обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="aa611-157">This is the event handler code.</span></span> <span data-ttu-id="aa611-158">Если возникают проблемы приступим источника входных данных, поза указатель будет сохранена для следующего цикла обновления.</span><span class="sxs-lookup"><span data-stu-id="aa611-158">If the input source is experiencing a Grasp, the pointer pose will be stored for the next update loop.</span></span> <span data-ttu-id="aa611-159">В противном случае он будет проверять наличие нажатие выберите вместо этого.</span><span class="sxs-lookup"><span data-stu-id="aa611-159">Otherwise, it will check for a Select press instead.</span></span> <span data-ttu-id="aa611-160">Из SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="aa611-160">From SpatialInputHandler.cpp:</span></span>




```cpp
void SpatialInputHandler::OnSourceUpdated(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    if (args->State->Source->IsGraspSupported)
    {
        if (args->State->IsGrasped)
        {
            m_sourceState = args->State;
        }
    }
    else
    {
        if (args->State->IsSelectPressed)
        {
            m_sourceState = args->State;
        }
    }
}
```

<span data-ttu-id="aa611-161">Убедитесь в том, что отменить регистрацию обработчика событий в деструкторе.</span><span class="sxs-lookup"><span data-stu-id="aa611-161">Make sure to unregister the event handler in the destructor.</span></span> <span data-ttu-id="aa611-162">Из SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="aa611-162">From SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

<span data-ttu-id="aa611-163">Повторная компиляция и затем повторно развернуть.</span><span class="sxs-lookup"><span data-stu-id="aa611-163">Recompile, and then redeploy.</span></span> <span data-ttu-id="aa611-164">Проект шаблона должна появиться возможность распознавать взаимодействия может воспользоваться для изменения положения вращающегося куба.</span><span class="sxs-lookup"><span data-stu-id="aa611-164">Your template project should now be able to recognize Grasp interactions to reposition the spinning cube.</span></span>

<span data-ttu-id="aa611-165">Этот API SpatialInteractionSource поддерживает контроллеры с широкий спектр возможностей.</span><span class="sxs-lookup"><span data-stu-id="aa611-165">The SpatialInteractionSource API supports controllers with a wide range of capabilities.</span></span> <span data-ttu-id="aa611-166">В примере, показанном выше мы проверяем поддержке коммерческих тайн перед попыткой его использования.</span><span class="sxs-lookup"><span data-stu-id="aa611-166">In the example shown above, we check to see if Grasp is supported before trying to use it.</span></span> <span data-ttu-id="aa611-167">SpatialInteractionSource поддерживает следующие дополнительные возможности Помимо общих **выберите** нажмите:</span><span class="sxs-lookup"><span data-stu-id="aa611-167">The SpatialInteractionSource supports the following optional features beyond the common **Select** press:</span></span>
* <span data-ttu-id="aa611-168">**Кнопка меню:** Проверка поддержки путем проверки свойства IsMenuSupported.</span><span class="sxs-lookup"><span data-stu-id="aa611-168">**Menu button:** Check support by inspecting the IsMenuSupported property.</span></span> <span data-ttu-id="aa611-169">Когда это возможно, проверьте [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) свойство, чтобы определить кнопку меню нажата.</span><span class="sxs-lookup"><span data-stu-id="aa611-169">When supported, check the [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if the menu button is pressed.</span></span>
* <span data-ttu-id="aa611-170">**Кнопка может воспользоваться:** Проверка поддержки путем проверки свойства IsGraspSupported.</span><span class="sxs-lookup"><span data-stu-id="aa611-170">**Grasp button:** Check support by inspecting the IsGraspSupported property.</span></span> <span data-ttu-id="aa611-171">Когда это возможно, проверьте [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) свойство, чтобы узнать, включен ли может воспользоваться.</span><span class="sxs-lookup"><span data-stu-id="aa611-171">When supported, check the [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if grasp is activated.</span></span>

<span data-ttu-id="aa611-172">Для контроллеров SpatialInteractionSource имеет свойство контроллера с помощью дополнительных возможностей.</span><span class="sxs-lookup"><span data-stu-id="aa611-172">For controllers, the SpatialInteractionSource has a Controller property with additional capabilities.</span></span>
* <span data-ttu-id="aa611-173">**HasThumbstick:** Если значение равно true, контроллер может джойстик.</span><span class="sxs-lookup"><span data-stu-id="aa611-173">**HasThumbstick:** If true, the controller has a thumbstick.</span></span> <span data-ttu-id="aa611-174">Проверьте [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) свойство SpatialInteractionSourceState получения джойстик x и y значения (ThumbstickX и ThumbstickY), а также его нажаты (IsThumbstickPressed).</span><span class="sxs-lookup"><span data-stu-id="aa611-174">Inspect the [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) property of the SpatialInteractionSourceState to acquire the thumbstick x and y values (ThumbstickX and ThumbstickY), as well as its pressed state (IsThumbstickPressed).</span></span>
* <span data-ttu-id="aa611-175">**HasTouchpad:** Если значение равно true, контроллер может сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="aa611-175">**HasTouchpad:** If true, the controller has a touchpad.</span></span> <span data-ttu-id="aa611-176">Проверьте свойство ControllerProperties SpatialInteractionSourceState получения сенсорной панели x и y значений (TouchpadX и TouchpadY) и знать, если пользователь касается планшета (IsTouchpadTouched) и если они нажав сенсорной вниз () IsTouchpadPressed).</span><span class="sxs-lookup"><span data-stu-id="aa611-176">Inspect the ControllerProperties property of the SpatialInteractionSourceState to acquire the touchpad x and y values (TouchpadX and TouchpadY), and to know if the user is touching the pad (IsTouchpadTouched) and if they are pressing the touchpad down (IsTouchpadPressed).</span></span>
* <span data-ttu-id="aa611-177">**SimpleHapticsController:** Интерфейс API SimpleHapticsController для контроллера, позволяет исследовать возможности haptics контроллера, а также позволяет управлять обратной связи haptic.</span><span class="sxs-lookup"><span data-stu-id="aa611-177">**SimpleHapticsController:** The SimpleHapticsController API for the controller allows you to inspect the haptics capabilities of the controller, and it also allows you to control haptic feedback.</span></span>

<span data-ttu-id="aa611-178">Обратите внимание, что диапазон для сенсорной панели и джойстик от -1 до 1 для обеих осях (снизу вверх и слева направо).</span><span class="sxs-lookup"><span data-stu-id="aa611-178">Note that the range for touchpad and thumbstick from -1 to 1 for both axes (from bottom to top, and from left to right).</span></span> <span data-ttu-id="aa611-179">Диапазон для аналоговой триггера, к которому можно получить с помощью свойства SpatialInteractionSourceState::SelectPressedValue, имеет диапазон от 0 до 1.</span><span class="sxs-lookup"><span data-stu-id="aa611-179">The range for the analog trigger, which is accessed using the SpatialInteractionSourceState::SelectPressedValue property, has a range of 0 to 1.</span></span> <span data-ttu-id="aa611-180">Значение 1 соответствует с IsSelectPressed равен true; любое другое значение связано с IsSelectPressed равен false.</span><span class="sxs-lookup"><span data-stu-id="aa611-180">A value of 1 correlates with IsSelectPressed being equal to true; any other value correlates with IsSelectPressed being equal to false.</span></span>

<span data-ttu-id="aa611-181">Обратите внимание, что для руки и контроллер с помощью SpatialInteractionSourceState::Properties::TryGetLocation предоставит положение руки пользователя – это отличается от поза указателя, представляющий указывающего Рэй контроллера.</span><span class="sxs-lookup"><span data-stu-id="aa611-181">Note that for both a hand and a controller, using SpatialInteractionSourceState::Properties::TryGetLocation will provide the user's hand position - this is distinct from the pointer pose representing the controller's pointing ray.</span></span> <span data-ttu-id="aa611-182">Если требуется нарисовать что-нибудь в расположении вручную, используйте TryGetLocation.</span><span class="sxs-lookup"><span data-stu-id="aa611-182">If you want to draw something at the hand location, use TryGetLocation.</span></span> <span data-ttu-id="aa611-183">Если вы хотите raycast, начиная с контроллера, получите указывающего луча из TryGetInteractionSourcePose на SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="aa611-183">If you want to raycast from the tip of the controller, get the pointing ray from TryGetInteractionSourcePose on the SpatialPointerPose.</span></span>

<span data-ttu-id="aa611-184">Также можно использовать другие события на SpatialInteractionManager, такие как SourceDetected и SourceLost, для реагирования на руках введите, или оставьте поле представления устройства или при переходе в или из него позицию Готово (вытянутым указательным пальцем возникает с palm вперед), или когда движения контроллеры будут отключены / или пару непарный.</span><span class="sxs-lookup"><span data-stu-id="aa611-184">You can also use the other events on SpatialInteractionManager, such as SourceDetected and SourceLost, to react when hands enter or leave the device's view or when they move in or out of the ready position (index finger raised with palm forward), or when motion controllers are turned on/off or are paired/unpaired.</span></span>

### <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="aa611-185">Поза захвата для изменения и указывающего поза</span><span class="sxs-lookup"><span data-stu-id="aa611-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="aa611-186">Windows Mixed Reality поддерживает движения контроллеров в различных форм-факторов, дизайна каждый контроллер, отличающихся по отношению между положение руки пользователя и натуральный «переслать» направление этого приложения следует использовать для команды при подготовке к просмотру контроллер.</span><span class="sxs-lookup"><span data-stu-id="aa611-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="aa611-187">Чтобы лучше представить эти контроллеры, существует два вида создает изучаться для каждого источника взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="aa611-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>
* <span data-ttu-id="aa611-188">**Поза захвата для изменения**, представляющий расположение руку, обнаруживаемые HoloLens или palm, удерживая контроллером движения.</span><span class="sxs-lookup"><span data-stu-id="aa611-188">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="aa611-189">На иммерсивную, это поза лучше всего подходит для подготовки к просмотру **руку пользователя** или **объект содержится в руки пользователя**, например помехой или оружия.</span><span class="sxs-lookup"><span data-stu-id="aa611-189">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="aa611-190">**Возьмитесь за позиции**: Palm центроида при удержании контроллер, естественно, корректируется, влево или вправо, чтобы центрировать позиция в пределах захвата.</span><span class="sxs-lookup"><span data-stu-id="aa611-190">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="aa611-191">**Возьмитесь за правой оси в ориентации**: При открытии полностью свои силы для формирования позу плоских 5 палец, луч, является нормальным для вашей palm (вперед от левой palm назад от правой palm)</span><span class="sxs-lookup"><span data-stu-id="aa611-191">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="aa611-192">**Возьмитесь за ориентации на ось, направленная вперед**: При закрытии вашей руке частично (как будто держа контроллеру), луч, указывающий «forward» трубку, образованное пальцы отличных от бегунка.</span><span class="sxs-lookup"><span data-stu-id="aa611-192">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="aa611-193">**Возьмитесь за ориентации элемента вверх оси**: Ось вверх, право и прямого определения содержится в разрешении.</span><span class="sxs-lookup"><span data-stu-id="aa611-193">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="aa611-194">Можно получить доступ к поза захвата для изменения через [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span><span class="sxs-lookup"><span data-stu-id="aa611-194">You can access the grip pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span></span>
* <span data-ttu-id="aa611-195">**Поза указатель**, представляющий кончика контроллера, указывающего вперед.</span><span class="sxs-lookup"><span data-stu-id="aa611-195">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="aa611-196">Этот поза лучше всего подходит для raycast при **обращены пользовательского интерфейса** при отрисовке самой модели контроллера.</span><span class="sxs-lookup"><span data-stu-id="aa611-196">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="aa611-197">Можно получить доступ к поза указатель через [SpatialInteractionSourceState.Properties.TryGetLocation(...). SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) или [SpatialInteractionSourceState.TryGetPointerPose(...). TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span><span class="sxs-lookup"><span data-stu-id="aa611-197">You can access the pointer pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...).SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) or [SpatialInteractionSourceState.TryGetPointerPose(...).TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span></span>

### <a name="composite-gestures-spatialgesturerecognizer"></a><span data-ttu-id="aa611-198">Составные жесты: SpatialGestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="aa611-198">Composite gestures: SpatialGestureRecognizer</span></span>

<span data-ttu-id="aa611-199">Объект [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) интерпретирует взаимодействия с пользователем от руки, контроллеры движения и команда «Выбрать» на события поверхности пространственных жестов, какие пользователи target, с помощью их головной взглядом.</span><span class="sxs-lookup"><span data-stu-id="aa611-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interprets user interactions from hands, motion controllers, and the "Select" voice command to surface spatial gesture events, which users target using their head gaze.</span></span>

<span data-ttu-id="aa611-200">Пространственных жесты являются ключевых разновидностью входных данных для приложений Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="aa611-200">Spatial gestures are a key form of input for Windows Mixed Reality apps.</span></span> <span data-ttu-id="aa611-201">Маршрутизации взаимодействий из SpatialInteractionManager для SpatialGestureRecognizer голограмма приложений может обнаруживать события касания, удержание, манипуляции и навигации равномерно в руки, голоса и пространственных устройств ввода, без необходимости обрабатывать нажатия и освобождает вручную.</span><span class="sxs-lookup"><span data-stu-id="aa611-201">By routing interactions from the SpatialInteractionManager to a hologram's SpatialGestureRecognizer, apps can detect Tap, Hold, Manipulation, and Navigation events uniformly across hands, voice, and spatial input devices, without having to handle presses and releases manually.</span></span>

<span data-ttu-id="aa611-202">SpatialGestureRecognizer выполняет только минимальный устранения неоднозначности между набор жестов, которые можно запросить.</span><span class="sxs-lookup"><span data-stu-id="aa611-202">SpatialGestureRecognizer performs only the minimal disambiguation between the set of gestures that you request.</span></span> <span data-ttu-id="aa611-203">К примеру Если вы запрашивали только Tap, пользователь может удерживать пальцев, пока они любят и отвод по-прежнему будет выполняться.</span><span class="sxs-lookup"><span data-stu-id="aa611-203">For example, if you request just Tap, the user may hold their finger down as long as they like and a Tap will still occur.</span></span> <span data-ttu-id="aa611-204">При запросе коснитесь и хранения, после того как об одной секунды удерживая пальцев, жест переведет в удержание и Tap не будет происходить.</span><span class="sxs-lookup"><span data-stu-id="aa611-204">If you request both Tap and Hold, after about a second of holding down their finger, the gesture will promote to a Hold and a Tap will no longer occur.</span></span>

<span data-ttu-id="aa611-205">Чтобы использовать SpatialGestureRecognizer, обрабатывать SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) событий и захвата SpatialPointerPose предоставляются существует.</span><span class="sxs-lookup"><span data-stu-id="aa611-205">To use SpatialGestureRecognizer, handle the SpatialInteractionManager's [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) event and grab the SpatialPointerPose exposed there.</span></span> <span data-ttu-id="aa611-206">Используйте Рэй головной взглядом пользователя из этого поза для пересечения с голограммы и поверхности сетки в окружения пользователя, чтобы определить, что пользователь собирается для взаимодействия с.</span><span class="sxs-lookup"><span data-stu-id="aa611-206">Use the user's head gaze ray from this pose to intersect with the holograms and surface meshes in the user's surroundings, in order to determine what the user is intending to interact with.</span></span> <span data-ttu-id="aa611-207">Затем направлять SpatialInteraction в аргументах событий для целевой голограмма SpatialGestureRecognizer, с помощью его [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) метод.</span><span class="sxs-lookup"><span data-stu-id="aa611-207">Then, route the SpatialInteraction in the event arguments to the target hologram's SpatialGestureRecognizer, using its [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) method.</span></span> <span data-ttu-id="aa611-208">Запустится интерпретации, реализуемый в соответствии с [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) задать на этот распознаватель, во время создания - или с [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span><span class="sxs-lookup"><span data-stu-id="aa611-208">This starts interpreting that interaction according to the [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) set on that recognizer at creation time - or by [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span></span>

<span data-ttu-id="aa611-209">На HoloLens взаимодействия и жесты следует обычно являются их выбора целевой платформы из головного взглядом пользователя, а не при визуализации или напрямую взаимодействовать в расположении вручную.</span><span class="sxs-lookup"><span data-stu-id="aa611-209">On HoloLens, interactions and gestures should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="aa611-210">После запуска взаимодействия относительный движения вручную может использоваться для управления жест, как и в случае с жестом манипуляции или навигации.</span><span class="sxs-lookup"><span data-stu-id="aa611-210">Once an interaction has started, relative motions of the hand may be used to control the gesture, as with the Manipulation or Navigation gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa611-211">См. также</span><span class="sxs-lookup"><span data-stu-id="aa611-211">See also</span></span>
* [<span data-ttu-id="aa611-212">Взглядом</span><span class="sxs-lookup"><span data-stu-id="aa611-212">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="aa611-213">Жесты</span><span class="sxs-lookup"><span data-stu-id="aa611-213">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="aa611-214">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="aa611-214">Motion controllers</span></span>](motion-controllers.md)
