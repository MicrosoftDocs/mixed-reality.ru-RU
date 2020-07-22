---
title: Серия учебников по началу работы, часть 4. Размещение объектов в сцене
description: Из этого курса вы узнаете, как с помощью набора средств для смешанной реальности (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 356bfa788cd28e8c763a45a2d44c3a1241b8467e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306469"
---
# <a name="4-positioning-objects-in-the-scene"></a>4. Размещение объектов в сцене

## <a name="overview"></a>Обзор

В этом руководстве показано, как импортировать предоставляемые активы и размещать указанные объекты в сцене.

## <a name="objectives"></a>Задачи

* Научиться размещать объекты в сцене.
* Научиться использовать функцию коллекции объектов сетки в MRTK.

## <a name="importing-the-tutorial-assets"></a>Импорт активов для руководства

Скачайте и импортируйте следующий пользовательский пакет Unity:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage).

Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:

![mr-learning-base](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт набора средств для Смешанной реальности](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

## <a name="creating-the-parent-object"></a>Создание родительского объекта

Щелкните правой кнопкой мыши пустое место в окне Hierarchy (Иерархия) и выберите **Create Empty** (Создать пустой), чтобы добавить в сцену пустой объект.

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> Чтобы отобразить окна Scene (Сцена) и Game (Игра) рядом друг с другом, как на изображении ниже, перетащите окно Game (Игра) и поместите его справа от окна Scene (Сцена). Дополнительные сведения см. на странице <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Настройка рабочего пространства</a> в документации по Unity.

Щелкните правой кнопкой мыши созданный объект, выберите **Rename** (Переименовать) и измените имя на **RoverExplorer**:

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-2.png)

Выбрав объект RoverExplorer в окне инспектора настройте компонент **Transform** (Преобразование) следующим образом:

* **Position** (Положение): X = 0, Y = -0,6, Z = 2.
* **Rotation** (Поворот): X = 0, Y = 0, Z = 0.
* **Scale** (Масштаб): X = 1, Y = 1, Z = 1.

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> Камера представляет голову пользователя в исходном положении: X = 0, Y = 0, Z = 0. Обычно одна единица в Unity равна примерно одному метру в физическом мире. Но из этого правила могут быть исключения, например для дочерних объектов масштабированных объектов. В приведенном выше сценарии для RoverExplorer задается положение на расстоянии 2 метра перед головой пользователя и 0,6 метра ниже нее.

## <a name="adding-the-tutorial-prefabs"></a>Добавление заготовок для выполнения задач руководства

В окне Project (Проект) перейдите к папке **Assets (Активы)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Заготовки)** .

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Заготовкой</a> называется предварительно настроенный игровой объект (GameObject), который хранится в качестве актива Unity и может повторно использоваться в проекте.

В окне Project (Проект) щелкните и перетащите заготовку **Table** (Таблица) в объект **RoverExplorer**, чтобы сделать ее дочерним объектом RoverExplorer. Затем в окне инспектора настройте компонент **Transform** (Преобразование) следующим образом:

* **Position** (Положение): X = 0, Y = -0,005, Z = 0.
* **Rotation** (Поворот): X = 0, Y = 0, Z = 0.
* **Scale** (Масштаб): X = 1,2, Y = 0,01, Z = 1,2.

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> Для отображения сцены, как на рисунке ниже, используйте <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Манипулятор сцены) справа в верхнем углу окна сцены, чтобы направить угол взгляда вдоль оси Z вперед. Затем дважды щелкните объект MixedRealityPlayspace, чтобы перевести на него фокус камеры, и при необходимости увеличьте масштаб.

В окне Project (Проект) щелкните и перетащите заготовку **RoverAssembly** в объект **RoverExplorer**, чтобы сделать ее дочерним объектом RoverExplorer. Затем в окне инспектора настройте компонент **Transform** (Преобразование) следующим образом:

* **Position** (Положение): X = -0,1, Y = 0, Z = 0.
* **Rotation** (Поворот): X = 0, Y = -135, Z = 0.
* **Scale** (Масштаб): X = 1, Y = 1, Z = 1.

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a>Упорядочение объектов в коллекции

В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши объект **RoverExplorer** и выберите **Create Empty** (Создать пустой), чтобы добавить пустой объект в качестве дочернего объекта RoverExplorer. Присвойте объекту имя **RoverParts** и настройте компонент **Transform** (Преобразование), следующим образом:

* **Position** (Положение): X = 0, Y = 0,06, Z = 0.
* **Rotation** (Поворот): X = 0, Y = 90, Z = 0.
* **Scale** (Масштаб): X = 1, Y = 1, Z = 1.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-1.png)

В окне Hierarchy (Иерархия) выберите все дочерние объекты RoverExplorer > RoverAssembly > RoverModel > **Parts** (Части). Щелкните их правой кнопкой мыши и выберите **Duplicate** (Дублировать), чтобы создать копию каждой части.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> Чтобы выбрать несколько смежных объектов, нажав и удерживая клавишу SHIFT, выберите первый и последний объект.

Оставив выбранными только что продублированные дочерние объекты Parts (Части), щелкните и перетащите их в объект **RoverParts**, чтобы сделать их дочерними объектами RoverParts.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-3.png)

Чтобы со сценой было проще работать, в окне Hierarchy (Иерархия) щелкните значок с изображением **глаза** слева от объекта. Для объекта **RoverExplorer** будет отключена **видимость сцены**. Так вы скроете объект в окне сцены, не изменяя его внутриигровую видимость.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> Дополнительные сведения об элементах управления видимостью и их применении для оптимизации представления сцены и рабочего процесса вы можете найти на странице <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Видимость сцены</a> в документации по Unity.

В окне Hierarchy (Иерархия) очистите имена дочерних объектов RoverParts, изменив добавленную запись **(1)** на **_Part**:

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-5.png)

В окне Hierarchy (Иерархия) выберите объект **RoverParts**. Затем в окне инспектора нажмите кнопку **Add Component** (Добавить компонент). Найдите и выберите компонент **GridObjectCollection**, чтобы добавить его в объект RoverParts:

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-6.png)

Настройте значения компонента **GridObjectCollection** следующим образом:

* **Sort Type** (Тип сортировки): Alphabetical (По алфавиту).
* **Layout** (Макет): По горизонтали
* **Cell Width** (Ширина ячейки): 0,25.
* **Distance from parent** (Расстояние от родительского объекта): 0,38.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-7.png)

Затем нажмите кнопку **Update Collection** (Обновить коллекцию), чтобы обновить положение дочерних объектов RoverParts.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a>Поздравляем!

Из этого руководства вы узнали, как разместить объекты в сцене относительно пользователя и упорядочить объекты в коллекции с помощью функции коллекции объектов сетки MRTK.

[Следующее руководство: 5. Создание динамического содержимого с помощью решателей](mr-learning-base-05.md)
