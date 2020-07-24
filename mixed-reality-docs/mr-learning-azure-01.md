---
title: Учебники по облачным службам Azure — 1. Облачные службы Azure для HoloLens 2
description: В рамках этого курса вы узнаете, как реализовать различные службы Azure в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: azure, смешанная реальность, unity, учебник, hololens, hololens 2, хранилище blob-объектов azure, табличное хранилище azure, пространственные привязки azure, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306004"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1. Облачные службы Azure для HoloLens 2

## <a name="overview"></a>Обзор

Представляем вашему вниманию серию учебников, посвященных переносу **облачных служб Azure** в приложение **HoloLens 2**. Из этой серии учебников в пяти частях вы узнаете, как интегрировать несколько **облачных служб Azure** в проект **Unity** для **HoloLens 2**. В каждой из последующих глав будут добавляться новые **облачные службы Azure** для расширения возможностей приложений и взаимодействий с пользователем. Кроме того, вы узнаете об основных принципах роботы **облачной службы Azure**.

> [!NOTE]
> В этой серии учебников основное внимание уделяется **HoloLens 2**, но из-за межплатформенного характера Unity большая часть материалов будет также применяться для классических приложений и смартфонов.

В этом первом учебнике [Знакомство с облачными службами Azure для HoloLens 2](mr-learning-azure-01.md) разъясняются цели приложения, а также приведено краткое описание каждой облачной службы Azure и настройки проекта Unity.

Во втором учебнике [Интеграция службы хранилища Azure](mr-learning-azure-02.md) вы выполните интеграцию службы хранилища Azure в качестве решения сохраняемости для демонстрационного приложения, узнаете о различиях между Хранилищем BLOB-объектов и хранилищем таблиц, подготовите необходимые ресурсы проекта, настроите сцену и проверите операции чтения, обновления и удаления данных.

Продолжая работу с третьим учебником [Интеграция Пользовательского визуального распознавания Azure](mr-learning-azure-03.md), вы будете использовать Пользовательское визуальное распознавание Azure для обучения и обнаружения изображений в приложении HoloLens 2. В начале главы приведены сведения о настройке ресурса "Пользовательское визуальное распознавание Azure", подготовке компонентов сцены и действия для обучения и обнаружения изображений в приложении.

Далее в четвертом учебнике [Интеграция пространственных привязок Azure](mr-learning-azure-04.md) вы изучите службы пространственных привязок Azure для сохранения и поиска расположений, а также основные концепции, подготовите необходимые ресурсы, настроите сцены и приступите к использованию новой функции в приложении.

С помощью пятого руководства [Интеграция службы Azure Bot с LUIS](mr-learning-azure-05.md) вы завершите обучение, предоставляя приложению новый метод взаимодействия с пользователем с использованием естественного языка. Эта функция будет реализована с помощью платформы Azure Bot Framework, а также службы "Распознавания речи" (LUIS). В этой заключительной главе рассказывается о принципах работы службы Azure Bot и ускорении процесса, который вы будете использовать в качестве решения с нулевым кодом с помощью Bot Framework Composer. После создания бота вы интегрируете его в сцену и запустите его на завершающем этапе приложения HoloLens 2.

## <a name="application-goals"></a>Цели приложения

В этой серии учебников вы создадите приложение **HoloLens 2**, которое может обнаруживать объекты на изображениях и находить их пространственное положение. Чтобы установить язык домена, необходимо вызвать такие сущности из **отслеживаемого объекта**.
Пользователь может создать **отслеживаемый объект**, чтобы связать набор изображений с помощью компьютерного зрения или пространственного положения. Все данные должны быть сохранены в облаке. Кроме того, некоторые аспекты приложения будут дополнительно контролироваться естественным языком с помощью бота.

### <a name="features"></a>Возможности

* Базовое управление данными и изображениями.
* Обучение и обнаружение изображений.
* Хранение пространственного положения и инструкций.
* Бот-помощник для использования некоторых возможностей с помощью естественного языка.

## <a name="azure-cloud-services"></a>Облачные службы Azure

Чтобы разрешить необходимые функции для приложения, вы будете использовать указанные ниже **облачные службы Azure**.

### <a name="azure-storage"></a>Служба хранилища Azure

Для решения сохраняемости будет использоваться [служба хранилища Azure](https://azure.microsoft.com/services/storage/). Она позволяет хранить данные в таблице и отправлять большие двоичные файлы, например изображения.

### <a name="azure-custom-vision"></a>Пользовательское визуальное распознавание Azure

С помощью [Пользовательского визуального распознавания Azure](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (в составе [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) можно связать с *отслеживаемыми объектами* набор изображений, обучить модель машинного обучения в наборе и определить *отслеживаемый объект*.

### <a name="azure-spatial-anchors"></a>Пространственные привязки Azure

Чтобы сохранить расположение *отслеживаемого объекта* и предоставить инструкции по его поиску, используйте [Пространственные привязки Azure](https://azure.microsoft.com/services/spatial-anchors/).

### <a name="azure-bot-service"></a>Служба Azure Bot

Приложение в основном управляется через традиционный пользовательский интерфейс, поэтому вы используете [службу Azure Bot](https://azure.microsoft.com/services/bot-service/), чтобы добавить некоторую индивидуальность и использовать новый метод взаимодействия.

## <a name="prerequisites"></a>Предварительные условия

>[!TIP]
>Если вы еще не прошли руководства из серии, посвященной [началу работы](mr-learning-base-01.md), мы рекомендуем начать знакомство именно с этой серии.

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* Базовые навыки программирования на C#.
* Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).
* Подключенная веб-камера, если вы хотите выполнить тестирование из редактора Unity.
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.X и модулем поддержки сборки универсальной платформы Windows.

> [!CAUTION]
> Рекомендуемая версия Unity для этой серии учебников — Unity 2019.3.X. Это заменяет все требования к версии Unity и рекомендации, указанные выше.

## <a name="creating-and-preparing-the-unity-project"></a>Создание и подготовка проекта Unity

В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.

Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:

1. [Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *Azure Cloud Tutorials*.
2. [Переключение платформы сборки.](mr-learning-base-02.md#configuring-the-unity-project)
3. [Импорт требуемых ресурсов TextMeshPro.](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Импорт набора средств для смешанной реальности (MRTK).](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Настройка проекта Unity.](mr-learning-base-02.md#configuring-the-unity-project)
6. [Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и назначение ей понятного имени, например *AzureCloudServices.*

Затем следуйте инструкциям по [изменению параметра отображения для отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), чтобы указать профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** для сцены и значение **Occlusion** (Перекрытие) для параметра отображения сетки отслеживания пространственного положения.

## <a name="installing-inbuilt-unity-packages"></a>Установка встроенных пакетов Unity

В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.

## <a name="importing-the-tutorial-assets"></a>Импорт активов для руководства

Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:

* [Хранилище Azure для Unity](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage).
* [Пространственные привязки Azure](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [MRTK.Tutorials.AzureCloudServices](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Создание и подготовка сцены
<!-- TODO: Consider renaming to 'Preparing the scene' -->

В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.

В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**. Удерживая нажатой клавишу CTRL, щелкните заготовки **SceneController**, **RootMenu** и **DataManager**, чтобы выбрать их:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

**SceneController (prefab)** (SceneController — заготовка) содержит два скрипта: **SceneController (script)** (SceneController — скрипт) и **UnityDispatcher (script)** (UnityDispatcher — скрипт). Компонент скрипта **SceneController** содержит несколько функций взаимодействия с пользователем и упрощает использование функции фотозахвата. **UnityDispatcher** является вспомогательным классом, позволяющим выполнять действия в основном потоке Unity.

**RootMenu (prefab)** (RootMenu — заготовка) является основной заготовкой пользовательского интерфейса, которая содержит все окна пользовательского интерфейса, подключенные друг к другу через различные небольшие компоненты скрипта и управляющие общим потоком интерфейса приложения.

**DataManager (prefab)** (DataManager — заготовка) отвечает за взаимодействие с хранилищем Azure. Она будет описана в следующем учебнике.

Теперь, когда все три заготовки будут выбраны, перетащите их вместе в окно "Иерархия", чтобы добавить в сцену:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

Чтобы перенести фокус на объекты сцены, дважды щелкните объект **RootMenu** и немного уменьшите масштаб представления:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> Если вы считаете, что большие значки в сцене (как большие "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение.

## <a name="configuring-the-scene"></a>Настройка сцены

В этом разделе вы будете вместе соединять объекты *SceneManager*, *DataManager* и *RootMenu*, чтобы подготовить рабочую сцену к работе со следующим учебником по [интеграции службы хранилища Azure](mr-learning-azure-01.md).

### <a name="connect-the-objects"></a>Соединение объектов

В окне Hierarchy (Иерархия) выберите объект **DataManager**:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

В окне Inspector (Инспектор) найдите компонент **DataManager (Script)** (DataManager — скрипт), вы увидите пустой слот в событии **On Data Manager Ready ()** . Теперь в окне Hierarchy (Иерархия) перетащите объект **SceneController** в событие **On Data Manager Ready ()** .

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

Вы увидите, что раскрывающееся меню события стало активным, щелкните его и перейдите к **SceneController**. В подменю выберите параметр **init ()** :

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

В окне Hierarchy (Иерархия) выберите объект **SceneController**. В окне Inspector (Инспектор) вы найдете компонент **SceneController (script)** (SceneController — скрипт).

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

Отобразятся несколько незаполненных полей. Заполните их. Переместите объект **DataManager** из окна Hierarchy (Иерархия) в поле *Data Manager* (Диспетчер данных) и переместите GameObject **RootMenu** из окна Hierarchy (Иерархия) в поле *Main Menu* (Главное меню).

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

Теперь сцена подготовлена для работы со следующими учебниками. Не забудьте сохранить ее в проекте.

## <a name="prepare-project-build-pipeline"></a>Подготовка конвейера сборки проекта

Хотя в проект еще нужно добавлять содержимое, выполните несколько действий, чтобы проект был готов к созданию **HoloLens 2**.

### <a name="1-add-additional-required-capabilities"></a>1. Добавление дополнительных требуемых возможностей

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

В окне параметров проекта выберите элемент **Player** (Проигрыватель), а затем — **Publishing Settings** (Параметры публикации):

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient** (Интернет-клиент), **Microphone** (Микрофон) и **SpatialPerception** (Пространственное восприятие), которые вы включили при создании проекта в начале работы с этим учебником. Теперь включите возможности **InternetClientServer** (Сервер интернет-клиента), **PrivateNetworkClientServer** (Сервер клиента частной сети) и **Webcam** (Веб-камера):

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Разверните приложение на устройстве HoloLens 2

Не все функции, которые будут использоваться в этой серии учебников, можно выполнять внутри редактора Unity. Это означает, что вам необходимо получить сведения о развертывании приложения на устройстве HoloLens 2.

> [!TIP]
> Чтобы вспомнить, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, воспользуйтесь инструкциями из раздела о [разработке приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2) в учебнике по началу работы.

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Запустите приложение на HoloLens 2 и следуйте предоставленным инструкциям

> [!CAUTION]
> Все службы Azure используют Интернет, поэтому обеспечьте подключение устройства к Интернету.

Когда приложение запускается на устройстве, предоставьте доступ к следующим запрошенным возможностям:

* микрофон
* Камера

Эти функции необходимы для правильной работы таких служб, как *чат-бот* и *Пользовательское визуальное распознавание*.

## <a name="congratulations"></a>Поздравляем!

Здесь вы ознакомились с серией учебников, узнали о функциях, которые будете реализовывать, и о том, как согласовывать **облачные службы Azure**, чтобы реализовать приложение *HoloLens 2*. Вы добавили необходимые компоненты в проект и подготовили сцену для работы с этой серией учебников.

На следующем уроке вы будете использовать хранилище Azure в качестве облачного решения для сохранения данных и изображений.

[Следующее руководство: 2. Интеграция службы хранилища Azure](mr-learning-azure-02.md)