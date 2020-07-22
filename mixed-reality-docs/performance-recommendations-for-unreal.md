---
title: Рекомендации по производительности для Unreal
description: Рекомендации по оптимизации производительности для приложений смешанной реальности в Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, производительность, оптимизация, параметры, документация
ms.openlocfilehash: a7972962eeb2b1480a7da38210b5ee77104f508b
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303643"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="d1f17-104">Рекомендации по производительности для Unreal</span><span class="sxs-lookup"><span data-stu-id="d1f17-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="d1f17-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="d1f17-105">Overview</span></span>

<span data-ttu-id="d1f17-106">Эта статья служит продолжением обсуждения, начатого в [рекомендациях по оптимизации производительности для смешанной реальности](understanding-performance-for-mixed-reality.md), но посвящена функциям, специфичным для Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="d1f17-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="d1f17-107">Прежде чем продолжать, рекомендуется прочесть о факторах, ограничивающих производительность приложения, анализе и профилировании приложений смешанной реальности, а также общих настройках, повышающих производительность.</span><span class="sxs-lookup"><span data-stu-id="d1f17-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="d1f17-108">Рекомендуемые параметры для проекта Unreal</span><span class="sxs-lookup"><span data-stu-id="d1f17-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="d1f17-109">Каждый из параметров, о которых идет речь ниже, можно найти в разделе **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="d1f17-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="d1f17-110">При использовании мобильного отрисовщика виртуальной реальности:</span><span class="sxs-lookup"><span data-stu-id="d1f17-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="d1f17-111">Прокрутите до раздела **Project** (Проект), выберите **Target Hardware** (Целевое оборудование) и выберите целевую платформу **Mobile/Tablet** (Мобильное устройство или планшет).</span><span class="sxs-lookup"><span data-stu-id="d1f17-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Выбор мобильного устройства в качестве целевого](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="d1f17-113">Отключение отбрасывания загораживаемых объектов:</span><span class="sxs-lookup"><span data-stu-id="d1f17-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="d1f17-114">Прокрутите до раздела **Engine** (Подсистема), выберите **Rendering** (Отрисовка), разверните раздел **Culling** (Отбрасывание объектов) и снимите флажок **Occlusion Culling** (Отбрасывание загораживаемых объектов).</span><span class="sxs-lookup"><span data-stu-id="d1f17-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="d1f17-115">Если вам требуется удаление скрытых объектов для подробной отрисовки сцены, рекомендуется установить флажок **Support Software Occlusion Culling** (Поддержка программного удаления скрытых объектов) в разделе **Engine > Rendering** (Движок > Отрисовка).</span><span class="sxs-lookup"><span data-stu-id="d1f17-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="d1f17-116">Это позволит Unreal выполнять соответствующую обработку на центральном процессоре, избегая запросов для этой цели к GPU, которые выполняются неэффективно на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d1f17-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![Отключение отбрасывания загораживаемых объектов](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="d1f17-118">Использование нескольких представлений для мобильных устройств:</span><span class="sxs-lookup"><span data-stu-id="d1f17-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="d1f17-119">Прокрутите до раздела **Engine** (Подсистема), выберите пункт **Rendering** (Отрисовка), разверните раздел **VR** (Виртуальная реальность) и установите флажки **Instanced Stereo** (Параллельное стерео) и **Mobile Multi-View** (Мобильная мультиотрисовка).</span><span class="sxs-lookup"><span data-stu-id="d1f17-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="d1f17-120">Необходимо снять флажок Mobile HDR (HDR для мобильных устройств).</span><span class="sxs-lookup"><span data-stu-id="d1f17-120">Mobile HDR should be unchecked.</span></span>

![Параметры отрисовки виртуальной реальности](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="d1f17-122">Установите для параметра **Maximum number of CSM cascades to render** (Максимальное число каскадов CSM для отрисовки) значение **1** и для параметра **Max Movable Spotlights / Point Lights** (Максимальное число перемещаемых прожекторов или точечных источников) значение **0**.</span><span class="sxs-lookup"><span data-stu-id="d1f17-122">Setting the **Maximum number of CSM cascades to render** to **1** and **Max Movable Spotlights / Point Lights** to **0**.</span></span> 
