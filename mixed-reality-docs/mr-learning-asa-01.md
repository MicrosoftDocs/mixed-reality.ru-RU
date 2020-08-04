---
title: Руководства по Пространственным привязкам Azure, часть 1 Введение
description: Пройдите этот курс и узнайте, как реализовать Пространственные привязки Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f273c573d40b1e65e325bd31b5dd9e14c1ee66ec
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376556"
---
# <a name="1-introduction"></a>1. Введение

## <a name="overview"></a>Обзор

Добро пожаловать в руководства по Пространственным привязкам Azure! Из этой серии руководств вы узнаете о <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Пространственных привязках Azure</a> (ASA) и о том, как использовать возможности смешанной реальности в реальном мире. Вы также узнаете, как развернуть проект в Android и iOS.

Руководства в этой серии:

1. [Введение](mr-learning-asa-01.md)
2. [Начало работы с Пространственными привязками Azure](mr-learning-asa-02.md)
3. [Сохранение, получение и совместное использование Пространственных привязок Azure](mr-learning-asa-03.md)
4. [Отображение сведений о Пространственных привязках Azure](mr-learning-asa-04.md)
5. [Пространственные привязки Azure для Android и iOS](mr-learning-asa-05.md)

## <a name="objectives"></a>Задачи

* Узнать, как создавать пространственные привязки и получать их из Azure.
* Узнать, как обеспечить пространственное выравнивание в сеансах приложения.
* Узнать, как реализовать пространственное выравнивание на нескольких устройствах.
* Узнать, как подготовить, создать и развернуть проект в Android и iOS.

## <a name="prerequisites"></a>Предварительные условия

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем поддержки сборки универсальной платформы Windows.
* Выполненные инструкции из раздела [Создание ресурса Пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) статьи [Краткое руководство. Создание приложения Unity HoloLens, которое использует Пространственные привязки Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).
* Знакомство с серией [руководств по началу работы](mr-learning-base-01.md) или базовый опыт работы с Unity и MRTK.
* Знакомство с серией [руководств по Пространственным привязкам Azure](mr-learning-asa-01.md) или опыт создания учетной записи Пространственных привязок Azure.
* Если планируется развертывание на устройствах Android и HoloLens
  * Устройство Android с <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">включенными возможностями разработки</a> и <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">поддержкой ARCore</a>, подключенное через USB к компьютеру Windows или macOS.
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем Android Build Support.
* Если планируется развертывание на устройствах iOS и HoloLens
  * Компьютер macOS с последней версией <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> и <a href="https://cocoapods.org" target="_blank">CocoaPods</a>.
  * <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">Совместимое с ARKit</a> устройство iOS, подключенное через USB к компьютеру macOS.
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем iOS Build Support.

> [!CAUTION]
> Рекомендуемая версия набора средств для Смешанной реальности для этой серии руководств — МРТК 2.4.0.

> [!CAUTION]
> Рекомендуемая версия Unity для этой серии руководств — Unity 2019.3.15. Это заменяет все требования к версии Unity, указанные выше.

[Следующее руководство: 2. Начало работы с Пространственными привязками Azure](mr-learning-asa-02.md)
