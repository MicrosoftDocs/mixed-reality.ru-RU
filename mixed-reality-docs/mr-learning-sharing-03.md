---
title: Руководства по многопользовательским возможностям, часть 3. Подключение нескольких пользователей
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5937b581e92ffc5a13b55574ffd8a0ca7c4bca40
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376396"
---
# <a name="3-connecting-multiple-users"></a>3. Подключение нескольких пользователей

Из этого учебника вы узнаете, как подключить несколько пользователей для организации совместного взаимодействия в реальном времени. По завершении работы с этим руководством вы сможете запустить приложение на нескольких устройствах, и каждый пользователь сможет увидеть, как аватар других пользователей перемещается в реальном времени.

## <a name="objectives"></a>Задачи

* Подключение нескольких пользователей к общему взаимодействию

## <a name="preparing-the-scene"></a>Подготовка сцены

В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.

В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Активы > MRTK.Tutorials.MultiUserCapabilities > Заготовки), а затем щелкните и перетащите следующие заготовки в окно Hierarchy (Иерархия), чтобы добавить их в сцену:

* заготовка **NetworkLobby**;
* заготовка **SharedPlayground**.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Активы > MRTK.Tutorials.AzureSpatialAnchors > Заготовки), а затем щелкните и перетащите следующие заготовки в окно Hierarchy (Иерархия), чтобы добавить их в сцену:

* заготовка **DebugWindow**.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>Создание заготовки пользователя

В рамках этого раздела вы создадите заготовку, которая будет использоваться для представления пользователей в общем интерфейсе.

### <a name="1-create-and-configure-the-user"></a>1. Создание и настройка пользователя

Щелкните правой кнопкой мыши пустое место в окне "Иерархия" и выберите **Create Empty** (Создать пустой), чтобы добавить пустой объект в сцену. Присвойте объекту имя **PhotonUser** и настройте его, как описано ниже.

* Убедитесь, что для свойства **Позиция** в области "Преобразование" установлены такие значения: X = 0, Y = 0, Z = 0.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

В окне Hierarchy (Иерархия) выберите **PhotonUser**, перейдите в окно Inspector (Инспектор) и нажмите кнопку **Add component** (Добавить компонент), чтобы добавить в объект PhotonUser компонент **Photon User (Script)** (Пользователь Photon — скрипт).

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

В окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить в объект PhotonUser компонент **Generic Net Sync (Script)** (Generic Net Sync — скрипт) и настроить его, как описано ниже.

* Установите флажок **Is User** (Пользователь).

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

В окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить в объект PhotonUser компонент **Photon View (Script)** (Photon View — скрипт) и настроить его, как описано ниже.

* В поле **Observed Components** (Наблюдаемые компоненты) укажите компонент **Generic Net Sync (Script)** (Generic Net Sync — скрипт).

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2. Создание аватара

В окне Project (Проект) перейдите к папке **Assets** > **MRTK** > **SDK** > **StandardAssets**  > **Materials** (Активы > MRTK > Пакет SDK > Стандартные активы > Материалы), чтобы найти материалы MRTK.

Затем щелкните правой кнопкой мыши объект **PhotonUser** в окне Hierarchy (Иерархия) и последовательно выберите **3D Object** > **Sphere** (Трехмерный объект > Сфера), чтобы создать сферический объект в качестве дочернего для объекта PhotonUser и настроить его следующим образом:

* Убедитесь, что для свойства **Позиция** в области "Преобразование" установлены такие значения: X = 0, Y = 0, Z = 0.
* Измените для преобразования свойство **Масштаб** до нормального размера, например X = 0,15, Y = 0,15 и Z = 0,15.
* Перейдите к полю MeshRenderer > Materials (Материалы) > **Element 0** (Элемент 0) и укажите материал **MRTK_Standard_White**.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3. Создание заготовки

В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

Сохраняя выделение папки Resources (Ресурсы), **щелкните и перетащите** объект **PhotonUser** из окна "Иерархия" в папку **Resources** (Ресурсы), чтобы сделать заготовку из объекта PhotonUser.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

Щелкните правой кнопкой мыши объект **PhotonUser** в окне "Иерархия" и выберите **Удалить**, чтобы удалить его из сцены.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Настройка PUN для создания заготовки пользователя

В рамках этого раздела вы настроите проект для использования заготовки PhotonUser, созданной в предыдущем разделе.

В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).

В окне "Иерархия" разверните объект **NetworkLobby** и выберите дочерний объект **NetworkRoom**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.

* В поле **Photon User Prefab** (Заготовка пользователя Photon) укажите заготовку **PhotonUser** из папки Resources (Ресурсы).

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Взаимодействие с несколькими пользователями

Если вы теперь создадите и развернете проект Unity в HoloLens, а затем вернетесь в Unity и во время выполнения приложения на устройстве HoloLens перейдете в игровой режим, вы увидите, как с движением вашей головы (HoloLens) перемещается аватар пользователя HoloLens.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Сведения о том, как правильно скомпилировать проект Unity и развернуть его в HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> Этому приложению требуется подключение к Photon, поэтому не забудьте проверить подключение компьютера или устройства к Интернету.

## <a name="congratulations"></a>Поздравляем!

Вы успешно настроили проект. Теперь несколько пользователей могут подключаться к одному интерфейсу и просматривать перемещения друг друга. В следующем учебнике вы реализуете функциональность, чтобы предоставить общий доступ к перемещению объектов на нескольких устройствах.

[Следующее руководство: 4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям](mr-learning-sharing-04.md)
