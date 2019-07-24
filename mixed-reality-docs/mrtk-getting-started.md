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
# <a name="getting-started-with-mrtk-v2"></a>Начало работы с МРТК v2

## <a name="mrtk-getting-started-guide"></a>МРТК начало работы
Сведения о начале работы с МРТК v2 см. в разделе [руководство по началу работы с мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) .

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Что такое набор средств для смешанной реальности (МРТК)?
МРТК — это чудесный набор средств с открытым исходным кодом, с момента первого выпуска HoloLens, который не был в настоящее время без жесткой работы нашего сообщества разработчиков, который участвовал в этом. За последние 3 года мы прослушались на отзыве сообщества разработчиков и создали МРТК v2, чтобы принять во внимание самые существенные проблемы.  

МРТК v2 с Unity — это набор средств межплатформенного развертывания с открытым исходным кодом для приложений смешанной реальности.  МРТК версии 2 предназначена для ускорения разработки приложений, предназначенных для головных телефонов Microsoft HoloLens, Windows Mixed Reality (VR) и платформы Опенвр. Целью проекта является снижение барьеров для создания приложений смешанной реальности и внесение вклада в развитие сообщества по мере расширения личного опыта. 


Дополнительные сведения см. на [портале документации по мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) .

## <a name="feature-areas"></a>Функциональные области

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Входная система" width="105"> Входная система 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Отслеживание вручную (HoloLens 2)" width="105"> Отслеживание вручную (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Отслеживание взгляда (HoloLens 2)" width="105">
    Отслеживание взгляда (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Голосовое Командое" width="105"> Голосовое Командое
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Взгляните + SELECT (HoloLens (1-й общий))" width="105">
    Взгляните + SELECT (HoloLens (1-й общий))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Пропорции" width="105"> Пропорции
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Элементы управления пользовательским интерфейсом" width="105"> Элементы управления пользовательским интерфейсом
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Поиск и взаимодействие" width="105"> Поиск и взаимодействие
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Визуализация контроллера" width="105"> Визуализация контроллера
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Пространственное понимание" width="105"> Пространственное понимание
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Средство диагностики" width="105"> Средство диагностики
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Стандартный шейдер МРТК" width="105"> Стандартный шейдер МРТК
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>Стандартные блоки пользовательского интерфейса и взаимодействия

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Кнопка" width="250"><br>
    **Button**<br>
    Элемент управления "Кнопка", поддерживающий различные методы ввода, включая наладонный объект HoloLens 2<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Ограничивающий прямоугольник" width="250"><br>
    **Ограничивающий прямоугольник**<br>
    Стандартный пользовательский интерфейс для манипулирования объектами в трехмерном пространстве<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Обработчик манипуляции" width="250"><br>
    **Обработчик манипуляции**<br>
    Скрипт для манипулирования объектами с одной или двумя руки<a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Рекламы" width="250"><br>
    **Рекламы** <br>
    плоскость двумерных стилей, которая поддерживает прокрутку с помощью клавиатуры с вытеканием руки<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Системная клавиатура" width="250"><br>
    **Системная клавиатура**<br>
    Пример сценария использования системной клавиатуры в Unity<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Элементом" width="250"><br>
     **Элементом** <br>
     Скрипт, обеспечивающий взаимодействие объектов с визуальными состояниями и поддержкой тем<a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Найден" width="250"><br>
    **Найден** <br>
    Различные поведения позиционирования объектов, такие как тег, блокировка тела, размер представления константы и магнит поверхностей поверхности<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Коллекция объектов" width="250"><br>
    **Коллекция объектов**<br>
    Скрипт для размещения массива объектов в трехмерной фигуре<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Всплывающая подсказка" width="250">  <br>
    **Сказок**<br>
    Пользовательский интерфейс заметки с гибкой системой привязки и сведениями, который можно использовать для создания меток для контроллеров движения и объектов<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Панель приложения" width="250"><br>
    **Панель приложения**<br>
    Пользовательский интерфейс для активации ограничивающего прямоугольника вручную<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Указатели" width="250"><br>
    **Указател**<br>
    Дополнительные сведения о различных типах указателей<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Удобное графическое представление" width="250"><br>
     **Удобное графическое представление**<br>
     Визуальное взаимодействие с учетом того, что повышает уверенность в прямом взаимодействии<a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    **Slider**<br>
    Пользовательский интерфейс ползунка для настройки значений, поддерживающих взаимодействие с отслеживанием прямого отслеживания<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Стандартный шейдер МРТК" width="250"><br>
    **Стандартный шейдер МРТК**<br>
    Стандартный шейдер МРТК поддерживает различные элементы проектирования Fluent с производительностью<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Часер муфта" width="250"><br>
     **Часер муфта**<br>
     Демонстрирует использование решателя для присоединения объектов к рукой<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Отслеживание взгляда: Выбор целевого объекта" width="250"><br>
    **Отслеживание взгляда: Выбор целевого объекта**<br>
    Объедините глаза, голоса и руки, чтобы быстро и легко выбирать голограммы в сцене.<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Отслеживание взгляда: Навигация" width="250"><br>
    **Отслеживание взгляда: Месяца**<br>
    Узнайте, как выполнять автоматическую прокрутку текста или свободно изменять содержимое в зависимости от того, что вы ищете.<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Отслеживание взгляда: Тепловая схема" width="250"><br>
    **Отслеживание взгляда: Тепловая схема**<br>
    Примеры ведения журнала, загрузки и визуализации того, что пользователи просматривают в приложении<a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>Минимальные требования для МРТК v2
* Unity 2018.3.x
* Microsoft Visual Studio 2017 или более поздней версии
* Windows SDK 18362 + 
* Windows 10 1803 или более поздняя версия

## <a name="new-with-mrtk-v2"></a>Новые с МРТК v2
Мы хотим нагрузить наши обязательства на эти средства платформы.  На самом деле мы воспользуемся МРТК версии 2 для разработки нашего процесса входящих сообщений, таких как программа установки (OOBE) и приложение для обучения смешанной реальности.  Вы также можете увидеть новые возможности HoloLens 2, впервые предоставляемые через МРТК, так как мы считаем, что это лучший способ разработки на нашей платформе. 

### <a name="modular"></a>Полк
Мы создали модульный подход, так что вам не нужно брать каждый из них в свой проект.  Для этого есть несколько преимуществ.  Это позволяет уменьшить размер проекта, а также упростить управление.  Поверх этого, поскольку он построен с помощью объектов с поддержкой сценариев и является управляемым интерфейсом, можно также заменить компоненты, включенные в собственный, для поддержки других служб, систем и платформ.


### <a name="cross-platform"></a>Поддержка разных платформ
Говоря о других платформах, она поддерживает кросс-платформенную поддержку.  И хотя это и не означает, что каждая отдельная платформа поддерживается не всегда, мы сделали так, что ни один из программных средств не будет нарушен при переключении цели сборки на другие платформы.  Надежность и расширяемость с модульным проектированием устанавливаются с учетом хорошего пути для поддержки нескольких платформ, таких как Аркоре, ARKit и Опенвр.


### <a name="performant"></a>Высокопроизводительных
Работая с мобильными платформами, мы составили его с учетом производительности.  Это очень важно, и мы хотим убедиться, что средства не будут работать с вами.


## <a name="see-also"></a>См. также
* [Руководство по началу работы с МРТК](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Домашняя страница документации по МРТК](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Установка средств](install-the-tools.md)
* [Перенос из ХТК/МРТК в МРТК версии 2](mrtk-porting-guide.md)
