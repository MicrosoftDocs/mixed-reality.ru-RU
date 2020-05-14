---
title: Рекомендации по производительности для Unreal
description: Рекомендации по оптимизации производительности для приложений смешанной реальности в Unreal
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, производительность, оптимизация, параметры, документация
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840203"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="b1627-104">Рекомендации по производительности для Unreal</span><span class="sxs-lookup"><span data-stu-id="b1627-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="b1627-105">Эта статья является продолжением обсуждения, начатого в [рекомендациях по производительности для смешанной реальности](understanding-performance-for-mixed-reality.md), но посвящена более узким вопросам, имеющим отношение к среде Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="b1627-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unreal Engine environment.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="b1627-106">Рекомендуемые параметры для проекта Unreal</span><span class="sxs-lookup"><span data-stu-id="b1627-106">Recommended Unreal project settings</span></span>

- <span data-ttu-id="b1627-107">Используйте модуль отрисовки виртуальной реальности для мобильных устройств. В параметрах проекта обязательно установите значение целевой платформы Mobile/Tablet (Мобильное устройство или планшет) в разделе Project – Target Hardware (Проект — Целевое оборудование).</span><span class="sxs-lookup"><span data-stu-id="b1627-107">Use the mobile VR renderer- in your project settings, ensure your target platform is set to "Mobile/Tablet" under "Project – Target Hardware"</span></span>
- <span data-ttu-id="b1627-108">Отключите отбрасывание загораживаемых объектов. На странице Engine (Система) — Rendering (Отрисовка) в разделе Culling (Отбрасывание) снимите флажок Occlusion Culling (Отбрасывание загораживаемых объектов).</span><span class="sxs-lookup"><span data-stu-id="b1627-108">Disable occlusion culling- under "Engine – Rendering" in the "Culling" section, uncheck "Occlusion Culling"</span></span>
    + <span data-ttu-id="b1627-109">Если отбрасывание загораживаемых объектов в вашем проекте необходимо для отрисовки очень подробной сцены, мы рекомендуем включить параметр Support Software Occlusion Culling (Поддержка программного отбрасывания загораживаемых объектов) в разделе Engine — Rendering (Система — Отрисовка).</span><span class="sxs-lookup"><span data-stu-id="b1627-109">If occlusion culling is required because a very detailed scene needs to be rendered, it is recommended that "Support Software Occlusion Culling" is enabled Under "Engine – Rendering".</span></span> <span data-ttu-id="b1627-110">Это позволит Unreal выполнять отбрасывание загораживаемых объектов средствами ЦП, избегая запросов на отбрасывание к GPU, которые очень плохо работают на устройствах HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b1627-110">This allows Unreal to do occlusion culling on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
- <span data-ttu-id="b1627-111">Включите параметры Instanced Stereo (Экземпляры стерео) и Mobile Multi-View (Просмотр на нескольких мобильных устройствах) в разделе Engine — Rendering (Система — Отрисовка) в категории VR (Виртуальная реальность).</span><span class="sxs-lookup"><span data-stu-id="b1627-111">Enable both "Instanced Stereo" and "Mobile Multi-View" under "Engine – Rendering" in the "VR" category.</span></span> <span data-ttu-id="b1627-112">Возможно, для включения параметра Mobile Multi-View (Просмотр на нескольких мобильных устройствах) потребуется снять флажок Mobile Post-Processing (Постобработка на мобильном устройстве).</span><span class="sxs-lookup"><span data-stu-id="b1627-112">You may need to uncheck "Mobile Post-Processing" in order to be able to check "Mobile Multi-View"</span></span>
