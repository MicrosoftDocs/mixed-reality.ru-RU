---
title: Журнал версий службы удаленного взаимодействия с holographic
description: Журнал версий для удаленного взаимодействия holographic в HoloLens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: f051dbf24cab550470a312933ffb99e1ba595257
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181964"
---
# <a name="holographic-remoting-version-history"></a>Журнал версий службы удаленного взаимодействия с holographic

> [!IMPORTANT]
> Это руководство относится к удаленному взаимодействию с HoloLens 2.

## Версия 2.0.18.0 (17 декабря, 2019)<a name="v2.0.18"></a>
* Добавлена поддержка Холографиквиевконфигуратион: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration
* Исправлены различные ошибки, приводящие к сбоям.
* Исправлена ошибка обратного вызова Холографикспаце. Камерааддед, чтобы Холографиккамера был принят и показана как добавленная Камера в Холорафикфраме.

## Версия 2.0.16 (11 ноября, 2019)<a name="2.0.16"></a>
* Исправлена взаимоблокировка при отслеживании QR-кода.
* Исправлено исключение унханделед из-за блокировки ожидания в основном потоке.

## Версия 2.0.14 (26 октября, 2019)<a name="v2.0.14"></a>
* Поддержка новых API Перцептиондевице (обновление Windows 10 за ноябрь 2019).
* Исправлена проблема, препятствующая срабатыванию событий жестов с помощью Спатиалжестуререкогнизер.
* Исправлена проблема с потоками при использовании Спатиалсурфацеобсервер. Сетбаундингволуме.

## Версия 2.0.12 (18 октября, 2019)<a name="v2.0.12"></a>
* Исправлена проблема сбоя в Спатиалжестуререкогнизер при использовании Навигатионраил (X/Y/Z).

## Версия 2.0.10 (10 октября, 2019)<a name="v2.0.10"></a>
* Исправлена аварийное завершение работы при использовании кнопки триггера контроллеров VR. Holographic удаленное взаимодействие не полностью поддерживает контроллеры, только кнопка "триггер" и кнопка Windows работают, если они связаны с HoloLens 2.

## Версия 2.0.9 (19 сентября 2019 г.)<a name="v2.0.9"></a>
* Добавлена поддержка [спатиаланчорекспортер](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) .
* Добавлен новый интерфейс ```IPlayerContext2``` (реализованный ```PlayerContext```), предоставляющий следующие члены:
  - Свойство [блитремотефраметимеаут](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* Для ```BlitResult``` Добавлено ```Failed_RemoteFrameTooOld``` значение
* Улучшения стабильности и надежности

## Версия 2.0.8 (20 августа 2019 г.)<a name="v2.0.8"></a>

* Исправлена сбой при вызове [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) с параметром [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) в качестве параметра.
* Улучшения стабильности и надежности

## Версия 2.0.7 (26 июля, 2019)<a name="v2.0.7"></a>

* Первый общедоступный выпуск holographic Remoting для HoloLens 2.

## <a name="see-also"></a>См. также
* [Написание пользовательского приложения для удаленного взаимодействия holographic](holographic-remoting-create-player.md)
* [Создание хост-приложения holographic с удаленным взаимодействием](holographic-remoting-create-host.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)
