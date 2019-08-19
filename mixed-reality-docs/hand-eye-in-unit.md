---
title: Взгляд на руки и отслеживание глаз в Unity
description: Существует два основных способа выполнения действий с вашим взглядом в Unity, жестами и контроллерами движения.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: жесты, контроллеры движения, Unity, взгляд, входные данные
ms.openlocfilehash: 13016879e47b3b61eb417ce9425e48ea56c1b726
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2019
ms.locfileid: "64580758"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Взгляд на руки и отслеживание глаз в Unity

В HoloLens 2 появились новые интересные возможности: «руки» и «отслеживание глаз».

Самый простой способ использовать новую возможность в Unity — МРТК v2. Также есть несколько примеров сцен, которые помогут вам приступить к работе. 

* [Приступая к работе с наладонными руками в МРТК v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSystem/HandTracking.html)
* [Приступая к работе с отслеживанием взгляда в МРТК v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)


# <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>Стандартные блоки, поддерживающие руки, глаза и др. в МРТК v2

МРТК v2 предоставляет набор элементов управления пользовательского интерфейса и стандартных блоков, помогающих ускорить разработку. 

|  [![Кнопка](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [Кнопка](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [Ограничивающий](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) ограничивающий прямоугольник [ ![](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | [Обработчик манипуляций](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) обработчика манипуляций [ ![](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| Элемент управления "Кнопка", поддерживающий различные методы ввода, включая HoloLens2's с определенными руками | Стандартный пользовательский интерфейс для манипулирования объектами в трехмерном пространстве | Скрипт для манипулирования объектами с одной или двумя руки |
|  [Содержание](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) планшета [ ![](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | [![Системная клавиатура](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) [Системная клавиатура](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [![Взаимодействие](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) [Взаимодействие](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| плоскость двумерных стилей, которая поддерживает прокрутку с помощью клавиатуры с вытеканием руки | Пример сценария использования системной клавиатуры в Unity  | Скрипт, обеспечивающий взаимодействие объектов с визуальными состояниями и поддержкой тем |
|  [![Поиск решения](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) [Поиск решения](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [Коллекция объектов](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) коллекции объектов [ ![](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [![Подсказка](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) [Подсказка](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| Различные поведения позиционирования объектов, такие как тег, блокировка тела, размер представления константы и магнит поверхностей поверхности | Скрипт для размещения массива объектов в трехмерной фигуре | Пользовательский интерфейс заметки с гибкой системой привязки и сведениями, который можно использовать для пометки контроллеров и объектов движения. |
|  [Панель приложения](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) панели приложений [ ![](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [![Указатели](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) [Указатели](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) | Высокоудобное [Графическое](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) представление [ ![](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| Пользовательский интерфейс для активации ограничивающего прямоугольника вручную | Дополнительные сведения о различных типах указателей | Визуальное взаимодействие с учетом того, что повышает уверенность в прямом взаимодействии |
|  [![Отслеживание взгляда: Отслеживание выбора](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) [целевого объекта: Выбор целевого объекта](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [![Отслеживание взгляда: Отслеживание](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) взгляда на навигацию [: Месяца](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [![Отслеживание взгляда: Отслеживание взгляда на тепловую карту](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html): [ Тепловая схема](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Объедините глаза, голоса и руки, чтобы быстро и легко выбирать голограммы в сцене. | Узнайте, как выполнять автоматическую прокрутку текста или свободно изменять содержимое в зависимости от того, что вы ищете.| Примеры ведения журнала, загрузки и визуализации того, что пользователи просматривают в приложении |

# <a name="example-scenes"></a>Примеры сцен
Изучите различные типы взаимодействий и элементов управления пользовательского интерфейса МРТК в [этом примере сцены](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

Другие примеры сцен можно найти в разделе **Assets/микседреалититулкит. examples/демонстрационные материалы**в GitHub с набором средств для [смешанной реальности](https://github.com/Microsoft/MixedRealityToolkit-Unity) .

[![Пример сцены](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>См. также

* [Жесты](gestures.md)
* [Контроллеры движения](motion-controllers.md)
* [UnityEngine. XR. WSA. input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. Инпуттраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
