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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Ввод с клавиатуры, мыши и контроллера в DirectX

Клавиатуры, мыши и игровые контроллеры могут быть полезными в качестве входных данных для устройств Windows Mixed Reality. Клавиатуры и мыши Bluetooth поддерживаются в HoloLens для использования с отладкой приложения или в качестве альтернативного вида входных данных. Windows Mixed Reality также поддерживает впечатляющие головные телефоны, подключенные к компьютерам, на которых были исторически мышь, клавиатуры и игровые контроллеры.

Чтобы использовать ввод с клавиатуры для HoloLens, свяжите клавиатуру Bluetooth с устройством или используйте виртуальный ввод через портал устройств Windows. Чтобы использовать ввод с клавиатуры при людьмиии иммерсивного головной гарнитуры Windows Mixed Reality, присвойте фокус ввода смешанной реальности, поместив устройство или используя сочетание клавиш Windows + Y. Помните, что приложения, предназначенные для HoloLens, должны предоставлять функциональные возможности без подключения к этим устройствам.

>[!NOTE]
>Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

## <a name="subscribe-for-corewindow-input-events"></a>Подписка на события ввода CoreWindow

### <a name="keyboard-input"></a>Ввод с клавиатуры

В шаблоне приложения Windows holographic мы включаем обработчик событий для ввода с клавиатуры точно так же, как любое другое приложение UWP. Приложение использует входные данные клавиатуры так же, как и в Windows Mixed Reality.

Из Аппвиев. cpp:

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

### <a name="virtual-keyboard-input"></a>Виртуальный ввод с клавиатуры
Для впечатляющих головок настольных компьютеров можно также поддерживать виртуальные клавиатуры, отображаемые Windows, в режиме погружения. Для поддержки этой возможности приложение может реализовать **коретекстедитконтекст**. Это позволяет Windows понять состояние собственных текстовых полей, отображаемых в приложении, поэтому виртуальная клавиатура может правильно участвовать в тексте.

Дополнительные сведения о реализации поддержки Коретекстедитконтекст см. в [примере коретекстедитконтекст](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Ввод с помощью мыши

Вы также можете использовать ввод с помощью мыши, используя обработчики событий ввода UWP CoreWindow. Вот как можно изменить шаблон приложения Windows holographic для поддержки щелчков мыши так же, как нажатые жесты. После внесения этого изменения щелкните мышью, когда людьми иммерсивное устройство гарнитуры изменит расположение Куба.

Обратите внимание, что приложения UWP также могут получать необработанные ТОЧЕЧные данные для мыши с помощью API [мауседевице](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) .

Начните с объявления нового обработчика Онпоинтерпрессед в Аппвиев. h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

В Аппвиев. cpp добавьте следующий код в Сетвиндов:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Затем установите это определение для Онпоинтерпрессед в нижней части файла:

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

Только что добавленный обработчик событий является транзитным классом шаблона Main. Давайте изменим класс main для поддержки этого транзитного класса. Добавьте это объявление общедоступного метода в заголовочный файл:

```
// Handle mouse input.
       void OnPointerPressed();
```

Вам потребуется также эта переменная члена Private:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Наконец, мы будем обновлять класс Main с помощью новой логики для поддержки щелчков мыши. Начните с добавления этого обработчика событий. Обязательно обновите имя класса:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Теперь в методе Update замените существующую логику для получения указателя a следующим:

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

Перекомпиляция и повторное развертывание. Обратите внимание, что щелчок мыши теперь перемещает куб в иммерсивное головной или HoloLens с подключенной мышью по Bluetooth.

### <a name="game-controller-support"></a>Поддержка игрового контроллера

Игровые контроллеры могут быть увлекательным и удобным способом предоставления пользователям возможности контролировать иммерсивное взаимодействие с Windows Mixed Reality.

Первым шагом в добавлении поддержки игровых контроллеров в шаблон приложения Windows holographic является добавление следующих закрытых объявлений членов в класс Header для основного файла:

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

Инициализируйте события игрового планшета и все подключенные к нему игровые планшеты в конструкторе основного класса:

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

Добавьте эти обработчики событий в основной класс. Обязательно обновите имя класса:

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

Наконец, обновите логику ввода, чтобы распознать изменения в состоянии контроллера. Здесь мы используем ту же переменную m_pointerPressed, описанную в разделе выше, для добавления событий мыши. Добавьте его в метод Update, непосредственно перед тем, как он проверяет наличие Спатиалпоинтерпосе:

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

Не забудьте отменить регистрацию событий при очистке основного класса:

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

Перекомпиляция и повторное развертывание. Теперь можно присоединить или связать игровой контроллер и использовать его для перемещения вращающегося куба.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Важные рекомендации по вводу с клавиатуры и мыши

Существует ряд ключевых различий в том, как этот код можно использовать в Microsoft HoloLens, то есть на устройстве, который в основном используется для естественного ввода данных, и о том, что доступно на ПК с поддержкой Windows Mixed Reality.
* Вы не можете полагаться на ввод с клавиатуры или с помощью мыши. Все функции вашего приложения должны работать с помощью взгляда, жеста и речевого ввода.
* При подключении клавиатуры Bluetooth может быть полезно включить ввод с клавиатуры для любого текста, который может запрашивать приложение. Например, это может быть отличным дополнением для диктовки.
* Когда дело доходит до разработки приложения, не полагайтесь на то, что (например,) трассе и мышь для поиска в игре. HoloLens предназначен для пользователя, чтобы проанализировать комнату. В этом случае пользователь управляет камерой напрямую. Интерфейс для передачи камеры вокруг комнаты с элементами управления перемещением и просмотром не обеспечивает такой же возможности.
* Ввод с клавиатуры может быть отличным способом управления аспектами отладки приложения или игрового модуля, особенно потому, что пользователю не потребуется использовать клавиатуру. Подключение выполняется так же, как и при использовании API-интерфейсов событий CoreWindow. В этом сценарии вы можете реализовать способ настройки приложения для маршрутизации событий клавиатуры в режим "только входные данные" во время сеансов отладки.
* Контроллеры Bluetooth также работают.

## <a name="see-also"></a>См. также
* [Аксессуары к оборудованию](hardware-accessories.md)
