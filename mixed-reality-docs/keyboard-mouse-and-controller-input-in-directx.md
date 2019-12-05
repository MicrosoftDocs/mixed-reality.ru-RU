---
title: Ввод с клавиатуры, мыши и контроллера в DirectX
description: В этой статье объясняется, как создать приложение для Windows Mixed Reality, которое использует клавиатуру, мышь и игровые контроллеры.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, клавиатура, мышь, игровой контроллер, контроллер Xbox, HoloLens, Настольный компьютер, пошаговое руководство, пример кода
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835100"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="3bba0-104">Ввод с клавиатуры, мыши и контроллера в DirectX</span><span class="sxs-lookup"><span data-stu-id="3bba0-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="3bba0-105">Клавиатуры, мыши и игровые контроллеры могут быть полезными в качестве входных данных для устройств Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3bba0-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="3bba0-106">Клавиатуры и мыши Bluetooth поддерживаются в HoloLens для использования с отладкой приложения или в качестве альтернативного вида входных данных.</span><span class="sxs-lookup"><span data-stu-id="3bba0-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="3bba0-107">Windows Mixed Reality также поддерживает впечатляющие головные телефоны, подключенные к компьютерам, на которых были исторически мышь, клавиатуры и игровые контроллеры.</span><span class="sxs-lookup"><span data-stu-id="3bba0-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="3bba0-108">Чтобы использовать ввод с клавиатуры для HoloLens, свяжите клавиатуру Bluetooth с устройством или используйте виртуальный ввод через портал устройств Windows.</span><span class="sxs-lookup"><span data-stu-id="3bba0-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="3bba0-109">Чтобы использовать ввод с клавиатуры при людьмиии иммерсивного головной гарнитуры Windows Mixed Reality, присвойте фокус ввода смешанной реальности, поместив устройство или используя сочетание клавиш Windows + Y.</span><span class="sxs-lookup"><span data-stu-id="3bba0-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="3bba0-110">Помните, что приложения, предназначенные для HoloLens, должны предоставлять функциональные возможности без подключения к этим устройствам.</span><span class="sxs-lookup"><span data-stu-id="3bba0-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="3bba0-111">Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="3bba0-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="3bba0-112">Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="3bba0-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="3bba0-113">Подписка на события ввода CoreWindow</span><span class="sxs-lookup"><span data-stu-id="3bba0-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="3bba0-114">Ввод с клавиатуры</span><span class="sxs-lookup"><span data-stu-id="3bba0-114">Keyboard input</span></span>

<span data-ttu-id="3bba0-115">В шаблоне приложения Windows holographic мы включаем обработчик событий для ввода с клавиатуры точно так же, как любое другое приложение UWP.</span><span class="sxs-lookup"><span data-stu-id="3bba0-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="3bba0-116">Приложение использует входные данные клавиатуры так же, как и в Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3bba0-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="3bba0-117">Из Аппвиев. cpp:</span><span class="sxs-lookup"><span data-stu-id="3bba0-117">From AppView.cpp:</span></span>

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a><span data-ttu-id="3bba0-118">Виртуальный ввод с клавиатуры</span><span class="sxs-lookup"><span data-stu-id="3bba0-118">Virtual keyboard input</span></span>
<span data-ttu-id="3bba0-119">Для впечатляющих головок настольных компьютеров можно также поддерживать виртуальные клавиатуры, отображаемые Windows, в режиме погружения.</span><span class="sxs-lookup"><span data-stu-id="3bba0-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="3bba0-120">Для поддержки этой возможности приложение может реализовать **коретекстедитконтекст**.</span><span class="sxs-lookup"><span data-stu-id="3bba0-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="3bba0-121">Это позволяет Windows понять состояние собственных текстовых полей, отображаемых в приложении, поэтому виртуальная клавиатура может правильно участвовать в тексте.</span><span class="sxs-lookup"><span data-stu-id="3bba0-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="3bba0-122">Дополнительные сведения о реализации поддержки Коретекстедитконтекст см. в [примере коретекстедитконтекст](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="3bba0-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="3bba0-123">Ввод с помощью мыши</span><span class="sxs-lookup"><span data-stu-id="3bba0-123">Mouse Input</span></span>

<span data-ttu-id="3bba0-124">Вы также можете использовать ввод с помощью мыши, используя обработчики событий ввода UWP CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="3bba0-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="3bba0-125">Вот как можно изменить шаблон приложения Windows holographic для поддержки щелчков мыши так же, как нажатые жесты.</span><span class="sxs-lookup"><span data-stu-id="3bba0-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="3bba0-126">После внесения этого изменения щелкните мышью, когда людьми иммерсивное устройство гарнитуры изменит расположение Куба.</span><span class="sxs-lookup"><span data-stu-id="3bba0-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="3bba0-127">Обратите внимание, что приложения UWP также могут получать необработанные ТОЧЕЧные данные для мыши с помощью API [мауседевице](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) .</span><span class="sxs-lookup"><span data-stu-id="3bba0-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="3bba0-128">Начните с объявления нового обработчика Онпоинтерпрессед в Аппвиев. h:</span><span class="sxs-lookup"><span data-stu-id="3bba0-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="3bba0-129">В Аппвиев. cpp добавьте следующий код в Сетвиндов:</span><span class="sxs-lookup"><span data-stu-id="3bba0-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="3bba0-130">Затем установите это определение для Онпоинтерпрессед в нижней части файла:</span><span class="sxs-lookup"><span data-stu-id="3bba0-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

<span data-ttu-id="3bba0-131">Только что добавленный обработчик событий является транзитным классом шаблона Main.</span><span class="sxs-lookup"><span data-stu-id="3bba0-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="3bba0-132">Давайте изменим класс main для поддержки этого транзитного класса.</span><span class="sxs-lookup"><span data-stu-id="3bba0-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="3bba0-133">Добавьте это объявление общедоступного метода в заголовочный файл:</span><span class="sxs-lookup"><span data-stu-id="3bba0-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="3bba0-134">Вам потребуется также эта переменная члена Private:</span><span class="sxs-lookup"><span data-stu-id="3bba0-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="3bba0-135">Наконец, мы будем обновлять класс Main с помощью новой логики для поддержки щелчков мыши.</span><span class="sxs-lookup"><span data-stu-id="3bba0-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="3bba0-136">Начните с добавления этого обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="3bba0-136">Start by adding this event handler.</span></span> <span data-ttu-id="3bba0-137">Обязательно обновите имя класса:</span><span class="sxs-lookup"><span data-stu-id="3bba0-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="3bba0-138">Теперь в методе Update замените существующую логику для получения указателя a следующим:</span><span class="sxs-lookup"><span data-stu-id="3bba0-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="3bba0-139">Перекомпиляция и повторное развертывание.</span><span class="sxs-lookup"><span data-stu-id="3bba0-139">Recompile and redeploy.</span></span> <span data-ttu-id="3bba0-140">Обратите внимание, что щелчок мыши теперь перемещает куб в иммерсивное головной или HoloLens с подключенной мышью по Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="3bba0-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="3bba0-141">Поддержка игрового контроллера</span><span class="sxs-lookup"><span data-stu-id="3bba0-141">Game controller support</span></span>

<span data-ttu-id="3bba0-142">Игровые контроллеры могут быть увлекательным и удобным способом предоставления пользователям возможности контролировать иммерсивное взаимодействие с Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3bba0-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="3bba0-143">Первым шагом в добавлении поддержки игровых контроллеров в шаблон приложения Windows holographic является добавление следующих закрытых объявлений членов в класс Header для основного файла:</span><span class="sxs-lookup"><span data-stu-id="3bba0-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

<span data-ttu-id="3bba0-144">Инициализируйте события игрового планшета и все подключенные к нему игровые планшеты в конструкторе основного класса:</span><span class="sxs-lookup"><span data-stu-id="3bba0-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

<span data-ttu-id="3bba0-145">Добавьте эти обработчики событий в основной класс.</span><span class="sxs-lookup"><span data-stu-id="3bba0-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="3bba0-146">Обязательно обновите имя класса:</span><span class="sxs-lookup"><span data-stu-id="3bba0-146">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

<span data-ttu-id="3bba0-147">Наконец, обновите логику ввода, чтобы распознать изменения в состоянии контроллера.</span><span class="sxs-lookup"><span data-stu-id="3bba0-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="3bba0-148">Здесь мы используем ту же переменную m_pointerPressed, описанную в разделе выше, для добавления событий мыши.</span><span class="sxs-lookup"><span data-stu-id="3bba0-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="3bba0-149">Добавьте его в метод Update, непосредственно перед тем, как он проверяет наличие Спатиалпоинтерпосе:</span><span class="sxs-lookup"><span data-stu-id="3bba0-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="3bba0-150">Не забудьте отменить регистрацию событий при очистке основного класса:</span><span class="sxs-lookup"><span data-stu-id="3bba0-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

<span data-ttu-id="3bba0-151">Перекомпиляция и повторное развертывание.</span><span class="sxs-lookup"><span data-stu-id="3bba0-151">Recompile, and redeploy.</span></span> <span data-ttu-id="3bba0-152">Теперь можно присоединить или связать игровой контроллер и использовать его для перемещения вращающегося куба.</span><span class="sxs-lookup"><span data-stu-id="3bba0-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="3bba0-153">Важные рекомендации по вводу с клавиатуры и мыши</span><span class="sxs-lookup"><span data-stu-id="3bba0-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="3bba0-154">Существует ряд ключевых различий в том, как этот код можно использовать в Microsoft HoloLens, то есть на устройстве, который в основном используется для естественного ввода данных, и о том, что доступно на ПК с поддержкой Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3bba0-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="3bba0-155">Вы не можете полагаться на ввод с клавиатуры или с помощью мыши.</span><span class="sxs-lookup"><span data-stu-id="3bba0-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="3bba0-156">Все функции вашего приложения должны работать с помощью взгляда, жеста и речевого ввода.</span><span class="sxs-lookup"><span data-stu-id="3bba0-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="3bba0-157">При подключении клавиатуры Bluetooth может быть полезно включить ввод с клавиатуры для любого текста, который может запрашивать приложение.</span><span class="sxs-lookup"><span data-stu-id="3bba0-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="3bba0-158">Например, это может быть отличным дополнением для диктовки.</span><span class="sxs-lookup"><span data-stu-id="3bba0-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="3bba0-159">Когда дело доходит до разработки приложения, не полагайтесь на то, что (например,) трассе и мышь для поиска в игре.</span><span class="sxs-lookup"><span data-stu-id="3bba0-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="3bba0-160">HoloLens предназначен для пользователя, чтобы проанализировать комнату.</span><span class="sxs-lookup"><span data-stu-id="3bba0-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="3bba0-161">В этом случае пользователь управляет камерой напрямую.</span><span class="sxs-lookup"><span data-stu-id="3bba0-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="3bba0-162">Интерфейс для передачи камеры вокруг комнаты с элементами управления перемещением и просмотром не обеспечивает такой же возможности.</span><span class="sxs-lookup"><span data-stu-id="3bba0-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="3bba0-163">Ввод с клавиатуры может быть отличным способом управления аспектами отладки приложения или игрового модуля, особенно потому, что пользователю не потребуется использовать клавиатуру.</span><span class="sxs-lookup"><span data-stu-id="3bba0-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="3bba0-164">Подключение выполняется так же, как и при использовании API-интерфейсов событий CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="3bba0-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="3bba0-165">В этом сценарии вы можете реализовать способ настройки приложения для маршрутизации событий клавиатуры в режим "только входные данные" во время сеансов отладки.</span><span class="sxs-lookup"><span data-stu-id="3bba0-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="3bba0-166">Контроллеры Bluetooth также работают.</span><span class="sxs-lookup"><span data-stu-id="3bba0-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bba0-167">См. также</span><span class="sxs-lookup"><span data-stu-id="3bba0-167">See also</span></span>
* [<span data-ttu-id="3bba0-168">Аксессуары к оборудованию</span><span class="sxs-lookup"><span data-stu-id="3bba0-168">Hardware accessories</span></span>](hardware-accessories.md)
