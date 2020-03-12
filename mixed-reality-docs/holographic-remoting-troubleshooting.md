---
title: Устранение неполадок и ограничения удаленного взаимодействия с holographic
description: Действия по устранению неполадок для удаленного взаимодействия holographic в HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, holographic удаленное взаимодействие, удаленная визуализация, Сетевая визуализация, HoloLens, удаленные голограммы, устранение неполадок, помощь
ms.openlocfilehash: 79258832d29741c56a1e7e89baeb7d728c806dd1
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092364"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="27e62-104">Устранение неполадок удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="27e62-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27e62-105">Это руководство относится к удаленному взаимодействию с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="27e62-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="27e62-106">Не найдены библиотеки, снижающие опасность устранением рисков Spectre.</span><span class="sxs-lookup"><span data-stu-id="27e62-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="27e62-107">В примере приложений с удаленным взаимодействием с устранением рисков Spectre (/Qspectre) включено устранение рисков в конфигурации выпуска.</span><span class="sxs-lookup"><span data-stu-id="27e62-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="27e62-108">Если вы получаете неустранимую ошибку компоновщика, в которой говорится, что не удается открыть "vccorlib. lib", убедитесь, что Рабочая нагрузка Visual Studio включает библиотеки, снижающие опасность устранением рисков Spectre.</span><span class="sxs-lookup"><span data-stu-id="27e62-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="27e62-109">Дополнительные сведения см. в разделе https://aka.ms/Ofhn4c.</span><span class="sxs-lookup"><span data-stu-id="27e62-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="27e62-110">Ограничения</span><span class="sxs-lookup"><span data-stu-id="27e62-110">Limitations</span></span>

<span data-ttu-id="27e62-111">В настоящее время следующие API **не** поддерживаются при использовании удаленного взаимодействия holographic для HoloLens 2 и вызывают ошибку ```ERROR_NOT_SUPPORTED```, если не указано иное:</span><span class="sxs-lookup"><span data-stu-id="27e62-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="27e62-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="27e62-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="27e62-113">Холографиккамера. Виевконфигуратион</span><span class="sxs-lookup"><span data-stu-id="27e62-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="27e62-114">Поддерживается начиная с версии [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="27e62-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="27e62-115">В предыдущих версиях всегда вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="27e62-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="27e62-116">Холографиквиевконфигуратион. Рекуестрендертаржетсизе</span><span class="sxs-lookup"><span data-stu-id="27e62-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="27e62-117">Не завершается ошибкой, но размер целевого объекта прорисовки не изменится.</span><span class="sxs-lookup"><span data-stu-id="27e62-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="27e62-118">Холографиккамерапосе. Оверридепрожектионтрансформ</span><span class="sxs-lookup"><span data-stu-id="27e62-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="27e62-119">Холографиккамерапосе. Оверридевиевпорт</span><span class="sxs-lookup"><span data-stu-id="27e62-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="27e62-120">Холографиккамерапосе. Оверридевиевтрансформ</span><span class="sxs-lookup"><span data-stu-id="27e62-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="27e62-121">Холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="27e62-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="27e62-122">Не завершается ошибкой, но буфер глубины не будет удален.</span><span class="sxs-lookup"><span data-stu-id="27e62-122">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="27e62-123">Поддерживается начиная с версии [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span><span class="sxs-lookup"><span data-stu-id="27e62-123">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="27e62-124">Холографикдисплай. Трижетвиевконфигуратион</span><span class="sxs-lookup"><span data-stu-id="27e62-124">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="27e62-125">Запрос Холографиквиевконфигуратионкинд. Фотовидеокамера всегда будет возвращать ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="27e62-125">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="27e62-126">Поддерживается начиная с версии [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="27e62-126">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="27e62-127">В предыдущих версиях всегда вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="27e62-127">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="27e62-128">Холографикспаце. Креатефрамепресентатионмонитор</span><span class="sxs-lookup"><span data-stu-id="27e62-128">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="27e62-129">Холографикдисплай. по умолчанию</span><span class="sxs-lookup"><span data-stu-id="27e62-129">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="27e62-130">Сообщает об ошибке, если она вызвана до установления соединения.</span><span class="sxs-lookup"><span data-stu-id="27e62-130">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="27e62-131">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="27e62-131">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="27e62-132">SpatialLocation. Абсолутеангуларакцелератион</span><span class="sxs-lookup"><span data-stu-id="27e62-132">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="27e62-133">SpatialLocation. Абсолутеангуларакцелератионаксисангле</span><span class="sxs-lookup"><span data-stu-id="27e62-133">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="27e62-134">SpatialLocation. АбсолутеангуларвелоЦити</span><span class="sxs-lookup"><span data-stu-id="27e62-134">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="27e62-135">SpatialLocation. АбсолутеангуларвелоЦитяксисангле</span><span class="sxs-lookup"><span data-stu-id="27e62-135">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="27e62-136">SpatialLocation. Абсолутелинеаракцелератион</span><span class="sxs-lookup"><span data-stu-id="27e62-136">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="27e62-137">SpatialLocation. АбсолутелинеарвелоЦити</span><span class="sxs-lookup"><span data-stu-id="27e62-137">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="27e62-138">Спатиалстажефрамеофреференце. Current</span><span class="sxs-lookup"><span data-stu-id="27e62-138">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="27e62-139">Всегда возвращает ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="27e62-139">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="27e62-140">Спатиалстажефрамеофреференце. Рекуестневстажеасинк</span><span class="sxs-lookup"><span data-stu-id="27e62-140">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="27e62-141">Спатиаланчор. Ремоведбюсер</span><span class="sxs-lookup"><span data-stu-id="27e62-141">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="27e62-142">Спатиаланчорекспортер. по умолчанию</span><span class="sxs-lookup"><span data-stu-id="27e62-142">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="27e62-143">Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="27e62-143">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="27e62-144">В предыдущих версиях всегда возвращает ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="27e62-144">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="27e62-145">Спатиаланчорекспортер. Рекуестакцессасинк</span><span class="sxs-lookup"><span data-stu-id="27e62-145">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="27e62-146">Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="27e62-146">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="27e62-147">В предыдущих версиях асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="27e62-147">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="27e62-148">Спатиаланчортрансферманажер. Рекуестакцессасинк</span><span class="sxs-lookup"><span data-stu-id="27e62-148">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="27e62-149">Асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="27e62-149">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="27e62-150">Спатиаланчортрансферманажер. Трекспортанчорсасинк</span><span class="sxs-lookup"><span data-stu-id="27e62-150">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="27e62-151">Асинхронная операция всегда завершается с ```false```.</span><span class="sxs-lookup"><span data-stu-id="27e62-151">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="27e62-152">Спатиаланчортрансферманажер. Тримпортанчорсасинк</span><span class="sxs-lookup"><span data-stu-id="27e62-152">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="27e62-153">Асинхронная операция всегда завершается с ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="27e62-153">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="27e62-154">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="27e62-154">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="27e62-155">Спатиалинтерактионсаурце. Трикреатехандмешобсервер</span><span class="sxs-lookup"><span data-stu-id="27e62-155">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="27e62-156">Спатиалинтерактионсаурце. Трикреатехандмешобсерверасинк</span><span class="sxs-lookup"><span data-stu-id="27e62-156">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="27e62-157">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="27e62-157">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="27e62-158">Спатиалграфинтероппревиев. Креателокаторфорноде</span><span class="sxs-lookup"><span data-stu-id="27e62-158">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="27e62-159">Спатиалграфинтероппревиев. Трикреатефрамеофреференце</span><span class="sxs-lookup"><span data-stu-id="27e62-159">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="27e62-160">Спатиалинтерактионсаурце. Controller</span><span class="sxs-lookup"><span data-stu-id="27e62-160">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="27e62-161">См. также</span><span class="sxs-lookup"><span data-stu-id="27e62-161">See Also</span></span>
* [<span data-ttu-id="27e62-162">Журнал версий службы удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="27e62-162">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="27e62-163">Создание удаленного приложения holographic с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="27e62-163">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="27e62-164">Написание пользовательского приложения для удаленного взаимодействия holographic</span><span class="sxs-lookup"><span data-stu-id="27e62-164">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="27e62-165">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="27e62-165">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="27e62-166">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="27e62-166">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
