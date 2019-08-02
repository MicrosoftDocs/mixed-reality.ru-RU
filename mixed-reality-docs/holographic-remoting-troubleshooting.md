---
title: Устранение неполадок и ограничения удаленного взаимодействия с holographic
description: Действия по устранению неполадок для удаленного взаимодействия holographic в HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 08/01/2019
ms.topic: article
keywords: Windows Mixed Reality, голограммы, holographic удаленное взаимодействие, удаленная визуализация, Сетевая визуализация, HoloLens, удаленные голограммы, устранение неполадок, помощь
ms.openlocfilehash: 86b6979dbfc9b514b3af13ebdcc3d3ece17e6335
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718148"
---
# <a name="holographic-remoting-troubleshooting"></a>Устранение неполадок удаленного взаимодействия с holographic

> [!IMPORTANT]
> Это руководство относится к удаленному взаимодействию с HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Не найдены библиотеки, снижающие опасность устранением рисков Spectre.

В примере приложений с удаленным взаимодействием с устранением рисков Spectre (/Qspectre) включено устранение рисков в конфигурации выпуска.

Если вы получаете неустранимую ошибку компоновщика, в которой говорится, что не удается открыть "vccorlib. lib", убедитесь, что Рабочая нагрузка Visual Studio включает библиотеки, снижающие опасность устранением рисков Spectre. Дополнительные сведения см. в разделе https://aka.ms/Ofhn4c.

# <a name="limitations"></a>Ограничения

В настоящее время следующие API **не** поддерживаются при использовании удаленного взаимодействия holographic для HoloLens 2 и вызывают ```ERROR_NOT_SUPPORTED``` ошибку, если не указано иное:

[Windows.Graphics.Holographic](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic)

* [Холографиккамера. Виевконфигуратион](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [Холографиккамерапосе. Оверридепрожектионтрансформ](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [Холографиккамерапосе. Оверридевиевпорт](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [Холографиккамерапосе. Оверридевиевтрансформ](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [Холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) — не завершается ошибкой, но буфер глубины не будет удален.
* [Холографикдисплай. Трижетвиевконфигуратион](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [Холографикспаце. Креатефрамепресентатионмонитор](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[Windows.Perception.Spatial](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial)

* [SpatialLocation. Абсолутеангуларакцелератион](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation. Абсолутеангуларакцелератионаксисангле](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. АбсолутеангуларвелоЦити](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation. АбсолутеангуларвелоЦитяксисангле](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. Абсолутелинеаракцелератион](https://docs.microsoft.com/is-is/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. АбсолутелинеарвелоЦити](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [Спатиалстажефрамеофреференце. Current](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) — всегда возвращает ```nullptr```значение.
* [Спатиалстажефрамеофреференце. Рекуестневстажеасинк](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [Спатиаланчор. Ремоведбюсер](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [Спатиаланчорекспортер. по умолчанию](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
) — всегда возвращает. ```nullptr```
* [Спатиаланчорекспортер. рекуестакцессасинк](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
) — асинхронная операция всегда завершается ```SpatialPerceptionAccessStatus.DeniedBySystem```с.
* [Спатиаланчортрансферманажер. рекуестакцессасинк](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) — асинхронная операция всегда завершается ```SpatialPerceptionAccessStatus.DeniedBySystem```с.
* [Спатиаланчортрансферманажер. трекспортанчорсасинк](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) — асинхронная операция всегда завершается ```false```с.
* [Спатиаланчортрансферманажер. тримпортанчорсасинк](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
) — асинхронная операция всегда завершается ```nullptr```с.

[Windows.UI.Input.Spatial](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial)

* [Спатиалинтерактионсаурце. Трикреатехандмешобсервер](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [Спатиалинтерактионсаурце. Трикреатехандмешобсерверасинк](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview)

* [Спатиалграфинтероппревиев. Креателокаторфорноде](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [Спатиалграфинтероппревиев. Трикреатефрамеофреференце](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>См. также
* [Создание хост-приложения holographic с удаленным взаимодействием](holographic-remoting-create-host.md)
* [Написание пользовательского приложения для удаленного взаимодействия holographic](holographic-remoting-create-player.md)
* [Условия лицензии на программное обеспечение удаленного взаимодействия holographic](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление о конфиденциальности Майкрософт](https://go.microsoft.com/fwlink/?LinkId=521839)