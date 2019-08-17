---
title: Использование HoloLens в новых пространствах
description: HoloLens узнает, как выглядит пространство с течением времени. Пользователи могут упростить этот процесс, переместив HoloLens определенным образом через пространство.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality, проектирование, пространственное сопоставление, HoloLens, реконструкция поверхностей, сетка, отслеживание головок, сопоставление
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566023"
---
# <a name="use-hololens-in-new-spaces"></a><span data-ttu-id="5271d-105">Использование HoloLens в новых пространствах</span><span class="sxs-lookup"><span data-stu-id="5271d-105">Use HoloLens in New Spaces</span></span>

<span data-ttu-id="5271d-106">*Карты*HoloLens или сведения о среде, когда пользователь перемещается по пробелом.</span><span class="sxs-lookup"><span data-stu-id="5271d-106">HoloLens *maps*, or learns information about, its environment as the user moves around a space.</span></span> <span data-ttu-id="5271d-107">Со временем HoloLens создает *пространственное соответствие* всех частей наблюдаемой среды.</span><span class="sxs-lookup"><span data-stu-id="5271d-107">Over time, the HoloLens builds up a *spatial map* of all parts of the environment that have been observed.</span></span> <span data-ttu-id="5271d-108">HoloLens обновляет карту при обнаружении изменений в среде.</span><span class="sxs-lookup"><span data-stu-id="5271d-108">HoloLens updates the map as changes in the environment are observed.</span></span> <span data-ttu-id="5271d-109">Эта проверка будет автоматически сохраняться между запусками приложений.</span><span class="sxs-lookup"><span data-stu-id="5271d-109">This scan will automatically persist between app launches.</span></span>

<span data-ttu-id="5271d-110">HoloLens создаст и обновит карты при условии, что устройство включено и пользователь вошел в систему.</span><span class="sxs-lookup"><span data-stu-id="5271d-110">HoloLens will create and update maps as long as the device is on and a user is logged in.</span></span> <span data-ttu-id="5271d-111">При удержании или износе устройства с камерами, на которые указывает место, устройство попытается соотнести эту область.</span><span class="sxs-lookup"><span data-stu-id="5271d-111">If you hold or wear the device with the cameras pointed at a space, the device will try to map the area.</span></span> <span data-ttu-id="5271d-112">В то время как HoloLens будет изучать пространство с течением времени, существуют советы и рекомендации, позволяющие быстрее и эффективнее сопоставлять пространство.</span><span class="sxs-lookup"><span data-stu-id="5271d-112">While the HoloLens will learn a space naturally over time, there are tips and tricks available to map the space faster and more efficiently.</span></span> 

<span data-ttu-id="5271d-113">Если HoloLens не может сопоставлять ваше пространство или выходит за пределы калибровки, можно войти в ограниченный режим.</span><span class="sxs-lookup"><span data-stu-id="5271d-113">If your HoloLens can’t map your space or is out of calibration, you may enter Limited mode.</span></span> <span data-ttu-id="5271d-114">В режиме ограниченного режима вы не сможете размещать голограммы в окружающей обстановке.</span><span class="sxs-lookup"><span data-stu-id="5271d-114">In Limited mode, you won’t be able to place holograms in your surroundings.</span></span>

## <a name="tips-and-tricks-for-mapping-spaces"></a><span data-ttu-id="5271d-115">Советы и рекомендации по сопоставлению пространств</span><span class="sxs-lookup"><span data-stu-id="5271d-115">Tips and tricks for mapping spaces</span></span>

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a><span data-ttu-id="5271d-116">Убедитесь, что пространство настроено для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="5271d-116">Make sure the space is set up for mixed reality</span></span>

<span data-ttu-id="5271d-117">Функции в среде могут усложнить работу HoloLens для интерпретации пространства.</span><span class="sxs-lookup"><span data-stu-id="5271d-117">Features in an environment can make it difficult for the HoloLens to interpret a space.</span></span> <span data-ttu-id="5271d-118">Неяркий уровень, материалы в пространстве, макет объектов и другие могут влиять на то, как HoloLens сопоставляет область.</span><span class="sxs-lookup"><span data-stu-id="5271d-118">Light levels, materials in the space, the layout of objects, and more can all affect how HoloLens maps an area.</span></span>

<span data-ttu-id="5271d-119">Советы по настройке пространства для HoloLens и других устройств смешанной реальности можно найти в статье [рекомендации по среде для hololens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="5271d-119">Tips for setting up your space for HoloLens and other mixed reality devices can be found in [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

### <a name="understand-the-scenarios-for-the-area"></a><span data-ttu-id="5271d-120">Общие сведения о сценариях области</span><span class="sxs-lookup"><span data-stu-id="5271d-120">Understand the scenarios for the area</span></span>

<span data-ttu-id="5271d-121">Важно потратить больше времени на то, когда вы будете использовать HoloLens, чтобы обеспечить актуальность и полноту схемы.</span><span class="sxs-lookup"><span data-stu-id="5271d-121">It is important to spend the most time where you will be using the HoloLens so that the map is relevant and complete.</span></span> 

<span data-ttu-id="5271d-122">Например, если пользовательский сценарий для HoloLens предполагает переход от точки A к точке B, пройдите по пути с двух до трех раз, просматривая все направления при перемещении.</span><span class="sxs-lookup"><span data-stu-id="5271d-122">For example, if a user scenario for HoloLens involves moving from Point A to Point B, walk that path two to three times, looking in all directions as you move.</span></span> 

### <a name="walk-slowly-around-the-space"></a><span data-ttu-id="5271d-123">Замедлить обход пространства</span><span class="sxs-lookup"><span data-stu-id="5271d-123">Walk slowly around the space</span></span>

<span data-ttu-id="5271d-124">Если вы слишком быстро проведете обход области, скорее всего, HoloLens не будет сопоставлять области.</span><span class="sxs-lookup"><span data-stu-id="5271d-124">If you walk too quickly around the area, it's likely that the HoloLens will miss mapping areas.</span></span> <span data-ttu-id="5271d-125">Пройдите по медленному пространству, остановите каждые 5-8 метров, чтобы проанализировать окружающую границу.</span><span class="sxs-lookup"><span data-stu-id="5271d-125">Walk slowly around the space, stopping every 5-8 feet to look around at your surroundings.</span></span>

<span data-ttu-id="5271d-126">Гладкие перемещения также помогают карте HoloLens более еффеЦиентли.</span><span class="sxs-lookup"><span data-stu-id="5271d-126">Smooth movements also help the HoloLens map more effeciently.</span></span>

### <a name="look-in-all-directions"></a><span data-ttu-id="5271d-127">Просмотреть во всех направлениях</span><span class="sxs-lookup"><span data-stu-id="5271d-127">Look in all directions</span></span>

<span data-ttu-id="5271d-128">Когда вы сопоставляете пространство, он предоставляет HoloLens дополнительные данные относительно друг друга.</span><span class="sxs-lookup"><span data-stu-id="5271d-128">Looking around as you map the space gives the HoloLens more data on where points are relative to each other.</span></span> 

<span data-ttu-id="5271d-129">Если вы не ищите, например, HoloLens может не узнать, где находится потолок в комнате.</span><span class="sxs-lookup"><span data-stu-id="5271d-129">If you don't look up, for example, the HoloLens may not know where the ceiling in a room is.</span></span> 

<span data-ttu-id="5271d-130">Не забывайте при сопоставлении пространства в пол.</span><span class="sxs-lookup"><span data-stu-id="5271d-130">Don't forget to look down at the floor as you map the space.</span></span>

### <a name="cover-key-areas-multiple-times"></a><span data-ttu-id="5271d-131">Несколько раз охватывать ключевые области</span><span class="sxs-lookup"><span data-stu-id="5271d-131">Cover key areas multiple times</span></span>

<span data-ttu-id="5271d-132">Перемещение по области несколько раз поможет выбрать функции, которые могли быть пропущены в первом пошаговом руководстве.</span><span class="sxs-lookup"><span data-stu-id="5271d-132">Moving through an area multiple times will help pick up features you may have missed on the first walkthrough.</span></span> <span data-ttu-id="5271d-133">Попробуйте прохождение в области от двух до трех раз, чтобы создать идеальную карту.</span><span class="sxs-lookup"><span data-stu-id="5271d-133">Try traversing an area two to three times to build an ideal map.</span></span>

<span data-ttu-id="5271d-134">Если это возможно, при повторении этих перемещений следует потратить время на переход по области в одном направлении, а затем поворачивать и отбираться с вами.</span><span class="sxs-lookup"><span data-stu-id="5271d-134">If possible, while repeating these movements, spend time walking through an area in one direction, then turn around and walk back the way you came.</span></span>

### <a name="take-your-time-mapping-the-area"></a><span data-ttu-id="5271d-135">Приведите ваше время к сопоставлению области</span><span class="sxs-lookup"><span data-stu-id="5271d-135">Take your time mapping the area</span></span>

<span data-ttu-id="5271d-136">Для того чтобы HoloLens полностью сопоставлялся и направляться в окружающую его подстановку, может потребоваться от 15 до 20 минут.</span><span class="sxs-lookup"><span data-stu-id="5271d-136">It can take between 15 and 20 minutes for the HoloLens to fully map and adjust itself to its surroundings.</span></span> <span data-ttu-id="5271d-137">Если у вас есть место, в котором планируется часто использовать HoloLens, то это может привести к невозможности возникновения проблем.</span><span class="sxs-lookup"><span data-stu-id="5271d-137">If you have a space in which you plan to use a HoloLens frequently, taking that time up front to map the space can prevent issues later on.</span></span> 

## <a name="possible-errors-in-the-spatial-map"></a><span data-ttu-id="5271d-138">Возможные ошибки в пространственной карте</span><span class="sxs-lookup"><span data-stu-id="5271d-138">Possible errors in the spatial map</span></span>

<span data-ttu-id="5271d-139">Ошибки в данных пространственного сопоставления попадают в одну из трех категорий:</span><span class="sxs-lookup"><span data-stu-id="5271d-139">Errors in spatial mapping data fall into one of three categories:</span></span>

* <span data-ttu-id="5271d-140">*Отверстия*: В данных пространственного сопоставления отсутствуют поверхности реального мира.</span><span class="sxs-lookup"><span data-stu-id="5271d-140">*Holes*: Real-world surfaces are missing from the spatial mapping data.</span></span>
* <span data-ttu-id="5271d-141">*ХаллуЦинатионс*: Поверхности существуют в данных пространственного сопоставления, которые не существуют в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="5271d-141">*Hallucinations*: Surfaces exist in the spatial mapping data that do not exist in the real world.</span></span>
* <span data-ttu-id="5271d-142">*Норки*: HoloLens "теряет" часть пространственной схемы, думая, что она находится в другой части, чем на самом деле.</span><span class="sxs-lookup"><span data-stu-id="5271d-142">*Wormholes*: HoloLens 'loses' part of the spatial map by thinking it is in a different part of the map than it actually is.</span></span>
* <span data-ttu-id="5271d-143">*Сдвиг*: Поверхности в данных пространственного сопоставления несовершенно согласованы с реальными областями, которые либо помещаются в, либо извлекаются.</span><span class="sxs-lookup"><span data-stu-id="5271d-143">*Bias*: Surfaces in the spatial mapping data are imperfectly aligned with real-world surfaces, either pushed in or pulled out.</span></span>

<span data-ttu-id="5271d-144">Многие из этих ошибок могут быть устранены путем [удаления голограмм](environment-considerations-for-hololens.md) и повторного сопоставления пространства.</span><span class="sxs-lookup"><span data-stu-id="5271d-144">Many of these errors can be mitigated by [deleting your holograms](environment-considerations-for-hololens.md) and re-mapping the space.</span></span>