---
title: Серия руководств по началу работы, часть 5. Создание динамического содержимого с помощью решателей
description: Из этого курса вы узнаете, как с помощью набора средств для смешанной реальности (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 1a5017d8bc18ef239db88ee62cb2b65c77b2ab6f
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376616"
---
# <a name="5-creating-dynamic-content-using-solvers"></a>5. Создание динамического содержимого с помощью решателей

## <a name="overview"></a>Обзор

В этом учебнике мы рассмотрим способы динамического помещения голограмм с помощью доступных инструментов размещения MRTK, известных как "решатели" и предназначенных для сложных сценариев пространственного размещения. В MRTK решатели — это система сценариев и поведений, которые мы используем, чтобы разрешить объектам следовать за вами, пользователем или другими игровыми объектами на сцене. С их помощью также можно выполнить прикрепление к определенной позиции, что делает приложение интуитивно понятным.

## <a name="objectives"></a>Задачи

* Знакомство с решателями MRTK.
* Узнайте, как использовать решатели для направления пользователя к объектам.
* Узнайте, как использовать решатели для изменения расположения объектов.

## <a name="location-of-solvers-in-the-mrtk"></a>Расположение решателей в MRTK

 Решатели MRTK размещаются в папке пакета SDK MRTK. Чтобы просмотреть доступные в проекте решатели, в окне проекта перейдите к папке **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers**:

![mr-learning-base](images/mr-learning-base/base-05-section1-step1-1.png)

В этом учебнике мы рассмотрим реализацию решателя указателей направлений и решателя размещения касанием. Чтобы получить дополнительную информацию о полном наборе решателей, доступных в MRTK, просмотрите раздел [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) (Решатели) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

> [!NOTE]
> Решатель указателей направлений не расположен в папках решателей, указанных выше. Он расположен в папках Assets > MRTK > SDK > Experimental > Features > Utilities, так как это экспериментальная функция.

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a>Использование решателя указателей направлений для направления пользователя к объектам

В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, щелкните и перетащите заготовку **Chevron** в окно иерархии и задайте для него преобразование **положения**, X = 0, Y = 0, Z = 2, чтобы разместить его рядом с объектом RoverExplorer:

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> Если вы обнаружите, что камера или другие значки в сцене скрывают объекты или отвлекают от них внимание, их можно скрыть, <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведя манипуляторы</a> в отключенное положение, как показано на рисунке выше. Дополнительные сведения о меню Gizmos (Манипуляторы) и его применении для оптимизации представления сцены вы можете найти в <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">этом разделе</a> документации.

Переименуйте вновь добавленный **индикатор** объекта шеврона, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компоненты **DirectionalIndicator** и **контроллер индикатора направления (скрипт)** .

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> При добавлении решателя (в нашем примере — DirectionalIndicator) автоматически добавляется еще компонент SolverHandler, который является обязательным для решателя.

> [!NOTE]
> Контроллер индикатора направления (скрипт) не является частью МРТК, но включен в учебные материалы.

Настройте компоненты DirectionalIndicator и SolverHandler следующим образом:

* Убедитесь, что для параметра **Tracked Target Type** (Тип отслеживаемой цели) компонента **SolverHandler** указано значение **Head** (Головной).
* Назначьте параметру **DirectionalIndicator** компонента **Directional Target** (Целевое направление) значение **RoverExplorer**, перетащив его из окна иерархии в поле **None (Transform)** (Нет (преобразование)).
* Измените значение параметра **View Offset** (Смещение вида) на 0,2.

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-3.png)

Нажмите кнопку Play (Воспроизведение), чтобы перейти в игровой режим, затем нажмите и удерживайте правую кнопку мыши, перемещая указатель мыши влево или вправо, чтобы повернуть направление взгляда и проверить следующее поведение.

* Когда вы выйдете из объекта RoverExplorer, появится объект Indicator и будет указывать на объект RoverExplorer.

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> Если вы не видите в окне Scene (Сцена) луч направления камеры, проверьте, включено ли меню Gizmos (Манипуляторы), как показано на изображении выше.

> [!TIP]
> Сведения о том, как можно использовать встроенный имитатор ввода, см. в руководстве [по использованию имитации ввода с помощью рук в редакторе для тестирования сцены](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene), размещенному на [портале документации MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

> [!TIP]
> Если на компьютере установлен микрофон, можно легко переключить активное состояние панели Diagnostics (Диагностика), отображаемой в окне Game (Игра), с помощью голосовой команды toggle diagnostics (переключить диагностику). Кроме того, ее можно отключить в разделе MRTK Configuration Profile (Профиль конфигурации MRTK) > Diagnostics (Диагностика) > Enable Diagnostics System (Включить систему диагностики). Обычно рекомендуется оставлять систему диагностики активной во время разработки.

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a>Использование решателя размещения касанием, чтобы изменить расположение объектов

В окне Hierarchy (Иерархия) выберите объект RoverExplorer > **RoverAssembly**, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **Tap To Place (Script)** (Размещение касанием — скрипт), и настройте его следующим образом:

* Убедитесь, что для параметра **Tracked Target Type** (Тип отслеживаемой цели) компонента **SolverHandler** указано значение **Head** (Головной).
* Установите флажок **Keep Orientation Vertical** (Оставить вертикальную ориентацию).
* В выпадающем списке **Magnetic Surfaces** > **Element 0** (Магнитные поверхности > Элемент 0) снимите флажки всех параметров, кроме **Spatial Awareness** (Отслеживание пространственного положения).

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> Параметр Magnetic Surfaces (Магнитные поверхности) определяет, какие объекты может обнаружить компонент Tap To Place (Script) (Размещение касанием — скрипт) при размещении объекта. Если изменить параметр на Spatial Awareness (Отслеживание пространственного положения), компонент Tap To Place (Script) (Размещение касанием — скрипт) сможет поместить луноход на объекты в слое Unity с именем Spatial Awareness (Отслеживание пространственного положения), который по умолчанию является сеткой отслеживания пространственного положения, созданной HoloLens.
>
>Чтобы получить дополнительные сведения о слоях, воспользуйтесь <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">этим разделом</a> из документации по Unity.

> [!TIP]
> Если необходимо просмотреть сетку отслеживания пространственного положения при тестировании функций размещения касанием в HoloLens, можно временно установить для параметра отображения наблюдателя виртуальной сетки значение Visible (Видимый). Чтобы вспомнить, как изменить параметр отображения, просмотрите инструкции в разделе [Изменение параметров отображения наблюдателя виртуальной сетки](mr-learning-base-03.md#changing-the-spatial-awareness-display-option).

Если в окне Hierarchy (Иерархия) все еще выбран объект RoverAssembly, в окне инспектора перейдите к событию **On Placing Started ()** и щелкните значок **+** , чтобы добавить новое событие.

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-2.png)

Настройте событие следующим образом:

* Назначьте объект **RoverAssembly** в качестве прослушивателя для события On Placing Started (), перетащив его из окна Hierarchy (Иерархия) в поле **None (Object)** (Отсутствует (объект)).
* В раскрывающемся списке **No Function** (Нет функции) выберите **TapToPlace** > **float SurfaceNormalOffset**, чтобы обновить значение свойства SurfaceNormalOffset при срабатывании события.
* Убедитесь, что для аргумента задано значение **0**.

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-3.png)

В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши пустое место и выберите **3D Object** (Трехмерный объект) > **Cube (Куб)** , чтобы создать временный объект, представляющий землю, и настройте компонент **Transform** (Преобразование) следующим образом:

* **Position** (Положение): X = 0, Y = –1,65, Z = 6.
* **Rotation** (Поворот): X = 0, Y = 0, Z = 0.
* **Scale** (Масштаб): X = 10, Y = 0,2, Z = 10.

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-4.png)

Не отменяя выбор временного куба в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) выберите в раскрывающимся списке **Layers** (Слои) значение, чтобы параметр слоя куба содержал только слой **Spatial Awareness** (Отслеживание пространственного положения).

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-5.png)

Нажмите кнопку Play (Воспроизведение), чтобы перейти в игровой режим, а затем нажмите и удерживайте правую кнопку мыши, пока взгляд не будет направлен на объект RoverAssembly:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-6.png)

Нажмите левую кнопку мыши, чтобы запустить процесс размещения касанием:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-7.png)

Нажмите и удерживайте правую кнопку мыши, перемещая указатель мыши влево или вправо для поворота направления взгляда. Если размещение вас устраивает, нажмите левую кнопку мыши:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-8.png)

После завершения тестирования функции в игровом режиме щелкните правой кнопкой мыши объект Cube (Куб) и нажмите кнопку **Delete** (Удалить), чтобы удалить его со сцены:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a>Поздравляем!

Из этого учебника вы узнали, как использовать решатель указателя направления MRTK, чтобы элемент пользовательского интерфейса интуитивно направлял пользователя к объектам. Вы также узнали, как использовать решатель размещения касанием, чтобы без проблем изменять расположение объектов.

Чтобы получить дополнительные сведения об этих и других решателях в составе MRTK, ознакомьтесь с руководством [Решатели](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Следующее руководство: 6. Создание пользовательских интерфейсов](mr-learning-base-06.md)
