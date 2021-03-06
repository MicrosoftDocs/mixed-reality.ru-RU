---
title: Рекомендации по Опенкср
description: Ознакомьтесь с рекомендациями по повышению качества, стабильности и производительности приложений Опенкср.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя, рекомендации, производительность, качество, стабильность
ms.openlocfilehash: 0a0bbd37521be52ec328b4f32e53969c0ec7fef4
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549369"
---
# <a name="openxr-app-best-practices"></a>Рекомендации по приложениям Опенкср

Ниже приведены примеры лучших методов в файле Опенксрпрограм. cpp для <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">басикксрапп</a>. Функция Run () в начале фиксирует типичный поток кода приложения Опенкср из инициализации в цикле событий и отрисовки.

## <a name="best-practices-for-visual-quality-and-stability"></a>Рекомендации по качеству и стабильности визуального элемента

Рекомендации в этом разделе описывают, как получить лучшее визуальное качество и стабильность в любом приложении Опенкср.

Дополнительные рекомендации по производительности, относящиеся к HoloLens 2, см. в разделе рекомендации по [производительности в hololens 2](#best-practices-for-performance-on-hololens-2) ниже.

### <a name="gamma-correct-rendering"></a>Гамма-Правильная отрисовка

Необходимо соблюдать осторожность, чтобы убедиться, что конвейер отрисовки является гамма-правильным. При подготовке к просмотру в имеющуюся цепочку буферов формат представления "Визуализация-целевой объект" должен соответствовать формату имеющуюся цепочку буферов (например, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` как для формата имеющуюся цепочку буферов, так и для представления целевого объекта визуализации).
Исключением является ситуация, когда конвейер отрисовки приложения выполняет ручное преобразование sRGB в коде шейдера. в этом случае приложение должно запрашивать формат имеющуюся цепочку буферов sRGB, но использовать линейный формат для представления целевого объекта визуализации (например, запрос `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` как формат имеющуюся цепочку буферов, но использовать `DXGI_FORMAT_B8G8R8A8_UNORM` в качестве представления целевого объекта), чтобы предотвратить исправление содержимого с помощью двойной гаммы.

### <a name="submit-depth-buffer-for-projection-layers"></a>Отправка буфера глубины для слоев проекции

Всегда используйте расширение `XR_KHR_composition_layer_depth` и отправьте буфер глубины вместе с слоем проекции при отправке кадра в `xrEndFrame`.
Это повышает устойчивость к голограммам за счет повышения глубины оборудования в HoloLens 2.

### <a name="choose-a-reasonable-depth-range"></a>Выберите приемлемый диапазон глубины

Предпочтительнее использовать более узкий диапазон глубины виртуального содержимого, чтобы повысить стабильность работы HoloLens.
Например, в примере Опенксрпрограм. cpp используется 0,1 – 20 метров.
Используйте [Обратный-Z](https://developer.nvidia.com/content/depth-precision-visualized) для более однородного разрешения глубины.
Обратите внимание, что в HoloLens 2 использование предпочтительного формата глубины `DXGI_FORMAT_D16_UNORM` поможет достичь лучшей частоты кадров и производительности, хотя буферы 16-разрядной глубины обеспечивают меньшее разрешение глубины по сравнению с 24-разрядными буферами глубины.
Поэтому следует выполнить эти рекомендации, чтобы лучше использовать разрешение глубины.

### <a name="prepare-for-different-environment-blend-modes"></a>Подготовка к различным режимам смешения среды

Если приложение также будет работать на впечатляющих наушниках, которые полностью блокируют мир, обязательно перечислите поддерживаемые режимы наложения среды с помощью `xrEnumerateEnvironmentBlendModes` API и подготовьте содержимое для подготовки к просмотру соответствующим образом.
Например, для системы с `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE`, например HoloLens, приложение должно использовать прозрачный цвет в качестве четкого цвета, а для системы с `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`приложение должно визуализировать некоторый непрозрачный цвет или некоторую виртуальную комнату в фоновом режиме.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>Выбрать неограниченное пространство ссылок в качестве корневого пространства приложения

Приложения обычно устанавливают некоторое корневое пространство координат для подключения представлений, действий и голограмм.
Используйте `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT`, если расширение поддерживается для установления [геометрической системы координат](coordinate-systems.md#building-a-world-scale-experience), что позволяет приложению избежать нежелательного уменьшения голограммы, когда пользователь перемещается (например, 5 метров) с места запуска приложения.
Используйте `XR_REFERENCE_SPACE_TYPE_LOCAL` в качестве резервной, если не существует расширения неограниченного пространства.

### <a name="associate-hologram-with-spatial-anchor"></a>Связать голограмму с пространственной привязкой

При использовании неограниченного пространства ссылок голограммы, размещенные непосредственно в этом справочном пространстве, [могут быть смещены по мере того, как пользователь переходит к удаленным комнатам, а затем](coordinate-systems.md#building-a-world-scale-experience)возвращается.
Для пользователей с голограммами, которые помещаются в дискретное место в мире, [Создайте пространственное привязку](spatial-anchors.md#best-practices) с помощью функции расширения `xrCreateSpatialAnchorSpaceMSFT` и поместите голограмму в ее начало.
Это обеспечит нестабильную голограмму в зависимости от времени.

### <a name="support-mixed-reality-capture"></a>Поддержка записи смешанной реальности

Несмотря на то, что основной дисплей HoloLens 2 использует Аддитивное смешение среды, когда пользователь инициирует [запись смешанной реальности](mixed-reality-capture-for-developers.md), содержимое отрисовки приложения будет иметь альфа-смешение с потоком видео среды.
Для достижения наилучшего визуального качества в видеороликах смешанной реальности лучше установить `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` на `layerFlags`слоя проекции.

## <a name="best-practices-for-performance-on-hololens-2"></a>Рекомендации по повышению производительности в HoloLens 2

Как мобильное устройство с поддержкой РЕПРОЕКЦИИ оборудования, HoloLens 2 имеет более четкие требования для достижения оптимальной производительности.  Существует несколько способов отправки данных композиции с помощью `xrEndFrame` что приведет к последующей обработке, которая будет заметно снижена в производительности.

### <a name="select-a-swapchain-format"></a>Выберите формат имеющуюся цепочку буферов

Всегда перечислите Поддерживаемые форматы пикселей с помощью `xrEnumerateSwapchainFormats`и выберите первый цвет и формат пикселей глубины из среды выполнения, которую поддерживает приложение, поскольку среда выполнения предпочитает оптимальную производительность. Обратите внимание, что в HoloLens 2 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` и `DXGI_FORMAT_D16_UNORM`, как правило, являются первым выбором для достижения лучшей производительности отрисовки. Этот параметр может отличаться на гарнитурах VR, работающих на настольном ПК, где 24-разрядные буферы глубины меньше влияют на производительность.
  
**Предупреждение о производительности:** Использование формата, отличного от основного цвета имеющуюся цепочку буферов, приведет к последующей обработке во время выполнения, что приводит к значительному снижению производительности.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Подготовка к просмотру с рекомендуемыми параметрами отрисовки и временем кадров

Всегда выводится с рекомендуемой шириной или высотой конфигурации представления (`recommendedImageRectWidth` и `recommendedImageRectHeight` из `XrViewConfigurationView`) и всегда используйте API `xrLocateViews`, чтобы запросить Рекомендуемые параметры представления, фов и другие для подготовки к просмотру.
Всегда используйте `XrFrameEndInfo.predictedDisplayTime` из последнего вызова `xrWaitFrame` при запросе представлений и объектов.
Это позволит HoloLens настроить визуализацию и оптимизировать визуальное качество для пользователя, людьми HoloLens.

### <a name="use-a-single-projection-layer"></a>Использование одного слоя проекции

HoloLens 2 имеет ограниченную мощность GPU для приложений для отрисовки содержимого и аппаратного компоновщика, оптимизированного для одного уровня проекции.
Всегда использование одного уровня проекции может помочь снизить частоту работы приложения, голограмму и качество визуального элемента.  
  
**Предупреждение о производительности:** Передача любого, но одного уровня защиты приведет к последующей обработке во время выполнения, что значительно снижает производительность.

### <a name="render-with-texture-array-and-vprt"></a>Отрисовка с помощью массива текстур и ВПРТ

Создайте один `xrSwapchain` для левого и правого глаз, используя `arraySize=2` для цвета имеющуюся цепочку буферов и один для глубины.
Просматривайте левый глаз в срезе 0 и вправо на срез 1.
Используйте шейдер с ВПРТ и экземплярными вызовами Draw для отрисовки стереоскопик, чтобы избежать загрузки GPU.
Это также позволяет оптимизировать среду выполнения для достижения наилучшей производительности в HoloLens 2.
Альтернативы использованию массива текстур, такого как отрисовка на уровне Double или отдельная имеющуюся цепочку буферов на глаз, приводят к последующей обработке во время выполнения, что значительно снижает производительность.

### <a name="avoid-quad-layers"></a>Избегайте использования четырех уровней

Вместо того чтобы отправлять четыре слоя в виде слоев композиции с `XrCompositionLayerQuad`, выводите это содержимое непосредственно в имеющуюся цепочку буферов проекции.

**Предупреждение о производительности:** Предоставление дополнительных слоев за пределами одного слоя проекции, например четырех слоев, приведет к последующей обработке во время выполнения, что значительно снижает производительность.