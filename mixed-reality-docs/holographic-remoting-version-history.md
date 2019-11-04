---
title: Журнал версий службы удаленного взаимодействия с holographic
description: Журнал версий для удаленного взаимодействия holographic в HoloLens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: 75e7c276560b4efbbdcbf2ea7579ed5ad7aadb4d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439235"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="f7b51-104">Журнал версий службы удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="f7b51-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7b51-105">Это руководство относится к удаленному взаимодействию с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f7b51-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="f7b51-106">Версия 2.0.14 (26 октября, 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="f7b51-106">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="f7b51-107">Поддержка новых API Перцептиондевице (обновление Windows 10 за ноябрь 2019).</span><span class="sxs-lookup"><span data-stu-id="f7b51-107">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="f7b51-108">Исправлена проблема, препятствующая срабатыванию событий жестов с помощью Спатиалжестуререкогнизер.</span><span class="sxs-lookup"><span data-stu-id="f7b51-108">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="f7b51-109">Исправлена проблема сеадинг при использовании Спатиалсурфацеобсервер. Сетбаундингволуме.</span><span class="sxs-lookup"><span data-stu-id="f7b51-109">Fixed theading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="f7b51-110">Версия 2.0.12 (18 октября, 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="f7b51-110">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="f7b51-111">Исправлена проблема сбоя в Спатиалжестуререкогнизер при использовании Навигатионраил (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="f7b51-111">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="f7b51-112">Версия 2.0.10 (10 октября, 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="f7b51-112">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="f7b51-113">Исправлена аварийное завершение работы при использовании кнопки триггера контроллеров VR.</span><span class="sxs-lookup"><span data-stu-id="f7b51-113">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="f7b51-114">Holographic удаленное взаимодействие не полностью поддерживает контроллеры, только кнопка "триггер" и кнопка Windows работают, если они связаны с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f7b51-114">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="f7b51-115">Версия 2.0.9 (19 сентября 2019 г.)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="f7b51-115">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="f7b51-116">Добавлена поддержка [спатиаланчорекспортер](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) .</span><span class="sxs-lookup"><span data-stu-id="f7b51-116">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="f7b51-117">Добавлен новый интерфейс ```IPlayerContext2``` (реализованный ```PlayerContext```), предоставляющий следующие члены:</span><span class="sxs-lookup"><span data-stu-id="f7b51-117">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="f7b51-118">Свойство [блитремотефраметимеаут](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="f7b51-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="f7b51-119">Для ```BlitResult``` Добавлено ```Failed_RemoteFrameTooOld``` значение</span><span class="sxs-lookup"><span data-stu-id="f7b51-119">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="f7b51-120">Улучшения стабильности и надежности</span><span class="sxs-lookup"><span data-stu-id="f7b51-120">Stability and reliability improvements</span></span>

## <span data-ttu-id="f7b51-121">Версия 2.0.8 (20 августа 2019 г.)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="f7b51-121">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="f7b51-122">Исправлена сбой при вызове [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) с параметром [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) в качестве параметра.</span><span class="sxs-lookup"><span data-stu-id="f7b51-122">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="f7b51-123">Улучшения стабильности и надежности</span><span class="sxs-lookup"><span data-stu-id="f7b51-123">Stability and reliability improvements</span></span>

## <span data-ttu-id="f7b51-124">Версия 2.0.7 (26 июля, 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="f7b51-124">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="f7b51-125">Первый общедоступный выпуск holographic Remoting для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f7b51-125">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7b51-126">См. также</span><span class="sxs-lookup"><span data-stu-id="f7b51-126">See Also</span></span>
* [<span data-ttu-id="f7b51-127">Написание пользовательского приложения для удаленного взаимодействия holographic</span><span class="sxs-lookup"><span data-stu-id="f7b51-127">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="f7b51-128">Создание хост-приложения holographic с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="f7b51-128">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="f7b51-129">Устранение неполадок и ограничения удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="f7b51-129">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="f7b51-130">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="f7b51-130">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="f7b51-131">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="f7b51-131">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
