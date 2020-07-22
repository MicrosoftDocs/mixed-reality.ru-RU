---
title: Руководства по многопользовательским возможностям, часть 2. Настройка Photon Unity Networking
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: e5817338dbed944232664a86f8b0625bc9d3e1e7
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306642"
---
# <a name="2-setting-up-photon-unity-networking"></a>2. Настройка Photon Unity Networking

## <a name="overview"></a>Обзор

В этом учебнике показано, как подготовиться к созданию совместного взаимодействия с помощью Photon Unity Networking (PUN). Вы узнаете, как создать приложение PUN, импортировать активы PUN в проект Unity и подключить проект Unity к приложению PUN.

## <a name="objectives"></a>Задачи

* Узнать, как создать приложение PUN.
* Узнать, как найти и импортировать активы PUN.
* Узнать, как подключить проект Unity к приложению PUN.

## <a name="creating-and-preparing-the-unity-project"></a>Создание и подготовка проекта Unity

В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.

Для этого сначала выполните инструкции из руководства [Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md) (исключая раздел [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2)), в том числе следующие действия:

1. [Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.
1. [Переключение платформы сборки.](mr-learning-base-02.md#configuring-the-unity-project)
1. [Импорт требуемых ресурсов TextMeshPro.](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [Импорт набора средств для Смешанной реальности (MRTK).](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [Настройка проекта Unity.](mr-learning-base-02.md#configuring-the-unity-project)
1. [Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей понятного имени, например *MultiUserCapabilities*.

Затем выполните инструкции из раздела [Изменение параметра отображения отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option):

1. Измените **профиль конфигурации MRTK** на **DefaultHoloLens2ConfigurationProfile**.
1. Измените **параметры отображения сетки отслеживания пространственного положения** на **Occlusion** (Загораживание).

## <a name="enabling-additional-capabilities"></a>Включение дополнительных возможностей

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player** >  **Publishing Settings** (Проигрыватель > Параметры публикации).

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient**, **Microphone**, **SpatialPerception** и **GazeInput**, которые вы включили при выполнении шага [Настройка проекта Unity](mr-learning-base-02.md#configuring-the-unity-project) ранее.

Затем включите следующие дополнительные возможности:

* возможность **InternetClientServer**;
* возможность **PrivateNetworkClientServer**.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a>Установка встроенных пакетов Unity

В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.

## <a name="importing-the-tutorial-assets"></a>Импорт активов для руководства

Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (версия 2.2.1);
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage);
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage).

Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт набора средств для Смешанной реальности](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

> [!NOTE]
> После импорта пакета учебных активов MultiUserCapabilities в окне консоли появятся несколько ошибок [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246). Они указывают на отсутствие типа или пространства имен. Это ожидаемое поведение, и ошибки будут устранены при работе со следующим разделом при импорте активов PUN.

## <a name="importing-the-pun-assets"></a>Импорт активов PUN

В меню Unity последовательно выберите **Window** > **Asset Store** (Окно > Asset Store), чтобы открыть окно Asset Store. Найдите и выберите актив **PUN 2 — FREE** от Exit Games, а затем нажмите кнопку **Download** (Скачать), чтобы скачать пакет активов в учетную запись Unity.

После скачивания нажмите кнопку **Импорт**, чтобы открыть окно Import Unity Package (Импорт пакета Unity).

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

Когда в Unity завершится процесс импорта, появится окно мастера PUN с открытым меню PUN Setup (Настройка PUN). На данный момент вы можете проигнорировать или закрыть это окно.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a>Создание приложения PUN

В этом разделе показано, как создать учетную запись Photon, если у вас ее еще нет, а также приложение PUN.

Перейдите на <a href="https://dashboard.photonengine.com/account/signin" target="_blank">панель мониторинга</a> Photon и войдите в систему, если у вас уже есть учетная запись, которую вы хотите использовать. В противном случае щелкните ссылку **Создать** и следуйте инструкциям, чтобы зарегистрировать новую учетную запись.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

После входа нажмите кнопку **Создать приложение**.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

На странице создания приложения введите приведенные ниже значения.

* В раскрывающемся списке Photon Type (Тип Photon) выберите PUN.
* В поле "Имя" введите подходящее имя, например _MRTK Tutorials_.
* В поле "Описание" можно ввести описание (необязательно).
* Поле "URL-адрес" оставьте пустым.

Затем нажмите кнопку **Create** (Создать), чтобы создать приложение.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

Когда Photon завершит процесс создания, на панели мониторинга появится новое приложение PUN.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Подключение проекта Unity к приложению PUN

В этом разделе показано, как подключить проект Unity к приложению PUN, которое вы создали при работе с предыдущим разделом.

На панели мониторинга Photon щелкните поле **ИД приложения**, чтобы отобразить идентификатор приложения, а затем скопируйте его в буфер обмена.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

В меню Unity последовательно выберите **Window** > **Photon Unity Networking** > **PUN Wizard** (Окно > Photon Unity Networking > Мастер PUN), чтобы открыть окно мастера PUN. Затем нажмите кнопку **Проект установки**, чтобы открыть меню PUN Setup (Настройка PUN), и настройте его, как описано ниже.

* В поле **AppId or Email** (Идентификатор приложения или адрес электронной почты) вставьте идентификатор приложения PUN, скопированный на предыдущем шаге.

Затем нажмите кнопку **Проект установки**, чтобы применить идентификатор приложения.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

Когда в Unity завершится процесс настройки PUN, в меню PUN Setup (Настройка PUN) появится сообщение **Готово!** В окне Project (Проект) будет автоматически выбран актив **PhotonServerSettings**, чтобы в окне Inspector (Инспектор) отображались его свойства.

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a>Поздравляем!

Вы успешно создали приложение PUN и подключили его к проекту Unity. Следующим шагом будет разрешение подключений для других пользователей, чтобы несколько пользователей могли видеть работу друг друга.

[Следующее руководство: 3. Подключение нескольких пользователей](mr-learning-sharing-03.md)
