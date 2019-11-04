---
title: Устранение неполадок и ограничения удаленного взаимодействия с holographic
description: Действия по устранению неполадок для удаленного взаимодействия holographic в HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 10/28/2019
ms.topic: article
keywords: Windows Mixed Reality, голограммы, holographic удаленное взаимодействие, удаленная визуализация, Сетевая визуализация, HoloLens, удаленные голограммы, устранение неполадок, помощь
ms.openlocfilehash: 7b438d9169c9306e0056655e561c04b62b1662cf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434235"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="fc27b-104">Устранение неполадок удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="fc27b-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc27b-105">Это руководство относится к удаленному взаимодействию с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fc27b-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="fc27b-106">Не найдены библиотеки, снижающие опасность устранением рисков Spectre.</span><span class="sxs-lookup"><span data-stu-id="fc27b-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="fc27b-107">В примере приложений с удаленным взаимодействием с устранением рисков Spectre (/Qspectre) включено устранение рисков в конфигурации выпуска.</span><span class="sxs-lookup"><span data-stu-id="fc27b-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="fc27b-108">Если вы получаете неустранимую ошибку компоновщика, в которой говорится, что не удается открыть "vccorlib. lib", убедитесь, что Рабочая нагрузка Visual Studio включает библиотеки, снижающие опасность устранением рисков Spectre.</span><span class="sxs-lookup"><span data-stu-id="fc27b-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="fc27b-109">Дополнительные сведения см. в разделе https://aka.ms/Ofhn4c.</span><span class="sxs-lookup"><span data-stu-id="fc27b-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="fc27b-110">Ограничения</span><span class="sxs-lookup"><span data-stu-id="fc27b-110">Limitations</span></span>

<span data-ttu-id="fc27b-111">В настоящее время следующие API **не** поддерживаются при использовании удаленного взаимодействия holographic для HoloLens 2 и вызывают ошибку ```ERROR_NOT_SUPPORTED```, если не указано иное:</span><span class="sxs-lookup"><span data-stu-id="fc27b-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="fc27b-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="fc27b-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="fc27b-113">Холографиккамера. Виевконфигуратион</span><span class="sxs-lookup"><span data-stu-id="fc27b-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="fc27b-114">Холографиккамерапосе. Оверридепрожектионтрансформ</span><span class="sxs-lookup"><span data-stu-id="fc27b-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="fc27b-115">Холографиккамерапосе. Оверридевиевпорт</span><span class="sxs-lookup"><span data-stu-id="fc27b-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="fc27b-116">Холографиккамерапосе. Оверридевиевтрансформ</span><span class="sxs-lookup"><span data-stu-id="fc27b-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="fc27b-117">Холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="fc27b-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="fc27b-118">Не завершается ошибкой, но буфер глубины не будет удален.</span><span class="sxs-lookup"><span data-stu-id="fc27b-118">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="fc27b-119">Холографикдисплай. Трижетвиевконфигуратион</span><span class="sxs-lookup"><span data-stu-id="fc27b-119">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="fc27b-120">Холографикспаце. Креатефрамепресентатионмонитор</span><span class="sxs-lookup"><span data-stu-id="fc27b-120">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="fc27b-121">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="fc27b-121">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="fc27b-122">SpatialLocation. Абсолутеангуларакцелератион</span><span class="sxs-lookup"><span data-stu-id="fc27b-122">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="fc27b-123">SpatialLocation. Абсолутеангуларакцелератионаксисангле</span><span class="sxs-lookup"><span data-stu-id="fc27b-123">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="fc27b-124">SpatialLocation. АбсолутеангуларвелоЦити</span><span class="sxs-lookup"><span data-stu-id="fc27b-124">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="fc27b-125">SpatialLocation. АбсолутеангуларвелоЦитяксисангле</span><span class="sxs-lookup"><span data-stu-id="fc27b-125">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="fc27b-126">SpatialLocation. Абсолутелинеаракцелератион</span><span class="sxs-lookup"><span data-stu-id="fc27b-126">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="fc27b-127">SpatialLocation. АбсолутелинеарвелоЦити</span><span class="sxs-lookup"><span data-stu-id="fc27b-127">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="fc27b-128">Спатиалстажефрамеофреференце. Current</span><span class="sxs-lookup"><span data-stu-id="fc27b-128">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="fc27b-129">Всегда возвращает ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="fc27b-129">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="fc27b-130">Спатиалстажефрамеофреференце. Рекуестневстажеасинк</span><span class="sxs-lookup"><span data-stu-id="fc27b-130">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="fc27b-131">Спатиаланчор. Ремоведбюсер</span><span class="sxs-lookup"><span data-stu-id="fc27b-131">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="fc27b-132">Спатиаланчорекспортер. по умолчанию</span><span class="sxs-lookup"><span data-stu-id="fc27b-132">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="fc27b-133">Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="fc27b-133">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="fc27b-134">В предыдущих версиях всегда возвращает ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="fc27b-134">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="fc27b-135">Спатиаланчорекспортер. Рекуестакцессасинк</span><span class="sxs-lookup"><span data-stu-id="fc27b-135">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="fc27b-136">Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="fc27b-136">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="fc27b-137">В предыдущих версиях асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="fc27b-137">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="fc27b-138">Спатиаланчортрансферманажер. Рекуестакцессасинк</span><span class="sxs-lookup"><span data-stu-id="fc27b-138">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="fc27b-139">Асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="fc27b-139">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="fc27b-140">Спатиаланчортрансферманажер. Трекспортанчорсасинк</span><span class="sxs-lookup"><span data-stu-id="fc27b-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="fc27b-141">Асинхронная операция всегда завершается с ```false```.</span><span class="sxs-lookup"><span data-stu-id="fc27b-141">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="fc27b-142">Спатиаланчортрансферманажер. Тримпортанчорсасинк</span><span class="sxs-lookup"><span data-stu-id="fc27b-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="fc27b-143">Асинхронная операция всегда завершается с ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="fc27b-143">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="fc27b-144">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="fc27b-144">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="fc27b-145">Спатиалинтерактионсаурце. Трикреатехандмешобсервер</span><span class="sxs-lookup"><span data-stu-id="fc27b-145">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="fc27b-146">Спатиалинтерактионсаурце. Трикреатехандмешобсерверасинк</span><span class="sxs-lookup"><span data-stu-id="fc27b-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="fc27b-147">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="fc27b-147">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="fc27b-148">Спатиалграфинтероппревиев. Креателокаторфорноде</span><span class="sxs-lookup"><span data-stu-id="fc27b-148">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="fc27b-149">Спатиалграфинтероппревиев. Трикреатефрамеофреференце</span><span class="sxs-lookup"><span data-stu-id="fc27b-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="fc27b-150">Спатиалинтерактионсаурце. Controller</span><span class="sxs-lookup"><span data-stu-id="fc27b-150">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="fc27b-151">См. также</span><span class="sxs-lookup"><span data-stu-id="fc27b-151">See Also</span></span>
* [<span data-ttu-id="fc27b-152">Журнал версий службы удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="fc27b-152">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="fc27b-153">Создание хост-приложения holographic с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="fc27b-153">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="fc27b-154">Написание пользовательского приложения для удаленного взаимодействия holographic</span><span class="sxs-lookup"><span data-stu-id="fc27b-154">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="fc27b-155">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="fc27b-155">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="fc27b-156">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="fc27b-156">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
