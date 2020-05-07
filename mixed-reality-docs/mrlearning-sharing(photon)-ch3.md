---
title: Руководства по многопользовательским возможностям, часть 4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610627"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a>3. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям

В этом учебнике вы узнаете, как совместно использовать перемещения объектов, чтобы все участники общего интерфейса могли взаимодействовать друг с другом и наблюдать эти взаимодействия.

## <a name="objectives"></a>Задачи

* Настройка проекта для совместного использования перемещений объектов
* Создание простого многопользовательского приложения для совместной работы

## <a name="preparing-the-scene"></a>Подготовка сцены

В рамках этого раздела вы подготовите сцену, добавив в нее заготовку для учебника.

В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Заготовки) и перетащите заготовку **TableAnchor** поверх объекта **SharedPlayground** в окне "Иерархия", чтобы добавить ее в сцену в качестве дочернего элемента объекта SharedPlayground.

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Настройка PUN для создания объектов

В рамках этого раздела вы настроите проект для использования заготовки RocketLauncher_Complete_Variant, которую вы создали в предыдущем разделе, а также определите, где она будет создана.

В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).

В окне "Иерархия" разверните объект **NetworkLobby** и выберите дочерний объект **NetworkRoom**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.

* В поле **Photon User Prefab** (Заготовка пользователя Photon) укажите заготовку **PhotonUser** из папки Resources (Ресурсы).

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

Сохраняя выделение объекта **NetworkRoom**, в окне "Иерархия" разверните объект **TableAnchor**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.

* В поле **Rocket Launcher Location** (Расположение Rocket Launcher) укажите дочерний объект **Table** из окна "Иерархия".

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Использование возможности общего перемещения объектов

Если вы теперь создадите и развернете проект Unity в HoloLens, а затем, вернувшись в Unity, во время выполнения приложения на устройстве HoloLens нажмете кнопку Play (Играть), чтобы перейти в игровой режим, вы увидите, как при перемещении объекта в HoloLens перемещается объект в Unity:

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a>Поздравляем!

Вы успешно настроили проект. Теперь перемещения объектов синхронизированы и пользователи могут видеть, как перемещаются объекты, когда их перемещают другие пользователи. В следующем учебнике вы реализуете функциональность для согласования общего интерфейса в реальном мире, чтобы пользователи увидели друг друга в их фактическом физическом расположении, а объекты отображались в одинаковом физическом положении и повороте для всех пользователей.

[Следующее руководство: 4. Интеграция Пространственных привязок Azure в общий интерфейс](mrlearning-sharing(photon)-ch4.md)
