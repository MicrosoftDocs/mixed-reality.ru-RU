---
title: Руководства по Пространственным привязкам Azure, часть 1 Начало работы с Пространственными привязками Azure
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: fa0ebc409fa38f664bdd0966906c6fd77f7a6081
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376151"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Начало работы с Пространственными привязками Azure

## <a name="overview"></a>Обзор

Вас приветствует вторая серия руководств по HoloLens 2. В трех частях этой серии руководств вы получите основные сведения о Пространственных привязках Azure.

Первое руководство [Начало работы с Пространственными привязками Azure](mrlearning-asa-ch1.md) поможет изучить процессы, необходимые для запуска и завершения сеанса Azure, а также для создания, отправки и скачивания привязок Azure на одном устройстве.

Из второго руководства [Сохранение, извлечение и совместное использование Пространственных привязок Azure](mrlearning-asa-ch2.md) вы узнаете, как сохранять Пространственные привязки Azure в нескольких сеансах приложения, сохраняя сведения о привязке в хранилище HoloLens 2, и как передать эти сведения о привязке на другие устройства для согласования привязок между несколькими устройствами.

Из третьего руководства [Отображение отзывов от Пространственной привязки Azure](mrlearning-asa-ch3.md) вы узнаете, как предоставить пользователям информацию о событиях и состояниях привязки при использовании Пространственных привязок Azure.

## <a name="objectives"></a>Задачи

* Изучите основы разработки Пространственных привязок Azure для HoloLens 2
* Создание, передача и скачивание пространственных привязок

## <a name="prerequisites"></a>Предварительные условия

>[!TIP]
>Если вы еще не прошли руководства из серии, посвященной [началу работы](mrlearning-base.md), мы рекомендуем начать знакомство именно с этой серии.

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* Базовые навыки программирования на C#.
* Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.
* Выполните инструкции из раздела [Создание ресурса Пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) в статье [Краткое руководство. Создание приложения Unity HoloLens, которое использует Пространственные привязки Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).

> [!IMPORTANT]
> Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X. Это заменяет все требования к версии Unity и рекомендации, указанные выше.

## <a name="creating-the-unity-project"></a>Создание проекта Unity
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.

Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mrlearning-base-ch1.md), за исключением раздела [Разработка приложения для устройства](mrlearning-base-ch1.md#build-your-application-to-your-device), то есть следующие действия:

1. [Создайте новый проект Unity](mrlearning-base-ch1.md#create-new-unity-project) и присвойте ему понятное имя, например *MRTK Tutorials*.

2. [Настройте проект Unity для Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality).

3. [Импортируйте требуемые ресурсы TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources).

4. [Импортируйте Набор средств для смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

5. [Настройте проект Unity для Набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit).

6. [Добавьте Набор средств для смешанной реальности к сцене Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) и присвойте этой сцене понятное имя, например *AzureSpatialAnchors*.

Затем следуйте инструкциям [по настройке профилей Набора средств для смешанной реальности (изменение параметра отображения сведений о пространственном состоянии)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option), чтобы указать для сцены профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** и значение **Перекрытие** для метода отображения сетки отслеживания пространственного положения.

> [!CAUTION]
> Как описано в инструкции по [настройке проекта Unity для Набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), ссылка на которую предложена выше, мы настоятельно рекомендуем не включать MSBuild для Unity.

## <a name="adding-inbuilt-unity-packages"></a>Добавление встроенных пакетов Unity
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

В рамках этого раздела вы установите встроенный пакет AR Foundation для Unity, который необходим для пакета SDK Пространственных привязок Azure, который вы будете импортировать в рамках следующей части руководства.

В меню Unity последовательно выберите **Window** > **Диспетчер пакетов**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> Может пройти несколько секунд, прежде чем пакет AR Foundation появится в списке.

В окне диспетчера пакетов выберите **AR Foundation** и установите этот пакет, щелкнув кнопку **Установить**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Импорт активов для руководства

Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (версия 2.1.1);
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage);
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage).

> [!TIP]
> Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Создание и подготовка сцены
<!-- TODO: Consider renaming to 'Preparing the scene' -->

В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.

В окне проекта перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Заготовки). Удерживая нажатой клавишу CTRL, последовательно щелкните заготовки **ButtonParent**, **DebugWindow**, **Instructions** и **ParentAnchor**, чтобы выбрать их:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

Когда все четыре заготовки будут выбраны, перетащите их вместе в окно "Иерархия", чтобы добавить в сцену:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

Чтобы перенести фокус на объекты сцены, дважды щелкните объект ParentAnchor и немного уменьшите масштаб представления:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> Если вы считаете, что большие значки в сцене (как большие "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Настройка кнопок для управления сценой

В рамках этого раздела вы добавите в сцену скрипты, чтобы создать серию событий кнопок для демонстрации базовых приемов работы и поведения локальных привязок, а также Пространственных привязок Azure в приложении.

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. Настройка компонента Pressable Button Holo Lens 2 (Script)

В окне "Иерархия" разверните объект **ButtonParent**. Выберите в нем первый дочерний объект с именем **StartAzureSession**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

В окне "Инспектор" найдите компонент **Pressable Button Holo Lens 2 (Script)** (Нажимаемая кнопка Holo Lens 2 — скрипт). Добавьте новый прослушиватель событий к событию **Button Pressed ()** (Нажатие кнопки), щелкнув значок **+** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

Сохраняя объект StartAzureSession выделенным в окне "Иерархия", щелкните и перетащите объект **ParentAnchor** из окна "Иерархия" в пустое поле **None (Object)** только что созданного прослушивателя событий, чтобы объект ParentAnchor ожидал передачи данных о событии нажатия для этой кнопки:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

Щелкните раскрывающийся список **No Function** (Нет функции) для того же прослушивателя событий. Затем выберите **AnchorModuleScript** > **StartAzureSession ()** , чтобы назначить функции StartAzureSession () роль действия, которое вызывается при получении от этой кнопки событий нажатия кнопки:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. Настройка компонента Interactable (Script)

Сохраняя объект StartAzureSession выделенным в окне "Иерархия", найдите в окне "Инспектор" компонент **Interactable (Script)** (Взаимодействие — скрипт). Повторно выполните описанный выше в шаге 1 процесс для события **OnClick ()** (Щелчок):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. Настройка остальных кнопок

Для всех остальных кнопок повторно выполните процессы, которые описаны выше в шагах 1 и 2, чтобы назначить функции событиям **Button Pressed ()** (Нажатие кнопки) и **OnClick ()** (Щелчок) следующим образом:

* Для объекта **StopAzureSession** назначьте функцию AnchorModuleScript > **StopAzureSession ()** .
* Для объекта **CreateAzureAnchor** назначьте функцию AnchorModuleScript > **CreateAzureAnchor ()** .
  * Затем снова перетащите **ParentAnchor** в пустое поле **None (Game Object)** .
* Для объекта **RemoveLocalAnchor** назначьте функцию AnchorModuleScript > **RemoveLocalAnchor ()** .
  * Затем снова перетащите **ParentAnchor** в пустое поле **None (Game Object)** .
* Для объекта **FindAzureAnchor** назначьте функцию AnchorModuleScript > **FindAzureAnchor ()** .
* Для объекта **DeleteAzureAnchor** назначьте функцию AnchorModuleScript > **DeleteAzureAnchor ()** .

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. Подключение сцены к ресурсу Azure

В окне "Иерархия" выберите объект **ParentAnchor**. Затем в окне "Инспектор" прокрутите содержимое вниз до компонента **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт).

Теперь в разделе **Учетные данные** вставьте значения идентификатора и ключа учетной записи Пространственных привязок, которую вы создали при подготовке [предварительных условий](mrlearning-asa-ch1.md#prerequisites) для этого руководства, в соответствующие поля **Spatial Anchors Account Id** (Идентификатор учетной записи пространственных привязок) и **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Изучение базового поведения Пространственных привязок Azure

Теперь, когда в сцене все готово для работы с основными функциями Пространственных привязок Azure, можно развернуть приложение и познакомиться с Пространственными привязками Azure.

### <a name="1-add-additional-required-capabilities"></a>1. Добавление дополнительных требуемых возможностей

В меню Unity последовательно щелкните элементы **Edit (Правка)**  > **Project Settings... (Параметры проекта...)** , чтобы открыть окно параметров проигрывателя:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

В окне "Параметры проигрывателя" выберите элемент **Проигрыватель**, а затем — элемент **Параметры публикации**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient** (Интернет-клиент), **Microphone** (Микрофон) и **SpatialPerception** (Пространственное восприятие), которые вы включили при создании проекта в начале работы с этим руководством. Теперь включите возможности **InternetClientServer** (Сервер интернет-клиента), **PrivateNetworkClientServer** (Сервер клиента частной сети), **RemovableStorage** (Съемный носитель) и **Webcam** (Веб-камера):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Разверните приложение на устройстве HoloLens 2

Пространственные привязки Azure не могут работать в Unity. Поэтому для проверки функциональных возможностей этой службы вам придется развернуть проект на устройстве.

> [!TIP]
> Чтобы вспомнить, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, воспользуйтесь инструкциями из раздела о [разработке приложения для устройства](mrlearning-base-ch1.md#build-your-application-to-your-device).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Запустите приложение на HoloLens 2 и следуйте предоставленным инструкциям

> [!CAUTION]
> Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки. Поэтому обеспечьте подключение устройства к Интернету.

Запустив на устройстве приложение, выполните инструкции, представленные на экране панели со сведениями для руководства по Пространственным привязкам Azure.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>Привязка к взаимодействию

В предыдущих разделах вы изучили базовые принципы Пространственных привязок Azure. С помощью куба мы представили и визуализировали родительский объект игры с прикрепленной привязкой. Из этого раздела вы узнаете, как привязать взаимодействие целиком, разместив его в дочернем элементе объекта ParentAnchor.

### <a name="1-add-the-rocket-launcher-experience"></a>1. Добавление взаимодействия Rocket Launcher

В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** и выберите заготовку **RocketLauncher_Complete**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

Сохраняя выбранной заготовку RocketLauncher_Complete, перетащите ее поверх объекта **ParentAnchor** в окне "Иерархия", чтобы сделать дочерним элементом объекта ParentAnchor:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. Перемещение взаимодействия Rocket Launcher

Вы можете изменять положение, угол наклона и масштаб объекта **RocketLauncher_Complete** произвольным образом, сохраняя объект **ParentAnchor** открытым, например:

* для параметра преобразования **Position** (Положение) укажите значения X = 0, Y = 0, Z = 3.75;
* для параметра преобразования **Rotation** (Поворот) укажите значения X = 0, Y = 90, Z = 0;
* для параметра преобразования **Scale** (Масштаб) укажите значения X = 10, Y = 10, Z = 10.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

В этом приложении пользователи могут перемещать взаимодействие Rocket Launcher целиком, передвигая соответствующий куб.

> [!TIP]
> Есть много потоков взаимодействия с пользователем для изменения положения, в том числе: перемещение объекта (например, куба в этом руководстве), включение ограничивающего прямоугольника вокруг взаимодействия нажатием кнопки, применение манипуляторов положения и вращения и другие.

## <a name="congratulations"></a>Поздравляем!

В рамках этого руководства вы изучили базовые принципы Пространственных привязок Azure. Этого руководство предоставило вам несколько кнопок, которые помогли изучить процессы, необходимые для запуска и завершения сеанса Пространственных привязок Azure, а также создания, отправки и скачивания привязок Azure на одном устройстве.

Из следующего урока вы узнаете, как сохранить идентификаторы привязок Azure на устройстве HoloLens 2 таким образом, чтобы их можно было извлечь даже после перезапуска, и как передавать идентификаторы привязок между несколькими устройствами для достижения пространственного выравнивания.

[Следующий урок. 2. Сохранение, получение и совместное использование пространственных привязок Azure](mrlearning-asa-ch2.md)
