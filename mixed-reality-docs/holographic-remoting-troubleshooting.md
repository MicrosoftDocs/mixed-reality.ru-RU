---
title: Устранение неполадок и ограничения удаленного взаимодействия с holographic
description: Действия по устранению неполадок для удаленного взаимодействия holographic в HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 12/17/2019
ms.topic: article
keywords: Windows Mixed Reality, голограммы, holographic удаленное взаимодействие, удаленная визуализация, Сетевая визуализация, HoloLens, удаленные голограммы, устранение неполадок, помощь
ms.openlocfilehash: 05333c8911010945a543cf603b9925eb30c841db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181974"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="186b7-104">Устранение неполадок удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="186b7-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="186b7-105">Это руководство относится к удаленному взаимодействию с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="186b7-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="186b7-106">Не найдены библиотеки, снижающие опасность устранением рисков Spectre.</span><span class="sxs-lookup"><span data-stu-id="186b7-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="186b7-107">В примере приложений с удаленным взаимодействием с устранением рисков Spectre (/Qspectre) включено устранение рисков в конфигурации выпуска.</span><span class="sxs-lookup"><span data-stu-id="186b7-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="186b7-108">Если вы получаете неустранимую ошибку компоновщика, в которой говорится, что не удается открыть "vccorlib. lib", убедитесь, что Рабочая нагрузка Visual Studio включает библиотеки, снижающие опасность устранением рисков Spectre.</span><span class="sxs-lookup"><span data-stu-id="186b7-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="186b7-109">Дополнительные сведения см. в разделе https://aka.ms/Ofhn4c.</span><span class="sxs-lookup"><span data-stu-id="186b7-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="186b7-110">Ограничения</span><span class="sxs-lookup"><span data-stu-id="186b7-110">Limitations</span></span>

<span data-ttu-id="186b7-111">В настоящее время следующие API **не** поддерживаются при использовании удаленного взаимодействия holographic для HoloLens 2 и вызывают ошибку ```ERROR_NOT_SUPPORTED```, если не указано иное:</span><span class="sxs-lookup"><span data-stu-id="186b7-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="186b7-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="186b7-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="186b7-113">Холографиккамера. Виевконфигуратион</span><span class="sxs-lookup"><span data-stu-id="186b7-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="186b7-114">Поддерживается начиная с версии [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="186b7-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="186b7-115">В предыдущих версиях всегда вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="186b7-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="186b7-116">Холографиквиевконфигуратион. Рекуестрендертаржетсизе</span><span class="sxs-lookup"><span data-stu-id="186b7-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="186b7-117">Не завершается ошибкой, но размер целевого объекта прорисовки не изменится.</span><span class="sxs-lookup"><span data-stu-id="186b7-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="186b7-118">Холографиккамерапосе. Оверридепрожектионтрансформ</span><span class="sxs-lookup"><span data-stu-id="186b7-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="186b7-119">Холографиккамерапосе. Оверридевиевпорт</span><span class="sxs-lookup"><span data-stu-id="186b7-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="186b7-120">Холографиккамерапосе. Оверридевиевтрансформ</span><span class="sxs-lookup"><span data-stu-id="186b7-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="186b7-121">Холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="186b7-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="186b7-122">Не завершается ошибкой, но буфер глубины не будет удален.</span><span class="sxs-lookup"><span data-stu-id="186b7-122">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="186b7-123">Холографикдисплай. Трижетвиевконфигуратион</span><span class="sxs-lookup"><span data-stu-id="186b7-123">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="186b7-124">Запрос Холографиквиевконфигуратионкинд. Фотовидеокамера всегда будет возвращать ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="186b7-124">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="186b7-125">Поддерживается начиная с версии [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="186b7-125">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="186b7-126">В предыдущих версиях всегда вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="186b7-126">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="186b7-127">Холографикспаце. Креатефрамепресентатионмонитор</span><span class="sxs-lookup"><span data-stu-id="186b7-127">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="186b7-128">Холографикдисплай. по умолчанию</span><span class="sxs-lookup"><span data-stu-id="186b7-128">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="186b7-129">Сообщает об ошибке, если она вызвана до установления соединения.</span><span class="sxs-lookup"><span data-stu-id="186b7-129">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="186b7-130">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="186b7-130">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="186b7-131">SpatialLocation. Абсолутеангуларакцелератион</span><span class="sxs-lookup"><span data-stu-id="186b7-131">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="186b7-132">SpatialLocation. Абсолутеангуларакцелератионаксисангле</span><span class="sxs-lookup"><span data-stu-id="186b7-132">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="186b7-133">SpatialLocation. АбсолутеангуларвелоЦити</span><span class="sxs-lookup"><span data-stu-id="186b7-133">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="186b7-134">SpatialLocation. АбсолутеангуларвелоЦитяксисангле</span><span class="sxs-lookup"><span data-stu-id="186b7-134">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="186b7-135">SpatialLocation. Абсолутелинеаракцелератион</span><span class="sxs-lookup"><span data-stu-id="186b7-135">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="186b7-136">SpatialLocation. АбсолутелинеарвелоЦити</span><span class="sxs-lookup"><span data-stu-id="186b7-136">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="186b7-137">Спатиалстажефрамеофреференце. Current</span><span class="sxs-lookup"><span data-stu-id="186b7-137">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="186b7-138">Всегда возвращает значение ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="186b7-138">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="186b7-139">Спатиалстажефрамеофреференце. Рекуестневстажеасинк</span><span class="sxs-lookup"><span data-stu-id="186b7-139">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="186b7-140">Спатиаланчор. Ремоведбюсер</span><span class="sxs-lookup"><span data-stu-id="186b7-140">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="186b7-141">Спатиаланчорекспортер. по умолчанию</span><span class="sxs-lookup"><span data-stu-id="186b7-141">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="186b7-142">Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="186b7-142">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="186b7-143">В предыдущих версиях всегда возвращает ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="186b7-143">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="186b7-144">Спатиаланчорекспортер. Рекуестакцессасинк</span><span class="sxs-lookup"><span data-stu-id="186b7-144">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="186b7-145">Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="186b7-145">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="186b7-146">В предыдущих версиях асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="186b7-146">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="186b7-147">Спатиаланчортрансферманажер. Рекуестакцессасинк</span><span class="sxs-lookup"><span data-stu-id="186b7-147">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="186b7-148">Асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="186b7-148">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="186b7-149">Спатиаланчортрансферманажер. Трекспортанчорсасинк</span><span class="sxs-lookup"><span data-stu-id="186b7-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="186b7-150">Асинхронная операция всегда завершается с ```false```.</span><span class="sxs-lookup"><span data-stu-id="186b7-150">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="186b7-151">Спатиаланчортрансферманажер. Тримпортанчорсасинк</span><span class="sxs-lookup"><span data-stu-id="186b7-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="186b7-152">Асинхронная операция всегда завершается с ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="186b7-152">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="186b7-153">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="186b7-153">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="186b7-154">Спатиалинтерактионсаурце. Трикреатехандмешобсервер</span><span class="sxs-lookup"><span data-stu-id="186b7-154">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="186b7-155">Спатиалинтерактионсаурце. Трикреатехандмешобсерверасинк</span><span class="sxs-lookup"><span data-stu-id="186b7-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="186b7-156">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="186b7-156">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="186b7-157">Спатиалграфинтероппревиев. Креателокаторфорноде</span><span class="sxs-lookup"><span data-stu-id="186b7-157">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="186b7-158">Спатиалграфинтероппревиев. Трикреатефрамеофреференце</span><span class="sxs-lookup"><span data-stu-id="186b7-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="186b7-159">Спатиалинтерактионсаурце. Controller</span><span class="sxs-lookup"><span data-stu-id="186b7-159">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="186b7-160">См. также</span><span class="sxs-lookup"><span data-stu-id="186b7-160">See Also</span></span>
* [<span data-ttu-id="186b7-161">Журнал версий службы удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="186b7-161">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="186b7-162">Создание хост-приложения holographic с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="186b7-162">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="186b7-163">Написание пользовательского приложения для удаленного взаимодействия holographic</span><span class="sxs-lookup"><span data-stu-id="186b7-163">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="186b7-164">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="186b7-164">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="186b7-165">Заявление Майкрософт о конфиденциальности</span><span class="sxs-lookup"><span data-stu-id="186b7-165">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
