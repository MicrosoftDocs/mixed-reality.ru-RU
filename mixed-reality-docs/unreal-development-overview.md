---
title: Обзор разработки для Unreal
description: Приступите к созданию приложений смешанной реальности на платформе Unreal.
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, бета-версия, потоковая передача, удаленное взаимодействие, смешанная реальность, разработка, начало работы, новый проект, эмулятор, документация
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491171"
---
# <a name="unreal-development-overview"></a>Обзор разработки для Unreal

Поддержка смешанной реальности для Unreal Engine 4 теперь доступна в бета-версии! Если вы не знакомы с разработкой для Unreal, то страница <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Get Started with UE4</a> (Приступая к работе с UE4) отлично подойдет для изучения. Если вам нужны ресурсы, для Unreal доступен исчерпывающий портал <a href="https://www.unrealengine.com/marketplace//store" target="_blank">marketplace</a>. 

Изучив основы Unreal Engine 4, вы можете посетить страницу <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens Development</a> (Разработка для Microsoft HoloLens) на сайте документации по Unreal Engine, чтобы узнать, как создавать и запускать приложения в HoloLens. Не забудьте посетить <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">форумы по смешанной реальности Unreal</a>, чтобы присоединиться к сообществу, создающему приложения смешанной реальности в Unreal. Там вы сможете находить решения для проблем, с которыми столкнулись.

## <a name="installing-the-prerequisites"></a>Установка необходимых компонентов

Чтобы приступить к созданию приложения HoloLens 2 в Unreal, потребуется [эмулятор HoloLens 2](using-the-hololens-emulator.md) или гарнитура HoloLens. Вам также потребуется установить последнюю версию Visual Studio с рабочими нагрузками и компонентами, указанными в разделе <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">предварительных требований HoloLens 2 для Unreal</a>.

## <a name="building-and-running-your-unreal-app"></a>Сборка и запуск приложения Unreal

Сначала <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">упакуйте приложение для HoloLens 2</a>. Затем выберите, где требуется развернуть пакет:
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">развертывание в эмуляторе HoloLens 2</a>;
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">развертывание на гарнитуре HoloLens 2</a>.

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a>Потоковая передача приложения на гарнитуру с помощью Holographic Remoting Player

Потоковая передача приложения с компьютера в приложение Holographic Remoting Player на гарнитуре HoloLens имеет два основных преимущества: 
* это ускоряет разработку, так как нет необходимости переупаковывать и передавать приложение после каждого внесения изменений;
* используются возможности компьютера, так что вы можете отображать столько многоугольников, сколько позволяет графический процессор вашего компьютера, а не только компьютер в гарнитуре.

Чтобы приступить к потоковой передаче, ознакомьтесь с разделом <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 Streaming Quick Start</a>[]() (Краткое руководство по потоковой передаче HoloLens 2).

## <a name="see-also"></a>См. также статью
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Рекомендации по производительности Unreal для мобильных устройств</a>
