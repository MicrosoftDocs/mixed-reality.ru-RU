---
title: Рекомендации по производительности для Unreal
description: Рекомендации по оптимизации производительности для приложений смешанной реальности в Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, производительность, оптимизация, параметры, документация
ms.openlocfilehash: 9f128a3ef09f29fc745c21b09b7ec97f5db33605
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533126"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="4eb07-104">Рекомендации по производительности для Unreal</span><span class="sxs-lookup"><span data-stu-id="4eb07-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="4eb07-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="4eb07-105">Overview</span></span>

<span data-ttu-id="4eb07-106">Эта статья служит продолжением обсуждения, начатого в [рекомендациях по оптимизации производительности для смешанной реальности](understanding-performance-for-mixed-reality.md), но посвящена функциям, специфичным для Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="4eb07-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="4eb07-107">Прежде чем продолжать, рекомендуется прочесть о факторах, ограничивающих производительность приложения, анализе и профилировании приложений смешанной реальности, а также общих настройках, повышающих производительность.</span><span class="sxs-lookup"><span data-stu-id="4eb07-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="4eb07-108">Рекомендуемые параметры для проекта Unreal</span><span class="sxs-lookup"><span data-stu-id="4eb07-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="4eb07-109">Каждый из параметров, о которых идет речь ниже, можно найти в разделе **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="4eb07-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="4eb07-110">При использовании мобильного отрисовщика виртуальной реальности:</span><span class="sxs-lookup"><span data-stu-id="4eb07-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="4eb07-111">Прокрутите до раздела **Project** (Проект), выберите **Target Hardware** (Целевое оборудование) и выберите целевую платформу **Mobile/Tablet** (Мобильное устройство или планшет).</span><span class="sxs-lookup"><span data-stu-id="4eb07-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Выбор мобильного устройства в качестве целевого](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="4eb07-113">Отключение отбрасывания загораживаемых объектов:</span><span class="sxs-lookup"><span data-stu-id="4eb07-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="4eb07-114">Прокрутите до раздела **Engine** (Подсистема), выберите **Rendering** (Отрисовка), разверните раздел **Culling** (Отбрасывание объектов) и снимите флажок **Occlusion Culling** (Отбрасывание загораживаемых объектов).</span><span class="sxs-lookup"><span data-stu-id="4eb07-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="4eb07-115">Если вам требуется удаление скрытых объектов для подробной отрисовки сцены, рекомендуется установить флажок **Support Software Occlusion Culling** (Поддержка программного удаления скрытых объектов) в разделе **Engine > Rendering** (Движок > Отрисовка).</span><span class="sxs-lookup"><span data-stu-id="4eb07-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="4eb07-116">Это позволит Unreal выполнять соответствующую обработку на центральном процессоре, избегая запросов для этой цели к GPU, которые выполняются неэффективно на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4eb07-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![Выбор мобильного устройства в качестве целевого](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="4eb07-118">Обновление отрисовки виртуальной реальности:</span><span class="sxs-lookup"><span data-stu-id="4eb07-118">Updating VR rendering:</span></span>
    * <span data-ttu-id="4eb07-119">Прокрутите до раздела **Engine** (Подсистема), выберите пункт **Rendering** (Отрисовка), разверните раздел **VR** (Виртуальная реальность) и установите флажки **Instanced Stereo** (Параллельное стерео) и **Mobile Multi-View** (Мобильная мультиотрисовка).</span><span class="sxs-lookup"><span data-stu-id="4eb07-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span>
        + <span data-ttu-id="4eb07-120">Возможно, для включения параметра **Mobile Multi-View** (Мобильная мультиотрисовка) потребуется снять флажок **Mobile Post-Processing** (Постобработка на мобильном устройстве).</span><span class="sxs-lookup"><span data-stu-id="4eb07-120">You may need to uncheck **Mobile Post-Processing** in order to be able to check **Mobile Multi-View**</span></span>

![Выбор мобильного устройства в качестве целевого](images/unreal/performance-recommendations-img-03.png)
