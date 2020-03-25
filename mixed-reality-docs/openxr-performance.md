---
title: Производительность Опенкср
description: Отлаживать производительность приложений Опенкср в графическом процессоре.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя, производительность, оптимизация, отладка GPU, Рендердок, PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163348"
---
# <a name="openxr-performance"></a>Производительность Опенкср

В HoloLens 2 существует несколько способов отправки данных композиции с помощью `xrEndFrame`, что приведет к заметному снижению производительности.
Чтобы избежать штрафов в производительности, [отправьте единое `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) со следующими характеристиками:
* [Использование имеющуюся цепочку буферов массива текстуры](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Использовать формат имеющуюся цепочку буферов основного цвета](openxr-best-practices.md#select-a-swapchain-format)
* [Использование рекомендуемых измерений представления](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Не устанавливайте флаг `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`
* Задайте для `XrCompositionLayerDepthInfoKHR` `minDepth` значение 0,0 f, а `maxDepth` — 1,0 f.

Дополнительные соображения приводят к лучшей производительности:
* [Использовать 16-разрядный формат глубины](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Сделать экземпляры вызовов Draw](openxr-best-practices.md#render-with-texture-array-and-vprt)
