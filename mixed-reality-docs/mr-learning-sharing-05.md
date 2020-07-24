---
title: Руководства по многопользовательским возможностям, часть 5. Интеграция Пространственных привязок Azure в общий интерфейс
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 79be23c9371bf90d03df0070b74f6cff3f0afafa
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306553"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Интеграция Пространственных привязок Azure в общий интерфейс

Из этого учебника вы узнаете, как интегрировать Пространственные привязки Azure в общий интерфейс. Пространственные привязки Azure позволяют нескольким устройствам в физическом мире использовать общие ориентиры, чтобы пользователи видели друг друга в их реальном физическом расположении и использовали общий интерфейс в одном расположении.

## <a name="objectives"></a>Задачи

* Интеграция Пространственных привязок Azure в общий интерфейс для согласования среды между устройствами.
* Изучение основных принципов Пространственных привязок Azure в контексте локального общего интерфейса.

## <a name="preparing-the-scene"></a>Подготовка сцены

В окне "Иерархия" разверните объект **SharedPlayground**, затем разверните объект **TableAnchor**, чтобы предоставить его дочерние объекты.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

В окне Project (Проект) перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Заготовки) и перетащите заготовку **Buttons** (Кнопки) на дочерний объект **TableAnchor**, чтобы добавить ее в сцену в качестве дочернего объекта TableAnchor.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Настройка кнопок для управления сценой

В этом разделе показано, как настроить серию событий кнопок, демонстрирующих базовые приемы использования Пространственных привязок Azure для достижения пространственного выравнивания в общем взаимодействии.

В окне "Иерархия" разверните объект **Button**. Выберите в нем первый дочерний объект кнопки с именем **StartAzureSession**:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

В окне "Инспектор" найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** (Щелчок), как описано ниже.

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.
* В раскрывающемся списке **No Function** (Нет функции) выберите функцию **AnchorModuleScript** > **StartAzureSession ()** .

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

В окне "Иерархия" выберите второй дочерний объект кнопки с именем **CreateAzureAnchor**. Затем в окне "Инспектор" найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** (Щелчок), как описано ниже.

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.
* В раскрывающемся списке **No Function** (Нет функции) выберите функцию **AnchorModuleScript** > **CreateAzureAnchor ()** .
* В появившемся поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **TableAnchor**.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

В окне "Иерархия" выберите третий дочерний объект кнопки с именем **ShareAzureAnchor**. Затем в окне "Инспектор" найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** (Щелчок), как описано ниже.

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.
* В раскрывающемся списке **No Function** (Нет функции) выберите функцию **SharingModuleScript** > **ShareAzureAnchor ()** .

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

В окне Hierarchy (Иерархия) выберите четвертый дочерний объект кнопки с именем **GetAzureAnchor**. Затем в окне Inspector (Инспектор) найдите компонент **Interactable (Script)** (Взаимодействие — скрипт) и настройте событие **OnClick ()** следующим образом:

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **TableAnchor**.
* В раскрывающемся списке **No Function** (Нет функции) выберите функцию **SharingModuleScript** > **GetAzureAnchor ()** .

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Подключение сцены к ресурсу Azure

В окне "Иерархия" разверните объект **SharedPlayground** и выберите объект **TableAnchor**.

В окне Inspector (Инспектор) найдите компонент **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт) и укажите в разделе **Credentials** (Учетные данные) данные учетной записи Пространственных привязок Azure, созданной при работе с разделом [предварительных требований](mr-learning-sharing-01.md#prerequisites) для этой серии руководств.

* В поле **Spatial Anchors Account ID** (Идентификатор учетной записи пространственных привязок) вставьте **идентификатор учетной записи** Пространственных привязок Azure.
* В поле **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок) вставьте первичный или вторичный **ключ доступа** учетной записи Пространственных привязок Azure.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> Вы можете задать идентификатор и ключ учетной записи Пространственных привязок не только для сцены, но и для всего проекта, если у вас есть несколько сцен с Пространственными привязками Azure. Для этого в окне Project (Проект) выберите Assets (Активы) > AzureSpatialAnchors.SDK > Resources (Ресурсы) > актив **SpatialAnchorConfig**, а затем задайте значения в окне Inspector (Инспектор).

В окне Hierarchy (Иерархия) выберите объект **TableAnchor**. Затем в окне Inspector (Инспектор) найдите компонент **Anchor Module (Script)** (Модуль привязок — скрипт) и настройте его следующим образом:

* В поле **Public Sharing Pin** (ПИН-код общего доступа) измените несколько цифр, чтобы код стал уникальным для вашего проекта.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

С выделенным объектом **TableAnchor** убедитесь, что в окне Inspector (Инспектор) **включены** все компоненты скрипта:

* Установите флажок рядом с компонентами **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт), чтобы включить их.
* Установите флажок рядом с компонентами **Anchor Module Script (Script)** (Скрипт модуля привязок — скрипт), чтобы включить их.
* Установите флажок рядом с компонентами **Sharing Module Script (Script)** (Скрипт модуля общего доступа — скрипт), чтобы включить их.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>Использование возможности пространственного выравнивания

> [!NOTE]
> Пространственные привязки Azure не могут работать в Unity. Поэтому для проверки функциональных возможностей этой службы вам нужно будет развернуть проект как минимум на двух устройствах.

После создания и развертывания проекта Unity на двух устройствах вы сможете реализовать пространственное выравнивание между ними, используя общий идентификатор привязки Azure. Чтобы проверить этот механизм, можно выполнить следующие действия.

1. На устройстве 1: **запустите приложение** (Rover Explorer создается и размещается в таблице).
2. На устройстве 2: **запустите приложение** (оба пользователя видят таблицу с Rover Explorer, но таблица не отображается в одном расположении, а аватары пользователей не отображаются там, где находятся пользователи).
3. На устройстве 1: нажмите кнопку **Start Azure Session** (Запуск сеанса Azure).
4. На устройстве 1: нажмите кнопку **Create Azure Anchor** (Создать привязку Azure) (создается привязка в расположении объекта TableAnchor и сохраняются сведения о ней в ресурсе Azure).
5. На устройстве 1: нажмите кнопку **Share Azure Anchor** (Поделиться привязкой Azure) (предоставляет другим пользователям доступ к идентификатору привязки в режиме реального времени).
6. На устройстве 2: нажмите кнопку **Start Azure Session** (Запуск сеанса Azure).
7. На устройстве 2: нажмите кнопку **Get Azure Anchor** (Получить привязку Azure) (подключается к ресурсу Azure, чтобы получить сведения о привязке для общего идентификатора привязки, затем перемещает объект TableAnchor в расположение, где с помощью устройства 1 была создана привязка).

> [!TIP]
> Если у вас нет доступа к двум устройствам HoloLens, выполните инструкции из статьи [Создание Пространственных привязок Azure для мобильных устройств](mr-learning-asa-05.md), чтобы развернуть проект на мобильном устройстве.

## <a name="congratulations"></a>Поздравляем!

Из этого учебника вы узнали, как интегрировать мощные возможности Пространственных привязок Azure для поддержки согласованного расположения устройств в общем интерфейсе.

На этом мы завершаем работу с этой серией руководств, из которой вы узнали, как настроить учетную запись Photon, создать приложение PUN, интегрировать PUN в проект Unity, настроить аватары пользователей и общие объекты, а также как согласовать разных участников с помощью Пространственных привязок Azure.