---
title: Серия руководств по началу работы, часть 6. Создание пользовательских интерфейсов
description: Из этого курса вы узнаете, как с помощью набора средств для смешанной реальности (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4eecbd7d292a4d23e0dddc8e9244ed2701a10381
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376626"
---
# <a name="6-creating-user-interfaces"></a>6. Создание пользовательских интерфейсов

## <a name="overview"></a>Обзор

В этом учебнике показано, как создать простой пользовательский интерфейс, используя кнопки MRTK и заготовки меню вместе с компонентом Unity TextMeshPro. Кроме того, здесь приведены сведения о том, как настроить кнопки для запуска событий и добавить динамические элементы интерфейса подсказки, чтобы предоставить пользователю дополнительную информацию.

## <a name="objectives"></a>Задачи

* Упорядочивание кнопок в коллекции
* Использование заготовок меню MRTK
* Взаимодействие с голограммами через кнопки и меню элементов пользовательского интерфейса
* Добавление текстовых элементов
* Динамическое создание подсказок для объектов

## <a name="creating-a-static-panel-of-buttons"></a>Создание статической панели кнопок

В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши объект **RoverExplorer** и выберите **Create Empty** (Создать пустой), чтобы добавить пустой объект в качестве дочернего объекта RoverExplorer, присвойте имя объекту **Buttons** (Кнопки) и настройте компонент **Transform** (Преобразование), как описано ниже.

* **Position** (Положение): X = –0,6, Y = 0,036, Z = –0,5
* **Rotation** (Поворот): X = 90, Y = 0, Z = 0.
* **Scale** (Масштаб): X = 1, Y = 1, Z = 1.

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-1.png)

В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, щелкните и перетащите заготовку **PressableRoundButton** к объекту **Buttons** (Кнопки), затем щелкните правой кнопкой мыши объект PressableRoundButton и выберите **Duplicate** (Дублировать), чтобы создать копию. Повторяйте эти действия до тех пор, пока у вас не будет три объекта PressableRoundButton:

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-2.png)

В окне Hierarchy (Иерархия) выберите объект **Buttons** (Кнопки), затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **GridObjectCollection** и настройте его, как описано ниже.

* **Sort Type** (Тип сортировки): Child Order (В порядке дочерних объектов)
* **Layout** (Макет): По горизонтали
* **Cell Width** (Ширина ячейки): 0,2
* **Anchor** (Привязка): Посередине слева

Затем нажмите кнопку **Update Collection** (Обновить коллекцию), чтобы обновить положение дочерних объектов объекта Buttons (Кнопки):

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-3.png)

В окне Hierarchy (Иерархия) присвойте имя кнопкам **Hints** (Подсказки), **Explode** (Развернуть) и **Reset** (Сброс).

Для каждой кнопки выберите дочерний объект **SeeItSayItLabel** > **TextMeshPro**, а затем в окне Inspector (Инспектор) измените текст соответствующего компонента **TextMeshPro - Text** (TextMeshPro — текст), чтобы он соответствовал именам кнопок:

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-4.png)

После этого сверните дочерние объекты объекта Buttons (Кнопки).

В окне Hierarchy (Иерархия) выберите объект кнопки **Hints** (Подсказки), затем в окне Inspector (Инспектор) настройте интерактивное событие **OnClick ()** следующим образом:

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverAssembly**.
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **PlacementHintsController** > **TogglePlacementHints ()** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-5.png)

В окне Hierarchy (Иерархия) выберите объект кнопки **Explode** (Развернуть), затем в окне Inspector (Инспектор) настройте интерактивное событие **OnClick ()** следующим образом:

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverAssembly**.
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ExplodedViewController** > **ToggleExplodedView ()** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-6.png)

Нажмите кнопку Play (Воспроизведение), чтобы перейти в игровой режим. Затем нажмите и удерживайте клавишу пробела, чтобы активировать руку, и с помощью мыши нажмите кнопку **Hints** (Подсказки), чтобы переключить видимость объектов с подсказками о размещении:

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-7.png)

и кнопку **Explode** (Развернуть) для включения и выключения развернутого представления:

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>Создание динамического меню, которое следует за пользователем

В окне Project (Проект) перейдите к папке **Assets** > **MRTK** > **SDK** > **UX** > **Prefabs** > **Menus**, щелкните и перетащите заготовку **NearMenu4x1** в окно Hierarchy (Иерархия), установите для параметра преобразования **Position** (Позиция) значение X = 0, Y = –0,4, Z = 0 и настройте его, как описано ниже.

* Убедитесь, что для параметра **Tracked Target Type** (Тип отслеживаемой цели) компонента **SolverHandler** указано значение **Head** (Головной).
* Установите флажок рядом с компонентом Solver **RadialView**, чтобы он был включен по умолчанию.

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-1.png)

В окне Hierarchy (Иерархия) переименуйте объект в **Menu** (Меню), затем разверните его дочерний объект **ButtonCollection**, чтобы открыть четыре кнопки:

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-2.png)

Переименуйте первую кнопку на **Indicator** (Индикатор), затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт), как описано ниже.

* Измените значение для параметра **Main Label Text** (Текст основной метки), чтобы он соответствовал названию кнопки.
* В поле **None (Object)** (Отсутствует (Объект)) укажите объект **Indicator** (Индикатор).
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **GameObject** > **SetActive (bool)** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.
* Убедитесь, что флажок аргумента **установлен**.
* Измените параметр **Icon** (Значок) на значок поиска.

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-3.png)

В окне Hierarchy (Иерархия) выберите объект **Indicator** (Индикатор), затем в окне Inspector (Инспектор) снимите флажок рядом с его именем, чтобы сделать его неактивным по умолчанию:

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> Теперь после запуска приложения объект Indicator (Индикатор) будет по умолчанию отключен (его можно включить с помощью кнопки Indicator (Индикатор)).

Переименуйте вторую кнопку на **TapToPlace**, затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт), как описано ниже.

* Измените значение для параметра **Main Label Text** (Текст основной метки), чтобы он соответствовал названию кнопки.
* В поле **None (Object)** (Отсутствует (Объект)) укажите объект RoverExplorer > **RoverAssembly**.
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **TapToPlace** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.
* Убедитесь, что флажок аргумента **установлен**.
* Измените параметр **Icon** (Значок) на значок руки с лучом.

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-5.png)

В окне Hierarchy (Иерархия) выберите объект **RoverAssembly**, затем в окне Inspector (Инспектор) настройте компонент **Tap To Place (Script)** (Размещение касанием — скрипт), как описано ниже.

* Снимите флажок рядом с его именем, чтобы сделать его неактивным по умолчанию.
* В разделе события **On Placing Started ()** щелкните значок **+** , чтобы добавить новое событие.
* В поле **None (Object)** (Отсутствует (Объект)) укажите объект RoverExplorer > **RoverAssembly**.
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **TapToPlace** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.
* Убедитесь, что флажок аргумента **снят**.

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> Теперь при запуске приложения функция Tap to Place (Размещение касанием) будет отключена по умолчанию (ее можно включить с помощью кнопки Tap to Place (Размещение касанием)). Кроме того, когда операция размещения нажатием завершена, функция отключится автоматически.

## <a name="adding-text-to-the-scene"></a>Добавление текста в сцену

В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши объект **Table** (Таблица) и выберите **3D Object** (Трехмерный объект) > **Text - TextMeshPro** (Текст — TextMeshPro), чтобы добавить текстовый объект в качестве дочернего для объекта Table (Таблица), а затем в окне Inspector (Инспектор) настройте компонент **Rect Transform** (Прямоугольное преобразование), как описано ниже.

* Укажите для параметра **Pos Y** (Позиция Y) значение 1.
* Укажите для параметра **Width** (Ширина) значение 1.
* Укажите для параметра **Height** (Высота) значение 1.
* Укажите для параметра **Rotation X** (Поворот X) значение 90.

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-1.png)

Затем настройте компонент **TextMeshPro - Text** (TextMeshPro — текст), как описано ниже.

* Укажите для параметра **Text** (Текст) значение Rover Explorer.
* Укажите для параметра **Font Style** (Стиль шрифта) значение "Полужирный".
* Укажите для параметра **Font Size** (Размер шрифта) значение 1.
* Укажите для параметра Extra Settings (Дополнительные параметры) > **Margins** (Поля) значение 0,03.

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>Добавление подсказок

В окне Project (Проект) перейдите в папку **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip**, чтобы найти заготовки подсказок:

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-1.png)

В окне Hierarchy (Иерархия) разверните объект RoverExplorer > **RoverParts** и выберите все его дочерние объекты лунохода, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить **ToolTipSpawner** ко всем выбранным объектам и настроить его, как описано ниже.

* Убедитесь, что установлен флажок **Focus Enabled** (Фокус включен), чтобы пользователь смог посмотреть на часть, где должна появиться подсказка.
* Укажите заготовку **Simple Line ToolTip** (Подсказка в отдельной строке) из окна Project (Проект) в поле **Tool Tip Prefab** (Заготовка подсказки).
* Измените значение параметра ToolTip Override Settings (Параметры переопределения подсказок) > **Settings Mode** (Режим параметров) на значение **Override** (Переопределение).
* Измените значение параметра ToolTip Override Settings (Параметры переопределения подсказок) > **Manual Pivot Location Position Y** (Позиция по оси Y расположения ручного поворота) на **1,5**.

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-2.png)

В окне Hierarchy (Иерархия) выберите первую часть лунохода (RoverParts > **Camera_Part**) и настройте компонент **ToolTipSpawner**, как описано ниже.

* Измените параметр **Tool Tip Text** (Текст подсказки), чтобы в нем было указано имя части (например, **Camera** (Камера)).

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-3.png)

**Повторите** этот шаг для каждого из объектов частей лунохода, чтобы настроить компонент **ToolTipSpawner**, как описано ниже.

* Для объекта **Generator_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на **Generator**.
* Для объекта **Lights_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на **Lights**.
* Для объекта **UHFAntenna_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на поле **UHF Antenna**.
* Для объекта **Spectrometer_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на **Spectrometer**.

Нажмите кнопку Play (Воспроизведение), чтобы перейти в игровой режим, а затем нажмите и удерживайте правую кнопку мыши, перемещая указатель мыши, пока не будет нажата одна из частей и не отобразится подсказка для этой части:

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>Поздравляем!

Из этого учебника вы узнали, как создать простой пользовательский интерфейс с помощью предоставляемых кнопок MRTK и заготовок меню вместе с компонентом Unity TextMeshPro, а также как настроить кнопки для запуска событий при их нажатии. Вы также узнали, как добавлять динамические элементы интерфейса подсказки, чтобы предоставить пользователю дополнительную информацию.

[Следующее руководство: 7. Взаимодействие с трехмерными объектами](mr-learning-base-07.md)
