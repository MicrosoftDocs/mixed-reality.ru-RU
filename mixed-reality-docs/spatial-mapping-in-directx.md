---
title: Пространственное сопоставление в DirectX
description: В этой статье описывается реализация пространственное сопоставление в приложении DirectX. Сюда входят подробные сведения о работе пространственное сопоставление пример приложения, который входит в состав пакета SDK универсальной платформы Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows смешанный реальность, пространственное сопоставление, среда, взаимодействие, directx, winrt, api, пример кода, UWP, пакет SDK, пошаговое руководство
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605136"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="68883-105">Пространственное сопоставление в DirectX</span><span class="sxs-lookup"><span data-stu-id="68883-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="68883-106">В этом разделе описывается реализация [пространственное сопоставление](spatial-mapping.md) в вашем приложении DirectX.</span><span class="sxs-lookup"><span data-stu-id="68883-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="68883-107">Сюда входят подробные сведения о работе пространственное сопоставление пример приложения, который входит в состав пакета SDK универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="68883-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="68883-108">В этом разделе используется код из [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) пример кода для универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="68883-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="68883-109">Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="68883-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="68883-110">Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.</span><span class="sxs-lookup"><span data-stu-id="68883-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="68883-111">Общие сведения о разработке DirectX</span><span class="sxs-lookup"><span data-stu-id="68883-111">DirectX development overview</span></span>

<span data-ttu-id="68883-112">Разработка приложения в машинном коде для пространственное сопоставление использует интерфейсы API, в разделе [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) пространства имен.</span><span class="sxs-lookup"><span data-stu-id="68883-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="68883-113">Эти API обеспечивают полный контроль над пространственное сопоставление функций, аналогично непосредственно к пространственное сопоставление API-интерфейсы, предоставляемые [Unity](spatial-mapping-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="68883-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="68883-114">API-интерфейсы восприятие</span><span class="sxs-lookup"><span data-stu-id="68883-114">Perception APIs</span></span>

<span data-ttu-id="68883-115">Далее приведены основные типы для разработки пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="68883-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="68883-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) предоставляет сведения о поверхности в регионах, определяемый приложением, места рядом пользователя в форме объектов SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="68883-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="68883-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) описывает единую для объекта пространственных поверхность, включая уникальный идентификатор, ограничивающий тома и время последнего изменения.</span><span class="sxs-lookup"><span data-stu-id="68883-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="68883-118">Он предоставит SpatialSurfaceMesh асинхронно по запросу.</span><span class="sxs-lookup"><span data-stu-id="68883-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="68883-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) содержит параметры, используемые для настройки объектов SpatialSurfaceMesh, запрашиваемых SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="68883-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="68883-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) представляет данные сетки для пространственного единую поверхность.</span><span class="sxs-lookup"><span data-stu-id="68883-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="68883-121">Данные для позиции вершин, нормали вершины и индексы треугольников содержатся в объектах-членах SpatialSurfaceMeshBuffer.</span><span class="sxs-lookup"><span data-stu-id="68883-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="68883-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) заключает в оболочку одного типа данных сетки.</span><span class="sxs-lookup"><span data-stu-id="68883-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="68883-123">При разработке приложения с помощью этих API, простой программы последовательность будет выглядеть (как показано в примере приложения, описанные ниже):</span><span class="sxs-lookup"><span data-stu-id="68883-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="68883-124">**Настройка вашей SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="68883-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="68883-125">Вызовите [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), чтобы убедиться, что пользователь предоставил разрешения для приложения для использования пространственных сопоставление возможностей устройства.</span><span class="sxs-lookup"><span data-stu-id="68883-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="68883-126">Создание экземпляра объекта SpatialSurfaceObserver.</span><span class="sxs-lookup"><span data-stu-id="68883-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="68883-127">Вызовите [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) для указания области пространства, в котором нужно получить сведения о пространственных поверхности.</span><span class="sxs-lookup"><span data-stu-id="68883-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="68883-128">Просто вызывайте эту функцию снова, вы можете изменять эти регионы в будущем.</span><span class="sxs-lookup"><span data-stu-id="68883-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="68883-129">Каждая область указывается с помощью [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span><span class="sxs-lookup"><span data-stu-id="68883-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="68883-130">Зарегистрируйтесь для [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) событие, которое будет срабатывать при поступлении новой информации о пространственных поверхности в области пространства, которые вы указали.</span><span class="sxs-lookup"><span data-stu-id="68883-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="68883-131">**Обработка событий ObservedSurfacesChanged**</span><span class="sxs-lookup"><span data-stu-id="68883-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="68883-132">В обработчике событий, вызовите [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) для получения карты SpatialSurfaceInfo объектов.</span><span class="sxs-lookup"><span data-stu-id="68883-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="68883-133">Используя эту карту, можно обновить записи какие Пространственные поверхностей [существует в среде пользователя](spatial-mapping.md#mesh-caching).</span><span class="sxs-lookup"><span data-stu-id="68883-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="68883-134">Для каждого объекта SpatialSurfaceInfo можно выполнить запрос [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) для определения пространственного экстенты рабочей области, выраженное в [Пространственные системы координат](coordinate-systems.md) по своему выбору.</span><span class="sxs-lookup"><span data-stu-id="68883-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="68883-135">Если вы решите запроса сетки для пространственного поверхности, вызовите [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="68883-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="68883-136">Может предоставлять параметры, указывающие требуемый плотность треугольники и формат возвращаемого сетки данных.</span><span class="sxs-lookup"><span data-stu-id="68883-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="68883-137">**Получать и обрабатывать сетки**</span><span class="sxs-lookup"><span data-stu-id="68883-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="68883-138">Каждый вызов aysnchronously TryComputeLatestMeshAsync будет возвращать один объект SpatialSurfaceMesh.</span><span class="sxs-lookup"><span data-stu-id="68883-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="68883-139">Из этого объекта можно получить доступ к содержащиеся объекты SpatialSurfaceMeshBuffer для доступа к индексов треугольников, позиции вершин и (при запросе) нормалей вершин сетки.</span><span class="sxs-lookup"><span data-stu-id="68883-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="68883-140">Эти данные будут в формате, полностью совместима с [интерфейсы API Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) используемой для визуализации сетки.</span><span class="sxs-lookup"><span data-stu-id="68883-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="68883-141">Отсюда приложения при необходимости можно выполнять анализ или [обработки](spatial-mapping.md#mesh-processing) сетки данных и использовать его для [отрисовки](spatial-mapping.md#rendering) и физики [точные точки для отслеживания и расчет столкновений](spatial-mapping.md#raycasting-and-collision).</span><span class="sxs-lookup"><span data-stu-id="68883-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="68883-142">Один важный момент, следует отметить том, что масштабируемый необходимо применить к позиции вершин сетки (например, в шейдер вершин, используемой для визуализации сетки), преобразовываемый оптимизированного целое число единиц, в которых они хранятся в буфере, на счетчики.</span><span class="sxs-lookup"><span data-stu-id="68883-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="68883-143">Этой шкалы можно получить, вызвав [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span><span class="sxs-lookup"><span data-stu-id="68883-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="68883-144">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="68883-144">Troubleshooting</span></span>
* <span data-ttu-id="68883-145">Не забудьте масштабировать позиции вершин сетки в шейдере вершин по масштабу, возвращенный [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="68883-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="68883-146">Пошаговое руководство по примеру кода пространственных сопоставления</span><span class="sxs-lookup"><span data-stu-id="68883-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="68883-147">[Holographic пространственных сопоставление](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) образец кода содержит код, который можно использовать для начала загрузки поверхности сетки в приложении, включая инфраструктуру для управления и поверхностью отрисовки сетки.</span><span class="sxs-lookup"><span data-stu-id="68883-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="68883-148">Теперь мы рассмотрим добавление поверхности возможности сопоставления в приложении DirectX.</span><span class="sxs-lookup"><span data-stu-id="68883-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="68883-149">Можно добавить этот код, чтобы ваши [Windows Holographic шаблон приложения](creating-a-holographic-directx-project.md) проектом или могут следить за действиями просмотра в образце кода, упомянутых выше.</span><span class="sxs-lookup"><span data-stu-id="68883-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="68883-150">Этот пример кода основан на Windows Holographic шаблон приложения.</span><span class="sxs-lookup"><span data-stu-id="68883-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="68883-151">Настройка приложения для использования возможности spatialPerception</span><span class="sxs-lookup"><span data-stu-id="68883-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="68883-152">Приложения должны иметь возможность использовать Пространственные возможности сопоставления.</span><span class="sxs-lookup"><span data-stu-id="68883-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="68883-153">Это необходимо, поскольку пространственный сетки является представлением среды пользователя, который может рассматриваться как закрытые данные.</span><span class="sxs-lookup"><span data-stu-id="68883-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="68883-154">Объявите данную возможность в файле package.appxmanifest для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="68883-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="68883-155">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="68883-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="68883-156">Возможность поступает из **uap2** пространства имен.</span><span class="sxs-lookup"><span data-stu-id="68883-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="68883-157">Чтобы получить доступ к этому пространству имен в манифесте, включить его как *xlmns* атрибут в &lt;пакета > элемента.</span><span class="sxs-lookup"><span data-stu-id="68883-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="68883-158">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="68883-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="68883-159">Проверьте наличие поддержки функция пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="68883-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="68883-160">Смешанная реальность Windows поддерживает широкий спектр устройств, включая устройства, которые не поддерживают пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="68883-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="68883-161">Если приложение можно использовать пространственное сопоставление или необходимо использовать пространственное сопоставление для обеспечения функциональности, оно должно проверить, чтобы убедиться в том, что пространственное сопоставление поддерживается перед попыткой его использования.</span><span class="sxs-lookup"><span data-stu-id="68883-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="68883-162">Например если пространственное сопоставление требуется приложением смешанной реальности, отобразится сообщение об ошибке, если пользователь пытается его запуск на устройстве без пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="68883-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="68883-163">Или, возможно, приложение может отображать собственной виртуальной среде, вместо среду, предоставляя функциональность, аналогичную что произойдет, если доступны пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="68883-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="68883-164">В любом случае этот API позволяет вашему приложению, которые следует учитывать при его не получить пространственное сопоставление данных и реагировать соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="68883-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="68883-165">Чтобы проверить текущее устройство для поддержки пространственное сопоставление, сначала убедитесь, что контракт универсальной платформы Windows находится на уровне 4 или более поздней версии и затем вызвать SpatialSurfaceObserver::IsSupported().</span><span class="sxs-lookup"><span data-stu-id="68883-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="68883-166">Вот как можно сделать это в контексте [Holographic пространственных сопоставление](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) пример кода.</span><span class="sxs-lookup"><span data-stu-id="68883-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="68883-167">Поддержка проверяется так же, прежде чем запрашивать доступ.</span><span class="sxs-lookup"><span data-stu-id="68883-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="68883-168">SpatialSurfaceObserver::IsSupported() API доступна, начиная с пакета SDK версии 15063.</span><span class="sxs-lookup"><span data-stu-id="68883-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="68883-169">При необходимости изменить целевую платформу проекта, чтобы версия платформы 15063 перед использованием этого API.</span><span class="sxs-lookup"><span data-stu-id="68883-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

<span data-ttu-id="68883-170">Обратите внимание, что если контракт UWP меньше, чем уровень 4, приложения должна продолжаться, как если бы устройства позволяют делать пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="68883-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="68883-171">Запрос на доступ к данным пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="68883-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="68883-172">Приложение должно запросить разрешение на доступ к пространственное сопоставление данных перед попыткой создания любой поверхности наблюдателей.</span><span class="sxs-lookup"><span data-stu-id="68883-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="68883-173">Ниже приведен пример, основываясь на наш пример поверхность сопоставления кода с более подробными сведениями, предоставляемые позже на этой странице:</span><span class="sxs-lookup"><span data-stu-id="68883-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a><span data-ttu-id="68883-174">Создание поверхности наблюдателя</span><span class="sxs-lookup"><span data-stu-id="68883-174">Create a surface observer</span></span>

<span data-ttu-id="68883-175">**Windows::Perception::Spatial::Surfaces** пространство имен включает [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) класс, который обнаруживает один или несколько томов, указанных в [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span><span class="sxs-lookup"><span data-stu-id="68883-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="68883-176">Используйте [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) экземпляра для доступа к данным сетки поверхности в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="68883-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="68883-177">Из **AppMain.h**:</span><span class="sxs-lookup"><span data-stu-id="68883-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="68883-178">Как отмечалось в предыдущем разделе, необходимо запросить доступ к данным пространственное сопоставление, прежде чем приложение может использовать его.</span><span class="sxs-lookup"><span data-stu-id="68883-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="68883-179">Такой доступ предоставляется автоматически в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="68883-179">This access is granted automatically on the HoloLens.</span></span>

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

<span data-ttu-id="68883-180">Далее необходимо настроить поверхности наблюдателя для наблюдения за определенный ограничивающий том.</span><span class="sxs-lookup"><span data-stu-id="68883-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="68883-181">Здесь мы заметили, поле, то есть 20 x 20 x 5 метров, начало системы координат.</span><span class="sxs-lookup"><span data-stu-id="68883-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

<span data-ttu-id="68883-182">Обратите внимание на то, можно задать несколько томов ограничивающий вместо этого.</span><span class="sxs-lookup"><span data-stu-id="68883-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="68883-183">*Это псевдокод:*</span><span class="sxs-lookup"><span data-stu-id="68883-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="68883-184">Можно также использовать другие ограничивающий фигуры — например усеченная или краю ограничивающий прямоугольник, который не оси.</span><span class="sxs-lookup"><span data-stu-id="68883-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="68883-185">*Это псевдокод:*</span><span class="sxs-lookup"><span data-stu-id="68883-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="68883-186">Если вашему приложению необходим действия по-разному при поверхности сопоставления данные недоступны, можно написать код для реагирования на случай где [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) не **разрешено** — например, он не сможет на ПК с иммерсивных устройствами, подключить, так как эти устройства нет оборудования для пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="68883-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="68883-187">Для этих устройств позволив пространственных рабочей области, сведения о среде и конфигурации устройства пользователя.</span><span class="sxs-lookup"><span data-stu-id="68883-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="68883-188">Инициализация и обновление коллекции сетки поверхности</span><span class="sxs-lookup"><span data-stu-id="68883-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="68883-189">Если поверхности наблюдатель был успешно создан, можно переходить к инициализации нашей коллекции сетки поверхности.</span><span class="sxs-lookup"><span data-stu-id="68883-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="68883-190">Здесь мы используем API модели по запросу для получения текущего набора наблюдаемых поверхностей прямо сейчас:</span><span class="sxs-lookup"><span data-stu-id="68883-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

<span data-ttu-id="68883-191">Имеется также для получения данных сетки поверхности модели принудительной отправки.</span><span class="sxs-lookup"><span data-stu-id="68883-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="68883-192">Можно разрабатывать приложения для использования только модели по запросу, если выбран, в этом случае необходимо будет запрашивать данные времени — скажем, один раз за кадр - или определенный период времени, например, во время установки игры.</span><span class="sxs-lookup"><span data-stu-id="68883-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="68883-193">Если Да, приведенный выше код является то, что вам нужно.</span><span class="sxs-lookup"><span data-stu-id="68883-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="68883-194">В нашем примере мы выбрали для демонстрации использования обеих моделей воспитательный целях.</span><span class="sxs-lookup"><span data-stu-id="68883-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="68883-195">Здесь мы подписаться на событие для получения данных в актуальном состоянии сетки поверхности всякий раз, когда система распознает изменения.</span><span class="sxs-lookup"><span data-stu-id="68883-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="68883-196">Наш пример кода также настраивается реагировать на эти события.</span><span class="sxs-lookup"><span data-stu-id="68883-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="68883-197">Давайте рассмотрим, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="68883-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="68883-198">**ПРИМЕЧАНИЕ.** Это может оказаться самым эффективным способом для вашего приложения для обработки данных сетки.</span><span class="sxs-lookup"><span data-stu-id="68883-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="68883-199">Этот код написан для ясности и не оптимизирован.</span><span class="sxs-lookup"><span data-stu-id="68883-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="68883-200">Сетки поверхности данные предоставлены в карту только для чтения, в которой хранятся [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) объектов с помощью [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) как ключевые значения.</span><span class="sxs-lookup"><span data-stu-id="68883-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="68883-201">Для обработки этих данных, мы сначала выполняют для значений ключей, которые отсутствуют в нашей коллекции.</span><span class="sxs-lookup"><span data-stu-id="68883-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="68883-202">Получите сведения о том, как данные хранятся в нашем примере далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="68883-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

<span data-ttu-id="68883-203">Нам также нужно удалить поверхности сетки, которые в нашей коллекции сетки поверхности, но которых нет в коллекции системных больше.</span><span class="sxs-lookup"><span data-stu-id="68883-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="68883-204">Чтобы сделать это, необходимо сделать что-то вроде противоположностью что мы только что показали за добавление и обновление сетки; Мы цикл по коллекции наше приложение и проверьте правильность **Guid** у нас есть в коллекции системы.</span><span class="sxs-lookup"><span data-stu-id="68883-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="68883-205">Если он не находится в коллекции системных, мы удалите его из нас.</span><span class="sxs-lookup"><span data-stu-id="68883-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="68883-206">Из в AppMain.cpp наш обработчик событий:</span><span class="sxs-lookup"><span data-stu-id="68883-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="68883-207">Реализация сетки очистки в RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="68883-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="68883-208">Получить и использовать буферы данных сетки поверхности</span><span class="sxs-lookup"><span data-stu-id="68883-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="68883-209">Получение сведений сетки поверхности был так же просто, как получение коллекции данных и обработки обновления для этой коллекции.</span><span class="sxs-lookup"><span data-stu-id="68883-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="68883-210">Теперь мы перейдем в подробности о том, как можно использовать данные.</span><span class="sxs-lookup"><span data-stu-id="68883-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="68883-211">В нашем примере мы решили использовать поверхности сетки для подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="68883-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="68883-212">Это распространенный сценарий для occluding голограммы за реальных поверхности.</span><span class="sxs-lookup"><span data-stu-id="68883-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="68883-213">Вы можете также отображают сетки или отрисовки обработанные их версии., для представления пользователю область просматриваются комнате, прежде чем начать предоставление функциональных возможностей приложений или игр.</span><span class="sxs-lookup"><span data-stu-id="68883-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="68883-214">Пример кода запускает процесс, при получении обновлений сетки поверхности из обработчика событий от описанного в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="68883-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="68883-215">Важные строки кода в этой функции является вызов для обновления поверхности *mesh*: к этому моменту мы уже обработаны info сетки, и мы должны получить данные вершин и индексов для использования по мы усмотрению.</span><span class="sxs-lookup"><span data-stu-id="68883-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="68883-216">From RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="68883-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

<span data-ttu-id="68883-217">Наш пример кода предназначен, чтобы класс данных **SurfaceMesh**, обработка и вывод данных сетки дескрипторов.</span><span class="sxs-lookup"><span data-stu-id="68883-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="68883-218">Эти сетки являются что **RealtimeSurfaceMeshRenderer** фактически хранит карту.</span><span class="sxs-lookup"><span data-stu-id="68883-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="68883-219">Каждый из них имеет ссылку на SpatialSurfaceMesh, она поступила и мы используем его каждый раз, когда нам нужно получить доступ к сети буферы вершин или индекса, или получить преобразования для сетки.</span><span class="sxs-lookup"><span data-stu-id="68883-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="68883-220">Сейчас мы флаг сетки как требующие обновления.</span><span class="sxs-lookup"><span data-stu-id="68883-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="68883-221">Из SurfaceMesh.cpp:</span><span class="sxs-lookup"><span data-stu-id="68883-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="68883-222">При очередном сетки просят нарисовать сам себя, она проверяет флаг сначала.</span><span class="sxs-lookup"><span data-stu-id="68883-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="68883-223">Если требуется обновление, буферы вершин и индексов будет обновляться в GPU.</span><span class="sxs-lookup"><span data-stu-id="68883-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

<span data-ttu-id="68883-224">Во-первых мы запросов буферы необработанные данные:</span><span class="sxs-lookup"><span data-stu-id="68883-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="68883-225">Затем создаем буферы устройства Direct3D с сетки данных, предоставляемых HoloLens:</span><span class="sxs-lookup"><span data-stu-id="68883-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

<span data-ttu-id="68883-226">**ПРИМЕЧАНИЕ.** Вспомогательная функция CreateDirectXBuffer, используемых в предыдущем фрагменте кода см. в образце кода поверхность сопоставления: SurfaceMesh.cpp GetDataFromIBuffer.h.</span><span class="sxs-lookup"><span data-stu-id="68883-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="68883-227">Теперь завершении создания ресурсов устройства и сети считается загружены и готовы для обновления и визуализации.</span><span class="sxs-lookup"><span data-stu-id="68883-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="68883-228">Обновление и отрисовки поверхности сетки</span><span class="sxs-lookup"><span data-stu-id="68883-228">Update and render surface meshes</span></span>

<span data-ttu-id="68883-229">Наш класс SurfaceMesh имеется функция специализированные обновления.</span><span class="sxs-lookup"><span data-stu-id="68883-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="68883-230">Каждый [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) имеет свои собственные преобразования, а в нашем примере использует текущую систему координат для наших **SpatialStationaryReferenceFrame** получения преобразование.</span><span class="sxs-lookup"><span data-stu-id="68883-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="68883-231">Затем он обновляет буфера констант модель в графическом Процессоре.</span><span class="sxs-lookup"><span data-stu-id="68883-231">Then it updates the model constant buffer on the GPU.</span></span>

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

<span data-ttu-id="68883-232">Когда все готово для отрисовки поверхности сетки, делается некоторые подготовительную работу перед отображением в коллекцию.</span><span class="sxs-lookup"><span data-stu-id="68883-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="68883-233">Мы настраиваем конвейер шейдера для текущей конфигурации подготовки к просмотру, и мы настраиваем стадии ассемблера входных данных.</span><span class="sxs-lookup"><span data-stu-id="68883-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="68883-234">Обратите внимание, что вспомогательный класс holographic камеры **CameraResources.cpp** уже настроил буфера констант/проекция представления к этому моменту.</span><span class="sxs-lookup"><span data-stu-id="68883-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="68883-235">Из **RealtimeSurfaceMeshRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="68883-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

<span data-ttu-id="68883-236">После этого, мы цикл по нашей сеток и сообщить каждого из них нарисовать сам себя.</span><span class="sxs-lookup"><span data-stu-id="68883-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="68883-237">**ПРИМЕЧАНИЕ.** Этот пример кода не оптимизированы для использования любого вида поверхности пирамиды обзора, но следует включать эту функцию в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="68883-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

<span data-ttu-id="68883-238">Отдельных сеток несут ответственность за настройки буфера вершин и индексов, stride и буфер констант преобразования модели.</span><span class="sxs-lookup"><span data-stu-id="68883-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="68883-239">Как и в случае с вращающегося куба в шаблоне приложения с Windows Holographic, мы визуализируем stereoscopic буферов, с помощью создания экземпляров.</span><span class="sxs-lookup"><span data-stu-id="68883-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="68883-240">Из **SurfaceMesh::Draw**:</span><span class="sxs-lookup"><span data-stu-id="68883-240">From **SurfaceMesh::Draw**:</span></span>

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="68883-241">Подготовка к просмотру вариантов в поверхность сопоставления</span><span class="sxs-lookup"><span data-stu-id="68883-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="68883-242">В образце кода поверхность сопоставления предоставляет код для подготовки к просмотру только для перекрытия данных сетки поверхности, а также для отображения на экране поверхности сетки данных.</span><span class="sxs-lookup"><span data-stu-id="68883-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="68883-243">Какой путь выбран - или - зависит от приложения.</span><span class="sxs-lookup"><span data-stu-id="68883-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="68883-244">Мы рассмотрим обе конфигурации в этом документе.</span><span class="sxs-lookup"><span data-stu-id="68883-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="68883-245">**Подготовка к просмотру перекрытия буферов для holographic эффекта**</span><span class="sxs-lookup"><span data-stu-id="68883-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="68883-246">Для начала сняв целевой объект прорисовки для текущей виртуальной камеры.</span><span class="sxs-lookup"><span data-stu-id="68883-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="68883-247">Из AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="68883-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="68883-248">Это цикл «предвизуализации».</span><span class="sxs-lookup"><span data-stu-id="68883-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="68883-249">Здесь мы создадим в буфер перекрытия запросив сетки модуля подготовки отчетов к просмотру только глубины.</span><span class="sxs-lookup"><span data-stu-id="68883-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="68883-250">В этой конфигурации не Присоединяйте представления целевого объекта прорисовки и модуль подготовки отчетов сетки задает уровень построителя текстур пикселей **nullptr** таким образом, чтобы GPU не беспокоится Рисование пикселей.</span><span class="sxs-lookup"><span data-stu-id="68883-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="68883-251">Геометрия будет растровое буфер глубины, и существует остановит графического конвейера.</span><span class="sxs-lookup"><span data-stu-id="68883-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

<span data-ttu-id="68883-252">Можно провести голограммы с тестами дополнительный глубины для буфера перекрытия область сопоставления.</span><span class="sxs-lookup"><span data-stu-id="68883-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="68883-253">В этом примере кода мы построить пикселей на кубе другим цветом, если они находятся позади рабочую область.</span><span class="sxs-lookup"><span data-stu-id="68883-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="68883-254">Из AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="68883-254">From AppMain.cpp:</span></span>

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

<span data-ttu-id="68883-255">На основе кода из SpecialEffectPixelShader.hlsl:</span><span class="sxs-lookup"><span data-stu-id="68883-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

<span data-ttu-id="68883-256">**Примечание.** Для наших **GatherDepthLess** подпрограммы, см. в образце кода поверхность сопоставления: SpecialEffectPixelShader.hlsl.</span><span class="sxs-lookup"><span data-stu-id="68883-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="68883-257">**Данные отрисовки поверхности сетки для отображения**</span><span class="sxs-lookup"><span data-stu-id="68883-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="68883-258">Можно также просто провести поверхности сетки в стерео отображения буферы.</span><span class="sxs-lookup"><span data-stu-id="68883-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="68883-259">Мы выбрали для рисования полный лиц с помощью освещение, но вы можете рисования каркас, обрабатывать сеток перед отрисовкой, применить текстурной карты и т. д.</span><span class="sxs-lookup"><span data-stu-id="68883-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="68883-260">Здесь наш пример кода указывает модуль подготовки отчетов сетка для рисования в коллекцию.</span><span class="sxs-lookup"><span data-stu-id="68883-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="68883-261">Это время мы не указываем только для глубина прохода, поэтому он будет прикрепление шейдера пикселей и выполнения конвейера отрисовки, с помощью целевых объектов, которые мы указали для текущей виртуальной камеры.</span><span class="sxs-lookup"><span data-stu-id="68883-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a><span data-ttu-id="68883-262">См. также</span><span class="sxs-lookup"><span data-stu-id="68883-262">See also</span></span>
* [<span data-ttu-id="68883-263">Создание проекта holographic DirectX</span><span class="sxs-lookup"><span data-stu-id="68883-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="68883-264">Windows.Perception.Spatial API</span><span class="sxs-lookup"><span data-stu-id="68883-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
