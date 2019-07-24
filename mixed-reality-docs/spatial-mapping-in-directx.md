---
title: Пространственное сопоставление в DirectX
description: Объясняет, как реализовать пространственное сопоставление в приложении DirectX. Сюда входит подробное описание примера приложения пространственного сопоставления, которое входит в состав пакета SDK для универсальная платформа Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, пространственное сопоставление, среда, взаимодействие, DirectX, WinRT, API, пример кода, UWP, пакет SDK, пошаговое руководство
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550698"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="c0e81-105">Пространственное сопоставление в DirectX</span><span class="sxs-lookup"><span data-stu-id="c0e81-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="c0e81-106">В этом разделе описывается реализация [пространственного сопоставления](spatial-mapping.md) в приложении DirectX.</span><span class="sxs-lookup"><span data-stu-id="c0e81-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="c0e81-107">Сюда входит подробное описание примера приложения пространственного сопоставления, которое входит в состав пакета SDK для универсальная платформа Windows.</span><span class="sxs-lookup"><span data-stu-id="c0e81-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="c0e81-108">В этом разделе используется код из примера кода UWP для [холографикспатиалмаппинг](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .</span><span class="sxs-lookup"><span data-stu-id="c0e81-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="c0e81-109">Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="c0e81-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="c0e81-110">Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="c0e81-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="c0e81-111">Общие сведения о разработке DirectX</span><span class="sxs-lookup"><span data-stu-id="c0e81-111">DirectX development overview</span></span>

<span data-ttu-id="c0e81-112">При разработке собственного приложения для пространственного сопоставления используются интерфейсы API в пространстве имен [Windows. восприятие. пространственный.](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)</span><span class="sxs-lookup"><span data-stu-id="c0e81-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="c0e81-113">Эти API предоставляют полный контроль над функциями пространственного сопоставления, как и непосредственно аналогично API-интерфейсам пространственного сопоставления, предоставляемым [Unity](spatial-mapping-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="c0e81-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="c0e81-114">API-интерфейсы восприятия</span><span class="sxs-lookup"><span data-stu-id="c0e81-114">Perception APIs</span></span>

<span data-ttu-id="c0e81-115">Ниже приведены основные типы, предоставляемые для разработки пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="c0e81-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="c0e81-116">[Спатиалсурфацеобсервер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) предоставляет сведения о поверхностях в указанных в приложении областях пространства рядом с пользователем в виде объектов спатиалсурфацеинфо.</span><span class="sxs-lookup"><span data-stu-id="c0e81-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="c0e81-117">[Спатиалсурфацеинфо](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) описывает одну пространственно екстантную поверхность, включая уникальный идентификатор, связанный том и время последнего изменения.</span><span class="sxs-lookup"><span data-stu-id="c0e81-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="c0e81-118">Он предоставит Спатиалсурфацемеш асинхронно после запроса.</span><span class="sxs-lookup"><span data-stu-id="c0e81-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="c0e81-119">[Спатиалсурфацемешоптионс](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) содержит параметры, используемые для настройки объектов спатиалсурфацемеш, запрошенных из спатиалсурфацеинфо.</span><span class="sxs-lookup"><span data-stu-id="c0e81-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="c0e81-120">[Спатиалсурфацемеш](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) представляет данные сетки для отдельной пространственной поверхности.</span><span class="sxs-lookup"><span data-stu-id="c0e81-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="c0e81-121">Данные для позиций вершин, нормалей вершин и индексов треугольников содержатся в объектах-членах Спатиалсурфацемешбуффер.</span><span class="sxs-lookup"><span data-stu-id="c0e81-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="c0e81-122">[Спатиалсурфацемешбуффер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) заключает в оболочку один тип данных сетки.</span><span class="sxs-lookup"><span data-stu-id="c0e81-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="c0e81-123">При разработке приложения с использованием этих API основная последовательность программ будет выглядеть следующим образом (как показано в примере приложения, описанном ниже):</span><span class="sxs-lookup"><span data-stu-id="c0e81-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="c0e81-124">**Настройка Спатиалсурфацеобсервер**</span><span class="sxs-lookup"><span data-stu-id="c0e81-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="c0e81-125">Вызовите [рекуестакцессасинк](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), чтобы убедиться, что пользователь предоставил разрешение на использование возможностей пространственного сопоставления устройства.</span><span class="sxs-lookup"><span data-stu-id="c0e81-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="c0e81-126">Создайте экземпляр объекта Спатиалсурфацеобсервер.</span><span class="sxs-lookup"><span data-stu-id="c0e81-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="c0e81-127">Вызовите [сетбаундингволумес](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) , чтобы указать области пространства, в которых требуется получить сведения о пространственных поверхностях.</span><span class="sxs-lookup"><span data-stu-id="c0e81-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="c0e81-128">Вы можете изменить эти регионы в будущем, просто вызвав эту функцию еще раз.</span><span class="sxs-lookup"><span data-stu-id="c0e81-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="c0e81-129">Каждый регион указывается с помощью [спатиалбаундингволуме](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span><span class="sxs-lookup"><span data-stu-id="c0e81-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="c0e81-130">Зарегистрируйтесь на событие [обсерведсурфацесчанжед](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , которое будет срабатывать каждый раз, когда доступна новая информация о пространственных областях в указанных регионах.</span><span class="sxs-lookup"><span data-stu-id="c0e81-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="c0e81-131">**Обработка событий Обсерведсурфацесчанжед**</span><span class="sxs-lookup"><span data-stu-id="c0e81-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="c0e81-132">В обработчике событий вызовите [жетобсерведсурфацес](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) , чтобы получить карту объектов спатиалсурфацеинфо.</span><span class="sxs-lookup"><span data-stu-id="c0e81-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="c0e81-133">С помощью этой схемы можно обновить записи, для которых существуют пространственные поверхности [в среде пользователя](spatial-mapping.md#mesh-caching).</span><span class="sxs-lookup"><span data-stu-id="c0e81-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="c0e81-134">Для каждого объекта Спатиалсурфацеинфо можно запросить [трижетбаундс](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) , чтобы определить пространственные экстенты поверхности, выраженные в [пространственной системе координат](coordinate-systems.md) по вашему выбору.</span><span class="sxs-lookup"><span data-stu-id="c0e81-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="c0e81-135">Если вы решили запросить сетку для пространственной поверхности, вызовите [трикомпутелатестмешасинк](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="c0e81-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="c0e81-136">Вы можете указать параметры, задающие нужную плотность треугольников, и формат возвращаемых данных сетки.</span><span class="sxs-lookup"><span data-stu-id="c0e81-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="c0e81-137">**Сетка приема и обработки**</span><span class="sxs-lookup"><span data-stu-id="c0e81-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="c0e81-138">Каждый вызов Трикомпутелатестмешасинк будет айснчронаусли возвращать один объект Спатиалсурфацемеш.</span><span class="sxs-lookup"><span data-stu-id="c0e81-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="c0e81-139">Из этого объекта можно получить доступ к содержащимся объектам Спатиалсурфацемешбуффер, чтобы получить доступ к индексам треугольника, позициям вершин и (при запросе) нормалям вершин сетки.</span><span class="sxs-lookup"><span data-stu-id="c0e81-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="c0e81-140">Эти данные будут в формате, непосредственно совместимом с [API-интерфейсами Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) , используемыми для отрисовки сеток.</span><span class="sxs-lookup"><span data-stu-id="c0e81-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="c0e81-141">Здесь приложение может при необходимости выполнять анализ или [обработку](spatial-mapping.md#mesh-processing) данных сетки, а также использовать их для [визуализации](spatial-mapping.md#rendering) и создания физических [райкастинг и конфликтов](spatial-mapping.md#raycasting-and-collision).</span><span class="sxs-lookup"><span data-stu-id="c0e81-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="c0e81-142">Важно отметить, что необходимо применить шкалу к позициям вершин сетки (например, в шейдере вершин, используемом для отрисовки сеток), чтобы преобразовать их из оптимизированных целых единиц, в которых они хранятся в буфере, на метры.</span><span class="sxs-lookup"><span data-stu-id="c0e81-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="c0e81-143">Эту шкалу можно получить, вызвав [вертекспоситионскале](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span><span class="sxs-lookup"><span data-stu-id="c0e81-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="c0e81-144">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="c0e81-144">Troubleshooting</span></span>
* <span data-ttu-id="c0e81-145">Не забудьте масштабировать позиции вершин сетки в шейдере вершин, используя шкалу, возвращенную [спатиалсурфацемеш. вертекспоситионскале](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="c0e81-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="c0e81-146">Пример пошагового руководства по коду пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="c0e81-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="c0e81-147">Пример кода для [пространственного сопоставления holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) включает в себя код, который можно использовать для начала загрузки сеток поверхности в приложение, включая инфраструктуру для управления и визуализации сеток поверхности.</span><span class="sxs-lookup"><span data-stu-id="c0e81-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="c0e81-148">Теперь мы пошаговым инструкциями по добавлению функции сопоставления поверхности в приложение DirectX.</span><span class="sxs-lookup"><span data-stu-id="c0e81-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="c0e81-149">Этот код можно добавить в проект [шаблона приложения Windows holographic](creating-a-holographic-directx-project.md) . Кроме того, можно выполнить действия, просмотрев приведенный выше пример кода.</span><span class="sxs-lookup"><span data-stu-id="c0e81-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="c0e81-150">Этот пример кода основан на шаблоне приложения Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="c0e81-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="c0e81-151">Настройка приложения для использования возможности Спатиалперцептион</span><span class="sxs-lookup"><span data-stu-id="c0e81-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="c0e81-152">Приложение должно иметь возможность использовать функцию пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="c0e81-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="c0e81-153">Это необходимо потому, что пространственный сетчатый объект представляет собой представление среды пользователя, которое может считаться частными данными.</span><span class="sxs-lookup"><span data-stu-id="c0e81-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="c0e81-154">Объявите эту возможность в файле Package. appxmanifest для приложения.</span><span class="sxs-lookup"><span data-stu-id="c0e81-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="c0e81-155">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="c0e81-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="c0e81-156">Эта возможность поступает из пространства имен **uap2** .</span><span class="sxs-lookup"><span data-stu-id="c0e81-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="c0e81-157">Чтобы получить доступ к этому пространству имен в манифесте, включите его  в качестве атрибута кслмнс &lt;в элемент Package >.</span><span class="sxs-lookup"><span data-stu-id="c0e81-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="c0e81-158">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="c0e81-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="c0e81-159">Проверка поддержки функции пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="c0e81-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="c0e81-160">Windows Mixed Reality поддерживает широкий спектр устройств, включая устройства, которые не поддерживают пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="c0e81-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="c0e81-161">Если приложение может использовать пространственное сопоставление или должно использовать пространственное сопоставление для обеспечения функциональности, оно должно проверить, поддерживается ли пространственное сопоставление, прежде чем пытаться его использовать.</span><span class="sxs-lookup"><span data-stu-id="c0e81-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="c0e81-162">Например, если для приложения смешанной реальности требуется пространственное сопоставление, оно должно отображать это сообщение, если пользователь пытается запустить его на устройстве без пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="c0e81-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="c0e81-163">Кроме того, приложение может визуализировать собственную виртуальную среду вместо среды пользователя, предоставляя возможности, аналогичные тому, что произойдет, если было доступно пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="c0e81-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="c0e81-164">В любом событии этот API позволяет приложению знать, когда не будет получать данные пространственного сопоставления и реагировать соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="c0e81-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="c0e81-165">Чтобы проверить наличие поддержки пространственного сопоставления на текущем устройстве, убедитесь, что контракт UWP имеет уровень 4 или выше и затем вызовите Спатиалсурфацеобсервер:: support ().</span><span class="sxs-lookup"><span data-stu-id="c0e81-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="c0e81-166">Вот как это сделать в контексте примера кода [пространственного пространственного сопоставления](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .</span><span class="sxs-lookup"><span data-stu-id="c0e81-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="c0e81-167">Поддержка проверяется непосредственно перед запросом доступа.</span><span class="sxs-lookup"><span data-stu-id="c0e81-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="c0e81-168">API Спатиалсурфацеобсервер:: support () доступен начиная с пакета SDK версии 15063.</span><span class="sxs-lookup"><span data-stu-id="c0e81-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="c0e81-169">При необходимости перецелевой проект до версии платформы 15063 перед использованием этого API.</span><span class="sxs-lookup"><span data-stu-id="c0e81-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="c0e81-170">Обратите внимание, что если контракт UWP меньше уровня 4, приложение должно продолжать работу так, как будто устройство поддерживает пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="c0e81-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="c0e81-171">Запрос доступа к данным пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="c0e81-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="c0e81-172">Приложение должно запросить разрешение на доступ к данным пространственного сопоставления, прежде чем пытаться создать любые наблюдатели Surface.</span><span class="sxs-lookup"><span data-stu-id="c0e81-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="c0e81-173">Ниже приведен пример, основанный на нашем примере кода сопоставления Surface, с дополнительными сведениями, приведенными далее на этой странице.</span><span class="sxs-lookup"><span data-stu-id="c0e81-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="c0e81-174">Создание наблюдателя Surface</span><span class="sxs-lookup"><span data-stu-id="c0e81-174">Create a surface observer</span></span>

<span data-ttu-id="c0e81-175">Пространство имен **Windows::P ерцептион:: spatial::** Surfaces включает класс [спатиалсурфацеобсервер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) , который следит за одним или несколькими томами, указанными в [спатиалкурдинатесистем](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span><span class="sxs-lookup"><span data-stu-id="c0e81-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="c0e81-176">Используйте экземпляр [спатиалсурфацеобсервер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) для доступа к данным сетки Surface в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="c0e81-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="c0e81-177">Из **аппмаин. h**:</span><span class="sxs-lookup"><span data-stu-id="c0e81-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="c0e81-178">Как отмечалось в предыдущем разделе, необходимо запросить доступ к данным пространственного сопоставления, прежде чем приложение сможет его использовать.</span><span class="sxs-lookup"><span data-stu-id="c0e81-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="c0e81-179">Этот доступ предоставляется автоматически на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c0e81-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="c0e81-180">Далее необходимо настроить наблюдатель поверхности для наблюдения за конкретным ограничивающим томом.</span><span class="sxs-lookup"><span data-stu-id="c0e81-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="c0e81-181">Здесь мы наблюдаем поле, 20x20x5 измерительные приборы, центрированные по отношению к координатам системы координат.</span><span class="sxs-lookup"><span data-stu-id="c0e81-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="c0e81-182">Обратите внимание, что вместо этого можно задать несколько ограничивающих томов.</span><span class="sxs-lookup"><span data-stu-id="c0e81-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="c0e81-183">*Это псевдокод:*</span><span class="sxs-lookup"><span data-stu-id="c0e81-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="c0e81-184">Также можно использовать другие ограничивающие фигуры, такие как представление фрустум, или ограничивающий прямоугольник, не выравниваемая по осям.</span><span class="sxs-lookup"><span data-stu-id="c0e81-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="c0e81-185">*Это псевдокод:*</span><span class="sxs-lookup"><span data-stu-id="c0e81-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="c0e81-186">Если приложение должно выполнять какие-либо действия, если данные сопоставления поверхности недоступны, можно написать код для реагирования на случай, когда [спатиалперцептионакцессстатус](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) не **разрешен** — например, он не будет разрешен на компьютерах с иммерсивное устройства подключены, так как эти устройства не имеют оборудования для пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="c0e81-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="c0e81-187">Для этих устройств следует использовать пространственный этап для получения сведений о среде пользователя и конфигурации устройства.</span><span class="sxs-lookup"><span data-stu-id="c0e81-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="c0e81-188">Инициализация и обновление коллекции сеток поверхности</span><span class="sxs-lookup"><span data-stu-id="c0e81-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="c0e81-189">Если наблюдатель Surface был успешно создан, мы можем приступить к инициализации коллекции посети Surface.</span><span class="sxs-lookup"><span data-stu-id="c0e81-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="c0e81-190">Здесь мы используем API модели извлечения для немедленного получения текущего набора наблюдаемых поверхностей:</span><span class="sxs-lookup"><span data-stu-id="c0e81-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="c0e81-191">Существует также модель push-уведомлений, доступная для получения данных о сетке поверхности.</span><span class="sxs-lookup"><span data-stu-id="c0e81-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="c0e81-192">Вы можете разрабатывать приложение для использования только модели извлечения, если выбрать, в этом случае вы будете опрашивать данные каждые часто, например, один раз в кадре или в течение определенного периода времени, как во время настройки игры.</span><span class="sxs-lookup"><span data-stu-id="c0e81-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="c0e81-193">В этом случае приведенный выше код является необходимым.</span><span class="sxs-lookup"><span data-stu-id="c0e81-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="c0e81-194">В нашем примере кода мы решили продемонстрировать использование обеих моделей для воспитательный целей.</span><span class="sxs-lookup"><span data-stu-id="c0e81-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="c0e81-195">Здесь мы подписались на событие, чтобы получить актуальные данные о сетке поверхности всякий раз, когда система распознает изменение.</span><span class="sxs-lookup"><span data-stu-id="c0e81-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="c0e81-196">Наш пример кода также настроен для реагирования на эти события.</span><span class="sxs-lookup"><span data-stu-id="c0e81-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="c0e81-197">Давайте подробно рассмотрим, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="c0e81-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="c0e81-198">**ПРИМЕЧАНИЕ.** Это может быть не самым эффективным способом для работы приложения с данными сетки.</span><span class="sxs-lookup"><span data-stu-id="c0e81-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="c0e81-199">Этот код написан для ясности и не оптимизирован.</span><span class="sxs-lookup"><span data-stu-id="c0e81-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="c0e81-200">Данные сетки поверхности предоставляются в карте только для чтения, в которой хранятся объекты [спатиалсурфацеинфо](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) с использованием [Platform:: GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) в качестве значений ключа.</span><span class="sxs-lookup"><span data-stu-id="c0e81-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="c0e81-201">Для обработки этих данных сначала мы рассмотрим значения ключей, которых нет в нашей коллекции.</span><span class="sxs-lookup"><span data-stu-id="c0e81-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="c0e81-202">Сведения о том, как данные хранятся в нашем примере приложения, будут представлены далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="c0e81-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="c0e81-203">Также необходимо удалить сети Surface, которые находятся в коллекции посетей, но больше нет в коллекции систем.</span><span class="sxs-lookup"><span data-stu-id="c0e81-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="c0e81-204">Для этого необходимо сделать что-то на противоположное, что было показано для добавления и обновления сеток; Мы выполним цикл по сбору нашего приложения и проверяем, есть ли **идентификатор GUID** в коллекции системы.</span><span class="sxs-lookup"><span data-stu-id="c0e81-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="c0e81-205">Если он отсутствует в системной коллекции, мы удалим его из нашей.</span><span class="sxs-lookup"><span data-stu-id="c0e81-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="c0e81-206">Из нашего обработчика событий в Аппмаин. cpp:</span><span class="sxs-lookup"><span data-stu-id="c0e81-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="c0e81-207">Реализация удаления сетки в Реалтимесурфацемешрендерер. cpp:</span><span class="sxs-lookup"><span data-stu-id="c0e81-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="c0e81-208">Получение и использование буферов данных для сетки поверхности</span><span class="sxs-lookup"><span data-stu-id="c0e81-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="c0e81-209">Получение сведений о сетке поверхности было так же простым, как извлечение коллекции данных и обработка обновлений в этой коллекции.</span><span class="sxs-lookup"><span data-stu-id="c0e81-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="c0e81-210">Теперь мы подробно рассмотрим, как можно использовать данные.</span><span class="sxs-lookup"><span data-stu-id="c0e81-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="c0e81-211">В нашем примере кода мы решили использовать сетки Surface для отрисовки.</span><span class="sxs-lookup"><span data-stu-id="c0e81-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="c0e81-212">Это распространенный сценарий для окклудингных голограмм, стоящих за реальными областями.</span><span class="sxs-lookup"><span data-stu-id="c0e81-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="c0e81-213">Можно также визуализировать сетки или визуализировать обработанные версии, чтобы увидеть, какие области комнаты просматриваются, прежде чем приступить к работе с функциями приложения или игры.</span><span class="sxs-lookup"><span data-stu-id="c0e81-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="c0e81-214">Пример кода запускает процесс при получении обновлений сетки Surface из обработчика событий, описанного в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="c0e81-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="c0e81-215">Важной строкой кода в этой функции является вызов обновления *сетки*поверхности: на этот раз мы уже обработали сведения о сетке, и мы будем получать данные об вершинах и индексах, которые будут использоваться, как видно.</span><span class="sxs-lookup"><span data-stu-id="c0e81-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="c0e81-216">Из Реалтимесурфацемешрендерер. cpp:</span><span class="sxs-lookup"><span data-stu-id="c0e81-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="c0e81-217">Наш пример кода разработан таким образом, что класс данных **сурфацемеш**обрабатывает обработку и отрисовку данных в сети.</span><span class="sxs-lookup"><span data-stu-id="c0e81-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="c0e81-218">Эти сетки — это то, что **реалтимесурфацемешрендерер** на самом деле сохраняет карту.</span><span class="sxs-lookup"><span data-stu-id="c0e81-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="c0e81-219">У каждого из них есть ссылка на Спатиалсурфацемеш, и мы используем его в любой момент, когда нам нужно получить доступ к вершинной сетке или буферу индексов или получить преобразование для сетки.</span><span class="sxs-lookup"><span data-stu-id="c0e81-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="c0e81-220">Сейчас мы помечаем сетку как требующую обновления.</span><span class="sxs-lookup"><span data-stu-id="c0e81-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="c0e81-221">Из Сурфацемеш. cpp:</span><span class="sxs-lookup"><span data-stu-id="c0e81-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="c0e81-222">В следующий раз, когда сетка получит запрос на прорисовку, сначала будет проверяться флаг.</span><span class="sxs-lookup"><span data-stu-id="c0e81-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="c0e81-223">Если требуется обновление, буферы вершин и индексов будут обновлены на GPU.</span><span class="sxs-lookup"><span data-stu-id="c0e81-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="c0e81-224">Сначала мы получаем необработанные буферы данных:</span><span class="sxs-lookup"><span data-stu-id="c0e81-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="c0e81-225">Затем мы создадим буферы устройств Direct3D с данными сетки, предоставляемыми HoloLens:</span><span class="sxs-lookup"><span data-stu-id="c0e81-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="c0e81-226">**ПРИМЕЧАНИЕ.** Сведения о вспомогательной функции Креатедиректксбуффер, используемой в предыдущем фрагменте, см. в примере кода сопоставления Surface: Сурфацемеш. cpp, Жетдатафромибуффер. h.</span><span class="sxs-lookup"><span data-stu-id="c0e81-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="c0e81-227">Теперь создание ресурса устройства завершено, и сетка считается загруженной и готова к обновлению и визуализации.</span><span class="sxs-lookup"><span data-stu-id="c0e81-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="c0e81-228">Обновление и отрисовка сеток поверхности</span><span class="sxs-lookup"><span data-stu-id="c0e81-228">Update and render surface meshes</span></span>

<span data-ttu-id="c0e81-229">Наш класс Сурфацемеш имеет специализированную функцию Update.</span><span class="sxs-lookup"><span data-stu-id="c0e81-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="c0e81-230">Каждый [спатиалсурфацемеш](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) имеет собственное преобразование, и в нашем примере используется текущая система координат для **спатиалстатионариреференцефраме** , чтобы получить преобразование.</span><span class="sxs-lookup"><span data-stu-id="c0e81-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="c0e81-231">Затем он обновляет буфер констант модели на GPU.</span><span class="sxs-lookup"><span data-stu-id="c0e81-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="c0e81-232">Когда вы намерены приступить к отрисовке сеток Surface, мы выполняем некоторые подготовительные действия перед отрисовкой коллекции.</span><span class="sxs-lookup"><span data-stu-id="c0e81-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="c0e81-233">Мы настроили конвейер шейдера для текущей конфигурации подготовки к просмотру и настроили этап ассемблера входных данных.</span><span class="sxs-lookup"><span data-stu-id="c0e81-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="c0e81-234">Обратите внимание, что класс модуля поддержки holographic Camera **камераресаурцес. cpp** уже настроил буфер констант представления/проекции прямо сейчас.</span><span class="sxs-lookup"><span data-stu-id="c0e81-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="c0e81-235">Из **реалтимесурфацемешрендерер:: Render**:</span><span class="sxs-lookup"><span data-stu-id="c0e81-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="c0e81-236">По завершении этого цикла мы рассмотрим наши сети и поговорю, что каждый из них будет нарисован.</span><span class="sxs-lookup"><span data-stu-id="c0e81-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="c0e81-237">**ПРИМЕЧАНИЕ.** Этот пример кода не оптимизирован для использования какого-либо рода фрустумного отбора, но эту функцию следует включить в приложение.</span><span class="sxs-lookup"><span data-stu-id="c0e81-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="c0e81-238">Отдельные сети отвечают за настройку буферов вершин и индексов, а также буфера констант и преобразования модели.</span><span class="sxs-lookup"><span data-stu-id="c0e81-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="c0e81-239">Как и в случае вращающегося куба в шаблоне приложения Windows holographic, мы подготавливаем буферы стереоскопик с помощью создания экземпляров.</span><span class="sxs-lookup"><span data-stu-id="c0e81-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="c0e81-240">Из **сурфацемеш::D RAW**:</span><span class="sxs-lookup"><span data-stu-id="c0e81-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="c0e81-241">Отрисовка вариантов с помощью сопоставления поверхности</span><span class="sxs-lookup"><span data-stu-id="c0e81-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="c0e81-242">Пример кода сопоставления Surface предлагает код для отрисовки данных в виде сетки поверхности перекрытия, а также для отображения данных в сетке поверхности на экране.</span><span class="sxs-lookup"><span data-stu-id="c0e81-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="c0e81-243">Выбор пути зависит от приложения.</span><span class="sxs-lookup"><span data-stu-id="c0e81-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="c0e81-244">В этом документе мы рассмотрим обе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c0e81-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="c0e81-245">**Отрисовка буферов перекрытия для holographic Effect**</span><span class="sxs-lookup"><span data-stu-id="c0e81-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="c0e81-246">Начните с очистки представления целевого объекта прорисовки для текущей виртуальной камеры.</span><span class="sxs-lookup"><span data-stu-id="c0e81-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="c0e81-247">Из Аппмаин. cpp:</span><span class="sxs-lookup"><span data-stu-id="c0e81-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="c0e81-248">Это этап предварительной отрисовки.</span><span class="sxs-lookup"><span data-stu-id="c0e81-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="c0e81-249">Здесь мы создадим буфер перекрытия, запросив для модуля подготовки к сетке глубину прорисовки только глубины.</span><span class="sxs-lookup"><span data-stu-id="c0e81-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="c0e81-250">В этой конфигурации мы не подключим представление целевого объекта прорисовки, и модуль визуализации сетки задает для этапа Шейдер пикселей значение **nullptr** , чтобы GPU не проводился для рисования пикселей.</span><span class="sxs-lookup"><span data-stu-id="c0e81-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="c0e81-251">Геометрия будет помещена в буфер глубины, а графический конвейер будет останавливаться.</span><span class="sxs-lookup"><span data-stu-id="c0e81-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="c0e81-252">Мы можем нарисовать голограммы с дополнительным тестом глубины по отношению к буферу сопоставления поверхности перекрытия.</span><span class="sxs-lookup"><span data-stu-id="c0e81-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="c0e81-253">В этом примере кода выполняется отрисовка пикселов в Кубе по другому цвету, если они находятся за поверхностью.</span><span class="sxs-lookup"><span data-stu-id="c0e81-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="c0e81-254">Из Аппмаин. cpp:</span><span class="sxs-lookup"><span data-stu-id="c0e81-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="c0e81-255">На основе кода из СпеЦиалеффектпикселшадер. HLSL:</span><span class="sxs-lookup"><span data-stu-id="c0e81-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="c0e81-256">**Примечание.** Сведения о нашей подпрограмме **гасердепслесс** см. в примере кода сопоставления Surface: СпеЦиалеффектпикселшадер. HLSL.</span><span class="sxs-lookup"><span data-stu-id="c0e81-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="c0e81-257">**Отображение данных сетки поверхности для отображения**</span><span class="sxs-lookup"><span data-stu-id="c0e81-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="c0e81-258">Кроме того, можно просто нарисовать сетки Surface в экранных буферах вывода.</span><span class="sxs-lookup"><span data-stu-id="c0e81-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="c0e81-259">Мы решили нарисовать полные лица с освещением, но вы можете рисовать каркасную схему, обработать сетки перед отрисовкой, применить текстурную карту и т. д.</span><span class="sxs-lookup"><span data-stu-id="c0e81-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="c0e81-260">Здесь наш пример кода указывает, что модуль подготовки сетки рисует коллекцию.</span><span class="sxs-lookup"><span data-stu-id="c0e81-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="c0e81-261">На этот раз мы не будем указывать проход только по глубине, поэтому он присоединяет шейдер пикселей и завершает конвейер отрисовки, используя целевые объекты, которые мы указали для текущей виртуальной камеры.</span><span class="sxs-lookup"><span data-stu-id="c0e81-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c0e81-262">См. также</span><span class="sxs-lookup"><span data-stu-id="c0e81-262">See also</span></span>
* [<span data-ttu-id="c0e81-263">Создание голографического проекта в DirectX</span><span class="sxs-lookup"><span data-stu-id="c0e81-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="c0e81-264">API Windows. восприятие. пространственный</span><span class="sxs-lookup"><span data-stu-id="c0e81-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
