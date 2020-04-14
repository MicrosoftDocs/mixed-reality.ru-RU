---
title: Устранение неполадок и ограничения удаленного взаимодействия с holographic
description: Действия по устранению неполадок для удаленного взаимодействия holographic в HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, holographic удаленное взаимодействие, удаленная визуализация, Сетевая визуализация, HoloLens, удаленные голограммы, устранение неполадок, помощь
ms.openlocfilehash: c6d8333bf22c3abb254a9f1b6e30a785effa9999
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277352"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="27443-104">Устранение неполадок удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="27443-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27443-105">Это руководство относится к удаленному взаимодействию с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="27443-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="27443-106">Не найдены библиотеки, снижающие опасность устранением рисков Spectre.</span><span class="sxs-lookup"><span data-stu-id="27443-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="27443-107">В примере приложений с удаленным взаимодействием с устранением рисков Spectre (/Qspectre) включено устранение рисков в конфигурации выпуска.</span><span class="sxs-lookup"><span data-stu-id="27443-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="27443-108">Если вы получаете неустранимую ошибку компоновщика, в которой говорится, что не удается открыть "vccorlib. lib", убедитесь, что Рабочая нагрузка Visual Studio включает библиотеки, снижающие опасность устранением рисков Spectre.</span><span class="sxs-lookup"><span data-stu-id="27443-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="27443-109">Дополнительные сведения см. в разделе https://aka.ms/Ofhn4c.</span><span class="sxs-lookup"><span data-stu-id="27443-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="27443-110">Ограничения</span><span class="sxs-lookup"><span data-stu-id="27443-110">Limitations</span></span>

<span data-ttu-id="27443-111">В настоящее время следующие API **не** поддерживаются при использовании удаленного взаимодействия holographic для HoloLens 2 и вызывают ошибку ```ERROR_NOT_SUPPORTED```, если не указано иное:</span><span class="sxs-lookup"><span data-stu-id="27443-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="27443-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="27443-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="27443-113">Холографиккамера. Виевконфигуратион</span><span class="sxs-lookup"><span data-stu-id="27443-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="27443-114">Поддерживается начиная с версии [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="27443-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="27443-115">В предыдущих версиях всегда вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="27443-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="27443-116">Холографиквиевконфигуратион. Рекуестрендертаржетсизе</span><span class="sxs-lookup"><span data-stu-id="27443-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="27443-117">Не завершается ошибкой, но размер целевого объекта прорисовки не изменится.</span><span class="sxs-lookup"><span data-stu-id="27443-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="27443-118">Холографиккамерапосе. Оверридепрожектионтрансформ</span><span class="sxs-lookup"><span data-stu-id="27443-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="27443-119">Холографиккамерапосе. Оверридевиевпорт</span><span class="sxs-lookup"><span data-stu-id="27443-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="27443-120">Холографиккамерапосе. Оверридевиевтрансформ</span><span class="sxs-lookup"><span data-stu-id="27443-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="27443-121">Холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="27443-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="27443-122">Не завершается ошибкой, но буфер глубины не будет удален.</span><span class="sxs-lookup"><span data-stu-id="27443-122">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="27443-123">Поддерживается начиная с версии [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span><span class="sxs-lookup"><span data-stu-id="27443-123">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="27443-124">Холографикдисплай. Трижетвиевконфигуратион</span><span class="sxs-lookup"><span data-stu-id="27443-124">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="27443-125">Запрос Холографиквиевконфигуратионкинд. Фотовидеокамера всегда будет возвращать ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="27443-125">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="27443-126">Поддерживается начиная с версии [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="27443-126">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="27443-127">В предыдущих версиях всегда вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="27443-127">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="27443-128">Холографикспаце. Креатефрамепресентатионмонитор</span><span class="sxs-lookup"><span data-stu-id="27443-128">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="27443-129">Холографикдисплай. по умолчанию</span><span class="sxs-lookup"><span data-stu-id="27443-129">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="27443-130">Сообщает об ошибке, если она вызвана до установления соединения.</span><span class="sxs-lookup"><span data-stu-id="27443-130">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="27443-131">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="27443-131">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="27443-132">SpatialLocation. Абсолутеангуларакцелератион</span><span class="sxs-lookup"><span data-stu-id="27443-132">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="27443-133">SpatialLocation. Абсолутеангуларакцелератионаксисангле</span><span class="sxs-lookup"><span data-stu-id="27443-133">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="27443-134">SpatialLocation. АбсолутеангуларвелоЦити</span><span class="sxs-lookup"><span data-stu-id="27443-134">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="27443-135">SpatialLocation. АбсолутеангуларвелоЦитяксисангле</span><span class="sxs-lookup"><span data-stu-id="27443-135">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="27443-136">SpatialLocation. Абсолутелинеаракцелератион</span><span class="sxs-lookup"><span data-stu-id="27443-136">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="27443-137">SpatialLocation. АбсолутелинеарвелоЦити</span><span class="sxs-lookup"><span data-stu-id="27443-137">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="27443-138">Спатиалстажефрамеофреференце. Current</span><span class="sxs-lookup"><span data-stu-id="27443-138">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="27443-139">Всегда возвращает ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="27443-139">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="27443-140">Спатиалстажефрамеофреференце. Рекуестневстажеасинк</span><span class="sxs-lookup"><span data-stu-id="27443-140">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="27443-141">Спатиаланчор. Ремоведбюсер</span><span class="sxs-lookup"><span data-stu-id="27443-141">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="27443-142">Спатиаланчорекспортер. по умолчанию</span><span class="sxs-lookup"><span data-stu-id="27443-142">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="27443-143">Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="27443-143">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="27443-144">В предыдущих версиях всегда возвращает ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="27443-144">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="27443-145">Спатиаланчорекспортер. Рекуестакцессасинк</span><span class="sxs-lookup"><span data-stu-id="27443-145">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="27443-146">Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="27443-146">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="27443-147">В предыдущих версиях асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="27443-147">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="27443-148">Спатиаланчортрансферманажер. Рекуестакцессасинк</span><span class="sxs-lookup"><span data-stu-id="27443-148">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="27443-149">Асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="27443-149">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="27443-150">Спатиаланчортрансферманажер. Трекспортанчорсасинк</span><span class="sxs-lookup"><span data-stu-id="27443-150">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="27443-151">Асинхронная операция всегда завершается с ```false```.</span><span class="sxs-lookup"><span data-stu-id="27443-151">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="27443-152">Спатиаланчортрансферманажер. Тримпортанчорсасинк</span><span class="sxs-lookup"><span data-stu-id="27443-152">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="27443-153">Асинхронная операция всегда завершается с ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="27443-153">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="27443-154">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="27443-154">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="27443-155">Спатиалинтерактионсаурце. Трикреатехандмешобсервер</span><span class="sxs-lookup"><span data-stu-id="27443-155">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="27443-156">Спатиалинтерактионсаурце. Трикреатехандмешобсерверасинк</span><span class="sxs-lookup"><span data-stu-id="27443-156">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="27443-157">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="27443-157">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="27443-158">Спатиалграфинтероппревиев. Креателокаторфорноде</span><span class="sxs-lookup"><span data-stu-id="27443-158">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="27443-159">Спатиалграфинтероппревиев. Трикреатефрамеофреференце</span><span class="sxs-lookup"><span data-stu-id="27443-159">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="27443-160">Спатиалинтерактионсаурце. Controller</span><span class="sxs-lookup"><span data-stu-id="27443-160">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="27443-161">См. также</span><span class="sxs-lookup"><span data-stu-id="27443-161">See Also</span></span>
* [<span data-ttu-id="27443-162">Журнал версий службы удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="27443-162">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="27443-163">Создание удаленного приложения holographic с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="27443-163">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="27443-164">Написание пользовательского приложения для удаленного взаимодействия holographic</span><span class="sxs-lookup"><span data-stu-id="27443-164">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="27443-165">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="27443-165">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="27443-166">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="27443-166">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
