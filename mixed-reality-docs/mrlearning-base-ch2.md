---
title: Серия руководств по началу работы, часть 3 Создание пользовательского интерфейса и настройка Набора средств для смешанной реальности
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376141"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. Создание пользовательского интерфейса и настройка Набора средств для смешанной реальности
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

В предыдущем руководстве вы изучили некоторые возможности Набора средств для смешанной реальности (MRTK) на примере простейшего приложения для HoloLens 2. Из этого руководства вы узнаете, как создать и упорядочить кнопки и текстовые панели пользовательского интерфейса, а также как применить для каждой из кнопок взаимодействие по умолчанию (касание). Кроме того, вы освоите добавление простых действий и эффектов, например изменение размера, звука и цвета для объектов. В этом модуле представлены основные понятия, связанные с изменением профилей MRTK, начиная с отключения визуализации сетки для [пространственного картирования](spatial-mapping.md).

## <a name="objectives"></a>Задачи

* Настройка профилей набора средств для смешанной реальности
* Взаимодействие с голограммами через кнопки и элементы пользовательского интерфейса
* Базовый ввод данных и взаимодействие с помощью средства отслеживания руки

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Настройка профилей Набора средств для смешанной реальности (изменение параметра отображения для отслеживания пространственного положения)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

Из этого раздела вы узнаете, как настраивать профили МRТК по умолчанию.

В этом конкретном примере показано, как скрыть сетку отслеживания пространственного положения, изменив параметры наблюдателя виртуальной сетки. Те же принципы вы можете применить, чтобы настроить любые параметры или значения в профилях MRTK.

Ниже приведены основные шаги, которые позволяют скрыть сетку отслеживания пространственного положения.

1. Клонирование профиля конфигурация по умолчанию
2. Включение системы отслеживания пространственного положения
3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения
4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения
5. Изменение видимости сетки отслеживания пространственного положения

> [!NOTE]
> По умолчанию профили MRTK недоступны для редактирования. Это шаблоны профилей по умолчанию, которые вам нужно клонировать, прежде чем их можно будет редактировать. Существует несколько вложенных уровней профилей. Таким образом, при настройке одного или нескольких параметров часто нужно клонировать и редактировать несколько профилей.

### <a name="1-clone-the-default-configuration-profile"></a>1. Клонирование профиля конфигурация по умолчанию

> [!NOTE]
> Профиль конфигурации расположен на высшем уровне профилей. Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.

Выбрав объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), перейдите в окно Inspector (Инспектор) и измените **профиль конфигурации** Набора средств для смешанной реальности на **DefaultHoloLens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

В окне клонирования профиля нажмите кнопку **Клонировать**, чтобы создать изменяемую копию **DefaultHololens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.

> [!TIP]
> Не забывайте сохранять работу при работе с руководством.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Включение системы отслеживания пространственного положения

Сохраняя выделение объекта **MixedRealityToolkit** в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) выберите вкладку **Spatial Awareness** (Отслеживание пространственного положения), а затем установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения

На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

В окне клонирования профиля нажмите кнопку **Clone** (Клонировать), чтобы создать редактируемую копию **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения

Оставаясь на вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель виртуальной сетки Windows Mixed Reality), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

В окне клонирования профиля нажмите кнопку **Clone** (Клонировать), чтобы создать изменяемую копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Изменение видимости сетки отслеживания пространственного положения

В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Перекрытия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать. Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.

Вы только что узнали, как изменить параметр в профиле MRTK. Как вы уже поняли, для настройки параметров MRTK нужно создать копии стандартных профилей. Так как стандартные профили недоступны для редактирования, они всегда используются в качестве справочного варианта, если придется вернуться к параметрам по умолчанию. Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля для Набора средств для смешанной реальности](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) на [портале документации по МRТК](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>Обработка жестов и нажатий активных кнопок с помощью технологии отслеживания рук

Из этого раздела вы узнаете, как использовать отслеживание рук для нажатия кнопок и запуска событий, чтобы вызвать действие при нажатии кнопки.

В этом конкретном примере показано, как изменить цвет куба при нажатии кнопки и вернуть исходный цвет при отпускании кнопки. Но такими же методами вы можете создавать любые другие события.

Основные действия, которые нужно выполнить для изменения цвета куба:

1. Добавление заготовки нажимаемой кнопки в сцену.
2. Добавление куба в сцену.
3. Настройка типа события InteractableOnPressReceiver.
4. Настройка куба для получения события OnPress.
5. Определение действия, запускаемого событием OnPress.
6. Настройка куба для получения события OnRelease.
7. Определение действия, запускаемого событием OnRelease.
8. Тестирование кнопки с помощью имитации в редакторе.

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. Добавление заготовки нажимаемой кнопки в сцену

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Заготовкой</a> называется предварительно настроенный игровой объект (GameObject), который хранится в качестве актива Unity и может повторно использоваться в проекте.

В **окне проекта** в строку поиска введите запрос **PressableButtonHoloLens2**, чтобы найти заготовку для этого примера:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

В **результатах поиска** выберите заготовку **PressableButtonHoloLens2** и **перетащите** ее в окно **Hierarchy** (Иерархия), чтобы добавить в сцену:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> Для отображения сцены, как на рисунке ниже, дважды щелкните объект PressableButtonHoloLens2 в окне Hierarchy (Иерархия), чтобы перевести на него фокус, а затем используйте <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Манипулятор сцены) в правом верхнем углу окна сцены, чтобы направить угол взгляда вдоль оси Z вперед.

Сохраняя выделение объекта **PressableButtonHoloLens2**, в окне **Inspector** (Инспектор) выполните следующее:

* Измените для преобразования свойство **Position** (Положение) так, чтобы объект оказался перед камерой, размещенной в точке начала координат, например в точке с координатами x = 0, y = 0 и z = 0,5.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> Обычно одна единица положения в Unity примерно эквивалентна одному метру в реальных условиях. Но из этого правила могут быть исключения, например для дочерних объектов масштабированных объектов.

### <a name="2-add-a-cube-to-the-scene"></a>2. Добавление куба в сцену

Щелкните правой кнопкой мыши пустое место в окне Hierarchy (Иерархия) и выберите **3D Object** > **Cube** (Трехмерный объект > Куб), чтобы добавить куб в сцену:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

Сохраняя выделение объекта **Cube** (Куб), в окне **Inspector** (Инспектор) выполните следующее:

* Измените для преобразования свойство **Position** (Положение) так, чтобы объект оказался рядом с нажимаемой кнопкой, но не перекрыл ее, например в точке с координатами x = 0, y = 0,04 и z = 0,5.
* Измените для преобразования свойство **Scale** (Масштаб) до нормального размера, например x = 0,02, y = 0,02 и z = 0,02.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. Настройка типа события InteractableOnPressReceiver

В окне Hierarchy (Иерархия) выберите объект **PressableButtonHoloLens2**, затем в окне **Inspector** (Инспектор) откройте **меню "гамбургер"** и выберите **Collapse All Components** (Свернуть все компоненты), чтобы получить представление о компонентах этого объекта:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

Разверните компонент **Interactable (Script)** (Интерактивный — скрипт), затем найдите и разверните раздел **Events** > **Receivers** (События > Получатели):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

Щелкните кнопку **Add Event** (Добавить событие), чтобы создать получатель события с типом **InteractableOnPressReceiver**:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> Тип получателя событий InteractableOnPressReceiver отвечает за реагирование кнопки на событие нажатия, когда отслеживаемая рука нажимает эту кнопку.

Для нового получателя событий измените значение параметра **Interaction Filter** (Фильтр взаимодействия) на **Near and Far** (Ближнее и дальнее):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. Настройка куба для получения события OnPress

В окне Hierarchy (Иерархия) **щелкните и перетащите** объект **Cube** в поле объекта **Event Properties** (Свойства события), отвечающее за событие **On Press ()** , чтобы назначить этот куб получателем события OnPress() этого объекта:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. Определение действия, запускаемого событием OnPress

Щелкните раскрывающийся список действий, где сейчас выбран вариант **No Function** (Без действий), и выберите **MeshRenderer** > **Material material** (Материал material), чтобы значение материала куба изменялось при срабатывании события OnPress:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

Щелкните небольшой значок в форме **круга** рядом с полем материала, где сейчас выбран вариант **None (Material)** (Нет (материал)), чтобы открыть окно выбора материала:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

В окне выбора материала выполните **поиск** по строке **MRTK_Standard** и выберите подходящий материал, например **MRTK_Standard_Cyan**, чтобы изменять цвет куба при нажатии кнопки:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. Настройка куба для получения события OnRelease

**Повторите** шаг 4 для события OnRelease, назначив тот же объект **Cube** в качестве получателя события **On Release ()** .

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. Определение действия, запускаемого событием OnRelease

**Повторите** шаг 5 для события OnRelease, но теперь выберите материал **MRTK_Standard_LightGray**, чтобы куб возвращался к исходному светло-серому цвету при отпускании кнопки:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. Тестирование кнопки с помощью имитации в редакторе

Нажмите кнопку **Play** (Играть), чтобы перейти в игровой режим встроенного имитатора ввода и протестировать только что настроенные действия кнопки.

Кнопка не нажата (пробел и вращение колесика мыши назад):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

Кнопка нажата (пробел и вращение колесика мыши вперед):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> Сведения о том, как можно использовать встроенный имитатор ввода, см. в руководстве [по использованию имитации ввода с помощью рук в редакторе для тестирования сцены](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene), размещенному на [портале документации MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Создание панели кнопок с помощью коллекции объектов сетки MRTK

Из этого раздела вы узнаете, как реализовать автоматическое выравнивание нескольких кнопок с помощью средства GridObjectCollection из MRTK, чтобы получить аккуратный пользовательский интерфейс.

В этом примере показано, как создать панель с пятью кнопками, выровненными по горизонтали. Но такими же методами вы можете создавать любые другие макеты.

Для получения этого результата вам нужно выполнить следующие шаги:

1. Присвоение родительского объекта для объектов кнопок
2. Добавление и настройка компонента Grid Object Collection (Script) (Коллекция объектов сетки — скрипт).
3. Тестирование кнопок с помощью имитации в редакторе

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. Присвоение родительского объекта для объектов кнопок

Щелкните правой кнопкой мыши пустое место в окне Hierarchy (Иерархия) и выберите **Create Empty** (Создать пустой):

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

Щелкните новый объект правой кнопкой мыши, выберите **Rename** (Переименовать) и присвойте ему подходящее имя, например **ButtonCollection**:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

Выберите объект **PressableButtonHoloLens2** и **перетащите** его поверх объекта **ButtonCollection**, чтобы сделать его дочерним для объекта ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

Щелкните объект **PressableButtonHoloLens2** правой кнопкой мыши и выберите действие **Duplicate** (Дублировать), чтобы создать копию этого объекта:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

**Повторите** этот шаг еще четыре раза, чтобы получить пять объектов PressableButtonHoloLens2.

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Добавление и настройка компонента Grid Object Collection (Script) (Коллекция объектов сетки — скрипт).

Сохраняя выбранным объект ButtonCollection в окне Hierarchy (Иерархия), щелкните в окне Inspector (Инспектор) кнопку **Add Component** (Добавить компонент), затем найдите и выберите **Grid Object Collection** (Коллекция объектов сетки), чтобы добавить компонент "Grid Object Collection (Script)" (Коллекция объектов сетки — скрипт) к объекту ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

Настройте компонент "Grid Object Collection (Script)" (Коллекция объектов сетки — скрипт) следующим образом.

* Для параметра **Num Rows** (Число строк) установите значение 1, чтобы все кнопки разместились в одном ряду.
* Для параметра **Cell Width** (Ширина ячейки) установите значение 0,05, чтобы задать расстояние между кнопками в одном ряду.

Нажмите кнопку **Update Collection** (Обновить коллекцию), чтобы применить новую конфигурацию.

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> Изменения конфигурации, которые вы только что применили, — это минимально необходимый набор настроек для размещения кнопок в один горизонтальный ряд. Но в будущих проектах, в зависимости от ориентации родительского и дочерних объектов и (или) других факторов, может потребоваться изменить и другие параметры, например Orient Type (Тип ориентации). Дополнительные сведения о компоненте Grid Object Collection (Коллекция объектов сетки) в MRTK вы можете найти в [руководстве по коллекции скриптов](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

Сохраняя выбранным объект ButtonCollection в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) измените для этого объекта ButtonCollection значение преобразования **Position** (Положение), чтобы его дочерние объекты располагались перед камерой, размещенной в точке начала координат, например в точке с координатами x = 0, y = 0, и z = 0,5.

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> При первом добавлении в сцену заготовки PressableButtonHoloLens2, как описано выше в разделе [Обработка жестов и нажатий активных кнопок с помощью технологии отслеживания рук](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons), вы разместили эту заготовку перед камерой. Но из-за того, что коллекция объектов сетки определяет положение своих дочерних объектов, для дочернего объекта PressableButtonHoloLens2 положение по оси Z было автоматически сброшено на 0 в соответствии со значением 0 у параметра "Distance from parent" (Дистанция от родительского объекта) в объекте Grid Object Collection (Коллекция объектов сетки). По этой причине, а также для упорядоченности положений родительских и дочерних объектов, мы переместили объект ButtonCollection вперед, вместо того, чтобы изменять значение параметра "Distance from parent" (Дистанция от родительского объекта) для смещения дочернего объекта PressableButtonHoloLens2.

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. Тестирование кнопок с помощью имитации в редакторе

Нажмите кнопку Play (Играть), чтобы перейти в игровой режим и с помощью встроенного имитатора ввода протестировать кнопки в только что созданном наборе кнопок.

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> Теперь, если нажать любую из пяти кнопок, куб станет голубым. Чтобы взаимодействие стало интереснее, настройте для каждой кнопки другой цвет куба, используя полученные в этом руководстве знания.

## <a name="adding-text-into-your-scene"></a>Добавление текста в сцену

Из этого раздела вы узнаете, как добавить текст в интерфейс для смешанной реальности с помощью объекта TextMesh Pro, который вы подготовили в разделе [Импорт требуемых ресурсов TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) предыдущего руководства.

В этом конкретном примере вы добавите простую метку под коллекцией кнопок, которую вы создали в предыдущем разделе.

Щелкните правой кнопкой объект ButtonCollection и выберите элементы **3D Object** > **Text — TextMeshPro** (Трехмерный объект > Текст — TextMeshPro), чтобы создать объект TextMeshPro в качестве дочернего для объекта ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

Сохраняя выделение только что созданного объекта TextMesh Pro, измените его положение и размер в окне Inspector (Инспектор) так, чтобы объект был расположен прямо под коллекцией кнопок, например так:

* в разделе Rect Transform укажите для **Pos Y** значение -0,0425;
* в разделе Rect Transform укажите для **Width** значение 0,24;
* в разделе Rect Transform укажите для **Height** значение 0,024.

Теперь измените текст с учетом назначения этой метки и выберите параметры шрифта для аккуратного размещения этого текста на метке, например так:

* в разделе Text Mesh Pro (Script) укажите для **Text** (Текст) значение Button Collection (Коллекция кнопок);
* в разделе Text Mesh Pro (Script) укажите для **Font Style** (Стиль шрифта) значение Bold (Полужирный);
* в разделе Text Mesh Pro (Script) укажите для **Font Size** (Размер шрифта) значение 0,2;
* в разделе Text Mesh Pro (Script) укажите для **Alignment** (Выравнивание) значения Center (по центру) и Middle (посередине).

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>Поздравляем!

В рамках этого руководства вы научились клонировать и настраивать параметр профиля MRTK. Кроме того, вы узнали, как вызывать события для кнопок с помощью функции отслеживания рук в HoloLens 2. Наконец, вы создали простой пользовательский интерфейс с помощью компонента коллекции объектов сетки в MRTK и объекта Text Mesh Pro в Unity.

[Следующее руководство: 4. Размещение динамического содержимого и использование решателей](mrlearning-base-ch3.md)
