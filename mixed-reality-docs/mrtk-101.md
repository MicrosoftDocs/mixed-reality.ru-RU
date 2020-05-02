---
title: Общие сведения об MRTK. Как с помощью Набора средств Unity для смешанной реальности выполнять базовые операции взаимодействия (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Как с помощью Набора средств Unity для смешанной реальности выполнять базовые операции взаимодействия (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, МRТК, Набор средств для смешанной реальности, Windows Mixed Reality, проектирование, пример приложения, элементы управления
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028310"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>Общие сведения об MRTK. Как с помощью Набора средств Unity для смешанной реальности выполнять базовые операции взаимодействия (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)

![MRTK](images/MRTK101/MRTK101Cover.png)

Сведения о том, как использовать МRТК для достижения некоторых распространенных моделей взаимодействия в смешанной реальности.

- Как имитировать входные взаимодействия в редакторе Unity?
- Как взять и переместить объект?
- Как изменить размер объекта?
- Как аккуратно переместить или повернуть объект?
- Как сделать, чтобы объект реагировал на входные события?
- Как добавить визуальный отклик?
- Как добавить звуковой отклик?
- Как использовать заготовки кнопок в стиле HoloLens 2?
- Как сделать, чтобы объект следовал за вами?
- Как сделать, чтобы объект поворачивался к вам?

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>Как имитировать взаимодействия в редакторе Unity?
МRТК поддерживает имитацию входных данных в редакторе. Просто запустите сцену, нажав кнопку воспроизведения в Unity. Следующие клавиши позволяют имитировать входные данные.
Чтобы переместить камеру, нажимайте клавиши W, A, S, D.
Чтобы посмотреть по сторонам, перемещайте мышь при нажатой правой кнопке мыши.
Чтобы имитировать поднятие рук вверх, нажмите клавишу пробела (для правой руки) или левую клавишу SHIFT (для левой руки). Чтобы имитировать удержание рук в зоне видимости, нажмите клавишу "T" или "Y", а чтобы имитировать поворот рук, нажимайте клавиши "Q" и "E" (горизонтально) или "R" и "F" (вертикально).

- [Дополнительные сведения об имитации входных данных см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>Как взять и переместить объект?
Чтобы объект поддерживал захват и перемещение, назначьте ему следующие два скрипта: ManipulationHandler.cs и NearInteractionGrabbable.cs (для прямого захвата при отслеживании ввода с помощью рук). ManipulationHandler поддерживает как близкие, так и дальние взаимодействия. Вы можете захватить и переместить объект с использованием ввода с помощью рук в HoloLens 2 (ближнее), телекинеза (дальнее), сигнала контроллера движения (дальнее), курсора взгляда HoloLens, а также касания (дальнее).

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>Как изменить размер объекта?
ManipulationHandler.cs поддерживает масштабирование и вращение двумя руками. Это работает с разными типами входных данных, например ввод с помощью рук в HoloLens 2, ввод с помощью взгляда и жестов в HoloLens 1 или контроллера движений иммерсивной гарнитуры в Windows Mixed Reality.

- [Дополнительные сведения об обработчике манипулирования см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Как аккуратно переместить или повернуть объект?
Назначьте BoundingBox.cs объекту для использования ограничивающего прямоугольника, который представляет собой интерфейс для масштабирования и вращения объекта. По умолчанию в нем отображаются синие маркеры и границы, как в HoloLens 1. Чтобы использовать анимированные маркеры с учетом расстояния до объекта в стиле HoloLens 2, необходимо назначить заготовки и материалы. Дополнительные сведения о конфигурации см. в [документации по ограничивающему прямоугольнику](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) и в примере сцены BoundingBoxExamples.unity.

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [Дополнительные сведения об ограничивающем прямоугольнике см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>Как сделать, чтобы объект реагировал на входные события?
Назначьте объекту PointerHandler.cs. В инспекторе вы сможете применить события OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Чтобы использовать эти события в скрипте, реализуйте IMixedRealityPointerHandler.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Дополнительные сведения о системе ввода см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Как добавить визуальный отклик?
Присвойте объекту Interactable.cs. В инспекторе создайте новую тему. С помощью интерактивных профилей темы вы сможете легко добавить визуальный отклик для всех доступных состояний взаимодействий ввода.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Интерактивный объект предоставляет несколько типов тем, в том числе тему shader, которая позволяет управлять параметрами текстуры для каждого состояния взаимодействия.

- [Дополнительные сведения об интерактивном объекте см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Еще один важный строительный блок для создания визуального отклика — стандартный построитель текстуры MRTK. С помощью шейдера MRTK Standard можно легко добавлять визуальные эффекты для отклика, например эффект указателя и подсветки при приближении. Стандартный шейдер MRTK выполняет намного меньше вычислений, чем стандартный шейдер Unity, поэтому позволяет создать высокопроизводительную среду взаимодействия.

Создайте новый материал и выберите шейдер Mixed Reality Toolkit > Standard (Набор средств для смешанной реальности > Стандартный). Вы также можете выбрать любой из существующих материалов, для которых настроен стандартный шейдер MRTK.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Дополнительные сведения о стандартном шейдере MRTK см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Как добавить звуковой отклик?
Поместите AudioSource в объект. Затем в скриптах, которые предоставляют нужные события ввода (например, Interactable.cs или PointerHandler.cs), присвойте объекту событие и выберите AudioSource.PlayOneShot(). Вы можете использовать собственные звуковые клипы или выбрать подходящий из числа звуковых активов MRTK.

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>Как использовать заготовки кнопок в стиле HoloLens 2?
MRTK предоставляет несколько типов кнопок в стиле оболочки (ОС) HoloLens 2. Они поддерживают сложные типы визуального отклика, например подсветка при приближении, прямоугольник сжатия и эффект ряби на поверхности кнопки.

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

Вам нужно лишь перетащить любую из заготовок нажимаемых кнопок в стиле HoloLens 2 в сцену. В заготовках используется описанный выше Interactable.cs. Вы можете предоставлять в интерактивном объекте события для запуска действий, например OnClick().

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Дополнительные сведения о заготовках кнопок см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>Как сделать, чтобы объект следовал за вами?
Присвойте объекту RadialView.cs. Это часть целой серии скриптов Solver, которые позволяют использовать разные типы размещения объектов в трехмерном пространстве. SolverHandler.cs будет добавлен автоматически.
Ниже вы видите пример конфигурации RadialView, которая позволяет добиться поведения "ленивое следование", например начальное меню в оболочке HoloLens. Вы можете указать минимальную и максимальную дистанцию, а также минимальный и максимальный угол обзора. В следующем примере представлен объект с расстоянием от 0,4 до 0,8 м и диапазоном углов 15°. Измените значение параметра Lerp Time (Время линейной интерполяции), чтобы изменение положения выполнялось быстрее или медленнее.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Дополнительные сведения о инструменте решения см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>Как сделать, чтобы объект поворачивался к вам?
Присвойте объекту скрипт Billboard.cs. Теперь этот объект всегда будет развернут к вам, независимо от вашего положения. Вы можете указать расположение оси вращения.

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Вы готовы создать великолепные взаимодействия для смешанной реальности? Изучите предложенные ниже страницы, чтобы получить дополнительные сведения об MRTK и смешанной реальности.

## <a name="about-the-author"></a>Об авторе

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Дон Юн Парк</b> (Dong Yoon Park)<br>Разработчик средств взаимодействия с пользователем @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>См. также статью

* [Набор средств для смешанной реальности (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity) на сайте GitHub
* [Портал документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Начало работы с MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Рекомендации по переносу кода с HoloToolKit на MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
