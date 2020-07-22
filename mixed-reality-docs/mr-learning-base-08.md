---
title: Серия руководств по началу работы, часть 8 Использование функции отслеживания взгляда
description: Из этого курса вы узнаете, как с помощью набора средств для смешанной реальности (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 9a9fc7f860e6bf9c5cb3370a9c9ff11e627fe73f
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306594"
---
# <a name="8-using-eye-tracking"></a>8. Использование функции отслеживания взгляда

## <a name="overview"></a>Обзор

Из этого руководства вы узнаете, как включить функцию отслеживания взгляда для HoloLens 2 и добавить ее в объекты, чтобы активировать действия, когда пользователь смотрит на объекты.

> [!NOTE]
> Если вы также развертываете этот проект в HoloLens (1-е поколение), обратите внимание, что функция отслеживания взгляда поддерживается только в HoloLens 2.

## <a name="objectives"></a>Задачи

* Узнайте, как включить функцию отслеживания взгляда для HoleLens 2
* Узнайте, как с помощью функции отслеживания взгляда активировать действие

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Проверка того, включена ли функция ввода с использованием взгляда

В меню Unity последовательно выберите элементы Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Затем перейдите в раздел **UWP Capabilities** (Возможности UWP) и убедитесь, что раздел **Enable Eye Gaze Input Capability** (Включить ввод с использованием взгляда) выделен серым цветом.

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> Функция ввода с использованием взгляда должна была быть включена в ходе выполнения инструкций, приведенных в разделе [Применение параметров конфигуратора проекта MRTK](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings), при настройке проекта Unity в начале работы с этой серией руководств. Если функция отключена, включите ее сейчас.

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Включение отслеживания взгляда в поставщике данных о направлении взгляда

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, затем в окне Inspector (Инспектор) перейдите на вкладку MixedRealityToolkit > **Input** (Ввод) и выполните следующие действия:

* Клонируйте профиль **DefaultHoloLens2InputSystemProfile** и присвойте ему понятное имя, например _GettingStarted_HoloLens2InputSystemProfile_.
* Разверните раздел **Pointers** (Указатели).
* Клонируйте профиль **DefaultMixedRealityPointerProfile** и присвойте ему понятное имя, например _GettingStarted_MixedRealityPointerProfile_.
* В разделе **Gaze Settings** (Параметры взгляда) установите флажок **Is Eye Tracking Enabled** (Включено отслеживание взгляда).

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Включение имитации отслеживания взгляда для редактора Unity

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, в окне инспектора откройте вкладку **Input** (Ввод) и сделайте следующее:

* Разверните раздел **Input Data Providers**  > **Input Simulation Service** (Поставщики входных данных > Служба имитации ввода).
* Клонируйте профиль **DefaultMixedRealityInputSimulationProfile** и присвойте ему понятное имя, например _GettingStarted_MixedRealityInputSimulationProfile_.
* Найдите раздел **Eye Simulation** (Имитация взгляда) и установите флажок **Simulate Eye Position** (Имитировать положение глаз).

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>Добавление функции отслеживания взгляда в объекты

В окне Hierarchy (Иерархия) разверните объект RoverExplorer > **Buttons** (Кнопки). Для каждого из трех дочерних объектов кнопок разверните и выберите объект SeeItSayItLabel > **TextMeshPro**.

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

Выбрав три объекта TextMeshPro, в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить следующие компоненты ко всем выбранным объектам:

* компонент **Box Collider** (Прямоугольный коллайдер);
* компонент **EyeTrackingTarget**.

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

В окне Hierarchy (Иерархия) выберите объект **Hints** (Указания) > SeeItSayItLabel > **TextMeshPro**, а затем настройте компонент **EyeTrackingTarget** следующим образом:

* В разделе события **On Look At Start ()** (При взгляде на начало ())
  * Щелкните небольшой значок **+** , чтобы добавить событие.
  * Назначьте сам объект, т. е. тот же объект **TextMeshPro** полю **None (Object)** (Нет (объект)).
  * В раскрывающемся списке **No Function** (Нет функции) выберите **TextMeshPro** > **float fontSize**, чтобы обновлять это значение свойства при срабатывании события.
  * Задайте для аргумента значение **0,06**, чтобы увеличить текущий размер шрифта 0,04 на 50 %.
* В разделе события **On Look At Start ()** (При отведении взгляда ())
  * Щелкните небольшой значок **+** , чтобы добавить событие.
  * Назначьте сам объект, т. е. тот же объект **TextMeshPro** полю **None (Object)** (Нет (объект)).
  * В раскрывающемся списке **No Function** (Нет функции) выберите **TextMeshPro** > **float fontSize**, чтобы обновлять это значение свойства при срабатывании события.
  * Задайте для аргумента значение **0,04**, чтобы сбросить размер шрифта обратно до значения 0,04.

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

**Повторите** это действие для объекта **Explode** (Развернуть) > SeeItSayItLabel > **TextMeshPro** и объекта **Reset** (Сброс) > SeeItSayItLabel > **TextMeshPro**.

Если теперь перейти в режим игры, а затем нажать и удерживать правую кнопку мыши при перемещении указателя мыши до тех пор, пока взгляд не достигнет одной из меток, вы увидите, что размер шрифта увеличится на 50 %. При отведении взгляда текст вернется к исходному размеру.

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>Поздравляем!

Из этого руководства вы узнали, как включить функцию отслеживания взгляда для HoloLens 2 и добавить ее в объекты, чтобы активировать действия, когда пользователь смотрит на объекты.

[Следующее руководство: 9. Использование речевых команд](mr-learning-base-09.md)