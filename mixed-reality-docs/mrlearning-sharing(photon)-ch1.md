---
title: Руководства по многопользовательским возможностям, часть 1. Настройка Photon Unity Networking
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610797"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Настройка Photon Unity Networking

## <a name="overview"></a>Обзор

В этом учебнике вы узнаете, как подготовиться к созданию возможностей для совместного взаимодействия с помощью Photon Unity Networking (PUN). Photon — это одна из нескольких сетевых платформ, на основе которых разработчики смешанной реальности могут создавать возможности для совместного взаимодействия. Вы узнаете, как создать приложение Photon PUN, импортировать активы Photon PUN в проект Unity и подключить проект Unity к приложению Photon PUN.

## <a name="objectives"></a>Задачи

* Вы научитесь создавать приложение Photon PUN.
* Вы узнаете, как найти и импортировать активы Photon PUN.
* Вы узнаете, как подключить проект Unity к приложению Photon PUN.

## <a name="prerequisites"></a>Предварительные условия

>[!TIP]
>Если вы еще не прошли учебники по [началу работы](mrlearning-base.md) или по [Пространственным привязкам Azure](mrlearning-asa-ch1.md), мы рекомендуем начать знакомство именно с этих серий.

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* Базовые навыки программирования на C#.
* Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.
* Выполните инструкции из раздела [Создание ресурса Пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) в статье [Краткое руководство. Создание приложения Unity HoloLens, которое использует Пространственные привязки Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).

> [!IMPORTANT]
> Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X. Это заменяет все требования к версии Unity и рекомендации, указанные выше.

## <a name="creating-and-preparing-the-unity-project"></a>Создание и подготовка проекта Unity

В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.

Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mrlearning-base-ch1.md), за исключением раздела [Разработка приложения для устройства](mrlearning-base-ch1.md#build-your-application-to-your-device), то есть следующие действия:

1. [Создайте новый проект Unity](mrlearning-base-ch1.md#create-new-unity-project) и присвойте ему понятное имя, например *MRTK Tutorials*.

2. [Настройте проект Unity для Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality).

3. [Импортируйте требуемые ресурсы TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources).

4. [Импортируйте Набор средств для смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

5. [Настройте проект Unity для Набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit).

6. [Добавьте Набор средств для смешанной реальности к сцене Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) и присвойте этой сцене понятное имя, например *MultiUserCapabilities*.

Затем следуйте инструкциям [по настройке профилей Набора средств для смешанной реальности (изменение параметра отображения сведений о пространственном состоянии)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option), чтобы указать для сцены профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** и значение **Перекрытие** для метода отображения сетки отслеживания пространственного положения.

> [!CAUTION]
> Как описано в инструкции по [настройке проекта Unity для Набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), ссылка на которую предложена выше, мы настоятельно рекомендуем не включать MSBuild для Unity.

## <a name="configuring-the-capabilities"></a>Настройка функциональных возможностей

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player** >  **Publishing Settings** (Проигрыватель > Параметры публикации).

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient** (Интернет-клиент), **Microphone** (Микрофон) и **SpatialPerception** (Пространственное восприятие), которые вы включили при создании проекта в начале работы с этим руководством. Теперь включите возможности **InternetClientServer**, **PrivateNetworkClientServer** и **RemovableStorage**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a>Добавление встроенных пакетов Unity
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

В рамках этого раздела вы установите встроенный пакет AR Foundation для Unity, который необходим для пакета SDK Пространственных привязок Azure, который вы будете импортировать в рамках следующей части руководства.

В меню Unity последовательно выберите **Window** > **Диспетчер пакетов**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> Может пройти несколько секунд, прежде чем пакет AR Foundation появится в списке.

В окне диспетчера пакетов выберите **AR Foundation** и установите этот пакет, щелкнув кнопку **Установить**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Импорт активов для руководства

Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (версия 2.1.1);
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> После импорта пакета учебных активов MultiUserCapabilities в окне консоли появятся несколько ошибок [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246). Они указывают на отсутствие типа или пространства имен. Этих проблем следовало ожидать, инструкции по их устранению будут приведены в следующем разделе при импорте активов Photon.

## <a name="importing-the-photon-assets"></a>Импорт активов Photon

В рамках этого раздела вы импортируете активы Photon Unity Network (PUN) из портала Asset Store в Unity.

В меню Unity последовательно выберите **Window** > **Asset Store** (Окно > Asset Store), чтобы открыть окно Asset Store. Найдите и выберите актив **PUN 2 — FREE** от Exit Games, а затем нажмите кнопку **Скачать**, чтобы скачать пакет активов в учетную запись Unity:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

После скачивания нажмите кнопку **Импорт**, чтобы открыть окно Import Unity Package (Импорт пакета Unity).

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

Когда в Unity завершится процесс импорта, появится окно мастера PUN с открытым меню PUN Setup (Настройка PUN). На данный момент вы можете проигнорировать или закрыть это окно.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a>Настройка Photon

В рамках этого раздела вы создадите учетную запись Photon, если у вас ее еще нет, а также создадите приложение PUN.

Перейдите на <a href="https://dashboard.photonengine.com/account/signin" target="_blank">панель мониторинга</a> Photon и войдите в систему, если у вас уже есть учетная запись, которую вы хотите использовать. В противном случае щелкните ссылку **Создать** и следуйте инструкциям, чтобы зарегистрировать новую учетную запись.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

После входа нажмите кнопку **Создать приложение**.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

На странице создания приложения введите приведенные ниже значения.

* В раскрывающемся списке Photon Type (Тип Photon) выберите Photon PUN.
* В поле "Имя" введите подходящее имя, например _MRTK Tutorials_.
* В поле "Описание" можно ввести описание (необязательно).
* Поле "URL-адрес" оставьте пустым.

Затем нажмите кнопку **Создать**, чтобы создать приложение.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

Когда процесс создания завершится, на панели мониторинга появится новое приложение PUN.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Подключение проекта Unity к приложению PUN

В рамках этого раздела вы подключите проект Unity к приложению PUN, которое вы создали в предыдущем разделе.

На панели мониторинга Photon щелкните поле **ИД приложения**, чтобы отобразить идентификатор приложения, а затем скопируйте его в буфер обмена.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

В меню Unity последовательно выберите **Window** > **Photon Unity Networking** > **PUN Wizard** (Окно > Photon Unity Networking > Мастер PUN), чтобы открыть окно мастера PUN. Затем нажмите кнопку **Проект установки**, чтобы открыть меню PUN Setup (Настройка PUN), и настройте его, как описано ниже.

* В поле **AppId or Email** (Идентификатор приложения или адрес электронной почты) вставьте идентификатор приложения PUN, скопированный на предыдущем шаге.

Затем нажмите кнопку **Проект установки**, чтобы применить идентификатор приложения.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

Когда в Unity завершится процесс настройки PUN, в меню PUN Setup (Настройка PUN) появится сообщение **Готово!** и в окне проекта будет автоматически выбран актив **PhotonServerSettings**, чтобы в окне "Инспектор" отображались его свойства.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a>Поздравляем!

Вы успешно создали приложение Photon PUN и подключили его к проекту Unity. Следующим шагом будет разрешение подключений для других пользователей, чтобы несколько пользователей могли видеть работу друг друга.

[Следующее руководство: 2. Подключение нескольких пользователей](mrlearning-sharing(photon)-ch2.md)
