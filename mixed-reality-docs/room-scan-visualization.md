---
title: Визуализация сканирования комнаты
description: Приложения, требующие пространственное сопоставление данных полагаться на устройстве, чтобы автоматически собирать эти данные со временем и во всех сеансах, как пользователь изучает их среды с устройством active.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, шаблоны приложений, разработки, HoloLens, сканирование комнаты, пространственных сопоставление, область реконструкции, mesh
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829911"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="b4e52-104">Визуализация сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="b4e52-104">Room scan visualization</span></span>

<span data-ttu-id="b4e52-105">Приложения, требующие пространственное сопоставление данных полагаться на устройстве, чтобы автоматически собирать эти данные со временем и во всех сеансах, как пользователь изучает их среды с устройством active.</span><span class="sxs-lookup"><span data-stu-id="b4e52-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="b4e52-106">Полноты и качества этих данных зависит от ряда факторов, включая количество исследований, которые пользователь выполнит, сколько времени прошло с момента просмотра и ли объекты, такие как мебель и двери были перемещены, так как устройство сканирования области.</span><span class="sxs-lookup"><span data-stu-id="b4e52-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="b4e52-107">Чтобы обеспечить полезные пространственное сопоставление данных, разработчики приложений имеют несколько вариантов:</span><span class="sxs-lookup"><span data-stu-id="b4e52-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="b4e52-108">Полагаться на то, что могут уже присутствовать.</span><span class="sxs-lookup"><span data-stu-id="b4e52-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="b4e52-109">Эти данные могут быть неполными изначально.</span><span class="sxs-lookup"><span data-stu-id="b4e52-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="b4e52-110">Попросите пользователя с помощью жестов bloom получить для смешанной реальности Windows home, а затем рассмотрю область, которую они хотят использовать для работы.</span><span class="sxs-lookup"><span data-stu-id="b4e52-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="b4e52-111">Они могут использовать жест касания, чтобы убедиться, что все необходимые области известен на устройстве.</span><span class="sxs-lookup"><span data-stu-id="b4e52-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="b4e52-112">Просмотр пользовательского опыта в собственных приложениях.</span><span class="sxs-lookup"><span data-stu-id="b4e52-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="b4e52-113">Обратите внимание, что во всех этих случаях фактические данные, собранные во время просмотра хранится в системе, и приложение не нужно это сделать.</span><span class="sxs-lookup"><span data-stu-id="b4e52-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="b4e52-114">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="b4e52-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4e52-115"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="b4e52-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b4e52-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4e52-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4e52-117"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4e52-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4e52-118">Визуализация сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="b4e52-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="b4e52-119">✔️</span><span class="sxs-lookup"><span data-stu-id="b4e52-119">✔️</span></span></td>
        <td><span data-ttu-id="b4e52-120">❌</span><span class="sxs-lookup"><span data-stu-id="b4e52-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="b4e52-121">Создание пользовательского взаимодействия сканирования</span><span class="sxs-lookup"><span data-stu-id="b4e52-121">Building a custom scanning experience</span></span>

<span data-ttu-id="b4e52-122">Приложения могут посчитать анализа пространственное сопоставление данных в начале возможности определить, требуются ли пользователю выполнять дополнительные действия для повышения его полноты и качества.</span><span class="sxs-lookup"><span data-stu-id="b4e52-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="b4e52-123">Если анализ показывает, что следует улучшить качество, разработчикам следует предоставить визуализацию, чтобы наложить на мир, чтобы указать:</span><span class="sxs-lookup"><span data-stu-id="b4e52-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="b4e52-124">Сколько всего тома окружающими пользователей должен быть частью работы</span><span class="sxs-lookup"><span data-stu-id="b4e52-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="b4e52-125">Где пользователь должен перейти к улучшить данных</span><span class="sxs-lookup"><span data-stu-id="b4e52-125">Where the user should go to improve data</span></span>

<span data-ttu-id="b4e52-126">Пользователи не знают, что делает проверку «хорошие».</span><span class="sxs-lookup"><span data-stu-id="b4e52-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="b4e52-127">Они должны отображаться, или же говорили, что искать, если они запрос для оценки проверки — спрямления, расстояние от фактического стен и т.д. Разработчик должен реализовать цикл обратной связи, который включает в себя обновление пространственное сопоставление данных во время фазы сканирования и исследования.</span><span class="sxs-lookup"><span data-stu-id="b4e52-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="b4e52-128">Во многих случаях, возможно, следует сообщить пользователю, какие возможности нужны (например Обратите внимание на округление вверх, просмотрите за мебель), чтобы получить необходимые проверки качества.</span><span class="sxs-lookup"><span data-stu-id="b4e52-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="b4e52-129">Кэширование и непрерывной пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="b4e52-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="b4e52-130">Пространственное сопоставление данных является наиболее большой вес, который разрешается использовать приложения источника данных.</span><span class="sxs-lookup"><span data-stu-id="b4e52-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="b4e52-131">Чтобы избежать проблем с производительностью, таких как пропущенным кадрам или "дергания", использование этих данных следует соблюдать осторожность.</span><span class="sxs-lookup"><span data-stu-id="b4e52-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="b4e52-132">Active сканирование во время интерфейс может быть полезным или ущерб, и разработчику нужно будет решить, какой метод использовать исходя из опыта.</span><span class="sxs-lookup"><span data-stu-id="b4e52-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="b4e52-133">Кэшированные пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="b4e52-133">Cached spatial mapping</span></span>

<span data-ttu-id="b4e52-134">В случае кэшированный пространственное сопоставление, приложение обычно создается моментальный снимок данных пространственное сопоставление и использует этот моментальный снимок во время работы.</span><span class="sxs-lookup"><span data-stu-id="b4e52-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="b4e52-135">**Преимущества**</span><span class="sxs-lookup"><span data-stu-id="b4e52-135">**Benefits**</span></span>
* <span data-ttu-id="b4e52-136">Сокращение издержек в системе, процесс работает ведущим значительное степень, температуры и прирост производительности ЦП.</span><span class="sxs-lookup"><span data-stu-id="b4e52-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="b4e52-137">Простая реализация работать на основной, так как он не будет прерван изменения в пространственных данных.</span><span class="sxs-lookup"><span data-stu-id="b4e52-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="b4e52-138">Один один раз затрат на любой завершающей обработки пространственных данных для физики, графики и других целей.</span><span class="sxs-lookup"><span data-stu-id="b4e52-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="b4e52-139">**Недостатки**</span><span class="sxs-lookup"><span data-stu-id="b4e52-139">**Drawbacks**</span></span>
* <span data-ttu-id="b4e52-140">Перемещение объектов реального мира или людей не отражаться на кэшированные данные.</span><span class="sxs-lookup"><span data-stu-id="b4e52-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="b4e52-141">Например:</span><span class="sxs-lookup"><span data-stu-id="b4e52-141">E.g.</span></span> <span data-ttu-id="b4e52-142">приложения могут быть использованы двери открытым при теперь фактически закрыт.</span><span class="sxs-lookup"><span data-stu-id="b4e52-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="b4e52-143">Потенциально больше памяти приложения для поддержания кэшированной версии данных.</span><span class="sxs-lookup"><span data-stu-id="b4e52-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="b4e52-144">Хороший вариант для этого метода является игра верхней таблице или контролируемой среде.</span><span class="sxs-lookup"><span data-stu-id="b4e52-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="b4e52-145">Непрерывная пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="b4e52-145">Continuous spatial mapping</span></span>

<span data-ttu-id="b4e52-146">Некоторые приложения могут полагаться на продолжает сканирование, чтобы обновить данные пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="b4e52-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="b4e52-147">**Преимущества**</span><span class="sxs-lookup"><span data-stu-id="b4e52-147">**Benefits**</span></span>
* <span data-ttu-id="b4e52-148">Не нужно создавать в отдельной сканирования или просмотра раньше наращивание ресурсов выполняется в приложении.</span><span class="sxs-lookup"><span data-stu-id="b4e52-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="b4e52-149">Перемещение объектов реального мира можно будет отражаться на игры, несмотря на то что и в случае с некоторая задержка.</span><span class="sxs-lookup"><span data-stu-id="b4e52-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="b4e52-150">**Недостатки**</span><span class="sxs-lookup"><span data-stu-id="b4e52-150">**Drawbacks**</span></span>
* <span data-ttu-id="b4e52-151">Выше сложность в реализации основного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="b4e52-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="b4e52-152">Потенциальные издержки дополнительная обработка для графические данные или физики, как необходимость изменения постепенно начнет принимать эти системы.</span><span class="sxs-lookup"><span data-stu-id="b4e52-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="b4e52-153">Большей мощностью, охлаждения и нагрузкой на ЦП.</span><span class="sxs-lookup"><span data-stu-id="b4e52-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="b4e52-154">Хороший вариант для этого метода является одним где голограммы будут взаимодействовать с перемещением объектов, например holographic автомобиль, диски в процессе установки может потребоваться правильно столкнувшихся с дверь в зависимости от того, является ли это открытым или закрытым.</span><span class="sxs-lookup"><span data-stu-id="b4e52-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4e52-155">См. также</span><span class="sxs-lookup"><span data-stu-id="b4e52-155">See also</span></span>
* [<span data-ttu-id="b4e52-156">Проектирование пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="b4e52-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="b4e52-157">Системы координат</span><span class="sxs-lookup"><span data-stu-id="b4e52-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="b4e52-158">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="b4e52-158">Spatial sound design</span></span>](spatial-sound-design.md)
