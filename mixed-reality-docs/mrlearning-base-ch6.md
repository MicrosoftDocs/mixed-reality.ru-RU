---
title: Серия руководств по началу работы, часть 7 Создание примера приложения лунного модуля
description: В этом уроке мы объединим несколько концепций, которые узнали из предыдущих уроков, чтобы создать уникальный пример взаимодействия.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031567"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. Создание примера приложения лунного модуля
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

В этом руководстве несколько концепций, которые вы узнали из предыдущих уроков, объединяются в уникальный пример взаимодействия. Вы узнаете, как создать приложение для сборки деталей, в котором пользователю потребуется использовать отслеживание рук, чтобы поднять части лунного модуля и попытаться его собрать. Вы примените нажимаемые кнопки для включения подсказок по размещению, сброса выполненных действий и запуска лунного модуля в космос.

В последующих руководствах мы продолжим развивать этот пример, добавляя мощные многопользовательские сценарии применения, использующие Пространственные привязки Azure для пространственного выравнивания.

## <a name="objectives"></a>Задачи

* Объединить несколько концепций из предыдущих уроков, чтобы выполнить уникальный сценарий.
* Узнать, как переключать объекты.
* Запустить сложные события с помощью нажимаемых кнопок.
* Использовать силы и физику твердых тел.
* Изучить использование всплывающих подсказок.

## <a name="lunar-module-parts-overview"></a>Общие сведения о сборке лунного модуля
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

В этом разделе объясняется, как создать простую задачу сборки деталей, в которой пользователю предстоит правильно разместить пять деталей лунного модуля, разложенных на столе.

Для получения этого результата вам нужно выполнить следующие шаги:

1. Добавление в сцену заготовки Rocket Launcher.
2. Включение манипулирования объектом для всех деталей.
3. Добавление и настройка компонента "Part Assembly Demo (Script)" (Демонстрация сборки деталей — скрипт).

> [!NOTE]
> Компонент "Part Assembly Demo (Script)" (Демонстрация сборки деталей — скрипт) не входит в состав MRTK. Он был предоставлен с активами для этого руководства.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. Добавление в сцену заготовки Rocket Launcher

В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, перетащите заготовку **RocketLauncher** в окно Hierarchy (Иерархия), чтобы добавить ее в сцену, и поместите ее в приемлемое положение, например так:

* для параметра преобразования Position (Положение) укажите значения X = 1.5, Y = -0,4, Z = 0, чтобы деталь размещалась справа от пользователя на уровне груди;
* для параметра преобразования Rotation (Поворот) укажите значения X = 0, Y = 180, Z = 0, чтобы основные элементы объекта были направлены в сторону пользователя.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. Включение манипулирования объектом для всех деталей

В окне Hierarchy (Иерархия) найдите объект RocketLauncher > **LunarModuleParts** и выберите все его **дочерние объекты**, затем добавьте компоненты **Manipulation Handler (Script)** (Обработчик манипулирования — скрипт) и **Near Interaction Grabbable (Script)** (Возможность захвата при близком взаимодействии — скрипт) и настройте Manipulation Handler (Script) (Обработчик манипулирования — скрипт) следующим образом:

* снимите флажок **Allow Far Manipulation** (Разрешить дальнее манипулирование), чтобы поддерживать только ближнее взаимодействие;
* для параметра **Two Handed Manipulation Type** (Тип манипуляции двумя руками) укажите значение **Move Rotate** (Перемещение и вращение), чтобы отключить масштабирование.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> В разделе [Работа с трехмерными объектами](mrlearning-base-ch4.md#manipulating-3d-objects) вы можете освежить свои знания о реализации манипулирования объектами и получить пошаговые инструкции.

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. Добавление и настройка компонента "Part Assembly Demo (Script)" (Демонстрация сборки деталей — скрипт)

Выделив все дочерние объекты объекта LunarModuleParts, добавьте компонент **Audio Source** (Источник звука) и настройте его следующим образом:

* укажите подходящий аудиоклип в поле **AudioClip**, например MRKT_Scale_Start;
* снимите флажок **Play On Awake** (Воспроизвести при загрузке), чтобы аудиоклип не включался автоматически при загрузке сцены;
* для параметра **Spatial Blend** (Пространственное наложение) укажите значение 1, чтобы включить пространственный звук.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

Выделив все дочерние объекты объекта LunarModuleParts, добавьте компонент **Part Assembly Demo (Script)** (Демонстрация сборки деталей — скрипт):

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

В окне Hierarchy (Иерархия) выберите объект **RoverEnclosure** и настройте его компонент **Part Assembly Demo (Script)** (Демонстрация сборки деталей — скрипт) следующим образом:

* в поле **Object To Place** (Объект для размещения) укажите **сам объект**, в нашем примере это RoverEnclosure;
* в поле **Location To Place** (Расположение для размещения) сохраните соответствующий объект **PlacementHint**, в нашем примере это RoverEnclosure_PlacementHint;
* в поле **Tool Tip Object** (Всплывающая подсказка) сохраните соответствующий объект **ToolTip**, в нашем примере это RoverEnclosure_ToolTip;
* в поле **Audio Source** (Источник звука) укажите **сам объект**, в нашем примере это RoverEnclosure.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

**Повторите** этот процесс для всех дочерних объектов объекта LunarModuleParts: FuelTank, EnergyCell, DockingPortal и ExternalSensor.

Теперь если вы перейдете в игровой режим и переместите объект для размещения в расположение для размещения, произойдет следующее:

* Объект встанет на нужное место и станет дочерним объектом для LunarModule, то есть станет частью лунного модуля.
* Компонент Audio Source этого объекта воспроизведет назначенный ему аудиоклип в том расположении, где сейчас находится этот объект.
* Скроется соответствующая подсказка.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> Чтобы вспомнить, как использовать встроенный имитатор ввода, воспользуйтесь руководством [по использованию имитации ввода с помощью рук в редакторе для тестирования сцены](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene), размещенным на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="configuring-the-lunar-module"></a>Настройка лунного модуля

В этом разделе описывается, как добавить новые возможности в приложение Rocket Launcher, благодаря которым пользователь сможет выполнять следующие действия:

* взаимодействие с лунным модулем;
* запуск лунного модуля в космос со звуковым сопровождением;
* сброс состояния приложения, чтобы вернуть лунный модуль и все его детали на исходные места;
* отключение подсказок по размещению, чтобы усложнить задачу сборки деталей.

Для получения этого результата вам нужно выполнить следующие шаги:

1. Включение манипулирования объектами.
2. Включение физических законов.
3. Добавление компонента источника звука.
4. Добавление и настройка компонента "Launch Lunar Module (Script)" (Запуск лунного модуля — скрипт).
5. Добавление и настройка компонента "Toggle Placement Hints (Script)" (Переключение подсказок по размещению — скрипт).

> [!NOTE]
> Компоненты Launch Lunar Module (Script) (Запуск лунного модуля — скрипт) и Toggle Placement Hints (Script) (Переключение подсказок по размещению — скрипт) не входят в состав MRTK. Он был предоставлен с активами для этого руководства.

### <a name="1-enable-object-manipulation"></a>1. Включение манипулирования объектами

В окне Hierarchy (Иерархия) выберите объект RocketLauncher > **LunarModule** и добавьте компоненты **Manipulation Handler (Script)** (Обработчик манипулирования — скрипт) и **Near Interaction Grabbable (Script)** (Возможность захвата при близком взаимодействии — скрипт), а затем настройте Manipulation Handler (Script) (Обработчик манипулирования — скрипт) следующим образом:

* снимите флажок **Allow Far Manipulation** (Разрешить дальнее манипулирование), чтобы поддерживать только ближнее взаимодействие;
* для параметра **Two Handed Manipulation Type** (Тип манипуляции двумя руками) укажите значение "Move Rotate" (Перемещение и вращение), чтобы отключить масштабирование.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. Включение физических законов

Выделив объект RocketLauncher > **LunarModule**, добавьте компонент **RigidBody** и настройте его следующим образом:

* Снимите флажок **Use Gravity** (Использовать гравитацию), чтобы этот объект не подвергался земному притяжению.
* Установите флажок **Is Kinematic** (Кинематические свойства), чтобы этот объект изначально не подвергался влиянию физических законов.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. Добавление компонента источника звука

Сохраняя выделение объекта RocketLauncher > **LunarModule**, добавьте компонент **Audio Source** (Источник звука) и настройте его следующим образом:

* Для параметра **Spatial Blend** (Пространственное наложение) укажите значение 1, чтобы включить пространственный звук.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. Добавление и настройка компонента "Launch Lunar Module (Script)" (Запуск лунного модуля — скрипт)

Сохраняя выделение объекта RocketLauncher > **LunarModule**, добавьте компонент **Launch Lunar Module (Script)** (Запуск лунного модуля — скрипт) и настройте его следующим образом:

* Измените значение **Thrust** (Тяга), чтобы лунный модуль при запуске взлетал изящно, например укажите 0,01.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. Добавление и настройка компонента "Toggle Placement Hints (Script)" (Переключение подсказок по размещению — скрипт)

Сохраняя выделение объекта RocketLauncher > **LunarModule**, добавьте компонент **Toggle Placement Hints (Script)** (Переключение подсказок по размещению — скрипт) и настройте его следующим образом.

* В массиве игровых объектов для свойства **Size** (Размер) укажите значение 5.
* Каждый из **дочерних объектов** объекта RocketLauncher > LunarModule > **PlacementHints** добавьте в поле **Element** (Элемент) в массиве игровых объектов:

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>Настройка кнопки запуска

В окне Hierarchy (Иерархия) выберите объект RocketLauncher > Buttons > **LaunchButton**, затем для компонента **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) создайте новое событие **Button Pressed ()** (Нажатие кнопки), настройте получение этого события в объекте **LunarModule** и определите **LaunchLunarModule.StartThruster** в качестве активируемого действия:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> В разделе об [обработке жестов и нажатий активных кнопок с помощью средства отслеживания руки](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) вы можете освежить свои знания о реализации событий.

Сохраняя выделение объекта RocketLauncher > Buttons > **LaunchButton**, создайте в компоненте **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) новое событие **Button Pressed ()** (Нажатие кнопки), настройте получение этого события в объекте **LunarModule**, определите **AudioSource.PlayOneShot** в качестве действия для запуска и назначьте подходящий звуковой клип в поле **Audio Clip** (Аудиоклип), например MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

Сохраняя выделение объекта RocketLauncher > Buttons > **LaunchButton**, затем для компонента **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) создайте событие **Touch End ()** (Касание конца), настройте получение этого события в объекте **LunarModule** и определите **LaunchLunarModule.StopThruster** в качестве активируемого действия:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

Теперь, если вы войдете в игровой режим и нажмете кнопку запуска, будет запущен аудиоклип, а если вы будете удерживать эту кнопку примерно секунду или более, лунный модуль улетит в космос:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>Настройка кнопки сброса

В окне Hierarchy (Иерархия) выберите объект RocketLauncher > Buttons > **ResetButton**, затем для компонента **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) создайте новое событие **Button Pressed ()** (Нажатие кнопки), настройте получение этого события в объекте **LunarModule** и определите **LaunchLunarModule.ResetModule** в качестве запускаемого действия:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

Сохраняя выделение объекта RocketLauncher > Buttons > **ResetButton**, создайте для компонента **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) новое событие **Button Pressed ()** (Нажатие кнопки), настройте получение этого события в объекте **RocketLauncher**, определите **GameObject.BroadcastMessage** в качестве запускаемого действия и укажите **ResetPlacement** в поле сообщения:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> Действие GameObject.BroadcastMessage отправляет сообщение ResetPlacement из объекта RocketLauncher всем его дочерним объектам. Все дочерние объекты, для которых определена функция ResetPlacement из компонента Part Assembly Demo (Script) (Демонстрация сборки деталей — скрипт), добавленного ранее во все дочерние объекты объекта LunarModuleParts, вызовут эту функцию ResetPlacement для сброса расположения соответствующего дочернего объекта.

Теперь, если вы войдете в игровой режим, переместите некоторые детали и (или) запустите лунный модуль, а затем нажмете кнопку сброса, все детали и (или) сам лунный модуль будут возвращены на исходные места.

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>Настройка кнопки подсказок расположения
<!-- TODO: Rename to 'Configuring the Hints button'-->

В окне Hierarchy (Иерархия) выберите объект RocketLauncher > Buttons > **HintsButton**, затем для компонента **Pressable Button (Script)** (Нажимаемая кнопка — скрипт) создайте новое событие **Button Pressed ()** (Нажатие кнопки), настройте получение этого события в объекте **LunarModule** и определите **TogglePlacementHints.ToggleGameObjects** в качестве запускаемого действия:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

Теперь, если вы войдете в игровой режим, полупрозрачные подсказки расположения не будут отображаться по умолчанию, но вы сможете их включить нажатием соответствующей кнопки.

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>Поздравляем!

Вы полностью настроили это приложение. Теперь в этом приложении пользователи могут собрать лунный модуль из отдельных деталей, запустить его в космос, включить или выключить подсказки и сбросить состояние приложения для повторной игры.
