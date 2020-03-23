---
title: Руководства по многопользовательским возможностям, часть 3. Подключение нескольких пользователей
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031232"
---
# <a name="3-connecting-multiple-users"></a>3. Подключение нескольких пользователей

На этом занятии мы узнаем, как подключить несколько пользователей для организации совместного взаимодействия в реальном времени. К концу этого урока вы откроете приложение на нескольких устройствах и увидите аватары в виде сфер для каждого пользователя, который присоединяется к приложению.

## <a name="objectives"></a>Задачи

* Настройка PUN в приложении
* Настройка игроков
* Подключение нескольких пользователей к общему взаимодействию

## <a name="instructions"></a>Инструкции

1. В папке Assets (Активы) -> Resources (Ресурсы) -> Prefabs (Заготовки) на панели проекта щелкните заготовку NetworkLobby и перетащите ее в иерархию, как показано на рисунке ниже.

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Развернув NetworkLobby, вы увидите дочерний объект с именем NetworkRoom. Выбрав NetworkRoom, перейдите на панель Inspector (Инспектор) и щелкните Add Component (Добавить компонент). Выполните поиск PhotonView и добавьте этот компонент.

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Создайте в иерархии новый пустой игровой объект. Щелкните иерархию правой кнопкой мыши и выберите Empty (Пустой) в контекстном меню. Для положения укажите значения x = 0, y = 0, z = 0 и присвойте объекту имя PhotonUser.

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Нажмите кнопку Add Component (Добавить компонент) и введите "Generic Net Sync". Выберите класс Generic Net Sync. Когда появится этот класс, щелкните флажок User (Пользователь), чтобы включить его.

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Снова нажмите кнопку Add Component (Добавить компонент) и введите "Photon View". Выберите класс Photon View, который появится в раскрывающемся списке.

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Щелкните значок файла для класса Generic Net Sync. Перетащите его в поле Observed Components (Наблюдаемые компоненты) в представлении Photon.

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. Теперь мы создадим сферы, которые будут представлять каждого человека, который присоединяется к общему взаимодействию. Щелкните правой кнопкой мыши объект PhotonUser, который вы только что создали, прокрутите содержимое вниз до пункта 3D Object (Трехмерный объект) и щелкните Sphere (Сфера). Этот процесс создает игровой объект Sphere (Сфера) в качестве дочернего объекта для PhotonUser.

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Назначьте этой сфере размеры x = 0,06, y = 0,06 и z = 0,06.

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Перетащите игровой объект PhotonUser в папку Prefabs (Заготовки) на панели проекта, а затем удалите его из сцены. Так вы создали заготовку, которую можно использовать при создании экземпляров для новых игроков в общем взаимодействии.

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    >Убедитесь, что игровой объект успешно скопирован в папку Prefabs (Заготовки), прежде чем удалять его из иерархии.

10. Создайте еще один объект в иерархии, повторив процедуру из шага 3, и присвойте ему имя SharedPlayground. Теперь щелкните Add Component (Добавить компонент) и найдите "generic network manager".  Щелкните компонент Generic Network Manager (Универсальный диспетчер сети), чтобы добавить его. Укажите для этого объекта положение x = 0, y = 0 и z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a>Поздравляем!

Завершив все описанные выше шаги и дождавшись окончания процесса сборки, нажмите кнопку Play (Играть) и подключите устройство HoloLens 2. Вы увидите, как сфера в сцене перемещается синхронно с движениями вашей головы. Это будет видно любому пользователю, который подключится к этому проекту Unity.

[Следующий урок. 4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям](mrlearning-sharing(photon)-ch4.md)
