---
title: Руководства по использованию службы "Речь" в Azure, часть 1. Интеграция и использование средств распознавания и транскрибирования речи
description: В рамках этого курса вы узнаете, как реализовать пакет SDK службы "Речь" в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: a72eb808adbc14df65c55e694ea985d97f9ec24c
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79032474"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. Интеграция и использование средств распознавания и транскрибирования речи

## <a name="overview"></a>Обзор


В этой серии руководств вы создадите приложение смешанной реальности и на его примере изучите использование служб распознавания речи Azure с HoloLens 2. Изучив эту серию руководств, вы сможете применять микрофон устройства для транскрибирования речи в текст в режиме реального времени, переводить эту речь на другие языки и применять распознавание намерений для анализа голосовых команд с применением искусственного интеллекта.

## <a name="objectives"></a>Задачи

* Сведения об интеграции службы речи Azure с приложением HoloLens 2.
* Сведения об использовании функции распознавания речи для транскрибирования текста

## <a name="prerequisites"></a>Предварительные условия

>[!TIP]
>Если вы еще не прошли руководства из серии, посвященной [началу работы](mrlearning-base.md), мы рекомендуем начать знакомство именно с этой серии.

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* Базовые навыки программирования на C#.
* Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.

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

6. [Добавьте Набор средств для смешанной реальности к сцене Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) и присвойте этой сцене понятное имя, например *AzureSpeechServices*.

Затем следуйте инструкциям [по настройке профилей Набора средств для смешанной реальности (изменение параметра отображения сведений о пространственном состоянии)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option), чтобы указать для сцены профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** и значение **Перекрытие** для метода отображения сетки отслеживания пространственного положения.

> [!CAUTION]
> Как описано в инструкции по [настройке проекта Unity для Набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), ссылка на которую предложена выше, мы настоятельно рекомендуем не включать MSBuild для Unity.

## <a name="configuring-the-speech-commands-start-behavior"></a>Настройка поведения для начала речевых команд

Поскольку для распознавания и транскрибирования речи вы будете применять пакет SDK "Речь", вам нужно настроить речевые команды MRTK так, чтобы они не мешали работе пакета SDK "Речь". Чтобы добиться этого, измените поведение начала речевых команд с Auto Start (Автозапуск) на Manual Start (Запуск вручную).

Выделив объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), выберите в окне Inspector (Инспектор) вкладку **Input** (Ввод), клонируйте профили **DefaultHoloLens2InputSystemProfile** и **DefaultMixedRealitySpeechCommandsProfile**, а затем измените для речевых команд параметр **Start Behavior** (Поведение начала) на **Manual Start** (Старт вручную):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> Инструкции по [настройке Набора средств для смешанной реальности](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) помогут вам освежить в памяти клонирование и настройку профилей MRTK.

## <a name="configuring-the-capabilities"></a>Настройка функциональных возможностей

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player** >  **Publishing Settings** (Проигрыватель > Параметры публикации).

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient** (Интернет-клиент), **Microphone** (Микрофон) и **SpatialPerception** (Пространственное восприятие), которые вы включили при создании проекта в начале работы с этим руководством. Теперь включите возможности **InternetClientServer** (Сервер интернет-клиента) и **PrivateNetworkClientServer** (Сервер клиента частной сети):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Импорт активов для руководства

Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (последняя версия);
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage);
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage).

> [!TIP]
> Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a>Подготовка сцены

В этом разделе вы подготовите сцену, добавив заготовку для руководства, и настроите компонент Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт) для управления сценой.

В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** и перетащите заготовку **Lunarcom**в окно Hierarchy (Иерархия), чтобы добавить ее в сцену:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

В окне Hierarchy (Иерархия) сохраните выделение объекта **Lunarcom**, а в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Controller (Script)** (Контроллер Lunarcom — скрипт) к объекту Lunarcom.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> Компонент Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт) не входит в состав MRTK. Он был предоставлен с активами для этого руководства.

Сохраняя выделение объекта **Lunarcom**, разверните его для просмотра списка дочерних объектов, затем перетащите объект **Terminal** (Терминал) в поле **Terminal** (Терминал) объекта Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

Сохраняя выделение объекта **Lunarcom**, разверните объект Terminal (Терминал) для просмотра списка его дочерних объектов, затем перетащите объект **ConnectionLight** (Индикатор подключения) в поле **ConnectionLight** (Индикатор подключения) объекта Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт), а объект **OutputText** (Выходной текст) — в поле **Output Text** (Выходной текст):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

Сохраняя выделение объекта **Lunarcom**, разверните объект Buttons (Кнопки), чтобы открыть список его дочерних объектов, а затем в окне "Инспектор" разверните список **Buttons** (Кнопки), установите для его параметра **Size** (Размер) значение 3 и перетащите объекты **MicButton**, **SatelliteButton** и **RocketButton** в поля **Элемент** с номерами 0, 1 и 2, соответственно:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>Подключение проекта Unity к ресурсу Azure

Чтобы использовать службу речи Azure, потребуется создать ресурс Azure и получить ключ API для службы "Речь". Выполните инструкции [по применению бесплатной версии службы "Речь"](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) и выясните регион (расположение) вашей службы и значение ключа API (это может быть Key1 или Key2).

В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) найдите в компоненте **Lunarcom Controller (Script)** (Контроллер Lunarcom — скрипт) раздел **Speech SDK Credentials** (Учетные данные пакета SDK) и настройте его, как описано ниже.

* В поле **Speech Service API Key** (Ключ API службы "Речь") введите значение ключа API (Key1 или Key2).
* В поле **Speech Service Region** (Регион службы "Речь") введите значение региона (расположения) службы, переведя все буквы в нижний регистр и удалив пробелы.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>Использование функции распознавания речи для транскрибирования речи

В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Speech Recognizer (Script)** (Распознаватель речи Lunarcom — скрипт) к объекту Lunarcom.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> Компонент Lunarcom Speech Recognizer (Script) (Распознаватель речи Lunarcom — скрипт) не входит в состав MRTK. Он был предоставлен с активами для этого руководства.

Войдя в игровой режим, вы сможете проверить распознавание речи. Для начала нажмите кнопку микрофона.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

Теперь, если на компьютере подключен микрофон, любой сказанный вами текст будет выводиться на панели терминала:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> Этому приложению требуется подключение к Azure, поэтому не забудьте проверить связь компьютера или устройства с Интернетом.

## <a name="congratulations"></a>Поздравляем!

Вы успешно реализовали функцию распознавания речи на платформе Azure. Запустите приложение на устройстве и убедитесь, что все работает правильно.

В следующем учебнике вы узнаете, как выполнять команды с помощью распознавания речи Azure.

[Следующее руководство: 2. Использование функции распознавания речи для выполнения команд](mrlearning-speechSDK-ch2.md)
