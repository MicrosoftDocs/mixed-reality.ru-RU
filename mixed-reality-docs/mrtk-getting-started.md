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
# <a name="getting-started-with-mrtk-v2"></a>Приступая к работе с MRTK v2

## <a name="mrtk-getting-started-guide"></a>Руководство по началу MRTK работы
См. в разделе [MRTK руководство по началу](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) сведения по началу работы с MRTK V2.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Что такое набор средств смешанной реальности (MRTK)?
MRTK является набор с удивительные открытым кодом, что существовало с момента первого выпуска HoloLens и не будет там, где это сегодня без изнурительной работы по наше сообщество разработчиков, предоставили к нему. За последние 3 лет мы проанализировали отзывы наше сообщество разработчиков, а также построение v2 MRTK учитывать главных задач.  

V2 MRTK с помощью Unity — это пакету средств разработки кросс платформенных открытым исходным кодом для смешанной реальности приложений.  MRTK версии 2 предназначен для ускорения разработки приложений, предназначенных для Microsoft HoloLens, Windows Mixed Reality иммерсивную (VR) и OpenVR платформы. Проект является, предназначенные для снижения барьеры операции для создания приложения смешанной реальности и внести свой вклад сообщества по мере мы все роста. 


См. в разделе [портале документации MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) для получения дополнительных сведений.

## <a name="feature-areas"></a>Функциональные области

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Система ввода" width="105"> Система ввода 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Рука отслеживания (HoloLens 2)" width="105"> Рука отслеживания (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Отслеживания (HoloLens 2)" width="105">
    Отслеживания (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Голосовые команды" width="105"> Голосовые команды
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Помощи + Выбор (HoloLens (1-го поколения))" width="105">
    Помощи + Выбор (HoloLens (1-го поколения))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> Teleportation
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Элементы управления пользовательским интерфейсом" width="105"> Элементы управления пользовательским интерфейсом
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Средства поиска решения и взаимодействия" width="105"> Средства поиска решения и взаимодействия
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Контроллер визуализации" width="105"> Контроллер визуализации
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Пространственные понимание" width="105"> Пространственные понимание
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Средство диагностики" width="105"> Средство диагностики
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Стандартный шейдера MRTK" width="105"> Стандартный шейдера MRTK
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>Пользовательский Интерфейс и взаимодействие стандартных блоков

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Кнопка" width="250"><br>
    **Button**<br>
    Элемент управления button, который поддерживает различные методы ввода, включая HoloLens 2 ясно сформулированные вручную <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Ограничивающий прямоугольник" width="250"><br>
    **Ограничивающий прямоугольник**<br>
    Стандартный пользовательский Интерфейс для управления объектами в трехмерном пространстве <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Обработчик манипуляции" width="250"><br>
    **Обработчик манипуляции**<br>
    Скрипт для управления объектами с помощью одного или двух рук <a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Содержание рекламы" width="250"><br>
    **Содержание рекламы** <br>
    2D стиля плоскости, которая поддерживает прокрутку с входными данными ясно сформулированные вручную <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Системную клавиатуру" width="250"><br>
    **Системную клавиатуру**<br>
    Пример сценария использования клавиатуры системы в Unity <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Элементом" width="250"><br>
     **Элементом** <br>
     Скрипт для создания объектов элементом с помощью визуальных состояний и поддержка тем <a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Поиск решения" width="250"><br>
    **Поиск решения** <br>
    Различные объекта позиционирования особенности поведения, такие как tag-along, текст с блокировкой, размера представления константы и поверхности магнитного <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Коллекция объектов" width="250"><br>
    **Коллекция объектов**<br>
    Скрипт для размещать массив объектов в трехмерной фигуры <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Всплывающая подсказка" width="250">  <br>
    **Подсказка**<br>
    Заметка пользовательского интерфейса с гибкой привязки/pivot системы, который может использоваться для работы с метками контроллеров движения и объекта <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Панель приложения" width="250"><br>
    **Панель приложения**<br>
    Пользовательский Интерфейс для ручной активации ограничивающий прямоугольник <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Указатели" width="250"><br>
    **Указатели**<br>
    Дополнительные сведения о различных типов указателей <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Срезах визуализации" width="250"><br>
     **Срезах визуализации**<br>
     Visual affordance в срезах, облегчающее достоверности для прямого взаимодействия <a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    **Slider**<br>
    Ползунок пользовательского интерфейса для изменения значения поддержки прямой вручную отслеживания взаимодействия <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Стандартный шейдера MRTK" width="250"><br>
    **Стандартный шейдера MRTK**<br>
    Стандартный шейдера MRTK поддерживает различные элементы проектирования Fluent с производительностью <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Вручную сертификационного Chaser" width="250"><br>
     **Вручную сертификационного Chaser**<br>
     Демонстрирует использование средства поиска решения для присоединения объектов к соединений вручную <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Отслеживание глаза: Выбор назначения" width="250"><br>
    **Отслеживание глаза: Выбор назначения**<br>
    Объединить глаза, голоса и наличии входные данные быстро и легко выбирать голограммы в сценах <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Отслеживание глаза: Навигация" width="250"><br>
    **Отслеживание глаза: Навигации**<br>
    Узнайте, как auto прокрутить текст или меньшим числом запинок масштабирования в конкретное содержимое, в зависимости от того, что вы видите <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Отслеживание глаза: Тепловая карта" width="250"><br>
    **Отслеживание глаза: Тепловая карта**<br>
    Примеры для ведения журнала, загрузки и визуализация какие пользователи нуждались в в приложении <a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>Минимальным требованием для MRTK v2
* Unity 2018.3.x
* Microsoft Visual Studio 2017 или более поздней версии
* Windows SDK 18362 + 
* Windows 10 версии 1803 или более поздней версии

## <a name="new-with-mrtk-v2"></a>Новые возможности MRTK v2
Мы хотим стремлении к этим средствам платформы с нагрузкой.  На самом деле использовались MRTK версии 2 для разработки на нашем опыте работы папки "Входящие", такие как программа установки experience (OOBE) и наше приложение смешанной реальности обучения.  Кроме того, можно ожидать новые возможности HoloLens 2, сначала отображенном MRTK, так как мы считаем, что это лучший способ разработки на нашей платформе. 

### <a name="modular"></a>Модульная
Мы предусмотрели его модульной способом, таким образом, чтобы вам не нужно отключать каждый бит набора средств в проект.  Существует фактически дает несколько преимуществ это.  Она обеспечивает меньший размер вашего проекта, а также упрощает управление.  Поверх всего этого так как она основана на объекты сценариев и определяется интерфейс, можно также заменить компоненты, которые входят в состав собственным, для поддержки других служб, систем и платформ.


### <a name="cross-platform"></a>Поддержка разных платформ
Говоря о других платформах, он имеет Поддержка разных платформ.  И хотя это не означает, что каждый единую платформу поддерживается без дополнительной настройки, мы внесли в том, что никакой код toolkit нарушит работу при переходе целевой сборки с другими платформами.  Надежность и расширяемость с помощью модульную структуру настраивает по контуру хорошо иметь возможность обеспечить поддержку нескольких платформ, таких как ARCore, ARKit и OpenVR.


### <a name="performant"></a>Высокопроизводительные
Работа с мобильных платформ, мы составили его с учетом производительности.  Это крайне важно выверить, и мы хотели бы убедиться, что средства не будут работать для вас.


## <a name="see-also"></a>См. также
* [Руководство по началу работы MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Домашняя страница документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Установка средств](install-the-tools.md)
* [Перенос приложений из HTK/MRTK в MRTK версии 2](mrtk-porting-guide.md)
