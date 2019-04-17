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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Входные данные контроллера в DirectX, клавиатуры и мыши

Клавиатуры, мыши и игровые устройства управления может быть полезным форм ввода данных для устройств Windows смешанной реальности. Bluetooth клавиатуры и мыши в поддерживаются HoloLens, для отладки приложения или как альтернативная форма входных данных. Смешанная реальность Windows также поддерживает иммерсивную к ПК - где мыши, клавиатуры и игровых устройств управления традиционно были норма.

Чтобы использовать ввод с клавиатуры для HoloLens, пары клавиатуры Bluetooth для устройства или виртуальный вход через Windows Device Portal. Чтобы использовать ввод с клавиатуры, то иммерсивных гарнитуры смешанной реальности Windows, назначьте фокус ввода смешанной реальности по помещению на устройстве или с помощью клавиши Windows + Y сочетание клавиш. Имейте в виду, что приложения, предназначенные для HoloLens должен предоставить функциональность без эти устройства.

>[!NOTE]
>Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).  Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.

## <a name="subscribe-for-corewindow-input-events"></a>Подписки на события ввода CoreWindow

### <a name="keyboard-input"></a>Ввод с клавиатуры

В шаблоне приложения с Windows Holographic мы добавили обработчик событий для ввода с клавиатуры так же, как и любое другое приложение универсальной платформы Windows. Приложение принимает входные данные клавиатуры, так же, в Windows Mixed Reality.

Из AppView.cpp:

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

### <a name="virtual-keyboard-input"></a>Ввод с клавиатуры виртуальной
Для рабочего стола иммерсивную также могут поддерживать виртуальной клавиатуры, преобразовываемый для просмотра Windows через иммерсивных представления. Для этого приложения можно реализовать **CoreTextEditContext**. Это позволяет понять состояние собственные отрисованную приложением текстовые поля, поэтому на текст существует и правильно участия виртуальной клавиатуры Windows.

Дополнительные сведения о реализации поддержки CoreTextEditContext см. в разделе [CoreTextEditContext пример](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Ввод от мыши

Можно также использовать ввод от мыши, еще раз через обработчики событий ввода CoreWindow универсальной платформы Windows. Вот как можно изменить Windows Holographic шаблон приложения для поддержки щелчки мышью в те же жесты способом в нажатом состоянии. После выполнения это изменение, щелчок мыши, то устройство иммерсивных гарнитура вернется куба.

Обратите внимание, что приложений универсальной платформы Windows также можно получить необработанные данные x и y для мыши с помощью [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.

Сначала объявите новый обработчик OnPointerPressed в AppView.h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

Добавьте следующий код в AppView.cpp, SetWindow:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Затем поместите это определение для OnPointerPressed в нижней части файла:

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

Обработчик событий, который мы только что добавили является передачей в основной класс шаблона. Давайте изменим основной класс для поддержки такая Сквозная передача. Добавьте это объявление открытый метод в файл заголовка:

```
// Handle mouse input.
       void OnPointerPressed();
```

Вам потребуется эта переменная закрытого члена, а также:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Наконец мы будем обновлять основной класс новая логика для поддержки щелчков мышью. Начните с добавления обработчика событий. Не забудьте обновить имя класса:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Теперь в метод обновления, замените существующую логику для получения позу указатель с этим:

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

Перекомпилировать и переустановить. Следует заметить, что щелчок мышью теперь вернется куба в иммерсивных гарнитура - или HoloLens с bluetooth подключено.

### <a name="game-controller-support"></a>Поддержка игровой контроллер

Игровые устройства управления может быть веселым и удобный способ обеспечить возможность пользователя для управления Windows Mixed Reality присутствия.

Добавлена поддержка игровых устройств с Windows Holographic шаблоном приложения, первым делом для добавьте следующие объявления закрытого члена в класс основной файл заголовка:

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

Инициализируйте игровой события и игровые любой панели, который в данный момент присоединены, в конструкторе для основного класса:

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

Добавьте эти обработчики событий для основного класса. Не забудьте обновить имя класса:

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

Наконец обновите логика ввода для распознавания изменений в состояние контроллера. Здесь мы используем ту же переменную m_pointerPressed, описано в разделе выше для добавления события мыши. Добавьте метод Update, перед которой он проверяет наличие SpatialPointerPose следующую строку:

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

Не забудьте отменить регистрацию событий при очистке основной класс:

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

Повторно скомпилируйте и выполните повторное развертывание. Теперь можно присоединить, или сопряжение, игровой контроллер и использовать его для изменения положения вращающегося куба.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Важные моменты, касающиеся клавиатуру и мышь

Существует ряд ключевых различий в том, как этот код можно использовать в Microsoft HoloLens — это устройство, которое в основном зависит от естественность ввода данных – и что доступно на ПК с поддержкой Windows Mixed Reality.
* Нельзя полагаться на клавиатуру или мышь, входные данные должны присутствовать. Все приложения-функции необходимо работать с взглядом, жестов и речевого ввода.
* При присоединении клавиатуры Bluetooth, может быть полезно включить для любого текста, приложение может запросить ввод с клавиатуры. Это может быть отличным дополнением для диктовки, например.
* Когда речь идет о разработке приложения, не полагайтесь на (к примеру) один круг по ТРАССЕ и мыши выглядеть элементы управления для игры. HoloLens предназначен для пользователя для обхода комнате. В этом случае пользователь управляет камеры напрямую. Интерфейс для ездить камеры по комнате с элементами управления для перемещения или внешний вид не точно так же.
* Ввод с клавиатуры может быть отличным способом управления отладки аспекты своего приложения или игровых движков, особенно в том случае, поскольку пользователь не должны будут использовать клавиатуру. Подключив он совпадает с вы привыкли, с помощью API-интерфейсов событий CoreWindow. В этом случае вы можете реализовать возможность настроить приложение службы приложений маршрутизацию событий клавиатуры в режим «Отладка только входные данные» во время сеансов отладки.
* Также работать контроллеры Bluetooth.

## <a name="see-also"></a>См. также
* [Стандартные оборудования](hardware-accessories.md)
