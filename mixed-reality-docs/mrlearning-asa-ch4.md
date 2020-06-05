---
title: Руководства по Пространственным привязкам Azure, часть 4 Пространственные привязки Azure для Android и iOS
description: В этом руководстве показано, как реализовать Пространственные привязки Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: смешанная реальность, unity, руководство, курс, hololens, azure, пространственные привязки
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867626"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a>4. Пространственные привязки Azure для Android и iOS

В этом руководстве показано, как выполнить сборку проекта на устройствах Android и iOS с помощью пакетов AR Foundation, ARCore XR Plugin и ARKit XR Plugin.

## <a name="objectives"></a>Задачи

* Узнайте, как выполнить сборку проекта на устройстве Android с помощью пакетов Unity AR Foundation и ARCore XR Plugin.
* Узнайте, как выполнить сборку проекта на устройстве iOS с помощью пакетов Unity AR Foundation и ARKit XR Plugin.

[!NOTE] Для работы с этим руководством необходимо сначала изучить [руководство по началу работы с Пространственными привязками Azure](mrlearning-asa-ch1.md).

## <a name="adding-inbuilt-unity-packages"></a>Добавление встроенных пакетов Unity

В этом разделе показано, как установить встроенные в Unity пакеты AR Foundation, ARCore XR Plugin и ARKit XR Plugin, требуемые для включения поддержки устройств Android и iOS.

Убедитесь, что установлена правильная версия следующих пакетов Unity:

* **AR Foundation 2.1.4;**
* **ARCore XR Plugin 2.2.0 (предварительная версия 2);**
* **ARKit XR Plugin 2.1.1.**

[!NOTE] Если вы разрабатываете проект для Android, устанавливать пакет ARKit XR Plugin не нужно. Если вы разрабатываете проект для iOS, устанавливать пакет ARCore XR Plugin также не нужно.

В меню Unity последовательно выберите **Window** > **Диспетчер пакетов**:

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

Для отображения всех пакетов в списке может потребоваться несколько секунд. Чтобы увидеть предварительные версии пакетов, откройте дополнительные параметры и щелкните **Show preview packages** (Показать предварительные версии пакетов).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

В окне диспетчера пакетов выберите **AR Foundation**. В полном списке версий выберите 2.1.4 и обновите пакет, нажав кнопку **Update to 2.1.4** (Обновить до версии 2.1.4).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

Для включения поддержки устройств Android выполните такую же процедуру, чтобы импортировать пакет ARCore XR Plugin 2.2.0, предварительная версия 2.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

Для включения поддержки устройств iOS необходимо импортировать пакет **ARKit XR Plugin 2.1.1** для Unity из диспетчера пакетов.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a>Настройка MRTK для включения поддержки камеры AR Foundation

Настройте параметры MRTK для поддержки AR Foundation, выбрав MixedRealityToolKit в окне Hierarchy (Иерархия) и нажав кнопку **Clone** (Клонировать) в наборе средств для Смешанной реальности MRTK в окне Inspector (Инспектор).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

Если нажать кнопку **Clone** (Клонировать), появится окно Clone Profile (Клонировать профиль). Нажмите кнопку Clone (Клонировать) еще раз, чтобы клонировать профиль DefaultMixedRealityToolkitProfile.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

Аналогичным образом клонируйте профиль камеры в окне Inspector (Инспектор), присвойте профилю имя UnityARConfigurationProfile и нажмите кнопку **Clone** (Клонировать). В окне Inspector (Инспектор) найдите MixedReality, выберите вкладку Camera (Камера), разверните поставщиков параметров камеры в окне Inspector (Инспектор) и щелкните **+Add Camera Setting Provider** (+Добавить поставщика параметров камеры). Затем разверните пункт **New data provider 1** (Новый поставщик данных 1), выберите для параметра Type (Тип) значение **None** (Нет), после чего выберите **Microsoft .MixedReality.Toolkit.Experimental.UnityAR** и **UnityARCameraSettings**.


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

Выбрав объект MixedRealityToolKit в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) добавьте вспомогательные скрипты, нажав кнопку **Add component** (Добавить компонент), введите AR Reference Point Manager и выберите скрипт.

При добавлении скрипта AR Reference Point Manager в окне Inspector (Инспектор) также будет автоматически добавлен скрипт AR Session Origin. После добавления вспомогательных скриптов окно Inspector (Инспектор) должно выглядеть следующим образом.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a>Создание приложения на устройстве Android

Чтобы создать приложение на устройстве Android, щелкните **File** (Файл) в верхней части окна и выберите **Build Settings** (Параметры сборки). В открывшемся окне выберите **Android** и щелкните **Switch Platform** (Сменить платформу). Переключение платформы займет несколько минут. После перехода на платформу Android щелкните **Add Open Scenes** (Добавить открытые сцены) и убедитесь, что текущая сцена является единственной выбранной сценой в списке **Scenes In Build** (Сцены в сборке).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

Закройте окно **Build Settings** (Параметры сборки). В меню Unity выберите **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств Смешанной реальности > Утилиты > Настроить проект Unity) и нажмите кнопку **Apply** (Применить), чтобы настроить проект Unity для платформы Android.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

В меню Unity выберите **Edit** > **Project Settings** (Правка > Параметры проекта), чтобы открыть окно Project Settings (Параметры проекта). В окне Project Settings (Параметры проекта) выберите вкладку **Player** (Проигрыватель), разверните раздел Other Settings (Другие параметры), а затем выберите и удалите **Vulkan**, щелкнув значок -.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

Закройте окно Player Settings (Параметры проигрывателя) и снова откройте окно Build Settings (Параметры сборки). Затем с помощью USB-кабеля подключите устройство Android к компьютеру и выберите устройство в раскрывающемся списке **Build and Run on** (Выполнить сборку и запустить на), а затем щелкните **Build And Run** (Выполнить сборку и запустить). Вам будет предложено сохранить APK-файл, для которого можно выбрать любое имя.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> Если в окне консоли Unity появится сообщение об ошибке, связанной с модулями пакетов SDK, NDK или JDK для Android, необходимо открыть Unity Hub и установить соответствующие модули пакетов SDK, NDK и JDK для модуля Android Build Support.

По завершении сборки приложения должны автоматически загрузиться на устройство Android.

## <a name="build-application-to-ios-device"></a>Создание приложения на устройстве iOS

Чтобы создать приложение на устройстве iOS, щелкните **File** (Файл) в верхней части окна и выберите **Build Settings** (Параметры сборки). В открывшемся окне выберите **iOS** и щелкните **Switch Platform** (Сменить платформу).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

Закройте окно **Build Settings** (Параметры сборки). В меню Unity выберите **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств Смешанной реальности > Утилиты > Настроить проект Unity) и нажмите кнопку **Apply** (Применить), чтобы настроить проект Unity для платформы iOS.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

Чтобы выполнить сборку проекта iOS XCode, перейдите к настройкам сборки и щелкните **Build** (Выполнить сборку).

Изучите [это руководство](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project), чтобы узнать, как развернуть этот проект на своем устройстве iOS.

## <a name="congratulations"></a>Поздравляем!

Из этого руководства вы узнали, как создать проект для устройств Android и iOS. Вы также узнали, как использовать пакеты AR Foundation, ARCore XR Plugin и ARKit XR Plugin для выполнения проекта на устройствах Android и iOS.