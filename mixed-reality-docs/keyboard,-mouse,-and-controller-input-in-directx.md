---
title: Входные данные контроллера в DirectX, клавиатуры и мыши
description: Объясняется, как создать приложение для Windows Mixed Reality, использующий клавиатуры, мыши и игровые устройства управления.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, клавиатура, мышь, игровой контроллер, контроллер xbox, HoloLens, настольных компьютеров, пошаговое руководство, пример кода
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605086"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="3c453-104">Входные данные контроллера в DirectX, клавиатуры и мыши</span><span class="sxs-lookup"><span data-stu-id="3c453-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="3c453-105">Клавиатуры, мыши и игровые устройства управления может быть полезным форм ввода данных для устройств Windows смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="3c453-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="3c453-106">Bluetooth клавиатуры и мыши в поддерживаются HoloLens, для отладки приложения или как альтернативная форма входных данных.</span><span class="sxs-lookup"><span data-stu-id="3c453-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="3c453-107">Смешанная реальность Windows также поддерживает иммерсивную к ПК - где мыши, клавиатуры и игровых устройств управления традиционно были норма.</span><span class="sxs-lookup"><span data-stu-id="3c453-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="3c453-108">Чтобы использовать ввод с клавиатуры для HoloLens, пары клавиатуры Bluetooth для устройства или виртуальный вход через Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="3c453-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="3c453-109">Чтобы использовать ввод с клавиатуры, то иммерсивных гарнитуры смешанной реальности Windows, назначьте фокус ввода смешанной реальности по помещению на устройстве или с помощью клавиши Windows + Y сочетание клавиш.</span><span class="sxs-lookup"><span data-stu-id="3c453-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="3c453-110">Имейте в виду, что приложения, предназначенные для HoloLens должен предоставить функциональность без эти устройства.</span><span class="sxs-lookup"><span data-stu-id="3c453-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="3c453-111">Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="3c453-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="3c453-112">Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.</span><span class="sxs-lookup"><span data-stu-id="3c453-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="3c453-113">Подписки на события ввода CoreWindow</span><span class="sxs-lookup"><span data-stu-id="3c453-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="3c453-114">Ввод с клавиатуры</span><span class="sxs-lookup"><span data-stu-id="3c453-114">Keyboard input</span></span>

<span data-ttu-id="3c453-115">В шаблоне приложения с Windows Holographic мы добавили обработчик событий для ввода с клавиатуры так же, как и любое другое приложение универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="3c453-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="3c453-116">Приложение принимает входные данные клавиатуры, так же, в Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3c453-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="3c453-117">Из AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="3c453-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="3c453-118">Ввод с клавиатуры виртуальной</span><span class="sxs-lookup"><span data-stu-id="3c453-118">Virtual keyboard input</span></span>
<span data-ttu-id="3c453-119">Для рабочего стола иммерсивную также могут поддерживать виртуальной клавиатуры, преобразовываемый для просмотра Windows через иммерсивных представления.</span><span class="sxs-lookup"><span data-stu-id="3c453-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="3c453-120">Для этого приложения можно реализовать **CoreTextEditContext**.</span><span class="sxs-lookup"><span data-stu-id="3c453-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="3c453-121">Это позволяет понять состояние собственные отрисованную приложением текстовые поля, поэтому на текст существует и правильно участия виртуальной клавиатуры Windows.</span><span class="sxs-lookup"><span data-stu-id="3c453-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="3c453-122">Дополнительные сведения о реализации поддержки CoreTextEditContext см. в разделе [CoreTextEditContext пример](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="3c453-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="3c453-123">Ввод от мыши</span><span class="sxs-lookup"><span data-stu-id="3c453-123">Mouse Input</span></span>

<span data-ttu-id="3c453-124">Можно также использовать ввод от мыши, еще раз через обработчики событий ввода CoreWindow универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="3c453-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="3c453-125">Вот как можно изменить Windows Holographic шаблон приложения для поддержки щелчки мышью в те же жесты способом в нажатом состоянии.</span><span class="sxs-lookup"><span data-stu-id="3c453-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="3c453-126">После выполнения это изменение, щелчок мыши, то устройство иммерсивных гарнитура вернется куба.</span><span class="sxs-lookup"><span data-stu-id="3c453-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="3c453-127">Обратите внимание, что приложений универсальной платформы Windows также можно получить необработанные данные x и y для мыши с помощью [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span><span class="sxs-lookup"><span data-stu-id="3c453-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="3c453-128">Сначала объявите новый обработчик OnPointerPressed в AppView.h:</span><span class="sxs-lookup"><span data-stu-id="3c453-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="3c453-129">Добавьте следующий код в AppView.cpp, SetWindow:</span><span class="sxs-lookup"><span data-stu-id="3c453-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="3c453-130">Затем поместите это определение для OnPointerPressed в нижней части файла:</span><span class="sxs-lookup"><span data-stu-id="3c453-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="3c453-131">Обработчик событий, который мы только что добавили является передачей в основной класс шаблона.</span><span class="sxs-lookup"><span data-stu-id="3c453-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="3c453-132">Давайте изменим основной класс для поддержки такая Сквозная передача.</span><span class="sxs-lookup"><span data-stu-id="3c453-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="3c453-133">Добавьте это объявление открытый метод в файл заголовка:</span><span class="sxs-lookup"><span data-stu-id="3c453-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="3c453-134">Вам потребуется эта переменная закрытого члена, а также:</span><span class="sxs-lookup"><span data-stu-id="3c453-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="3c453-135">Наконец мы будем обновлять основной класс новая логика для поддержки щелчков мышью.</span><span class="sxs-lookup"><span data-stu-id="3c453-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="3c453-136">Начните с добавления обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="3c453-136">Start by adding this event handler.</span></span> <span data-ttu-id="3c453-137">Не забудьте обновить имя класса:</span><span class="sxs-lookup"><span data-stu-id="3c453-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="3c453-138">Теперь в метод обновления, замените существующую логику для получения позу указатель с этим:</span><span class="sxs-lookup"><span data-stu-id="3c453-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="3c453-139">Перекомпилировать и переустановить.</span><span class="sxs-lookup"><span data-stu-id="3c453-139">Recompile and redeploy.</span></span> <span data-ttu-id="3c453-140">Следует заметить, что щелчок мышью теперь вернется куба в иммерсивных гарнитура - или HoloLens с bluetooth подключено.</span><span class="sxs-lookup"><span data-stu-id="3c453-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="3c453-141">Поддержка игровой контроллер</span><span class="sxs-lookup"><span data-stu-id="3c453-141">Game controller support</span></span>

<span data-ttu-id="3c453-142">Игровые устройства управления может быть веселым и удобный способ обеспечить возможность пользователя для управления Windows Mixed Reality присутствия.</span><span class="sxs-lookup"><span data-stu-id="3c453-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="3c453-143">Добавлена поддержка игровых устройств с Windows Holographic шаблоном приложения, первым делом для добавьте следующие объявления закрытого члена в класс основной файл заголовка:</span><span class="sxs-lookup"><span data-stu-id="3c453-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="3c453-144">Инициализируйте игровой события и игровые любой панели, который в данный момент присоединены, в конструкторе для основного класса:</span><span class="sxs-lookup"><span data-stu-id="3c453-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="3c453-145">Добавьте эти обработчики событий для основного класса.</span><span class="sxs-lookup"><span data-stu-id="3c453-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="3c453-146">Не забудьте обновить имя класса:</span><span class="sxs-lookup"><span data-stu-id="3c453-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="3c453-147">Наконец обновите логика ввода для распознавания изменений в состояние контроллера.</span><span class="sxs-lookup"><span data-stu-id="3c453-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="3c453-148">Здесь мы используем ту же переменную m_pointerPressed, описано в разделе выше для добавления события мыши.</span><span class="sxs-lookup"><span data-stu-id="3c453-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="3c453-149">Добавьте метод Update, перед которой он проверяет наличие SpatialPointerPose следующую строку:</span><span class="sxs-lookup"><span data-stu-id="3c453-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="3c453-150">Не забудьте отменить регистрацию событий при очистке основной класс:</span><span class="sxs-lookup"><span data-stu-id="3c453-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="3c453-151">Повторно скомпилируйте и выполните повторное развертывание.</span><span class="sxs-lookup"><span data-stu-id="3c453-151">Recompile, and redeploy.</span></span> <span data-ttu-id="3c453-152">Теперь можно присоединить, или сопряжение, игровой контроллер и использовать его для изменения положения вращающегося куба.</span><span class="sxs-lookup"><span data-stu-id="3c453-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="3c453-153">Важные моменты, касающиеся клавиатуру и мышь</span><span class="sxs-lookup"><span data-stu-id="3c453-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="3c453-154">Существует ряд ключевых различий в том, как этот код можно использовать в Microsoft HoloLens — это устройство, которое в основном зависит от естественность ввода данных – и что доступно на ПК с поддержкой Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3c453-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="3c453-155">Нельзя полагаться на клавиатуру или мышь, входные данные должны присутствовать.</span><span class="sxs-lookup"><span data-stu-id="3c453-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="3c453-156">Все приложения-функции необходимо работать с взглядом, жестов и речевого ввода.</span><span class="sxs-lookup"><span data-stu-id="3c453-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="3c453-157">При присоединении клавиатуры Bluetooth, может быть полезно включить для любого текста, приложение может запросить ввод с клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="3c453-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="3c453-158">Это может быть отличным дополнением для диктовки, например.</span><span class="sxs-lookup"><span data-stu-id="3c453-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="3c453-159">Когда речь идет о разработке приложения, не полагайтесь на (к примеру) один круг по ТРАССЕ и мыши выглядеть элементы управления для игры.</span><span class="sxs-lookup"><span data-stu-id="3c453-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="3c453-160">HoloLens предназначен для пользователя для обхода комнате.</span><span class="sxs-lookup"><span data-stu-id="3c453-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="3c453-161">В этом случае пользователь управляет камеры напрямую.</span><span class="sxs-lookup"><span data-stu-id="3c453-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="3c453-162">Интерфейс для ездить камеры по комнате с элементами управления для перемещения или внешний вид не точно так же.</span><span class="sxs-lookup"><span data-stu-id="3c453-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="3c453-163">Ввод с клавиатуры может быть отличным способом управления отладки аспекты своего приложения или игровых движков, особенно в том случае, поскольку пользователь не должны будут использовать клавиатуру.</span><span class="sxs-lookup"><span data-stu-id="3c453-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="3c453-164">Подключив он совпадает с вы привыкли, с помощью API-интерфейсов событий CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="3c453-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="3c453-165">В этом случае вы можете реализовать возможность настроить приложение службы приложений маршрутизацию событий клавиатуры в режим «Отладка только входные данные» во время сеансов отладки.</span><span class="sxs-lookup"><span data-stu-id="3c453-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="3c453-166">Также работать контроллеры Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="3c453-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c453-167">См. также</span><span class="sxs-lookup"><span data-stu-id="3c453-167">See also</span></span>
* [<span data-ttu-id="3c453-168">Стандартные оборудования</span><span class="sxs-lookup"><span data-stu-id="3c453-168">Hardware accessories</span></span>](hardware-accessories.md)
