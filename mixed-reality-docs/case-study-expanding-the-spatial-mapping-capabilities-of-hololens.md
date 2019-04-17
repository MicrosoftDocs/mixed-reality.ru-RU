---
title: Пример использования - расширением пространственных сопоставление возможностей HoloLens
description: При создании наши первого приложения для Microsoft HoloLens, мы были рады увидеть, насколько просто можно передать границы пространственное сопоставление на устройстве.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Пространственное сопоставление Windows Mixed Reality, HoloLens,
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602836"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="79bb3-104">Пример использования - расширением пространственных сопоставление возможностей HoloLens</span><span class="sxs-lookup"><span data-stu-id="79bb3-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="79bb3-105">При создании наши первого приложения для Microsoft HoloLens, мы были рады увидеть, насколько просто можно передать границы пространственное сопоставление на устройстве.</span><span class="sxs-lookup"><span data-stu-id="79bb3-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="79bb3-106">Джефф Evertt, инженер по в Microsoft Studios, объясняет, как это новая технология была разработана из потребность в больший контроль над размещение голограммы в реальной среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="79bb3-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="79bb3-107">Просмотрите видео</span><span class="sxs-lookup"><span data-stu-id="79bb3-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="79bb3-108">Помимо пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="79bb3-108">Beyond spatial mapping</span></span>

<span data-ttu-id="79bb3-109">Хотя мы работали над [фрагментов](https://www.microsoft.com/p/fragments/9nblggh5ggm8) и [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), два первой игры для HoloLens, мы обнаружили, что когда мы создавали процедурного размещение голограммы в физическом мире, нам нужно более высокого уровня понимания о среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="79bb3-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="79bb3-110">Каждая игра была потребностям конкретного размещения: Во фрагментах, например, мы хотели бы иметь возможность различать между различными поверхностями — например ближайшее снизу целое или таблице — для размещения подсказки в интересующих нас мест.</span><span class="sxs-lookup"><span data-stu-id="79bb3-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="79bb3-111">Мы также хотели бы иметь возможность идентифицировать поверхности бездействию life-size holographic символов может, например диване или стула.</span><span class="sxs-lookup"><span data-stu-id="79bb3-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="79bb3-112">В Conker Young нам нужно было Conker и его противников, чтобы иметь возможность использовать вызванное поверхности в комнате игрока в качестве платформы.</span><span class="sxs-lookup"><span data-stu-id="79bb3-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="79bb3-113">[Asobo Studios](http://www.asobostudio.com/index.html), наш партнер по разработке для этих игр сталкиваются решает эту проблему и создать это технология, которая расширяет возможности сопоставления пространственных HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79bb3-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="79bb3-114">Используя эту возможность, мы может анализ игрока комнаты и определение поверхности, например стены, таблицы, стульев и пол.</span><span class="sxs-lookup"><span data-stu-id="79bb3-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="79bb3-115">Оно также дало нам возможность оптимизировать с набором ограничений для определения размещения holographic объектов.</span><span class="sxs-lookup"><span data-stu-id="79bb3-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="79bb3-116">Пространственные понимание кода</span><span class="sxs-lookup"><span data-stu-id="79bb3-116">The spatial understanding code</span></span>

<span data-ttu-id="79bb3-117">Мы заняло Asobo в исходный код и создали библиотеку, которая инкапсулирует этой технологии.</span><span class="sxs-lookup"><span data-stu-id="79bb3-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="79bb3-118">Корпорация Майкрософт и Asobo теперь открытый исходный код этого кода и делает ее доступной на [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) для использования в собственных проектах.</span><span class="sxs-lookup"><span data-stu-id="79bb3-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="79bb3-119">Весь исходный код включается, позволяя настраивать его под свои нужды и поделиться с сообществом улучшений.</span><span class="sxs-lookup"><span data-stu-id="79bb3-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="79bb3-120">Код для C++ средства поиска решения в оболочку в библиотеку DLL для универсальной платформы Windows и доступ к Unity с [prefab сборка, содержащихся в MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span><span class="sxs-lookup"><span data-stu-id="79bb3-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="79bb3-121">Существует множество полезных запросов, входящей в состав примера Unity, вы сможете найти свободное место на стене, поместите объекты на ближайшее сверху целое или большие пробелы в условиях, определить, для символов средством обработки и множество других запросов пространственных основные сведения о.</span><span class="sxs-lookup"><span data-stu-id="79bb3-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="79bb3-122">Хотя решение пространственное сопоставление, предоставляемые HoloLens предназначен быть универсальными, в соответствии с потребностями весь спектр пространства состояний, пространственных основные сведения о модуле была создана для поддержки потребностей два игр.</span><span class="sxs-lookup"><span data-stu-id="79bb3-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="79bb3-123">Таким образом его решение рассматриваются специфические идентификаторы процессов и набор предположения:</span><span class="sxs-lookup"><span data-stu-id="79bb3-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="79bb3-124">**Фиксированного размера playspace**: Пользователь задает размер максимального playspace в вызове метода init.</span><span class="sxs-lookup"><span data-stu-id="79bb3-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="79bb3-125">**Процесс однократную проверку**: Этот процесс требует дискретный определение playspace, сканирование этап, когда пользователь выходит вокруг.</span><span class="sxs-lookup"><span data-stu-id="79bb3-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="79bb3-126">Функции запросов, не будут работать до, после проверки завершена.</span><span class="sxs-lookup"><span data-stu-id="79bb3-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="79bb3-127">**Управляемая playspace «рисование» пользователем**: Во время фазы сканирования пользователь перемещает и ищет вокруг playspace эффективно закрашивание области, которые должны быть включены.</span><span class="sxs-lookup"><span data-stu-id="79bb3-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="79bb3-128">Отзыв пользователя на этом этапе важно созданный сетки.</span><span class="sxs-lookup"><span data-stu-id="79bb3-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="79bb3-129">**Улице домашней или офисной установки**: Функции запросов разрабатываются на основе плоскими поверхностями и стены под прямым углом.</span><span class="sxs-lookup"><span data-stu-id="79bb3-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="79bb3-130">Это мягкое ограничение.</span><span class="sxs-lookup"><span data-stu-id="79bb3-130">This is a soft limitation.</span></span> <span data-ttu-id="79bb3-131">Однако во время фазы сканирования анализа основной оси выполняется для оптимизации тесселяции сетки на основной и вспомогательной оси.</span><span class="sxs-lookup"><span data-stu-id="79bb3-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="79bb3-132">Процесс сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="79bb3-132">Room Scanning Process</span></span>

<span data-ttu-id="79bb3-133">При загрузке модуля пространственных понимание первое, что вы сделаете — сканирования сферы, так что все также можно использовать областей — например floor, ceiling и стен — идентифицируются и с меткой.</span><span class="sxs-lookup"><span data-stu-id="79bb3-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="79bb3-134">В процессе сканирования оглядитесь комнате и «paint "области, которые должны быть включены во время проверки.</span><span class="sxs-lookup"><span data-stu-id="79bb3-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="79bb3-135">Сетки, которая происходит во время этого этапа является важной характеристикой визуальную обратную связь, которая дает пользователям понять, какие части комнаты выполняется сканирование.</span><span class="sxs-lookup"><span data-stu-id="79bb3-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="79bb3-136">Библиотеки DLL для пространственных основные сведения о модуле внутреннее хранение playspace как сетка 8cm размера voxel кубов.</span><span class="sxs-lookup"><span data-stu-id="79bb3-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="79bb3-137">Во время начальной части сканирования завершения анализа основного компонента для определения осей комнаты.</span><span class="sxs-lookup"><span data-stu-id="79bb3-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="79bb3-138">Внутри он хранит пространства voxel, выровненным по этим осям.</span><span class="sxs-lookup"><span data-stu-id="79bb3-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="79bb3-139">Сетка создается приблизительно каждую секунду путем извлечения isosurface voxel тома.</span><span class="sxs-lookup"><span data-stu-id="79bb3-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![Пространственные сопоставление сетки белого цвета и понимание playspace mesh зеленым цветом](images/spatial-mapping-500px.png)

<span data-ttu-id="79bb3-141">Пространственные сопоставление сетки белого цвета и понимание playspace mesh зеленым цветом</span><span class="sxs-lookup"><span data-stu-id="79bb3-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="79bb3-142">Включаемый файл SpatialUnderstanding.cs управляет процессом сканирования этапа.</span><span class="sxs-lookup"><span data-stu-id="79bb3-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="79bb3-143">Он вызывает следующие функции:</span><span class="sxs-lookup"><span data-stu-id="79bb3-143">It calls the following functions:</span></span>
* <span data-ttu-id="79bb3-144">**SpatialUnderstanding_Init**: Вызывается один раз в начале.</span><span class="sxs-lookup"><span data-stu-id="79bb3-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="79bb3-145">**GeneratePlayspace_InitScan**: Указывает, что должно начинаться на этапе проверки.</span><span class="sxs-lookup"><span data-stu-id="79bb3-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="79bb3-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Вызывается каждого кадра, чтобы обновить процесс сканирования.</span><span class="sxs-lookup"><span data-stu-id="79bb3-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="79bb3-147">Положение камеры и ориентацию переданный и используется для playspace рисования, описанный выше процесс.</span><span class="sxs-lookup"><span data-stu-id="79bb3-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="79bb3-148">**GeneratePlayspace_RequestFinish**: Вызывается для завершения playspace.</span><span class="sxs-lookup"><span data-stu-id="79bb3-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="79bb3-149">Области «закрасить» на этапе проверки будут использованы для определения и заблокировать playspace.</span><span class="sxs-lookup"><span data-stu-id="79bb3-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="79bb3-150">Приложение может запросить статистику во время сканирования этапа, а также запроса пользовательского сетки для предоставления отзывов пользователей.</span><span class="sxs-lookup"><span data-stu-id="79bb3-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="79bb3-151">**Import_UnderstandingMesh**: Во время сканирования, **SpatialUnderstandingCustomMesh** поведение модулем и помещаются в prefab понимание будет периодически опрашивает процессом пользовательского сетки.</span><span class="sxs-lookup"><span data-stu-id="79bb3-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="79bb3-152">Кроме того это делается еще раз после завершения сканирования.</span><span class="sxs-lookup"><span data-stu-id="79bb3-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="79bb3-153">Сканирования потока, обусловленных **SpatialUnderstanding** вызовы поведение **InitScan**, затем **UpdateScan** каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="79bb3-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="79bb3-154">При разумным покрытия отчете статистики запроса, пользователь может airtap для вызова **RequestFinish** для указания на конец фазы сканирования.</span><span class="sxs-lookup"><span data-stu-id="79bb3-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="79bb3-155">**UpdateScan** по-прежнему вызываться, пока он не возвращаемое значение указывает, что библиотека DLL завершило обработку.</span><span class="sxs-lookup"><span data-stu-id="79bb3-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="79bb3-156">Запросы</span><span class="sxs-lookup"><span data-stu-id="79bb3-156">The queries</span></span>

<span data-ttu-id="79bb3-157">Когда сканирование будет закончено, можно получить доступ к три различных типа запросов в интерфейсе:</span><span class="sxs-lookup"><span data-stu-id="79bb3-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="79bb3-158">**Топология запросов**: Это быстрое выполнение запросов, которые основываются на топологии отсканированные комнаты.</span><span class="sxs-lookup"><span data-stu-id="79bb3-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="79bb3-159">**Формирование запросов**: Они используют результаты запросов топологии для поиска по горизонтали поверхностях, расположенных хорошего соответствия среди пользовательских фигур, определенных вами.</span><span class="sxs-lookup"><span data-stu-id="79bb3-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="79bb3-160">**Запросы на размещение объектов**: Это более сложные запросы, найти наилучшее расположение, на основе набора правил и ограничений для объекта.</span><span class="sxs-lookup"><span data-stu-id="79bb3-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="79bb3-161">Помимо трех запросов основной интерфейс точные точки для отслеживания, который может использоваться для извлечения с тегами типы поверхностей и пользовательских watertight место сетки может быть скопирован обратно.</span><span class="sxs-lookup"><span data-stu-id="79bb3-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="79bb3-162">Топология запросов</span><span class="sxs-lookup"><span data-stu-id="79bb3-162">Topology queries</span></span>

<span data-ttu-id="79bb3-163">В этой библиотеке DLL диспетчера топологии обрабатывает пометки среды.</span><span class="sxs-lookup"><span data-stu-id="79bb3-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="79bb3-164">Как упоминалось выше, большая часть данных хранится в surfels, в которой содержатся в томе voxel.</span><span class="sxs-lookup"><span data-stu-id="79bb3-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="79bb3-165">Кроме того **PlaySpaceInfos** структура используется для хранения сведений о playspace, включая выравнивание по всему миру (Дополнительные сведения об этом ниже), floor и ceiling высоты.</span><span class="sxs-lookup"><span data-stu-id="79bb3-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="79bb3-166">Эвристики для определения floor, ceiling и стены.</span><span class="sxs-lookup"><span data-stu-id="79bb3-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="79bb3-167">Например максимальный и минимальный горизонтальный поверхности с более чем 1 m2 контактную зону считается ближайшее снизу целое.</span><span class="sxs-lookup"><span data-stu-id="79bb3-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="79bb3-168">Обратите внимание на то, что путь камеры во время сканирования также используется в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="79bb3-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="79bb3-169">Подмножество запросов, предоставляемых диспетчера топологии предоставляются посредством библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="79bb3-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="79bb3-170">Ниже приведены запросы предоставляемого топологии.</span><span class="sxs-lookup"><span data-stu-id="79bb3-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="79bb3-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="79bb3-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="79bb3-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="79bb3-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="79bb3-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="79bb3-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="79bb3-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="79bb3-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="79bb3-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="79bb3-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="79bb3-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="79bb3-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="79bb3-177">Каждый из запросов имеет набор параметров, зависящие от типа запроса.</span><span class="sxs-lookup"><span data-stu-id="79bb3-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="79bb3-178">В следующем примере пользователь указывает минимальную высоту и ширину нужного тома, высота минимальное размещения выше ближайшее снизу целое и минимальный объем зазор перед тома.</span><span class="sxs-lookup"><span data-stu-id="79bb3-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="79bb3-179">Все измерения, в метрах.</span><span class="sxs-lookup"><span data-stu-id="79bb3-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="79bb3-180">Каждый из запросов принимает предварительно выделить массив **TopologyResult** структуры.</span><span class="sxs-lookup"><span data-stu-id="79bb3-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="79bb3-181">**LocationCount** параметр указывает длину переданный массив.</span><span class="sxs-lookup"><span data-stu-id="79bb3-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="79bb3-182">Возвращаемое значение сообщает количество возвращаемых расположений.</span><span class="sxs-lookup"><span data-stu-id="79bb3-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="79bb3-183">Это число больше никогда не передается в **locationCount** параметра.</span><span class="sxs-lookup"><span data-stu-id="79bb3-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="79bb3-184">**TopologyResult** содержит центральную позицию возвращаемого тома, разворота направления (т. е. обычные) и размеры найден пространства.</span><span class="sxs-lookup"><span data-stu-id="79bb3-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="79bb3-185">Обратите внимание, что в образце Unity, каждый из этих запросов связанного к кнопке панели виртуального пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="79bb3-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="79bb3-186">Пример жестких коды параметры для каждого из этих запросов, приемлемые значения.</span><span class="sxs-lookup"><span data-stu-id="79bb3-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="79bb3-187">См. в разделе *SpaceVisualizer.cs* в образце кода Дополнительные примеры.</span><span class="sxs-lookup"><span data-stu-id="79bb3-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="79bb3-188">Запросы фигуры</span><span class="sxs-lookup"><span data-stu-id="79bb3-188">Shape queries</span></span>

<span data-ttu-id="79bb3-189">Внутри библиотеки DLL, анализатор фигуры (**ShapeAnalyzer_W**) использует анализатор топологии для сравнения пользовательские фигуры, определенные пользователем.</span><span class="sxs-lookup"><span data-stu-id="79bb3-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="79bb3-190">Пример Unity содержит предварительно определенный набор фигур, которые отображаются в меню запрос, на вкладке "Фигура".</span><span class="sxs-lookup"><span data-stu-id="79bb3-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="79bb3-191">Обратите внимание на то, что анализ фигуры работает на горизонтальной поверхностях только.</span><span class="sxs-lookup"><span data-stu-id="79bb3-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="79bb3-192">Диване, например, определяется области неструктурированных рабочих мест и плоский вверху диване обратно.</span><span class="sxs-lookup"><span data-stu-id="79bb3-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="79bb3-193">Запроса shape выполняет поиск двух областей определенного размера, высоту и аспект диапазона, с помощью двух областей выравнивается и подключен.</span><span class="sxs-lookup"><span data-stu-id="79bb3-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="79bb3-194">С помощью API-интерфейсы терминология, рабочих диване мест и верхней границей в конец диване являются фигуры компонентов и выравнивание, требования ограниченность компонентов фигуры.</span><span class="sxs-lookup"><span data-stu-id="79bb3-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="79bb3-195">Пример запроса, определенные в образце Unity (**ShapeDefinition.cs**), «sittable» объектов, выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="79bb3-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="79bb3-196">Каждый запрос фигуры определяется набор компонентов фигуры, каждая из которых набор ограниченность компонентов и ряд ограничений фигуры, которые перечислены зависимости между компонентами.</span><span class="sxs-lookup"><span data-stu-id="79bb3-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="79bb3-197">Этот пример включает три ограничения в определении один компонент и нет ограничений фигуры между компонентами (так как существует только один компонент).</span><span class="sxs-lookup"><span data-stu-id="79bb3-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="79bb3-198">Напротив диване фигура имеет два компонента фигуры и четыре ограничения фигуры.</span><span class="sxs-lookup"><span data-stu-id="79bb3-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="79bb3-199">Обратите внимание на то, что компоненты идентифицируются по их индекс в списке компонентов пользователя (0 и 1 в этом примере).</span><span class="sxs-lookup"><span data-stu-id="79bb3-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="79bb3-200">Функции-оболочки предоставляются в модуле Unity для упрощенного создания пользовательской фигуры определений.</span><span class="sxs-lookup"><span data-stu-id="79bb3-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="79bb3-201">Полный список ограничений компонента и фигуры можно найти в **SpatialUnderstandingDll.cs** в **ShapeComponentConstraint** и **ShapeConstraint** структуры.</span><span class="sxs-lookup"><span data-stu-id="79bb3-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![Синий прямоугольник выделяет результаты запроса shape кресло.](images/chair-shape-query-500px.png)

<span data-ttu-id="79bb3-203">Синий прямоугольник выделяет результаты запроса shape кресло.</span><span class="sxs-lookup"><span data-stu-id="79bb3-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="79bb3-204">Поиск решения для размещения объекта</span><span class="sxs-lookup"><span data-stu-id="79bb3-204">Object placement solver</span></span>

<span data-ttu-id="79bb3-205">Объект размещения запросы могут использоваться для обозначения идеальный расположений в физических комнаты для размещения ваших объектов.</span><span class="sxs-lookup"><span data-stu-id="79bb3-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="79bb3-206">Поиск будет найти наилучшее расположение, заданное объектом правила и ограничения.</span><span class="sxs-lookup"><span data-stu-id="79bb3-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="79bb3-207">Кроме того, запросы объектов действовать, пока объект удаляется с **Solver_RemoveObject** или **Solver_RemoveAllObjects** вызовы, позволяя ограниченное размещение нескольких объектов.</span><span class="sxs-lookup"><span data-stu-id="79bb3-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="79bb3-208">Объект размещения запросы состоят из трех частей: тип размещения с параметрами, список правил и список ограничений.</span><span class="sxs-lookup"><span data-stu-id="79bb3-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="79bb3-209">Чтобы выполнить запрос, используйте следующие API:</span><span class="sxs-lookup"><span data-stu-id="79bb3-209">To run a query, use the following API:</span></span>




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
<span data-ttu-id="79bb3-210">Эта функция принимает имя объекта, определение размещения и список правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="79bb3-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="79bb3-211">C# Оболочки предоставляют конструкции, вспомогательные функции для упрощения создания правила и ограничения.</span><span class="sxs-lookup"><span data-stu-id="79bb3-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="79bb3-212">Определение размещения содержит тип запроса — то есть одно из следующих:</span><span class="sxs-lookup"><span data-stu-id="79bb3-212">The placement definition contains the query type — that is, one of the following:</span></span>




```
public enum PlacementType
                {
                    Place_OnFloor,
                    Place_OnWall,
                    Place_OnCeiling,
                    Place_OnShape,
                    Place_OnEdge,
                    Place_OnFloorAndCeiling,
                    Place_RandomInAir,
                    Place_InMidAir,
                    Place_UnderFurnitureEdge,
                };
```

<span data-ttu-id="79bb3-213">Каждый из типов размещения имеет набор параметров, уникальный в тип.</span><span class="sxs-lookup"><span data-stu-id="79bb3-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="79bb3-214">**ObjectPlacementDefinition** структура содержит набор статических вспомогательных функций для создания этих определений.</span><span class="sxs-lookup"><span data-stu-id="79bb3-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="79bb3-215">Например чтобы найти место для размещения объекта в процессе установки, можно использовать следующую функцию:</span><span class="sxs-lookup"><span data-stu-id="79bb3-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="79bb3-216">Помимо размещения типа могут предоставить набор правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="79bb3-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="79bb3-217">Правила не может быть нарушено.</span><span class="sxs-lookup"><span data-stu-id="79bb3-217">Rules cannot be violated.</span></span> <span data-ttu-id="79bb3-218">Возможное размещение расположения, которые удовлетворяют типа и правила, затем оптимизируются с набором ограничений для выбора расположения оптимальное размещение.</span><span class="sxs-lookup"><span data-stu-id="79bb3-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="79bb3-219">Каждый из правила и ограничения могут создаваться предоставленный создания статических функций.</span><span class="sxs-lookup"><span data-stu-id="79bb3-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="79bb3-220">Ниже приведен пример правила и ограничения создания такой функции.</span><span class="sxs-lookup"><span data-stu-id="79bb3-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="79bb3-221">Ниже запроса размещения объектов требуется поместить половину измерения куба на края поверхности, от других ранее разместить объекты и рядом с центром комнаты.</span><span class="sxs-lookup"><span data-stu-id="79bb3-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




```
List<ObjectPlacementRule> rules = 
          new List<ObjectPlacementRule>() {
               ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
          };

     List<ObjectPlacementConstraint> constraints = 
          new List<ObjectPlacementConstraint> {
               ObjectPlacementConstraint.Create_NearCenter(),
          };

     Solver_PlaceObject(
          “MyCustomObject”,
          new ObjectPlacementDefinition.Create_OnEdge(
          new Vector3(0.25f, 0.25f, 0.25f), 
          new Vector3(0.25f, 0.25f, 0.25f)),
          rules.Count,
          UnderstandingDLL.PinObject(rules.ToArray()),
          constraints.Count,
          UnderstandingDLL.PinObject(constraints.ToArray()),
          UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="79bb3-222">В случае успешного выполнения **ObjectPlacementResult** возвращается структура, содержащая позицию, измерения и ориентацию.</span><span class="sxs-lookup"><span data-stu-id="79bb3-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="79bb3-223">Кроме того размещение добавляется внутренний список размещенных объектов для библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="79bb3-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="79bb3-224">Размещение последующие запросы будут учитывать этот объект.</span><span class="sxs-lookup"><span data-stu-id="79bb3-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="79bb3-225">**LevelSolver.cs** файл в образце Unity содержит дополнительные примеры запросов.</span><span class="sxs-lookup"><span data-stu-id="79bb3-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![Синие — результат из трех запросов Floor на месте с правилами «немедленно из позиции камеры».](images/away-from-camera-position-500px.png)

<span data-ttu-id="79bb3-227">Синие — результат из трех запросов Floor на месте с правилами «немедленно из позиции камеры».</span><span class="sxs-lookup"><span data-stu-id="79bb3-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="79bb3-228">**Советы:**</span><span class="sxs-lookup"><span data-stu-id="79bb3-228">**Tips:**</span></span>
* <span data-ttu-id="79bb3-229">Решения для расположения размещения нескольких объектов, необходимые для уровня или приложение сценария, следует сначала разрешить незаменимым и больших объектов, чтобы максимально увеличить вероятность того, что можно найти пробел.</span><span class="sxs-lookup"><span data-stu-id="79bb3-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="79bb3-230">Важен порядок размещения.</span><span class="sxs-lookup"><span data-stu-id="79bb3-230">Placement order is important.</span></span> <span data-ttu-id="79bb3-231">Если не удается найти объект размещения, попробуйте менее ограниченного конфигураций.</span><span class="sxs-lookup"><span data-stu-id="79bb3-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="79bb3-232">Набор настроек резервирования важно для поддержки функциональности в конфигурациях с много места.</span><span class="sxs-lookup"><span data-stu-id="79bb3-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="79bb3-233">Рэй приведения</span><span class="sxs-lookup"><span data-stu-id="79bb3-233">Ray casting</span></span>

<span data-ttu-id="79bb3-234">Помимо трех запросов основной интерфейсом Рэй приведения может использоваться для извлечения с тегами поверхности типов и пользовательских watertight playspace сетки можно скопировать out после комнате сканирования и завершает работу, метки внутренне создаются для поверхности, например FLOOR, ceiling и стены.</span><span class="sxs-lookup"><span data-stu-id="79bb3-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="79bb3-235">**PlayspaceRaycast** функция принимает луч и возвращает значение, если луч конфликтует с известных поверхность и если да, сведения, которые отображаются в виде **RaycastResult**.</span><span class="sxs-lookup"><span data-stu-id="79bb3-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

<span data-ttu-id="79bb3-236">На внутреннем уровне raycast вычисляется с представлением playspace voxel вычисляемый 8cm, в кубе.</span><span class="sxs-lookup"><span data-stu-id="79bb3-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="79bb3-237">Каждый voxel содержит набор поверхности элементами и данными обработанные топологии (также известный как surfels).</span><span class="sxs-lookup"><span data-stu-id="79bb3-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="79bb3-238">Сравниваются surfels, содержащихся в ячейке пересекаемых voxel, наиболее подходящий, используемый для поиска сведений о топологии.</span><span class="sxs-lookup"><span data-stu-id="79bb3-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="79bb3-239">Эти данные топологии содержит такой параметр возвращается в виде **SurfaceTypes** перечисления, а также контактную зону поверхности пересекаемых.</span><span class="sxs-lookup"><span data-stu-id="79bb3-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="79bb3-240">В этом примере Unity курсора приводит луча каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="79bb3-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="79bb3-241">Во-первых от Unity colliders; Во-вторых от модуля общее представление о мире представления; и наконец, для элементов пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="79bb3-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="79bb3-242">В этом приложении пользовательского интерфейса получает приоритет, а затем результат понимание и, наконец, Unity colliders.</span><span class="sxs-lookup"><span data-stu-id="79bb3-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="79bb3-243">**SurfaceType** сообщается как текст рядом с курсором.</span><span class="sxs-lookup"><span data-stu-id="79bb3-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Результат Raycast reporting пересечение с ближайшее снизу целое.](images/raycast-result-500px.jpg)

<span data-ttu-id="79bb3-245">Результат Raycast reporting пересечение с ближайшее снизу целое.</span><span class="sxs-lookup"><span data-stu-id="79bb3-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="79bb3-246">Получите код</span><span class="sxs-lookup"><span data-stu-id="79bb3-246">Get the code</span></span>

<span data-ttu-id="79bb3-247">Открыть исходный код доступен в [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="79bb3-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="79bb3-248">Сообщите нам об этом [форумы разработчиков HoloLens](https://forums.hololens.com/) при использовании кода в проекте.</span><span class="sxs-lookup"><span data-stu-id="79bb3-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="79bb3-249">Мы очень хотим узнать, что делать с ним!</span><span class="sxs-lookup"><span data-stu-id="79bb3-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="79bb3-250">Об авторе</span><span class="sxs-lookup"><span data-stu-id="79bb3-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="79bb3-251"><b>Джефф Evertt</b> является руководителем разработки программного обеспечения, кто участвовал в разработке HoloLens с первых дней из руковожу к разработке приложений.</span><span class="sxs-lookup"><span data-stu-id="79bb3-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="79bb3-252">До HoloLens он работал на Kinect для Xbox и в отрасли игры на различных платформах и игр.</span><span class="sxs-lookup"><span data-stu-id="79bb3-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="79bb3-253">Джефф полон энтузиазма по поводу robotics, графики и вещи с помощью мигающие, которые необходимо выполнить звукового сигнала.</span><span class="sxs-lookup"><span data-stu-id="79bb3-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="79bb3-254">Он увлекается изучали новые и работа в программном обеспечении и оборудовании и особенно в место, где пересекаются.</span><span class="sxs-lookup"><span data-stu-id="79bb3-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="79bb3-255">См. также</span><span class="sxs-lookup"><span data-stu-id="79bb3-255">See also</span></span>
* [<span data-ttu-id="79bb3-256">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="79bb3-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="79bb3-257">Пространственное сопоставление конструктора</span><span class="sxs-lookup"><span data-stu-id="79bb3-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="79bb3-258">Визуализация сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="79bb3-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="79bb3-259">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="79bb3-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="79bb3-260">Asobo Studio: Уроки из оказался разработки HoloLens</span><span class="sxs-lookup"><span data-stu-id="79bb3-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
