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
# <a name="openxr-performance"></a><span data-ttu-id="c9c2a-104">Производительность Опенкср</span><span class="sxs-lookup"><span data-stu-id="c9c2a-104">OpenXR performance</span></span>

<span data-ttu-id="c9c2a-105">В HoloLens 2 существует несколько способов отправки данных композиции с помощью `xrEndFrame`, что приведет к заметному снижению производительности.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>
<span data-ttu-id="c9c2a-106">Чтобы избежать штрафов в производительности, [отправьте единое `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) со следующими характеристиками:</span><span class="sxs-lookup"><span data-stu-id="c9c2a-106">To avoid performance penalities, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="c9c2a-107">Использование имеющуюся цепочку буферов массива текстуры</span><span class="sxs-lookup"><span data-stu-id="c9c2a-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="c9c2a-108">Использовать формат имеющуюся цепочку буферов основного цвета</span><span class="sxs-lookup"><span data-stu-id="c9c2a-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="c9c2a-109">Использование рекомендуемых измерений представления</span><span class="sxs-lookup"><span data-stu-id="c9c2a-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="c9c2a-110">Не устанавливайте флаг `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`</span><span class="sxs-lookup"><span data-stu-id="c9c2a-110">Do not set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="c9c2a-111">Задайте для `XrCompositionLayerDepthInfoKHR` `minDepth` значение 0,0 f, а `maxDepth` — 1,0 f.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="c9c2a-112">Дополнительные соображения приводят к лучшей производительности:</span><span class="sxs-lookup"><span data-stu-id="c9c2a-112">Additional considerations will result in better performance:</span></span>
* [<span data-ttu-id="c9c2a-113">Использовать 16-разрядный формат глубины</span><span class="sxs-lookup"><span data-stu-id="c9c2a-113">Use the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="c9c2a-114">Сделать экземпляры вызовов Draw</span><span class="sxs-lookup"><span data-stu-id="c9c2a-114">Make instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
