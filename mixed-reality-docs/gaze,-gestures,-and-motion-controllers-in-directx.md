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
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a>Взглядом, жесты и контроллеры движения в DirectX

Если вы собираетесь создать непосредственно на базе платформы, необходимо обрабатывать информации, поступающей от пользователя — например, где пользователь смотрит через [головного взглядом](gaze.md) и что пользователь выбрал с [жесты](gestures.md) или [движения контроллеров](motion-controllers.md). Объединение этих форм ввода данных, вы можете включить пользователь не загрузит [голограмма](hologram.md) в вашем приложении. [Шаблон holographic приложения](creating-a-holographic-directx-project.md) содержит пример прост в использовании.

>[!NOTE]
>Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).  Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.

## <a name="gaze-input"></a>Ввод взглядом

Для доступа к пользователя [головного взглядом](gaze.md), использовании [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) типа. Шаблон holographic приложения включает в себя базовый код для понимания взглядом. Этот код предоставляет вектор, указывающий вперед между пользователя глаза, принимая во внимание устройства положение и ориентацию в заданной [системы координат](coordinate-systems-in-directx.md).




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

Возможно, вам вопрос о: «Но где система координат взять?»

Давайте ответить на этот вопрос. В нашем AppMain **обновления** функции, мы обрабатываемых пространственных события ввода его приобретения для наших StationaryFrameOfReference относительно координат. Помните, что StationaryFrameOfReference создан при настройке [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), и система координат была получена в начале [обновления](rendering-in-directx.md).




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

Обратите внимание на то, что данные привязан к указатель состояние какой-либо. Мы получаем от пространственных входного события. Объект данных события включают в системе координат, позволяющий всегда можно связать направление взглядом во время события независимо от пространственных систему координат, вам потребуется. На самом деле это необходимо сделать для получения поза указатель.

> [!NOTE]
> Дополнительные рекомендации, относящиеся к HoloLens 2 [ожидается в ближайшее время](index.md#news-and-notes).

## <a name="gesture-and-motion-controller-input"></a>Жест движения контроллер и входных данных

В Windows Mixed Reality, обе стороны [жесты](gestures.md) и [движения контроллеров](motion-controllers.md) обрабатываются с помощью того же пространственных входа API-интерфейсы, в [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) пространство имен. Это позволяет с легкостью выполнить общие действия, такие как **выберите** нажимает так же, как в руки и контроллеры движения.

Существует два уровня API-интерфейса можно ориентироваться при обработке жестов или движения контроллеров в смешанной реальности.
* [Взаимодействие](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) и [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), доступный с помощью [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)
* [Составные жесты](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), хранения, обработки, навигации), доступный с помощью [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a>Выберите/меню/коммерческих тайн/сенсорной панели/джойстик взаимодействия: SpatialInteractionManager

Чтобы обнаружить нажатие низкого уровня, выпусках и обновлениях в руки и устройств ввода в Windows Mixed Reality, запустите в [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx). SpatialInteractionManager имеет событие, которое информирует приложения при наличии или движения контроллер обнаружил входных данных.

Существуют три основные вида SpatialInteractionSource, каждый из которых представлен по другому значению SpatialInteractionSourceKind:
* **Рука** представляет обнаруженных руку пользователя. Рука источники доступны только для HoloLens.
* **Контроллер** представляет контроллер парных движения. Контроллеры движения может предложить широкий набор возможностей, например: Выберите триггеры, кнопки меню, кнопки коммерческих тайн, сенсорные панели и thumbsticks.
* **Голосовые** представляет голос пользователя, говоря система обнаружила ключевые слова. Это будет внедрить выберите press и выпуска всякий раз, когда пользователь скажет: «Выбрать».

Чтобы обнаружить нажатие во всех этих источниках взаимодействия, можно обрабатывать события SourcePressed SpatialInteractionManager в SpatialInputHandler.cpp:


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

Это событие нажатия отправляется в приложение асинхронно. Ваше приложение или игровое ядро может потребоваться выполнить некоторые задачи обработки прямо сейчас или требуется поставить данные событий в подпрограмму обработки входных данных.

В шаблоне есть вспомогательный класс, чтобы приступить к работе. Этот шаблон сложнее, чем обработку для простоты разработки. Вспомогательный класс следит за ли, что один или несколько **Pressed** события, которые возникли с момента последнего **обновления** вызова. Из SpatialInputHandler.cpp:




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

Если так, он возвращает [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) самые последние события ввода, во время следующего обновления. Из SpatialInputHandler.cpp:




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

Обратите внимание, что приведенный выше код будет рассматривать все нажимает так же ли пользователь выполняет первичную **выберите** press, ни вторичными **меню** или **осознавать** клавишу. **Выберите** press представляет собой основной форму взаимодействия поддерживаются в разных руки, контроллеры и голоса, активации, либо вручную, выполнение жест касания, контроллер движения с помощью его основного триггера или кнопки нажата, путем перемещения или пользователя Голосовая связь говорим: «Select». Выберите нажатия представляют намерение пользователя активировать голограмма, который их используете.

Происходит вопросов типа press, мы будем изменять обработчик событий SpatialInteractionManager::SourceUpdated. Наш код обнаружит нажатия коммерческих тайн (при наличии) и использовать их для изменения положения куба. Если коммерческих тайн недоступен, мы используем выберите нажатия.

Добавьте следующие объявления закрытого члена SpatialInputHandler.h: 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

Откройте SpatialInputHandler.cpp. Добавьте следующую регистрацию событий в конструктор: 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

Это код обработчика событий. Если возникают проблемы приступим источника входных данных, поза указатель будет сохранена для следующего цикла обновления. В противном случае он будет проверять наличие нажатие выберите вместо этого. Из SpatialInputHandler.cpp:




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

Убедитесь в том, что отменить регистрацию обработчика событий в деструкторе. Из SpatialInputHandler.cpp:


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

Повторная компиляция и затем повторно развернуть. Проект шаблона должна появиться возможность распознавать взаимодействия может воспользоваться для изменения положения вращающегося куба.

Этот API SpatialInteractionSource поддерживает контроллеры с широкий спектр возможностей. В примере, показанном выше мы проверяем поддержке коммерческих тайн перед попыткой его использования. SpatialInteractionSource поддерживает следующие дополнительные возможности Помимо общих **выберите** нажмите:
* **Кнопка меню:** Проверка поддержки путем проверки свойства IsMenuSupported. Когда это возможно, проверьте [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) свойство, чтобы определить кнопку меню нажата.
* **Кнопка может воспользоваться:** Проверка поддержки путем проверки свойства IsGraspSupported. Когда это возможно, проверьте [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) свойство, чтобы узнать, включен ли может воспользоваться.

Для контроллеров SpatialInteractionSource имеет свойство контроллера с помощью дополнительных возможностей.
* **HasThumbstick:** Если значение равно true, контроллер может джойстик. Проверьте [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) свойство SpatialInteractionSourceState получения джойстик x и y значения (ThumbstickX и ThumbstickY), а также его нажаты (IsThumbstickPressed).
* **HasTouchpad:** Если значение равно true, контроллер может сенсорной панели. Проверьте свойство ControllerProperties SpatialInteractionSourceState получения сенсорной панели x и y значений (TouchpadX и TouchpadY) и знать, если пользователь касается планшета (IsTouchpadTouched) и если они нажав сенсорной вниз () IsTouchpadPressed).
* **SimpleHapticsController:** Интерфейс API SimpleHapticsController для контроллера, позволяет исследовать возможности haptics контроллера, а также позволяет управлять обратной связи haptic.

Обратите внимание, что диапазон для сенсорной панели и джойстик от -1 до 1 для обеих осях (снизу вверх и слева направо). Диапазон для аналоговой триггера, к которому можно получить с помощью свойства SpatialInteractionSourceState::SelectPressedValue, имеет диапазон от 0 до 1. Значение 1 соответствует с IsSelectPressed равен true; любое другое значение связано с IsSelectPressed равен false.

Обратите внимание, что для руки и контроллер с помощью SpatialInteractionSourceState::Properties::TryGetLocation предоставит положение руки пользователя – это отличается от поза указателя, представляющий указывающего Рэй контроллера. Если требуется нарисовать что-нибудь в расположении вручную, используйте TryGetLocation. Если вы хотите raycast, начиная с контроллера, получите указывающего луча из TryGetInteractionSourcePose на SpatialPointerPose.

Также можно использовать другие события на SpatialInteractionManager, такие как SourceDetected и SourceLost, для реагирования на руках введите, или оставьте поле представления устройства или при переходе в или из него позицию Готово (вытянутым указательным пальцем возникает с palm вперед), или когда движения контроллеры будут отключены / или пару непарный.

### <a name="grip-pose-vs-pointing-pose"></a>Поза захвата для изменения и указывающего поза

Windows Mixed Reality поддерживает движения контроллеров в различных форм-факторов, дизайна каждый контроллер, отличающихся по отношению между положение руки пользователя и натуральный «переслать» направление этого приложения следует использовать для команды при подготовке к просмотру контроллер.

Чтобы лучше представить эти контроллеры, существует два вида создает изучаться для каждого источника взаимодействия:
* **Поза захвата для изменения**, представляющий расположение руку, обнаруживаемые HoloLens или palm, удерживая контроллером движения.
    * На иммерсивную, это поза лучше всего подходит для подготовки к просмотру **руку пользователя** или **объект содержится в руки пользователя**, например помехой или оружия.
    * **Возьмитесь за позиции**: Palm центроида при удержании контроллер, естественно, корректируется, влево или вправо, чтобы центрировать позиция в пределах захвата.
    * **Возьмитесь за правой оси в ориентации**: При открытии полностью свои силы для формирования позу плоских 5 палец, луч, является нормальным для вашей palm (вперед от левой palm назад от правой palm)
    * **Возьмитесь за ориентации на ось, направленная вперед**: При закрытии вашей руке частично (как будто держа контроллеру), луч, указывающий «forward» трубку, образованное пальцы отличных от бегунка.
    * **Возьмитесь за ориентации элемента вверх оси**: Ось вверх, право и прямого определения содержится в разрешении.
    * Можно получить доступ к поза захвата для изменения через [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).
* **Поза указатель**, представляющий кончика контроллера, указывающего вперед.
    * Этот поза лучше всего подходит для raycast при **обращены пользовательского интерфейса** при отрисовке самой модели контроллера.
    * Можно получить доступ к поза указатель через [SpatialInteractionSourceState.Properties.TryGetLocation(...). SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) или [SpatialInteractionSourceState.TryGetPointerPose(...). TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

### <a name="composite-gestures-spatialgesturerecognizer"></a>Составные жесты: SpatialGestureRecognizer

Объект [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) интерпретирует взаимодействия с пользователем от руки, контроллеры движения и команда «Выбрать» на события поверхности пространственных жестов, какие пользователи target, с помощью их головной взглядом.

Пространственных жесты являются ключевых разновидностью входных данных для приложений Windows Mixed Reality. Маршрутизации взаимодействий из SpatialInteractionManager для SpatialGestureRecognizer голограмма приложений может обнаруживать события касания, удержание, манипуляции и навигации равномерно в руки, голоса и пространственных устройств ввода, без необходимости обрабатывать нажатия и освобождает вручную.

SpatialGestureRecognizer выполняет только минимальный устранения неоднозначности между набор жестов, которые можно запросить. К примеру Если вы запрашивали только Tap, пользователь может удерживать пальцев, пока они любят и отвод по-прежнему будет выполняться. При запросе коснитесь и хранения, после того как об одной секунды удерживая пальцев, жест переведет в удержание и Tap не будет происходить.

Чтобы использовать SpatialGestureRecognizer, обрабатывать SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) событий и захвата SpatialPointerPose предоставляются существует. Используйте Рэй головной взглядом пользователя из этого поза для пересечения с голограммы и поверхности сетки в окружения пользователя, чтобы определить, что пользователь собирается для взаимодействия с. Затем направлять SpatialInteraction в аргументах событий для целевой голограмма SpatialGestureRecognizer, с помощью его [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) метод. Запустится интерпретации, реализуемый в соответствии с [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) задать на этот распознаватель, во время создания - или с [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

На HoloLens взаимодействия и жесты следует обычно являются их выбора целевой платформы из головного взглядом пользователя, а не при визуализации или напрямую взаимодействовать в расположении вручную. После запуска взаимодействия относительный движения вручную может использоваться для управления жест, как и в случае с жестом манипуляции или навигации.

## <a name="see-also"></a>См. также
* [Взглядом](gaze.md)
* [Жесты](gestures.md)
* [Контроллеры движения](motion-controllers.md)
