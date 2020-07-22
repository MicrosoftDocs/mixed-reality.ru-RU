---
title: Руководства по многопользовательским возможностям, часть 4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cd8f0cb8888e7225566acc8c4b26aced3e4d977e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306253"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям

В этом руководстве показано, как совместно использовать перемещения объектов, чтобы все участники общего взаимодействия могли взаимодействовать друг с другом и наблюдать за этими процессами.

## <a name="objectives"></a>Задачи

* Настройка проекта для совместного использования перемещений объектов
* Создать простое многопользовательское приложение для совместной работы.

## <a name="preparing-the-scene"></a>Подготовка сцены

В рамках этого раздела вы подготовите сцену, добавив в нее заготовку для учебника.

В окне Project (Проект) перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Заготовки) и перетащите заготовку **TableAnchor** на объект **SharedPlayground** в окне Hierarchy (Иерархия), чтобы добавить ее в сцену в качестве дочернего элемента объекта SharedPlayground.

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Настройка PUN для создания объектов

С помощью инструкций из этого раздела вы настроите в проекте использование взаимодействия Rover Explorer, созданного с помощью [руководств по началу работы](mr-learning-base-01.md), и определите расположение, в котором буде создан его экземпляр.

В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).

В окне "Иерархия" разверните объект **NetworkLobby** и выберите дочерний объект **NetworkRoom**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.

* В поле **Rover Explorer Prefab** (Заготовка Rover Explorer) назначьте заготовку **RoverExplorer_Complete_Variant** из папки Resources (Ресурсы).

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

Сохраняя выделение объекта **NetworkRoom**, в окне "Иерархия" разверните объект **TableAnchor**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.

* В поле **Rover Explorer Location** (Расположение Rover Explorer) укажите дочерний объект TableAnchor > **Table** из окна Hierarchy (Иерархия).

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Использование возможности общего перемещения объектов

Если вы теперь создадите и развернете проект Unity в HoloLens, а затем вернетесь в Unity и во время выполнения приложения на устройстве HoloLens нажмете кнопку Play (Играть), чтобы перейти в игровой режим, вы увидите, как при перемещении объекта в HoloLens перемещается объект в Unity.

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>Поздравляем!

Вы успешно настроили проект. Теперь перемещения объектов синхронизированы и пользователи могут видеть, как перемещаются объекты, когда их перемещают другие пользователи. В следующем руководстве показано, как реализовать функциональность для согласования взаимодействия с физическим миром. Благодаря этому пользователи будут видеть друг друга в фактическом физическом расположении, а объекты будут отображаться в одном физическом расположении и с одним поворотом для всех пользователей.

[Следующее руководство: 5. Интеграция Пространственных привязок Azure в общий интерфейс](mr-learning-sharing-05.md)
