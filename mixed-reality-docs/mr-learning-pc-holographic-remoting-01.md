---
title: Учебники по голографическому удаленному взаимодействию с ПК, часть 1. Начало работы с голографическим удаленным взаимодействием с ПК
description: Пройдите этот курс, чтобы узнать, как реализовать удаленное взаимодействие в режиме смешанной реальности между вашим компьютером и HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/29/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4929634d70a082e835eb7bd6b5680719338a5e92
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476976"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1. Начало работы с голографическим удаленным взаимодействием с ПК

## <a name="overview"></a>Обзор

  Вас приветствует серия учебников по HoloLens 2. Из этой серии учебников из двух частей вы узнаете, как выполнить демонстрацию взаимодействия со смешанной реальностью и как создать приложение на ПК для голографического удаленного взаимодействия.

   Вы научитесь создавать взаимодействие со смешанной реальностью, используя сведения из [этого учебника](mr-learning-pc-holographic-remoting-01.md). Здесь будут продемонстрированы элементы пользовательского интерфейса, функции управления трехмерными моделями, обрезки моделей, а также функции отслеживания взгляда.

  Во втором учебнике вы научитесь [создавать приложение на ПК для голографического удаленного взаимодействия](mr-learning-pc-holographic-remoting-02.md) и подключаться к HoloLens 2 в любой момент с помощью визуализации трехмерного содержимого в смешанной реальности.

## <a name="objectives"></a>Задачи

* Импорт ресурсов и настройка сцены.
* Взаимодействие с голограммами через кнопки и элементы пользовательского интерфейса
* Настройка трехмерных объектов для функции обрезки.
* Получение сведений об активации подсказок с помощью отслеживания взгляда.

## <a name="prerequisites"></a>Предварительные условия

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).
* Базовые навыки работы с C#.
* Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.X и модулем поддержки сборки универсальной платформы Windows.

Мы **настоятельно рекомендуем** предварительно ознакомиться с серией учебников [по началу работы](mr-learning-base-01.md) или иметь хотя бы базовый опыт работы с Unity и MRTK.

> [!IMPORTANT]
> * Рекомендуемая версия Unity для этой серии учебников — Unity 2019.3.X. Это заменяет все требования к версии Unity и рекомендации, указанные выше.
> * Голографическое удаленное взаимодействие с проектами MRTK будет работать только с устаревшими API XR. Паке SDK XR в настоящее время не поддерживается.

## <a name="creating-and-preparing-the-unity-project"></a>Создание и подготовка проекта Unity

В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.

Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:

1. [Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.

1. [Переключение платформы сборки.](mr-learning-base-02.md#configuring-the-unity-project)

1. [Импорт требуемых ресурсов TextMeshPro.](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Импорт набора средств для Смешанной реальности (MRTK).](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Настройка проекта Unity.](mr-learning-base-02.md#configuring-the-unity-project)

1. [Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей подходящего имени, например **Голографическое удаленное взаимодействие с ПК**.

Затем следуйте инструкциям по [изменению параметра отображения для отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), чтобы указать профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** для сцены. Измените параметры отображения сетки отслеживания в пространстве на **Occlusion** (Загораживание).

## <a name="importing-the-tutorial-assets"></a>Импорт активов для руководства

Скачайте и **импортируйте** пакет [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).

>[!TIP]
> Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Когда вы завершите импорт активов для учебника, окно проекта должно выглядеть примерно так:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a>Настройка и подготовка сцены

В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.

В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**. Удерживая нажатой клавишу CTRL, щелкните шесть заготовок, перечисленных ниже.

* ButtonParent;
* ClippingObjects;
* HandSpatialMapButton;
* Инструкции
* ModelParent;
* Платформа

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

Перетащите эти модели из папки заготовок в окно **Hierarchy** (Иерархия).

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

Чтобы перенести фокус на объекты сцены, дважды щелкните объект **ModelParent**, а затем снова немного увеличьте масштаб представления:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> Если вы считаете, что большие значки в сцене (как большие "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Настройка кнопок для управления сценой

В этом разделе вы добавите скрипты в сцену, чтобы создать события кнопки, демонстрирующие базовые принципы переключения моделей и функций обрезки.

### <a name="1-configuring-the-interactable-script-component"></a>1. Настройка компонента Interactable (Script) (Интерактивный — скрипт)

В окне Hierarchy (Иерархия) разверните объект **ButtonParent** и выберите **NextButton**. В окне Inspector (Инспектор) найдите компонент **Interactable (Script)** (Интерактивный — скрипт) и щелкните значок **+** в событии **OnClick ()** .

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

Сохраняя объект **NextButton** выделенным в окне Hierarchy (Иерархия), щелкните и перетащите объект **ButtonParent** из окна (Иерархия) в пустое поле **None (Object)** (Отсутствует (объект)) только что созданного события, чтобы объект ButtonParent ожидал передачи данных о событии нажатия для этой кнопки:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

Откройте раскрывающийся список **No Function** (Нет функции) того же события. Затем выберите **ViewButtonControl** > **NextModel ()** , чтобы установить функцию **NextModel ()** в качестве действия, запускаемого при срабатывании события нажатия кнопки.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2. Настройка остальных кнопок

Для всех остальных кнопок повторно выполните процессы, которые описаны выше, чтобы назначить функции событиям **OnClick ()** следующим образом:

* Для объекта PreviousButton назначьте функцию **ViewButtonContro**l > **PreviousModel ()** .

* Для объекта ClippingButton выберите функцию **ToggleButton** > **ToggleClipping ()** .

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3. Настройка компонентов View Button Control (Script) (Элемент управления кнопкой просмотра — скрипт) и Toggle Button (Script) (Выключатель — скрипт)

Теперь кнопки настроены, чтобы продемонстрировать функции переключения и обрезки модели. Время добавить трехмерные модели и объекты обрезки в скрипт.

Мы предоставили шесть различных трехмерных моделей для демонстрации, разверните ***ModelParentobject***, чтобы предоставить эти трехмерные модели.

Сохраняя объект ButtonParent выделенным в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) выберите **View Button Control (Script)** (Элемент управления кнопкой просмотра — скрипт) и разверните переменную **Models** (Модели).

В поле **Size** (Размер) введите число трехмерных моделей, которые будут находиться в сцене. В нашем случае — 6. Будет создано поле для добавления новых трехмерных моделей.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

Перетащите каждый дочерний объект объекта ModelParent в эти поля.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

Перетащите объект **ClippingObjects** из окна Hierarchy (Иерархия) в компонент **Toggle Button (Script)** (Переключатель — скрипт) поля **Clipping Object** (Обрезаемый объект).
>[!NOTE]
>Старайтесь использовать только родительский объект кнопки.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

В окне Hierarchy (Иерархия) выберите заготовку **ClippingObjects** и включите ее в окне Inspector (Инспектор), чтобы включить объекты обрезки.

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>Настройка объектов обрезки для включения функции обрезки

В этом разделе вы добавите отрисовщик дочерних объектов MarsCuriosityRover в отдельный объект обрезки, чтобы продемонстрировать обрезку модели MarsCuriosityRover.

В окне Hierarchy (Иерархия) разверните объект **ClippingObjects**, чтобы предоставить три различных объекта обрезки, которые будут использоваться в этом проекте.

Чтобы настроить объект **ClippingSphere**, щелкните его, а затем в окне Inspector (Инспектор) выберите компонент **Clipping Sphere (Script)** (Обрезка сферы — скрипт). Введите количество отрисовщиков в поле размера, которое необходимо добавить для трехмерной модели. В этом случае для дочерних объектов MarsCuriosityRover добавьте 10 отрисовщиков. Будут созданы поля для добавления отрисовщиков. Перетащите объекты дочерней модели MarsCuriosityRover в эти поля.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

Выполните тот же процесс и добавьте отрисовщики дочерних объектов MarsCuriosityRover в объекты **ClippingBox** и **ClippingPlane**.

В этом учебнике для демонстрации функции обрезки будет использоваться только модель MarsCuriosityRover. Функции обрезки были добавлены к большему количеству моделей. В результате этого размер отрисовщика увеличился и были добавлены индивидуальные отрисовщики сетки.

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>Настройка отслеживания взгляда для выделения всплывающих подсказок

Из этого раздела вы узнаете, как включить отслеживание взгляда в нашем демонстрационном проекте. Например, вы реализуете функции, чтобы выделить прикрепленные к деталям MarsCuriosityRover подсказки, когда вы на них смотрите, и скрыть их при отводе взгляда.

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1. Определите целевые объекты и связанные с ними подсказки.

В окне Hierarchy (Иерархия) выберите объект ModelParent. Разверните иерархию ***MarsCuriosity -> Rover***, чтобы найти пять основных деталей MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer** и **POI-RUHF Antenna**.

* Обратите внимание на пять соответствующих объектов подсказок, связанных с деталями MarsCuriosityRover в окне Hierarchy (Иерархия).
* Эти объекты будут настроены, чтобы выделять элементы при просмотре деталей MarsCuriosityRover.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2. Реализация событий While Looking At Target () и On Look Away ()

В окне Hierarchy (Иерархия) выберите объект ***POI-Camera***. В окне Inspector (Инспектор) найдите компонент**Eye Tracking Target (Script)** и настройте события **While Looking At Target ()**  & **On Look Away ()** следующим образом:

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **POI-Camera ToolTip**.
* В раскрывающемся списке **No Function** (Без функции) события **While Looking At Target ()** выберите **GameObject** > **SetActive (bool).** Установите **флажок**, чтобы выделить всплывающую подсказку в качестве действия, запускаемого при просмотре целевого объекта.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* Выполните тот же процесс и выберите раскрывающийся список **No Function** (Без функции) прослушивателя событий **On Look Away ()** . Затем выберите **GameObject** > **SetActive (bool**) и снимите **флажок**, чтобы скрыть всплывающую подсказку как действие, запускаемое при отведении взгляда от целевого объекта.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

Выполните тот же процесс и назначьте соответствующие объекты подсказки тем же деталям **MarsCuriosityRover** событий **While Looking At Target ()**  & **On Look Away ()** .

Чтобы включить отслеживание взгляда, следуйте приведенным [рекомендациям](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).

## <a name="congratulations"></a>Поздравляем!

Из этого учебника вы узнали, как создать взаимодействие в смешанной реальности с использованием элементов пользовательского интерфейса, управления трехмерными моделями, обрезкой моделей и функции отслеживания взгляда. В этом учебнике показано, как использовать объекты NextButton и PreviousButton, позволяющие исследовать возможности средства просмотра трехмерных моделей. ClippingObjectButton позволяет включить функцию обрезки объектов и интерфейса. Кроме того, в учебнике показано, как использовать элемент отслеживания взгляда, позволяющий выделять всплывающие подсказки в интерфейсе.

На следующем занятии вы узнаете, как создать приложение для голографического удаленного взаимодействия с ПК для подключения к HoloLens 2 в любой момент, позволяя выполнить визуализацию трехмерного содержимого в смешанной реальности.

[Следующий урок. 2. Создание приложения для голографического удаленного взаимодействия](mr-learning-pc-holographic-remoting-02.md)
