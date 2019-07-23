---
title: Spectator, представление
description: Визуализируйте голограммы с внешнего устройства как средства демонстрации смешанной реальности на внешнем дисплее или записи видео о работе в смешанной реальности.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, Камера, ARKit, HoloLens, Mixed Reality, Микседреалититулкит, демонстрация, запись
ms.openlocfilehash: 135a566456f1000669d2033edcf0d0b4649ccdf3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387664"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Spectator представление для HoloLens и HoloLens 2

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>Обзор

При людьми HoloLens мы часто будем забыть, что у человека, у которого нет этого, не может быть опыта чудеса, который мы можем. Представление spectator позволяет другим пользователям видеть на 2D-экране, что видит пользователь HoloLens в своем мире.
Spectator View предлагает быстрый и доступный подход к записи голограмм в HD с мобильными устройствами. Кроме того, он обеспечивает качественную запись голограмм с видеокамерами.

## <a name="key-resources"></a>Основные ресурсы

* [**Spectator представление в GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**AHA**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [**Регистрируют**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [**Инструкции по установке мобильных устройств**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [**Инструкции по настройке видеокамеры**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.VideoCamera.md)

## <a name="use-cases"></a>Варианты использования
* Вы можете записать опыт работы в смешанной реальности с помощью устройства iPhone или Android. Записывайте записи в полную версию HD и применяйте сглаживание к голограммам и даже тени. Это экономичный и быстрый способ записи видео о голограммах.
* Пропускайте потоки в смешанной реальности с помощью Apple TV непосредственно с iPhone или iPad, без задержек!
* Поделитесь опытом с гостями: Позвольте пользователям без HoloLens работать с голограммами непосредственно с их телефонов или планшетами.

## <a name="current-features"></a>Текущие возможности

* Пространственной синхронизации голограмм, так что все видят голограммы в одном месте.
* Поддержка iOS (устройства с поддержкой ARKit) и Android (устройства с поддержкой Аркоре).
Несколько гостей iOS.
Запись видео и голограмм + «окружающий звук» + «голограмма».
Общий доступ к листу для сохранения видео, электронной почты или совместного использования с другими вспомогательными приложениями.

![Маркер маркера маркера![](images/SpecViewPhoneDemo.jpg)
](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)

В следующей таблице показаны различные функции представления Spectator и их возможности. Выберите вариант, который наилучшим образом соответствует потребностям записи видео.

|                                      | Мобильный                  |                    Видеокамера              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Качество HD                           |         Полный HD         |        Профессиональная качественная пленка (определяется видеокамерой)      |
| Простое перемещение камеры                 |            ✔            |                      ✔                      |
| Представление третьих лиц                    |            ✔            |                      ✔                      |
| Может быть потоковой передачей на экраны           |            ✔            |                      ✔                      |
| Устройств                             |            ✔            |                                             |
| Беспроводная связь                             |            ✔            |                                             |
| Дополнительное необходимое оборудование         |     Телефон Android, iPhone    | HoloLens + тестовая платформа + трипод + видеокамера + PC + Unity |
| Инвестиции в оборудование                  |           Низкий            |                     Высокий                    |
| Поддержка разных платформ                       |           Android, iOS   |                                             |
| Синхронизированное содержимое                 |            ✔            |                      ✔                      |
| Длительность установки среды выполнения               |         Мгновенными          |                     Поздний доступ                    |
## <a name="see-also"></a>См. также

* [Съемка смешанной реальности](mixed-reality-capture.md) 
* [Съемка смешанной реальности для разработчиков](mixed-reality-capture-for-developers.md)
* [Общий доступ в смешанной реальности](shared-experiences-in-mixed-reality.md)
