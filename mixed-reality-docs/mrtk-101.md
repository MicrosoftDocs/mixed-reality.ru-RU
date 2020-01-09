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
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>МРТК 101: как использовать Unity набора средств Mixed Reality для базовых взаимодействий (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)

![мртк](images/MRTK101/MRTK101Cover.png)

Узнайте, как использовать МРТК для достижения некоторых наиболее часто используемых общих шаблонов взаимодействия в смешанной реальности.

- Как имитировать входные взаимодействия в редакторе Unity?
- Как взять и переместить объект?
- Как изменить размер объекта?
- Как переместить или повернуть объект с точностью?
- Как сделать объект реакцией на входные события?
- Как добавить визуальную обратную связь?
- Как добавить отзыв о звуках?
- Как использовать кнопку Prefabs в HoloLens 2?
- Как сделать объект следующим?
- Как сделать объект лицом к вам?

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>Как имитировать входные взаимодействия в редакторе Unity?
МРТК поддерживает имитацию входных данных в редакторе. Просто запустите сцену, нажав кнопку воспроизведения Unity. Используйте эти ключи для имитации входных данных.
Чтобы переместить камеру, нажмите клавиши W, A, S, D.
Удерживайте правую кнопку мыши и наведите указатель мыши на нужное место.
Чтобы отобразить смоделированные руки, нажмите клавишу пробела (справа) или клавишу SHIFT слева (слева), чтобы имитировать имитацию руки в представлении, нажмите клавишу «T» или «Y», чтобы повернуть смоделированные руки, нажмите клавишу Q или E (горизонтально)/R или F (вертикально)

- [Дополнительные сведения о моделировании ввода см. в документации по МРТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>Как взять и переместить объект?
Чтобы сделать объект неуправляемым, назначьте следующие два скрипта: ManipulationHandler.cs и Неаринтерактионграббабле. cs (для прямого захвата с помощью входных данных отслеживания) Манипулатионхандлер поддерживает почти и далеко взаимодействия. Вы можете захватить и переместить объект с использованием входных данных отслеживания с помощью HoloLens 2 (NEAR), руки (FAR), подвижного контроллера движения (FAR), курсора HoloLens, & воздушного касания (FAR).

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>Как изменить размер объекта?
ManipulationHandler.cs поддерживает двустороннюю масштабирование и вращение. Это работает с различными типами входных данных, такими как ввод с клавиатуры HoloLens 2, элемент управления "аналитика" HoloLens 1, ввод жеста, а также входные данные контроллера движения в Windows Mixed Reality.

- [Дополнительные сведения о обработчике манипуляций см. в документации по МРТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Как переместить или повернуть объект с точностью?
Назначьте BoundingBox.cs объекту для использования ограничивающего прямоугольника, который является интерфейсом для масштабирования и поворота объекта. По умолчанию он показывает синие маркеры и провода в стиле HoloLens 1. Чтобы использовать в стиле HoloLens 2 анимированные маркеры на основе расположения, необходимо назначить Prefabs и материалы. Сведения о конфигурации см. в [документации по ограничивающему прямоугольнику](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) и в сцене баундингбоксексамплес. Unity.

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [Дополнительные сведения о ограничивающем прямоугольнике в документации по МРТК](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>Как сделать объект реакцией на входные события?
Назначьте PointerHandler.cs объекту. В Инспекторе вы сможете использовать события Онпоинтердовн (), Онпоинтеруп (), Онпоинтеркликкед (), Онпоинтердрагжед () для использования этих событий в скрипте, реализовать Имикседреалитипоинтерхандлер.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Дополнительные сведения о системе ввода в документации по МРТК](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Как добавить визуальную обратную связь?
Назначьте Interactable.cs объекту. В инспекторе создайте новую тему. С помощью профилей темы, доступных для взаимодействия, можно легко добавить визуальную обратную связь во все доступные состояния взаимодействия.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Взаимодействие предоставляет различные типы тем, включая тему шейдера, которая позволяет управлять свойствами шейдера для каждого состояния взаимодействия.

- [Дополнительные сведения о взаимодействии в документации по МРТК](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Другим важным стандартным блоком для визуальной обратной связи является стандартный шейдер МРТК. С помощью шейдера МРТК Standard можно легко добавлять визуальные эффекты обратной связи, такие как навести указатель на освещение и освещение. Так как шейдер МРТК Standard выполняет значительно меньше вычислений, чем стандартный шейдер Unity, вы можете создать среду выполнения.

Создайте новый материал и выберите шейдер "Mixed Reality Toolkit > Standard". Или можно выбрать один из существующих материалов, использующих шейдер МРТК Standard.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Дополнительные сведения о шейдере МРТК Standard см. в документации по МРТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Как добавить отзыв о звуках?
Добавьте Аудиосаурце в объект. Затем в скриптах, которые предоставляют входные события (например, Interactable.cs или PointerHandler.cs), назначьте объект событию и выберите Аудиосаурце. Плайонешот (). Вы можете использовать звуковые клипы или выбрать один из звуковых ресурсов МРТК.

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>Как использовать кнопку Prefabs в HoloLens 2?
МРТК предоставляет различные типы кнопок в стиле оболочки HoloLens (ОС). Он предоставляет сложные визуальные отзывы, такие как освещение, сжатие и эффекты Ripple на поверхности кнопки.

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

Просто перетащите одну из prefab кнопок в стиле HoloLens 2 в сцену. Prefab использует Interactable.cs, представленный выше. Можно использовать предоставляемые события, такие как onclick (), в взаимодействии, чтобы активировать действия.

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Дополнительные сведения о кнопке Prefabs в документации МРТК](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>Как сделать объект следующим?
Назначение скрипта RadialView.cs объекту. Она является частью серии сценариев поиска решений, которая позволяет создавать различные типы позиционирования объектов в трехмерном пространстве. SolverHandler.cs будет автоматически добавлен.
Ниже приведен пример настройки Радиалвиев для выполнения тега "ленивой" функции, как и в меню "Пуск" в оболочке HoloLens. Вы можете указать минимальное и максимальное расстояние, а также минимальные и максимальные уровни представления. В приведенном ниже примере показано размещение объекта между 0,4 m и 0,8 m диапазоном в 15 °. Настройте значения времени Лерп, чтобы обеспечить быстрое или медленное выполнение позиционированного обновления.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Дополнительные сведения об поисковых решениях см. в документации по МРТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>Как сделать объект лицом к вам?
Назначение скрипта Billboard.cs объекту. Она всегда будет лицом, независимо от вашей должности. Можно указать параметр оси сведения.

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Готовы к созданию великолепных возможностей для смешанной реальности? Посетите страницы ниже и Узнайте больше о МРТК и смешанной реальности.

## <a name="about-the-author"></a>Об авторе

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Донг Йоон</b><br>@Microsoft конструктора UX</td>
</tr>
</table>

## <a name="see-also"></a>См. также статью

* [Набор средств для смешанной реальности — Unity (МРТК) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Портал документации по МРТК](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [начало работы с МРТК](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Руководство по переносу Холотулкит в МРТК](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
