---
title: Визуализация просмотра комнаты
description: Приложения, для которых требуются данные пространственного сопоставления, полагаются на устройство для автоматического получения этих данных с течением времени и между сеансами по мере того, как пользователь исследует среду с активным устройством.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, шаблоны приложений, проектирование, HoloLens, Просмотр комнаты, пространственное сопоставление, сетка
ms.openlocfilehash: bdb070407f27d04046bd022894c7a8a01b9658d1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437515"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="196f1-104">Визуализация просмотра комнаты</span><span class="sxs-lookup"><span data-stu-id="196f1-104">Room scan visualization</span></span>

<span data-ttu-id="196f1-105">Приложения, для которых требуются данные пространственного сопоставления, полагаются на устройство для автоматического получения этих данных с течением времени и между сеансами по мере того, как пользователь исследует среду с активным устройством.</span><span class="sxs-lookup"><span data-stu-id="196f1-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="196f1-106">Полнота и качество этих данных зависит от ряда факторов, в том числе от количества выполненных пользователем проверок, времени, прошедших с момента исследования и того, были ли объекты, такие как мебель и дверцы, перемещены, так как устройство проверило эту область.</span><span class="sxs-lookup"><span data-stu-id="196f1-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="196f1-107">Чтобы обеспечить полезные данные пространственного сопоставления, разработчики приложений имеют несколько вариантов:</span><span class="sxs-lookup"><span data-stu-id="196f1-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="196f1-108">Полагаться на то, что уже было собрано.</span><span class="sxs-lookup"><span data-stu-id="196f1-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="196f1-109">Изначально эти данные могут быть неполными.</span><span class="sxs-lookup"><span data-stu-id="196f1-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="196f1-110">Попросите пользователя использовать жест раскрытия для перехода на домашнюю страницу Windows Mixed Reality, а затем изучите область, которую хотите использовать для работы.</span><span class="sxs-lookup"><span data-stu-id="196f1-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="196f1-111">Они могут использовать воздушное касание для подтверждения того, что все необходимые области известны устройству.</span><span class="sxs-lookup"><span data-stu-id="196f1-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="196f1-112">Создание пользовательского интерфейса для просмотра в собственном приложении.</span><span class="sxs-lookup"><span data-stu-id="196f1-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="196f1-113">Обратите внимание, что во всех этих случаях фактические данные, собранные во время исследования, хранятся в системе, и приложению не нужно делать это.</span><span class="sxs-lookup"><span data-stu-id="196f1-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="196f1-114">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="196f1-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="196f1-115"><strong>Функциями</strong></span><span class="sxs-lookup"><span data-stu-id="196f1-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="196f1-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="196f1-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="196f1-117"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="196f1-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="196f1-118">Визуализация просмотра комнаты</span><span class="sxs-lookup"><span data-stu-id="196f1-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="196f1-119">✔️</span><span class="sxs-lookup"><span data-stu-id="196f1-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="196f1-120">Создание пользовательского интерфейса сканирования</span><span class="sxs-lookup"><span data-stu-id="196f1-120">Building a custom scanning experience</span></span>

<span data-ttu-id="196f1-121">Приложения могут проанализировать данные пространственного сопоставления в начале работы, чтобы определить, требуется ли пользователю выполнять дополнительные действия для улучшения его полноты и качества.</span><span class="sxs-lookup"><span data-stu-id="196f1-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="196f1-122">Если анализ означает, что качество следует улучшить, разработчики должны предоставить визуализацию для наложения на мир, чтобы указать:</span><span class="sxs-lookup"><span data-stu-id="196f1-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="196f1-123">Какая часть общего объема в области пользователей должна быть частью работы</span><span class="sxs-lookup"><span data-stu-id="196f1-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="196f1-124">Где пользователь должен переходить к улучшению данных</span><span class="sxs-lookup"><span data-stu-id="196f1-124">Where the user should go to improve data</span></span>

<span data-ttu-id="196f1-125">Пользователи не узнают, что делает «хорошее» сканирование.</span><span class="sxs-lookup"><span data-stu-id="196f1-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="196f1-126">Они должны отображаться или знать, что искать, если у них есть запрос на оценку сканирования — плоскости, расстояния от фактических стен и т. д. Разработчик должен реализовать цикл обратной связи, включающий обновление данных пространственного сопоставления на этапе сканирования или исследования.</span><span class="sxs-lookup"><span data-stu-id="196f1-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="196f1-127">Во многих случаях лучше сообщить пользователю, что нужно сделать (например, Взгляните на центр мебели), чтобы получить необходимое качество сканирования.</span><span class="sxs-lookup"><span data-stu-id="196f1-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="196f1-128">Кэшированное и непрерывное пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="196f1-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="196f1-129">Данные пространственного сопоставления — это наиболее интенсивно используемые приложения с данными о геовесовых источниках данных.</span><span class="sxs-lookup"><span data-stu-id="196f1-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="196f1-130">Чтобы избежать проблем с производительностью, таких как пропущенные кадры или "дергания", следует тщательно проделать эти данные.</span><span class="sxs-lookup"><span data-stu-id="196f1-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="196f1-131">Активное сканирование во время работы может быть полезным или негативным, и разработчику необходимо решить, какой метод использовать в зависимости от опыта работы.</span><span class="sxs-lookup"><span data-stu-id="196f1-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="196f1-132">Кэшированное пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="196f1-132">Cached spatial mapping</span></span>

<span data-ttu-id="196f1-133">В случае кэшированного пространственного сопоставления приложение обычно создает моментальный снимок данных пространственного сопоставления и использует этот моментальный снимок на время работы.</span><span class="sxs-lookup"><span data-stu-id="196f1-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="196f1-134">**Преимущества**</span><span class="sxs-lookup"><span data-stu-id="196f1-134">**Benefits**</span></span>
* <span data-ttu-id="196f1-135">Снижение издержек на работу системы в то время, как они работают с повышением производительности, перегревом и производительностью ЦП.</span><span class="sxs-lookup"><span data-stu-id="196f1-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="196f1-136">Более простая реализация основного интерфейса, так как она не прерывается изменениями в пространственных данных.</span><span class="sxs-lookup"><span data-stu-id="196f1-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="196f1-137">Один раз затраты на обработку пространственных данных для физических, графических и других целей.</span><span class="sxs-lookup"><span data-stu-id="196f1-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="196f1-138">**Недостатки**</span><span class="sxs-lookup"><span data-stu-id="196f1-138">**Drawbacks**</span></span>
* <span data-ttu-id="196f1-139">Перемещение реальных объектов или людей не отражается в кэшированных данных.</span><span class="sxs-lookup"><span data-stu-id="196f1-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="196f1-140">Например:</span><span class="sxs-lookup"><span data-stu-id="196f1-140">E.g.</span></span> <span data-ttu-id="196f1-141">приложение может рассматривать открытку, когда она на самом деле закрыта.</span><span class="sxs-lookup"><span data-stu-id="196f1-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="196f1-142">Потенциально больше памяти приложения для поддержания кэшированной версии данных.</span><span class="sxs-lookup"><span data-stu-id="196f1-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="196f1-143">Хорошим вариантом для этого метода является управляемая среда или верхняя игра в виде таблицы.</span><span class="sxs-lookup"><span data-stu-id="196f1-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="196f1-144">Непрерывное пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="196f1-144">Continuous spatial mapping</span></span>

<span data-ttu-id="196f1-145">Для обновления данных пространственного сопоставления некоторые приложения могут использовать для продолжения сканирования.</span><span class="sxs-lookup"><span data-stu-id="196f1-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="196f1-146">**Преимущества**</span><span class="sxs-lookup"><span data-stu-id="196f1-146">**Benefits**</span></span>
* <span data-ttu-id="196f1-147">В приложении не требуется выполнять сборку в отдельном сканировании или исследовании.</span><span class="sxs-lookup"><span data-stu-id="196f1-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="196f1-148">Движение реальных объектов в реальном мире может быть отражено в игре, хотя и с некоторой задержкой.</span><span class="sxs-lookup"><span data-stu-id="196f1-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="196f1-149">**Недостатки**</span><span class="sxs-lookup"><span data-stu-id="196f1-149">**Drawbacks**</span></span>
* <span data-ttu-id="196f1-150">Более высокая сложность реализации основного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="196f1-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="196f1-151">Потенциальные издержки на дополнительную обработку графики или физических ресурсов, так как изменения должны быть последовательно приняты этими системами.</span><span class="sxs-lookup"><span data-stu-id="196f1-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="196f1-152">Более высокая мощность, тепловые и ПРОЦЕССОРные последствия.</span><span class="sxs-lookup"><span data-stu-id="196f1-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="196f1-153">Хорошим вариантом для этого метода является ситуация, когда самые голограммы должны взаимодействовать с перемещением объектов, например, в г. автомобиль, на котором накопители в этаже могут правильно покрывать дверцу в зависимости от того, открыт или закрыт.</span><span class="sxs-lookup"><span data-stu-id="196f1-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="196f1-154">См. также</span><span class="sxs-lookup"><span data-stu-id="196f1-154">See also</span></span>
* [<span data-ttu-id="196f1-155">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="196f1-155">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="196f1-156">Системы координат</span><span class="sxs-lookup"><span data-stu-id="196f1-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="196f1-157">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="196f1-157">Spatial sound design</span></span>](spatial-sound-design.md)
