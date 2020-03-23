---
title: Руководства по многопользовательским возможностям, часть 5. Интеграция Пространственных привязок Azure в общий интерфейс
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031698"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Интеграция Пространственных привязок Azure в общий интерфейс

В этом уроке вы узнаете, как интегрировать Пространственные привязки Azure в совместное взаимодействие. Пространственные привязки Azure позволяют нескольким устройствам в одном физическом расположении использовать общие ориентиры, сопоставляя с ними виртуальные взаимодействия так, что все участники видят игровые объекты в одном физическом месте.

## <a name="objectives"></a>Задачи

* Интеграция Пространственных привязок Azure в совместное взаимодействие для согласования среды между устройствами
* Изучение основных принципов Пространственных привязок Azure в контексте локального совместного взаимодействия.

## <a name="instructions"></a>Инструкции

1. Выберите заготовку TableAnchor, которая является дочерним объектом для MixedRealityPlayspace, и удалите ее.

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. В представлении проекта перейдите к разделу Assets (Активы) -> Resources (Ресурсы) -> Prefabs (Заготовки) и перетащите заготовку TableAnchor поверх объекта SharedPlayground, чтобы сделать его дочерним.

3. Разверните родительский объект MixedRealityPlayspace, затем объект TableAnchor и объект Buttons.

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Теперь выберите в иерархии ShareAzureAnchorButton и перейдите на панель Inspector (Инспектор). Прокрутите ее вниз до раскрывающегося меню, которое представлено на рисунке ниже, выберите AnchorModuleScript и щелкните ShareAnchorNetwork().

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Выберите GetAzureAnchorButton (как на шаге 4) и снова перейдите на панель Inspector (Инспектор). Прокрутите ее вниз до раскрывающегося меню, которое представлено на рисунке ниже, выберите AnchorModuleScript и щелкните GetSharedAnchorNetwork().

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Повторите шаг 4, чтобы подключить функцию StartAzureSession() к кнопке StartAzureSessionButton.

7. Повторите шаг 4, чтобы подключить функцию CreateAzureAnchor() к кнопке CreateAzureAnchorButton, и убедитесь, что объект TableAnchor присвоен полю Game Object (Игровой объект) в качестве параметра этой функции.

8. Выполните инструкции [Подключение сцены к ресурсу Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource), чтобы подключить учетные данные службы пространственных привязок Azure.

9. Чтобы протестировать модуль общего доступа, нажмите кнопку Start Azure ASA Session (Запустить сеанс пространственных привязок Azure) и создайте привязку Azure, нажав кнопку Create Azure Anchor (Создать привязку Azure). Дождитесь создания привязки Azure. Когда создание привязки Azure завершится, нажмите кнопку Share Azure Anchor (Поделиться привязкой Azure), чтобы передать созданную привязку Azure из HoloLens.

10. Чтобы получить переданную привязку Azure в другом устройстве HoloLens, щелкните Start Azure ASA Session (Запустить сеанс пространственных привязок Azure), чтобы подключиться к текущему сеансу.

11. Нажмите кнопку Get Azure Anchor (Получить привязку Azure), чтобы получить общую привязку Azure от другого устройства HoloLens.

## <a name="congratulations"></a>Поздравляем!

На этом занятии вы узнали, как интегрировать мощные новые возможности пространственных привязок Azure для поддержки согласованного расположения устройств в совместном взаимодействии. На этом мы завершаем работу с модулем общего доступа. Мы узнали в нем, как настроить новую учетную запись Photon, как интегрировать Photon и PUN в новое приложение Unity, как настроить аватары и общие объекты и, наконец, как согласовать нескольких участников с помощью пространственных привязок Azure.
