---
title: Руководства по голографическому удаленному взаимодействию с компьютером, часть 2. Создание приложения для голографического удаленного взаимодействия с компьютером
description: Пройдите этот курс, чтобы узнать, как реализовать удаленное взаимодействие в режиме смешанной реальности между вашим компьютером и HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 6d11d91a0e08c48c09f676171dcb9bb8a0ff74de
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376376"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Создание приложения для голографического удаленного взаимодействия с компьютером

Из этого руководства вы узнаете, как создать приложение для компьютера, которое обеспечивает голографическое удаленное взаимодействие и подключение к HoloLens 2 в любой момент для визуализации трехмерного содержимого в смешанной реальности.

## <a name="objectives"></a>Задачи

* Настроить Unity для голографического удаленного взаимодействия.
* Научиться создать и развертывать приложения с использованием Visual Studio.
* Научиться развертывать приложения для голографического удаленного взаимодействия и подключение к HoloLens.

## <a name="configuring-your-scene-for-holographic-remoting"></a>Настройка сцены для голографического удаленного взаимодействия

В рамках этого раздела вы настроите проект для потоковой передачи данных смешанной реальности на устройство HoloLens 2 с компьютера в режиме реального времени с помощью подключения Wi-Fi.

В окне Project (Проект) перейдите к папке **Assets (Активы)**  > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs (Заготовки)** . Затем перетащите заготовку **HolographicRemoting** в свою сцену.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a>Разработка приложения для компьютера

Ваше приложение для голографического удаленного взаимодействия готово к сборке на компьютере. Выполните приведенные ниже инструкции и внесите необходимые изменения, чтобы выполнить сборку этого приложения на своем компьютере.

### <a name="1-set-the-player-settings"></a>1. Настройка параметров проигрывателя.

В меню Unity последовательно выберите элементы Edit (Правка) > Project Settings... (Параметры проекта...), чтобы открыть окно параметров проигрывателя.

В разделе **XR Settings** (Параметры XR) установите флажок **WSA Holographic Remoting Supported** (Поддержка голографического удаленного взаимодействия WSA) и включите функцию голографического удаленного взаимодействия.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Создание проекта Unity.

В меню Unity щелкните File (Файл) > Build Settings... (Параметры сборки...), чтобы открыть окно параметров сборки:

В окне Build Settings (Параметры сборки) нажмите кнопку ***Add Open Scenes*** (Добавить открытые сцены), чтобы добавить текущую сцену в список Scenes (Сцены). В списке Build (Сборка) нажмите кнопку ***Build*** (Сборка), чтобы открыть окно Build Universal Windows Platform (Создание приложений универсальной платформы Windows):

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

В окне Build Universal Windows Platform (Создание приложений универсальной платформы Windows) выберите подходящее расположение для хранения своей сборки, например Documents\MixedRealityLearning. Создайте папку и присвойте ей подходящее имя, например PCHolographicRemoting. Затем нажмите кнопку ***Select Folder*** (Выбрать папку), чтобы начать процесс сборки:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Подождите, пока Unity завершит сборку.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Сборка и развертывание приложения

По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой. Перейдите к папке и дважды щелкните файл SLN, чтобы открыть его в Visual Studio:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по установке средств.

Настройте Visual Studio для компьютера, выбрав конфигурацию "Выпуск" архитектуру x64 и целевой объект "Локальный компьютер":

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Нажмите кнопку ***Локальный компьютер***. Запустится сборка и развертывание приложения на вашем компьютере. Приложение будет установлено на ваш компьютер по умолчанию.

## <a name="testing-holographic-remoting-remote-application"></a>Проверка приложения для голографического удаленного взаимодействия

Чтобы подключить свое приложение для компьютера к HoloLens 2, выполните следующие действия:

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. Установка приложения Remoting Player на устройство HoloLens 2.

* На устройстве HoloLens 2 перейдите к приложению Store и выполните поиск по фразе "**Remoting Player**".
* Выберите приложение **Remoting Player**.
* Коснитесь элемента **Install** (Установить), чтобы скачать и установить приложение.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. Подключение приложения для голографического удаленного взаимодействия с компьютером к Remoting Player.

* Запустите **Remoting Player** на устройстве HoloLens.
* Запишите **IP-адрес** HoloLens. Он отобразится в **Remoting Player** в виде голограммы сразу же после запуска.
* Откройте приложение для голографического удаленного взаимодействия на компьютере.
* Когда приложение запустится, введите **IP-адрес** и нажмите кнопку **Connect** (Подключиться), чтобы установить подключение.

## <a name="congratulations"></a>Поздравляем!

Из этого руководства вы узнали, как создать удаленное приложение, которое обеспечивает голографическое удаленное взаимодействие и подключение к HoloLens 2 в любой момент для визуализации трехмерного содержимого в смешанной реальности. Когда устройство HoloLens будет подключено к приложению для голографического удаленного взаимодействия с компьютером, должна начаться потоковая передача данных смешанной реальности на устройство HoloLens 2.
