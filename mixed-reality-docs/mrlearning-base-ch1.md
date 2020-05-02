---
title: Руководства по началу работы Инициализация проекта и первое приложение
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 56adb4bfc66768684c8269c0f0cafd70c486ea8a
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376211"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Инициализация проекта и первое приложение

## <a name="overview"></a>Обзор

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
B этом первом руководстве описаны некоторые возможности <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">набора средств для Смешанной реальности (MRTK)</a>. Также вы узнаете, как запустить свое первое приложение для HoloLens 2 и развернуть его на устройстве.

## <a name="objectives"></a>Задачи

* Настройка Unity для разработки решений для HoloLens.
* Импорт ресурсов и настройка сцены.
* Визуализация сетки пространственного сканирования, виртуальных рук и счетчика частоты кадров.

## <a name="prerequisites"></a>Предварительные условия

* Компьютер с Windows 10, настроенный с требуемыми [установленными инструментами](install-the-tools.md).
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* Базовые навыки программирования на C#.
* Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.

> [!IMPORTANT]
> Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X. Это заменяет все требования к версии Unity и рекомендации, указанные выше.

## <a name="create-new-unity-project"></a>Создание проекта Unity

Запустите **Unity Hub**, откройте вкладку **Projects** (Проекты) и щелкните **стрелку вниз** рядом с кнопкой **New** (Создать):

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

Выберите версию Unity, указанную в разделе с [предварительными требованиями](#prerequisites) выше.

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

В окне Create a new project (Создание нового проекта) сделайте следующее:

* Убедитесь, что для параметра **Templates** (Шаблоны) задано значение **3D**.
* Укажите понятное **имя проекта**, например _MRTK Tutorials_.
* Выберите подходящее **расположение** для хранения проекта, например _D:\MixedRealityLearning_.
* Нажмите кнопку **Create** (Создать), чтобы создать и запустить новый проект Unity.

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> В Windows для переменной MAX_PATH есть ограничение в 255 символов. Так как эти ограничения распространяются и на Unity, может произойти сбой компиляции, если длина пути к файлу превысит 255 символов. Поэтому настоятельно рекомендуется хранить проект Unity как можно ближе к корневому каталогу диска.

Подождите, пока Unity создаст проект:

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Настройка проекта Unity для Windows Mixed Reality

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

В этом разделе описано, как переключить платформу сборки, включить виртуальную реальность и настроить возможность пространственного восприятия.

### <a name="1-switch-build-platform"></a>1. Переключение платформы сборки

В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

Подождите, пока Unity переключит платформу:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a>2. Включение виртуальной реальности

> [!NOTE]
> Включение виртуальной реальности также распространяется на гарнитуры дополненной и смешанной реальности, так как при этом включается стереоскопическое изображение (отрисовка разных изображений для каждого глаза).

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

В окне параметров проекта щелкните **Player** > **XR Settings** (Проигрыватель >Параметры XR), чтобы развернуть окно параметров XR:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

В окне параметров XR установите флажок **Virtual Reality Supported** (Поддерживаемая виртуальная реальность), чтобы включить виртуальную реальность, а затем щелкните значок **+** и выберите **Windows Mixed Reality**, чтобы добавить пакет SDK для Windows Mixed Reality:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

Подождите, пока Unity добавит пакет SDK:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

Когда Unity добавит пакет SDK, оптимизируйте параметры XR следующим образом:

* В Windows Mixed Reality задайте для параметра **Depth Format** (Формат глубины) значение **16-bit depth** (16-разрядная глубина).
* В Windows Mixed Reality установите флажок **Enable Depth Sharing** (Совместное использование глубины).
* Для параметра **Stereo Rendering Mode\*** (Режим стереоскопической отрисовки) задайте значение **Single Pass Instanced** (Однопроходная отрисовка экземпляра).

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> См. сведения об оптимизации Unity для Windows Mixed Reality в документации по [рекомендуемым параметрам для Unity](recommended-settings-for-unity.md).

### <a name="3-enable-spatial-perception"></a>3. Включение пространственного восприятия

> [!NOTE]
> Пространственное восприятие позволяет визуализировать сетку пространственного сканирования на устройствах Windows Mixed Reality.

В окне параметров проекта щелкните **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), чтобы развернуть окно параметров публикации:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

В окне параметров публикации прокрутите вниз до раздела **Capabilities** (Возможности) и установите флажок **Spatial Perception** (Пространственное восприятие).

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

Закройте окно параметров проекта.

## <a name="import-textmesh-pro-essential-resources"></a>Импорт требуемых ресурсов TextMesh Pro

> [!NOTE]
> Мы импортируем этот пакет, так как он требуется для работы элементов пользовательского интерфейса набора средств Смешанной реальности.

В меню Unity щелкните **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Окно > TextMeshPro > Импорт требуемых ресурсов TMP):

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a>Импорт набора средств для смешанной реальности

Скачайте пользовательский пакет Unity:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

В меню Unity щелкните **Assets** > **Import Package** > **Custom Package** (Ресурсы > Импорт пакетов > Пользовательский пакет), чтобы открыть окно импорта пакетов:

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

В окне импорта пакетов выберите скачанный пакет **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** и нажмите кнопку **Open** (Открыть):

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a>Настройка проекта Unity для набора средств для Смешанной реальности

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

После импорта пакета должно отобразиться окно конфигуратора проекта МРТК. В противном случае откройте это окно, щелкнув **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств для Смешанной реальности > Служебные программы > Настроить проект Unity) в меню Unity.

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

В окне конфигуратора проектов МРТК разверните раздел **Modify Configurations** (Изменение конфигураций), <u>снимите флажок</u> **Enable MSBuild for Unity** (Включить MSBuild для Unity), убедитесь, что настроены остальные параметры, и нажмите кнопку **Apply** (Применить), чтобы применить эти параметры:

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> Так как MSBuild для Unity может поддерживать не все пакеты SDK, которые будут использоваться, с отключением могут быть проблемы. Поэтому настоятельно рекомендуется не включать MSBuild для Unity.

## <a name="configure-the-mixed-reality-toolkit"></a>Настройка набора средств для смешанной реальности
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

В меню Unity щелкните **Mixed Reality Toolkit** > **Add to Scene and Configure** (Набор средств для Смешанной реальности > Добавить в сцену и настроить), чтобы добавить набор средств для Смешанной реальности в текущую сцену:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

Выбрав объект MixedRealityToolkit в окне иерархии, измените профиль конфигурации набора средств для Смешанной реальности на **DefaultMixedRealityToolkitConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

> [!IMPORTANT]
> Как правило, при разработке для HoloLens 2 используется DefaultHoloLens2ConfigurationProfile. Но при работе с этим руководством вы будете использовать DefaultMixedRealityToolkitConfigurationProfile, а затем при работе со следующим руководством по [созданию пользовательского интерфейса и настройке набора Средств смешанной реальности](mrlearning-base-ch2.md) — DefaultHoloLens2ConfigurationProfile.

В меню Unity щелкните **File** > **Save As...** (Файл > Сохранить как), чтобы открыть окно сохранения сцены:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

В окне сохранения сцены перейдите к папке **Scenes** проекта, присвойте сцене понятное имя, например _GettingStarted_, и нажмите кнопку **Save** (Сохранить), чтобы сохранить сцену:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a>Разработка приложения для устройства

### <a name="1-build-the-unity-project"></a>1. Создание проекта Unity

В меню Unity щелкните **File** > **Build Settings** (Файл > Параметры сборки), чтобы открыть окно параметров сборки.

В окне параметров сборки нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке), а затем нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки универсальной платформы Windows:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

В окне сборки универсальной платформы Windows выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_, создайте папку и присвойте ей понятное имя, например _GettingStarted_, а затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы запустить процесс сборки:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

Подождите, пока Unity завершит сборку:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Сборка и развертывание приложения

По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой. Перейдите в папку и дважды щелкните файл решения, чтобы открыть его в Visual Studio:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по [установке средств](install-the-tools.md).

Настройте Visual Studio для устройства HoloLens 2, выбрав конфигурацию **Ведущий** или **Выпуск**, архитектуру **ARM** и целевой объект **Устройство**:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

> [!NOTE]
> Если устройство не отображается как вариант, возможно, придется изменить проект запуска по умолчанию, указав вместо проекта IC2Lpp проект UWP. В **обозревателе решений** щелкните правой кнопкой мыши **имя_проекта (Universal Windows)** и выберите **Set as StartUp Project** (Назначить запускаемым проектом). 

Подключите HoloLens 2 к компьютеру.

> [!IMPORTANT]
> Перед выполнением сборки устройство нужно перевести в режим разработчика и связать с компьютером разработки. Оба эти действия можно выполнить, следуя [этим инструкциям](using-visual-studio.md).

Завершающий шаг — это сборка и развертывание на вашем устройстве. Для этого щелкните **Отладка** > **Запуск без отладки**:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

Хотя в этих инструкциях предполагается, что вы будете развертывать приложение на устройстве HoloLens 2, вы можете также развернуть его на [эмуляторе HoloLens 2](using-the-hololens-emulator.md) или создать [пакет приложения для передачи данных на другое локальное устройство](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).

Выбор параметра "Запуск без отладки" приведет к немедленному запуску приложения на вашем устройстве после успешной сборки, но без подключения отладчика и отображения сведений об отладке в Visual Studio. Это также означает, что вы можете отсоединить USB-кабель во время выполнения приложения на устройстве HoloLens 2, не прерывая его работу.

Кроме того, вы можете выбрать "Сборка" > "Развернуть решение", чтобы развернуть решение на устройстве без автоматического запуска приложения.

## <a name="congratulations"></a>Поздравляем!

<!-- TODO: Consider cleanup and adding in app screenshots -->
Вы развернули свое первое приложение HoloLens 2. Перемещаясь, вы увидите, как пространственная сетка сопоставления покрывает все поверхности, воспринятые HoloLens 2. Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения. Это лишь некоторые из основополагающих компонентов, входящих в комплект поставки набора средств для смешанной реальности. В следующих руководствах описано, как добавлять содержимое и интерактивные средства в сцену, чтобы в полной мере изучить возможности HoloLens 2 и набора средств для Смешанной реальности.

> [!NOTE]
> При работе приложения можно заметить, что профилировщик диагностики позволяет переключать видимость с помощью команды **Toggle Diagnostics** (Переключить диагностику). Но обычно рекомендуется не закрывать профилировщик во время разработки. Так вы сможете определить, влияют ли изменения приложения на производительность (например, приложение HoloLens 2 должно [непрерывно выполняться с частотой 60 кадров в секунду](understanding-performance-for-mixed-reality.md)).

[Следующее руководство: 3. Создание пользовательского интерфейса и настройка набора средств для Смешанной реальности](mrlearning-base-ch2.md)
