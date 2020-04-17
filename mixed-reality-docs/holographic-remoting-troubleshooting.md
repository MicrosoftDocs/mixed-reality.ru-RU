---
title: Устранение неполадок и ограничения удаленного взаимодействия с holographic
description: Действия по устранению неполадок для удаленного взаимодействия holographic в HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, holographic удаленное взаимодействие, удаленная визуализация, Сетевая визуализация, HoloLens, удаленные голограммы, устранение неполадок, помощь
ms.openlocfilehash: fc379eb4ad849fb5b236b82719711b37fead8a68
ms.sourcegitcommit: 48456c607a2d0dcf035a77e8ba67615396b0a211
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484314"
---
# <a name="holographic-remoting-troubleshooting"></a>Устранение неполадок удаленного взаимодействия с holographic

> [!IMPORTANT]
> Это руководство относится к удаленному взаимодействию с HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Не найдены библиотеки, снижающие опасность устранением рисков Spectre.

В примере приложений с удаленным взаимодействием с устранением рисков Spectre (/Qspectre) включено устранение рисков в конфигурации выпуска.

Если вы получаете неустранимую ошибку компоновщика, в которой говорится, что не удается открыть "vccorlib. lib", убедитесь, что Рабочая нагрузка Visual Studio включает библиотеки, снижающие опасность устранением рисков Spectre. Дополнительные сведения см. в разделе https://aka.ms/Ofhn4c.

## <a name="limitations"></a>Ограничения

В настоящее время следующие API **не** поддерживаются при использовании удаленного взаимодействия holographic для HoloLens 2 и вызывают ошибку ```ERROR_NOT_SUPPORTED```, если не указано иное:

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [Холографиккамера. Виевконфигуратион](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Поддерживается начиная с версии [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - В предыдущих версиях всегда вызывает ошибку.
* [Холографиккамера. Ишардвареконтентпротектионенаблед](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [Холографиквиевконфигуратион. Рекуестрендертаржетсизе](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Не завершается ошибкой, но размер целевого объекта прорисовки не изменится.
* [Холографиккамерапосе. Оверридепрожектионтрансформ](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [Холографиккамерапосе. Оверридевиевпорт](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [Холографиккамерапосе. Оверридевиевтрансформ](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [Холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Не завершается ошибкой, но буфер глубины не будет удален.
  - Поддерживается начиная с версии [2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [Холографикдисплай. Трижетвиевконфигуратион](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - Запрос Холографиквиевконфигуратионкинд. Фотовидеокамера всегда будет возвращать ```nullptr```.
  - Поддерживается начиная с версии [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - В предыдущих версиях всегда вызывает ошибку.
* [Холографикспаце. Креатефрамепресентатионмонитор](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [Холографикдисплай. по умолчанию](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Сообщает об ошибке, если она вызвана до установления соединения.


[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [SpatialLocation. Абсолутеангуларакцелератион](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation. Абсолутеангуларакцелератионаксисангле](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. АбсолутеангуларвелоЦити](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation. АбсолутеангуларвелоЦитяксисангле](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. Абсолутелинеаракцелератион](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. АбсолутелинеарвелоЦити](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [Спатиалстажефрамеофреференце. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Всегда возвращает ```nullptr```.
* [Спатиалстажефрамеофреференце. Рекуестневстажеасинк](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [Спатиаланчор. Ремоведбюсер](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [Спатиаланчорекспортер. по умолчанию](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - В предыдущих версиях всегда возвращает ```nullptr```. 
* [Спатиаланчорекспортер. Рекуестакцессасинк](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - В предыдущих версиях асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem```.
* [Спатиаланчортрансферманажер. Рекуестакцессасинк](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - Асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem```.
* [Спатиаланчортрансферманажер. Трекспортанчорсасинк](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - Асинхронная операция всегда завершается с ```false```.
* [Спатиаланчортрансферманажер. Тримпортанчорсасинк](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - Асинхронная операция всегда завершается с ```nullptr```.

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [Спатиалинтерактионсаурце. Трикреатехандмешобсервер](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [Спатиалинтерактионсаурце. Трикреатехандмешобсерверасинк](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [Спатиалинтерактионсаурце. Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [Спатиалграфинтероппревиев. Креателокаторфорноде](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [Спатиалграфинтероппревиев. Трикреатефрамеофреференце](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>См. также:
* [Журнал версий службы удаленного взаимодействия с holographic](holographic-remoting-version-history.md)
* [Создание удаленного приложения holographic с удаленным взаимодействием](holographic-remoting-create-host.md)
* [Написание пользовательского приложения для удаленного взаимодействия holographic](holographic-remoting-create-player.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление о конфиденциальности Майкрософт](https://go.microsoft.com/fwlink/?LinkId=521839)
