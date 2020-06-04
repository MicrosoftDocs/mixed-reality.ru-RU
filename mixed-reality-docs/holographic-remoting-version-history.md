---
title: Журнал версий службы удаленного взаимодействия с holographic
description: Журнал версий для удаленного взаимодействия holographic в HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: 319e76efbbe1085fc9d60251a6f0f38133de6505
ms.sourcegitcommit: 7011ac6fde80e5c45f04192fa1db6e1eb559e3b0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/03/2020
ms.locfileid: "84327904"
---
# <a name="holographic-remoting-version-history"></a>Журнал версий службы удаленного взаимодействия с holographic

> [!IMPORTANT]
> Это руководство относится к удаленному взаимодействию с HoloLens 2.

## <a name="version-213-may-25-2020"></a>Версия 2.1.3 (25 мая, 2020)<a name="v2.1.3"></a>
* Изменено поведение события [холографикспаце. камерааддед](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362) . В предыдущих версиях **не** гарантируется, что добавленный [холографиккамера](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera?view=winrt-18362) также имеет допустимый [холографиккамерапосе](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) при создании следующего кадра через [холографикспаце. креатенекстфраме](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createnextframe?view=winrt-18362#Windows_Graphics_Holographic_HolographicSpace_CreateNextFrame). Начиная с версии 2.1.3 [холографикспаце. камерааддед](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362) синхронизируется с данными о себе, поступающими от удаленного плеера holographic, и пользователи могут рассчитывать на то, что при добавлении камеры в следующем кадре также доступен допустимый [холографиккамерапосе](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) для этой камеры.
* Добавлена **отключенная** в депсбуфферстреамресолутион, которую можно использовать для отключения потоковой передачи буфера глубины через Ремотеконтекст. конфигуредепсвидеостреам. Обратите внимание, что при использовании [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer?view=winrt-18362#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) завершится с ошибкой *E_ILLEGAL_METHOD_CALL*.
* Экран запуска удаленного проигрывателя holographic был изменен и теперь не блокирует представление пользователей.
* Улучшения стабильности и исправления ошибок.

## <a name="version-212-april-5-2020"></a>Версия 2.1.2 (5 апреля, 2020)<a name="v2.1.2"></a>
* Исправлена проблема совместимости аудио обратной связи между последним удаленным проигрывателем удаленного взаимодействия и удаленных приложений с использованием версии меньше 2.1.0.
* Исправлена проблема с пространственной привязкой, которая неожиданно закрыла удаленный плеер Holographic. Эта проблема также затрагивает пользовательские проигрыватели.

## <a name="version-211-march-20-2020"></a>Версия: (20 марта, 2020)<a name="v2.1.1"></a>
* Исправлена проблема кодирования видео с удаленными приложениями при использовании GPU AMD.
* Улучшена производительность удаленного проигрывателя Holographic.

## <a name="version-210-march-11-2020"></a>Версия 2.1.0 (11 марта, 2020)<a name="v2.1.0"></a>
* Сетевой транспорт переключился на использование [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) через UDP. Безопасные подключения используют [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) сейчас. Обратите внимание, что [проигрыватель holographic Remoting](holographic-remoting-player.md) по-прежнему совместим со всеми ранее выпущенными версиями с удаленным взаимодействием. Чтобы воспользоваться преимуществами нового сетевого транспорта и, по вашему мнению, проигрыватель holographic Remoting и удаленное приложение должны использовать версию 2.1.0.
* Добавлена поддержка [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Версия 2.0.20 (2 февраля 2020 г.)<a name="v2.0.20"></a>
* Исправлены различные ошибки, приводящие к сбоям.

## <a name="version-2018-december-17-2019"></a>Версия 2.0.18 (17 декабря, 2019)<a name="v2.0.18"></a>
* Добавлена поддержка [холографиквиевконфигуратион](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration) .
* Исправлены различные ошибки, приводящие к сбоям.
* Исправлена ошибка обратного вызова Холографикспаце. Камерааддед, чтобы Холографиккамера был принят и показана как добавленная Камера в Холографикфраме.

## <a name="version-2016-november-11-2019"></a>Версия 2.0.16 (11 ноября, 2019)<a name="2.0.16"></a>
* Исправлена взаимоблокировка при отслеживании QR-кода.
* Исправлено исключение унханделед из-за блокировки ожидания в основном потоке.

## <a name="version-2014-october-26-2019"></a>Версия 2.0.14 (26 октября, 2019)<a name="v2.0.14"></a>
* Поддержка новых API Перцептиондевице (обновление Windows 10 за ноябрь 2019).
* Исправлена проблема, препятствующая срабатыванию событий жестов с помощью Спатиалжестуререкогнизер.
* Исправлена проблема с потоками при использовании Спатиалсурфацеобсервер. Сетбаундингволуме.

## <a name="version-2012-october-18-2019"></a>Версия 2.0.12 (18 октября, 2019)<a name="v2.0.12"></a>
* Исправлена проблема сбоя в Спатиалжестуререкогнизер при использовании Навигатионраил (X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Версия 2.0.10 (10 октября, 2019)<a name="v2.0.10"></a>
* Исправлена аварийное завершение работы при использовании кнопки триггера контроллеров VR. Holographic удаленное взаимодействие не полностью поддерживает контроллеры, только кнопка "триггер" и кнопка Windows работают, если они связаны с HoloLens 2.

## <a name="version-209-september-19-2019"></a>Версия 2.0.9 (19 сентября 2019 г.)<a name="v2.0.9"></a>
* Добавлена поддержка [спатиаланчорекспортер](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) .
* Добавлен новый интерфейс ```IPlayerContext2``` (реализованный ```PlayerContext``` ), предоставляющий следующие члены:
  - Свойство [блитремотефраметимеаут](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* Добавлено ```Failed_RemoteFrameTooOld``` значение в```BlitResult```
* Улучшения стабильности и надежности

## <a name="version-208-august-20-2019"></a>Версия 2.0.8 (20 августа 2019 г.)<a name="v2.0.8"></a>

* Исправлена сбой при вызове [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) с параметром [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) в качестве параметра.
* Улучшения стабильности и надежности

## <a name="version-207-july-26-2019"></a>Версия 2.0.7 (26 июля, 2019)<a name="v2.0.7"></a>

* Первый общедоступный выпуск holographic Remoting для HoloLens 2.

## <a name="see-also"></a>См. также:
* [Написание пользовательского приложения для удаленного взаимодействия holographic](holographic-remoting-create-player.md)
* [Создание хост-приложения holographic с удаленным взаимодействием](holographic-remoting-create-host.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)
