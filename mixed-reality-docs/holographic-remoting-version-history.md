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
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="535fb-104">Журнал версий службы удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="535fb-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="535fb-105">Это руководство относится к удаленному взаимодействию с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="535fb-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="535fb-106">Версия 2.0.18.0 (17 декабря, 2019)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="535fb-106">Version 2.0.18.0 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="535fb-107">Добавлена поддержка Холографиквиевконфигуратион: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="535fb-107">Added support for HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span></span>
* <span data-ttu-id="535fb-108">Исправлены различные ошибки, приводящие к сбоям.</span><span class="sxs-lookup"><span data-stu-id="535fb-108">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="535fb-109">Исправлена ошибка обратного вызова Холографикспаце. Камерааддед, чтобы Холографиккамера был принят и показана как добавленная Камера в Холорафикфраме.</span><span class="sxs-lookup"><span data-stu-id="535fb-109">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="535fb-110">Версия 2.0.16 (11 ноября, 2019)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="535fb-110">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="535fb-111">Исправлена взаимоблокировка при отслеживании QR-кода.</span><span class="sxs-lookup"><span data-stu-id="535fb-111">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="535fb-112">Исправлено исключение унханделед из-за блокировки ожидания в основном потоке.</span><span class="sxs-lookup"><span data-stu-id="535fb-112">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="535fb-113">Версия 2.0.14 (26 октября, 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="535fb-113">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="535fb-114">Поддержка новых API Перцептиондевице (обновление Windows 10 за ноябрь 2019).</span><span class="sxs-lookup"><span data-stu-id="535fb-114">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="535fb-115">Исправлена проблема, препятствующая срабатыванию событий жестов с помощью Спатиалжестуререкогнизер.</span><span class="sxs-lookup"><span data-stu-id="535fb-115">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="535fb-116">Исправлена проблема с потоками при использовании Спатиалсурфацеобсервер. Сетбаундингволуме.</span><span class="sxs-lookup"><span data-stu-id="535fb-116">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="535fb-117">Версия 2.0.12 (18 октября, 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="535fb-117">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="535fb-118">Исправлена проблема сбоя в Спатиалжестуререкогнизер при использовании Навигатионраил (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="535fb-118">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="535fb-119">Версия 2.0.10 (10 октября, 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="535fb-119">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="535fb-120">Исправлена аварийное завершение работы при использовании кнопки триггера контроллеров VR.</span><span class="sxs-lookup"><span data-stu-id="535fb-120">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="535fb-121">Holographic удаленное взаимодействие не полностью поддерживает контроллеры, только кнопка "триггер" и кнопка Windows работают, если они связаны с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="535fb-121">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="535fb-122">Версия 2.0.9 (19 сентября 2019 г.)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="535fb-122">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="535fb-123">Добавлена поддержка [спатиаланчорекспортер](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) .</span><span class="sxs-lookup"><span data-stu-id="535fb-123">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="535fb-124">Добавлен новый интерфейс ```IPlayerContext2``` (реализованный ```PlayerContext```), предоставляющий следующие члены:</span><span class="sxs-lookup"><span data-stu-id="535fb-124">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="535fb-125">Свойство [блитремотефраметимеаут](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="535fb-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="535fb-126">Для ```BlitResult``` Добавлено ```Failed_RemoteFrameTooOld``` значение</span><span class="sxs-lookup"><span data-stu-id="535fb-126">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="535fb-127">Улучшения стабильности и надежности</span><span class="sxs-lookup"><span data-stu-id="535fb-127">Stability and reliability improvements</span></span>

## <span data-ttu-id="535fb-128">Версия 2.0.8 (20 августа 2019 г.)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="535fb-128">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="535fb-129">Исправлена сбой при вызове [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) с параметром [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) в качестве параметра.</span><span class="sxs-lookup"><span data-stu-id="535fb-129">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="535fb-130">Улучшения стабильности и надежности</span><span class="sxs-lookup"><span data-stu-id="535fb-130">Stability and reliability improvements</span></span>

## <span data-ttu-id="535fb-131">Версия 2.0.7 (26 июля, 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="535fb-131">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="535fb-132">Первый общедоступный выпуск holographic Remoting для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="535fb-132">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="535fb-133">См. также</span><span class="sxs-lookup"><span data-stu-id="535fb-133">See Also</span></span>
* [<span data-ttu-id="535fb-134">Написание пользовательского приложения для удаленного взаимодействия holographic</span><span class="sxs-lookup"><span data-stu-id="535fb-134">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="535fb-135">Создание хост-приложения holographic с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="535fb-135">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="535fb-136">Устранение неполадок и ограничения удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="535fb-136">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="535fb-137">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="535fb-137">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="535fb-138">Заявление Майкрософт о конфиденциальности</span><span class="sxs-lookup"><span data-stu-id="535fb-138">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
