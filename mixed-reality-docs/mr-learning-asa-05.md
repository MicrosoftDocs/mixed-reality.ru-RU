---
title: Руководства по Пространственным привязкам Azure, часть 5 Пространственные привязки Azure для Android и iOS
description: Пройдите этот курс и узнайте, как развернуть проект Unity с использованием набора средств для смешанной реальности и Пространственных привязок Azure для Android и iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: смешанная реальность, unity, руководство, hololens, android, ios
ms.localizationpriority: high
ms.openlocfilehash: e95b659eed3bfb406dcc41d5b3ad6e5e18c764a5
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305989"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Пространственные привязки Azure для Android и iOS

В этом руководстве показано, как выполнить сборку проекта на устройствах Android и iOS с помощью пакетов AR Foundation, ARCore XR Plugin и ARKit XR Plugin.

## <a name="objectives"></a>Задачи

* Узнайте, как выполнить сборку проекта на своем устройстве Android с помощью пакетов Unity AR Foundation и ARCore XR Plugin.
* Узнайте, как выполнить сборку проекта на своем устройстве iOS с помощью пакетов Unity AR Foundation и ARKit XR Plugin.

## <a name="installing-inbuilt-unity-packages"></a>Установка встроенных пакетов Unity

В этом разделе будут обновлены и установлены следующие встроенные пакеты:

* AR Foundation 3.1.3;
* Legacy Input Helpers 2.1.4;
* пакет поддержки ARCore XR Plugin 3.1.3 для Android;
* пакет поддержки ARKit XR plugin 3.1.3 для iOS.

> [!CAUTION]
> Не все версии совместимы с MRTK. С набором будет работать только определенная версия, поэтому убедитесь, что установлены в точности те версии, которые перечислены выше.

В меню Unity выберите **Window (Окно)**  > **Package Manager (Диспетчер пакетов)** , чтобы открыть окно диспетчера пакетов. Затем выберите **AR Foundation** > **3.1.3** и нажмите кнопку **Update to 3.1.3** (Обновить до 3.1.3), чтобы обновить пакет.

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

С помощью той же процедуры вы можете по мере необходимости импортировать остальные пакеты.

> [!NOTE]
> Если вы разрабатываете проект для Android, устанавливать пакет ARKit XR Plugin не нужно. Если вы разрабатываете проект для iOS, устанавливать пакет ARCore XR Plugin также не нужно.

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Настройка MRTK для камеры AR Foundation

Из этого раздела вы узнаете, как настроить MRTK для развертывания на мобильном устройстве.

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**. Затем в окне Inspector (Инспектор) перейдите на вкладку **Camera** (Камера), клонируйте профиль камеры и присвойте ему понятное имя, например **AzureSpatialAnchors_ARCameraProfile**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).

Оставив выбранной вкладку **Camera** (Камера) в окне Inspector (Инспектор), разверните раздел **Camera Setting Providers** (Поставщики параметров камеры) и нажмите кнопку **+ Add Camera Setting Provider** (+ Добавить поставщик параметров), а затем разверните появившийся раздел **New data provider 1** (Новый поставщик данных 1).

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

В раскрывающемся списке **Type** (Тип) измените тип на **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

Оставив выбранным объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), нажмите кнопку **Add Component** (Добавить компонент) в окне Inspector (Инспектор), чтобы добавить следующие компоненты:

* диспетчер привязок AR (скрипт);
* DisableDiagnosticsSystem (скрипт).

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> При добавлении компонента диспетчера опорных точек AR (скрипт) автоматически добавляется компонент источника сеанса AR (скрипт), так как он необходим компоненту диспетчера опорных точек AR (скрипт).

## <a name="building-your-application-to-your-android-device"></a>Создание приложения для устройства Android

Из этого раздела вы узнаете, как настроить проект для сборки и развертывания на устройстве Android.

В меню Unity щелкните **File (Файл)**  > **Build Settings... (Параметры сборки...)** , чтобы открыть окно параметров сборки. Переключите платформу на Android.

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Сведения о процедуре можно найти в разделе [Переключение платформы сборки](mr-learning-base-02.md#switching-the-build-platform).

Закройте окно Build Settings (Параметры сборки).

В меню Unity выберите **Mixed Reality Toolkit (Набор средств для смешанной реальности)**  > **Utilities (Служебные программы)**  > **Configure Unity Project (Настройка проекта Unity)** ,чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Убедитесь, что выбраны все параметры, а затем нажмите кнопку **Apply** (Применить), чтобы применить эти параметры.

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player (Проигрыватель)**  >  **Other Settings (Другие параметры)** . Выберите элемент **Vulkan** и удалите его, щелкнув символ **-** .

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

Закройте окно Player Settings (Параметры проигрывателя) и снова откройте окно Build Settings (Параметры сборки).

В окне Build Settings (Параметры сборки) нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке). Затем с помощью USB-кабеля подключите к компьютеру устройство Android и выберите его в раскрывающемся списке **Run Device** (Запустить устройство).

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Если устройство не отображается в раскрывающемся списке Run Device (Запустить устройство), возможно, потребуется нажать кнопку Refresh (Обновить) рядом с раскрывающимся списком.

В окне Build Settings (Параметры сборки) нажмите кнопку **Build And Run** (Сборка и запуск), чтобы открыть окно сборка Android.

Выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_. Присвойте сборке APK понятное имя, например _MRTKTutorials-AzureSpatialAnchors_. Затем нажмите кнопку **Save** (Сохранить), чтобы запустить процесс сборки.

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
Если в окне консоли Unity появится сообщение об ошибке, связанной с модулями пакетов SDK, NDK и JDK для Android, необходимо открыть Unity Hub и установить соответствующие модули Android Build Support.

По завершении сборки приложения должны автоматически загрузиться на устройство Android.

## <a name="building-your-application-to-your-ios-device"></a>Создание приложения для устройства iOS

Из этого раздела вы узнаете, как настроить проект для сборки и развертывания на устройстве iOS.

В меню Unity щелкните **File (Файл)**  > **Build Settings... (Параметры сборки...)** , чтобы открыть окно параметров сборки. Переключите платформу на iOS.

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Сведения о процедуре можно найти в разделе [Переключение платформы сборки](mr-learning-base-02.md#switching-the-build-platform).

Закройте окно Build Settings (Параметры сборки).

В меню Unity выберите **Mixed Reality Toolkit (Набор средств для смешанной реальности)**  > **Utilities (Служебные программы)**  > **Configure Unity Project (Настройка проекта Unity)** ,чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Убедитесь, что выбраны все параметры, а затем нажмите кнопку **Apply** (Применить), чтобы применить эти параметры.

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player (Проигрыватель)**  >  **Other Settings (Другие параметры)** . Снимите флажок **Strip Engine Code** (Удалить код обработчика), чтобы отключить его.

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

Закройте окно Player Settings (Параметры проигрывателя) и снова откройте окно **Build Settings** (Параметры сборки).

В окне Build Settings (Параметры сборки) нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке).

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

В окне Build Settings (Параметры сборки) нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки iOS.

Выберите подходящее расположение для хранения проекта Xcode, например _D:\MixedRealityLearning\Builds_. Создайте папку и присвойте ей понятное имя, например _MRTKTutorials-AzureSpatialAnchors_. Затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы начать сборку.

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

После сборки выполните инструкции из раздела [Экспорт проект Xcode](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project), чтобы научиться развертывать проекты Xcode на устройствах iOS.

## <a name="congratulations"></a>Поздравляем!

Из этого руководства вы узнали, как выполнить сборку проекта на устройствах Android и iOS с помощью пакетов AR Foundation, ARCore XR Plugin и ARKit XR Plugin.
