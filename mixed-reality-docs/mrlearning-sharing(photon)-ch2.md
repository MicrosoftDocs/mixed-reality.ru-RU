---
title: Руководства по многопользовательским возможностям, часть 3. Подключение нескольких пользователей
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610893"
---
# <a name="2-connecting-multiple-users"></a>2. Подключение нескольких пользователей

Из этого учебника вы узнаете, как подключить несколько пользователей для организации совместного взаимодействия в реальном времени. По завершении работы с этим учебником вы сможете запустить приложение на нескольких устройствах, и каждый пользователь сможет увидеть, как аватар других пользователей перемещается в режиме реального времени.

## <a name="objectives"></a>Задачи

* Подключение нескольких пользователей к общему взаимодействию

## <a name="preparing-the-scene"></a>Подготовка сцены

В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.

В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Заготовки). Удерживая нажатой клавишу CTRL, щелкните заготовки **DebugWindow**, **NetworkLobby** и **SharedPlayground**, чтобы выбрать их.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

Когда все три заготовки будут выбраны, перетащите их вместе в окно "Иерархия", чтобы добавить в сцену:

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>Создание заготовки пользователя

В рамках этого раздела вы создадите заготовку, которая будет использоваться для представления пользователей в общем интерфейсе.

### <a name="1-create-and-configure-the-user"></a>1. Создание и настройка пользователя

Щелкните правой кнопкой мыши пустое место в окне "Иерархия" и выберите **Create Empty** (Создать пустой), чтобы добавить пустой объект в сцену. Присвойте объекту имя **PhotonUser** и настройте его, как описано ниже.

* Убедитесь, что для свойства **Позиция** в области "Преобразование" установлены такие значения: X = 0, Y = 0, Z = 0.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

Сохраняя выделение объекта **PhotonUser**, в окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить в объект PhotonUser компонент **Photon User (Script)** (Пользователь Photon — скрипт).

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

В окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить в объект PhotonUser компонент **Generic Net Sync (Script)** (Generic Net Sync — скрипт) и настроить его, как описано ниже.

* Установите флажок **Is User** (Пользователь).

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

В окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить в объект PhotonUser компонент **Photon View (Script)** (Photon View — скрипт) и настроить его, как описано ниже.

* В поле **Observed Components** (Наблюдаемые компоненты) укажите компонент Generic Net Sync (Script) (Generic Net Sync — скрипт).

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2. Создание аватара

Щелкните правой кнопкой мыши объект **PhotonUser** в окне "Иерархия" и последовательно выберите **3D Object** > **Sphere** (Трехмерный объект > Сфера), чтобы создать сферический объект в качестве дочернего для объекта PhotonUser и настроить его, как описано ниже.

* Убедитесь, что для свойства **Позиция** в области "Преобразование" установлены такие значения: X = 0, Y = 0, Z = 0.
* Измените для преобразования свойство **Масштаб** до нормального размера, например X = 0,15, Y = 0,15 и Z = 0,15.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3. Создание заготовки

В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

Сохраняя выделение папки Resources (Ресурсы), **щелкните и перетащите** объект **PhotonUser** из окна "Иерархия" в папку **Resources** (Ресурсы), чтобы сделать заготовку из объекта PhotonUser.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

Щелкните правой кнопкой мыши объект **PhotonUser** в окне "Иерархия" и выберите **Удалить**, чтобы удалить его из сцены.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Настройка PUN для создания заготовки пользователя

В рамках этого раздела вы настроите проект для использования заготовки PhotonUser, созданной в предыдущем разделе.

В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).

В окне "Иерархия" разверните объект **NetworkLobby** и выберите дочерний объект **NetworkRoom**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.

* В поле **Photon User Prefab** (Заготовка пользователя Photon) укажите заготовку **PhotonUser** из папки Resources (Ресурсы).

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Взаимодействие с несколькими пользователями

Если вы теперь создадите и развернете проект Unity в HoloLens, а затем, вернувшись в Unity, во время выполнения приложения на устройстве HoloLens нажмете кнопку Play (Играть), чтобы перейти в игровой режим, вы увидите, как с движением вашей головы (HoloLens) перемещается аватар пользователя HoloLens:

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> Чтобы вспомнить, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, воспользуйтесь инструкциями из раздела о [разработке приложения для устройства](mrlearning-base-ch1.md#build-your-application-to-your-device).

> [!CAUTION]
> Этому приложению требуется подключение к Photon, поэтому не забудьте проверить связь компьютера или устройства с Интернетом.

## <a name="congratulations"></a>Поздравляем!

Вы успешно настроили проект. Теперь несколько пользователей могут подключаться к одному интерфейсу и просматривать перемещения друг друга. В следующем учебнике вы реализуете функциональность, чтобы предоставить общий доступ к перемещению объектов на нескольких устройствах.

[Следующее руководство: 2. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям](mrlearning-sharing(photon)-ch3.md)
