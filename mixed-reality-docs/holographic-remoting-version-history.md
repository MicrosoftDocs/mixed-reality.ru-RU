---
title: Журнал версий службы удаленного взаимодействия с holographic
description: Журнал версий для удаленного взаимодействия holographic в HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: 62f54dbcf5327cdd5f13622704684a2cb0606d7d
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092308"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="f0e4e-104">Журнал версий службы удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="f0e4e-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0e4e-105">Это руководство относится к удаленному взаимодействию с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="f0e4e-106">Версия 2.1.0 (11 марта, 2020)<a name="v2.1.0"></a></span><span class="sxs-lookup"><span data-stu-id="f0e4e-106">Version 2.1.0 (March 11, 2020) <a name="v2.1.0"></a></span></span>
* <span data-ttu-id="f0e4e-107">Сетевой транспорт переключился на использование [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) через UDP.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-107">Switched network transport to use [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span></span> <span data-ttu-id="f0e4e-108">Безопасные подключения используют [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) сейчас.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-108">Secure connections use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) now.</span></span> <span data-ttu-id="f0e4e-109">Обратите внимание, что [проигрыватель holographic Remoting](holographic-remoting-player.md) по-прежнему совместим со всеми ранее выпущенными версиями с удаленным взаимодействием.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-109">Note, the [Holographic Remoting Player](holographic-remoting-player.md) is still compatible with all previously release Holographic Remoting versions.</span></span> <span data-ttu-id="f0e4e-110">Чтобы воспользоваться преимуществами нового сетевого транспорта и, по вашему мнению, проигрыватель holographic Remoting и удаленное приложение должны использовать версию 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-110">To benefit from the new network transport both, the Holographic Remoting Player and the remote app in question, have to use version 2.1.0.</span></span>
* <span data-ttu-id="f0e4e-111">Добавлена поддержка [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="f0e4e-111">Added support for [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span> 

## <span data-ttu-id="f0e4e-112">Версия 2.0.20 (2 февраля 2020 г.)<a name="v2.0.20"></a></span><span class="sxs-lookup"><span data-stu-id="f0e4e-112">Version 2.0.20 (February 2, 2020) <a name="v2.0.20"></a></span></span>
* <span data-ttu-id="f0e4e-113">Исправлены различные ошибки, приводящие к сбоям.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-113">Fixed various bugs that lead to crashes.</span></span>

## <span data-ttu-id="f0e4e-114">Версия 2.0.18 (17 декабря, 2019)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="f0e4e-114">Version 2.0.18 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="f0e4e-115">Добавлена поддержка [холографиквиевконфигуратион](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="f0e4e-115">Added support for [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span></span>
* <span data-ttu-id="f0e4e-116">Исправлены различные ошибки, приводящие к сбоям.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-116">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="f0e4e-117">Исправлена ошибка обратного вызова Холографикспаце. Камерааддед, чтобы Холографиккамера был принят и показана как добавленная Камера в Холорафикфраме.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-117">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="f0e4e-118">Версия 2.0.16 (11 ноября, 2019)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="f0e4e-118">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="f0e4e-119">Исправлена взаимоблокировка при отслеживании QR-кода.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-119">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="f0e4e-120">Исправлено исключение унханделед из-за блокировки ожидания в основном потоке.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-120">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="f0e4e-121">Версия 2.0.14 (26 октября, 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="f0e4e-121">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="f0e4e-122">Поддержка новых API Перцептиондевице (обновление Windows 10 за ноябрь 2019).</span><span class="sxs-lookup"><span data-stu-id="f0e4e-122">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="f0e4e-123">Исправлена проблема, препятствующая срабатыванию событий жестов с помощью Спатиалжестуререкогнизер.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-123">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="f0e4e-124">Исправлена проблема с потоками при использовании Спатиалсурфацеобсервер. Сетбаундингволуме.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-124">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="f0e4e-125">Версия 2.0.12 (18 октября, 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="f0e4e-125">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="f0e4e-126">Исправлена проблема сбоя в Спатиалжестуререкогнизер при использовании Навигатионраил (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="f0e4e-126">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="f0e4e-127">Версия 2.0.10 (10 октября, 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="f0e4e-127">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="f0e4e-128">Исправлена аварийное завершение работы при использовании кнопки триггера контроллеров VR.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-128">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="f0e4e-129">Holographic удаленное взаимодействие не полностью поддерживает контроллеры, только кнопка "триггер" и кнопка Windows работают, если они связаны с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-129">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="f0e4e-130">Версия 2.0.9 (19 сентября 2019 г.)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="f0e4e-130">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="f0e4e-131">Добавлена поддержка [спатиаланчорекспортер](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) .</span><span class="sxs-lookup"><span data-stu-id="f0e4e-131">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="f0e4e-132">Добавлен новый интерфейс ```IPlayerContext2``` (реализованный ```PlayerContext```), предоставляющий следующие члены:</span><span class="sxs-lookup"><span data-stu-id="f0e4e-132">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="f0e4e-133">Свойство [блитремотефраметимеаут](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="f0e4e-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="f0e4e-134">Для ```BlitResult``` Добавлено ```Failed_RemoteFrameTooOld``` значение</span><span class="sxs-lookup"><span data-stu-id="f0e4e-134">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="f0e4e-135">Улучшения стабильности и надежности</span><span class="sxs-lookup"><span data-stu-id="f0e4e-135">Stability and reliability improvements</span></span>

## <span data-ttu-id="f0e4e-136">Версия 2.0.8 (20 августа 2019 г.)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="f0e4e-136">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="f0e4e-137">Исправлена сбой при вызове [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) с параметром [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) в качестве параметра.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-137">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="f0e4e-138">Улучшения стабильности и надежности</span><span class="sxs-lookup"><span data-stu-id="f0e4e-138">Stability and reliability improvements</span></span>

## <span data-ttu-id="f0e4e-139">Версия 2.0.7 (26 июля, 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="f0e4e-139">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="f0e4e-140">Первый общедоступный выпуск holographic Remoting для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-140">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0e4e-141">См. также</span><span class="sxs-lookup"><span data-stu-id="f0e4e-141">See Also</span></span>
* [<span data-ttu-id="f0e4e-142">Написание пользовательского приложения для удаленного взаимодействия holographic</span><span class="sxs-lookup"><span data-stu-id="f0e4e-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="f0e4e-143">Создание хост-приложения holographic с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="f0e4e-143">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="f0e4e-144">Устранение неполадок и ограничения удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="f0e4e-144">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="f0e4e-145">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="f0e4e-145">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="f0e4e-146">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="f0e4e-146">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
