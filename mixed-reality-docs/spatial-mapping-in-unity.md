---
title: Пространственное сопоставление в Unity
description: Визуализация и конфликт с реальной геометрией в Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, пространственное сопоставление, модуль подготовки отчетов, средство обнаружения, сетка, сканирование, компонент
ms.openlocfilehash: 452e629a877df585ffbc0a6466ffeb2588b66ecf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438035"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="e47bd-104">Пространственное сопоставление в Unity</span><span class="sxs-lookup"><span data-stu-id="e47bd-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="e47bd-105">В этом разделе описывается использование [пространственного сопоставления](spatial-mapping.md) в проекте Unity, получение сеток треугольников, представляющих поверхности мира на устройстве HoloLens, для размещения, перекрытия, анализа комнаты и т. д.</span><span class="sxs-lookup"><span data-stu-id="e47bd-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="e47bd-106">Unity включает полную поддержку пространственного сопоставления, которое предоставляется разработчикам следующими способами:</span><span class="sxs-lookup"><span data-stu-id="e47bd-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="e47bd-107">Компоненты пространственного сопоставления, доступные в Микседреалититулкит, которые предоставляют удобный и быстрый путь для начала работы с пространственным сопоставлением.</span><span class="sxs-lookup"><span data-stu-id="e47bd-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="e47bd-108">API-интерфейсы пространственного сопоставления нижнего уровня, обеспечивающие полный контроль и обеспечивающие более сложную настройку приложений.</span><span class="sxs-lookup"><span data-stu-id="e47bd-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="e47bd-109">Чтобы использовать пространственное сопоставление в приложении, в AppxManifest необходимо задать возможность Спатиалперцептион.</span><span class="sxs-lookup"><span data-stu-id="e47bd-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="e47bd-110">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="e47bd-110">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e47bd-111"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="e47bd-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="e47bd-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e47bd-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e47bd-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e47bd-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e47bd-114"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="e47bd-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e47bd-115">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="e47bd-115">Spatial mapping</span></span></td>
        <td><span data-ttu-id="e47bd-116">✔️</span><span class="sxs-lookup"><span data-stu-id="e47bd-116">✔️</span></span></td>
        <td><span data-ttu-id="e47bd-117">✔️</span><span class="sxs-lookup"><span data-stu-id="e47bd-117">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="e47bd-118">Настройка возможности Спатиалперцептион</span><span class="sxs-lookup"><span data-stu-id="e47bd-118">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="e47bd-119">Чтобы приложение использовало данные пространственного сопоставления, необходимо включить возможность Спатиалперцептион.</span><span class="sxs-lookup"><span data-stu-id="e47bd-119">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="e47bd-120">Как включить функцию Спатиалперцептион:</span><span class="sxs-lookup"><span data-stu-id="e47bd-120">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="e47bd-121">В редакторе Unity откройте панель **"Параметры проигрывателя"** (измените > параметры проекта > Player).</span><span class="sxs-lookup"><span data-stu-id="e47bd-121">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="e47bd-122">Перейдите на вкладку **"Магазин Windows"** .</span><span class="sxs-lookup"><span data-stu-id="e47bd-122">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="e47bd-123">Разверните узел **"Параметры публикации"** и проверьте возможность **"спатиалперцептион** " в списке **"возможности"** .</span><span class="sxs-lookup"><span data-stu-id="e47bd-123">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="e47bd-124">Обратите внимание, что если вы уже экспортировали проект Unity в решение Visual Studio, необходимо либо экспортировать в новую папку, либо вручную [установить эту возможность в appxmanifest в Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="e47bd-124">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="e47bd-125">Для пространственного сопоставления также требуется Maxversiontested укажите установленную по меньшей мере 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="e47bd-125">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="e47bd-126">В Visual Studio щелкните правой кнопкой мыши **Package. appxmanifest** в Обозреватель решений и выберите **Просмотреть код** .</span><span class="sxs-lookup"><span data-stu-id="e47bd-126">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="e47bd-127">Найдите строку с указанием **TargetDeviceFamily** и измените **maxversiontested укажите установленную = "10.0.10240.0"** на **maxversiontested укажите установленную = "10.0.10586.0"** .</span><span class="sxs-lookup"><span data-stu-id="e47bd-127">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="e47bd-128">**Сохраните** пакет. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="e47bd-128">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="e47bd-129">Начало работы с встроенными компонентами пространственного сопоставления Unity</span><span class="sxs-lookup"><span data-stu-id="e47bd-129">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="e47bd-130">Unity предлагает 2 компонента для простого добавления пространственного сопоставления в приложение, модуль **подготовки** к пространственному сопоставлению и средство **сопоставления пространственных сопоставлений**.</span><span class="sxs-lookup"><span data-stu-id="e47bd-130">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="e47bd-131">Модуль подготовки пространственных сопоставлений</span><span class="sxs-lookup"><span data-stu-id="e47bd-131">Spatial Mapping Renderer</span></span>

<span data-ttu-id="e47bd-132">Модуль подготовки пространственных сопоставлений позволяет визуализировать сетку пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="e47bd-132">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Модуль подготовки пространственных сопоставлений в Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="e47bd-134">Конфликт пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="e47bd-134">Spatial Mapping Collider</span></span>

<span data-ttu-id="e47bd-135">Механизм обработки пространственных сопоставлений позволяет взаимодействовать с данными (или символами), например физикой, с сеткой пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="e47bd-135">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Конфликт пространственного сопоставления в Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="e47bd-137">Использование встроенных компонентов пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="e47bd-137">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="e47bd-138">Вы можете добавить оба компонента в приложение, если вы хотите визуализировать и взаимодействовать с физическими областями.</span><span class="sxs-lookup"><span data-stu-id="e47bd-138">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="e47bd-139">Чтобы использовать эти два компонента в приложении Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="e47bd-139">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="e47bd-140">Выберите GameObject в центре области, в которой вы хотите определить сетки пространственных поверхностей.</span><span class="sxs-lookup"><span data-stu-id="e47bd-140">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="e47bd-141">В окне инспектора **добавьте компонент** > **XR** > **пространственное сопоставление** или модуль **подготовки пространственных сопоставлений**.</span><span class="sxs-lookup"><span data-stu-id="e47bd-141">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="e47bd-142">Дополнительные сведения об использовании этих компонентов можно найти на <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">сайте документации по Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="e47bd-142">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="e47bd-143">Переход за пределы встроенных компонентов пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="e47bd-143">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="e47bd-144">Эти компоненты упрощают перетаскивание, чтобы начать работу с пространственным сопоставлением.</span><span class="sxs-lookup"><span data-stu-id="e47bd-144">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="e47bd-145"> Если вы хотите продолжить, необходимо изучить два основных пути:</span><span class="sxs-lookup"><span data-stu-id="e47bd-145"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="e47bd-146">Чтобы выполнить собственную обработку сетки более низкого уровня, см. раздел, посвященный API сценария низкоуровневого пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="e47bd-146">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="e47bd-147">Сведения об анализе сетки более высокого уровня см. в разделе, посвященном библиотеке Спатиалундерстандинг в <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">микседреалититулкит</a>.</span><span class="sxs-lookup"><span data-stu-id="e47bd-147">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="e47bd-148">Использование API пространственного сопоставления Unity с низким уровнем</span><span class="sxs-lookup"><span data-stu-id="e47bd-148">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="e47bd-149">Если вам требуется больший контроль, чем с помощью компонентов средства визуализации пространственных сопоставлений и средства создания пространственных сопоставлений, можно использовать низкоуровневые API скрипта пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="e47bd-149">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="e47bd-150">**Пространство имен:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="e47bd-150">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="e47bd-151">**Типы**: *сурфацеобсервер*, *сурфацечанже*, *сурфацедата*, *сурфацеид*</span><span class="sxs-lookup"><span data-stu-id="e47bd-151">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="e47bd-152">Ниже приведена структура предлагаемого потока для приложения, использующего API-интерфейсы пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="e47bd-152">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="e47bd-153">Настройка Сурфацеобсервер (s)</span><span class="sxs-lookup"><span data-stu-id="e47bd-153">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="e47bd-154">Создайте экземпляр одного объекта Сурфацеобсервер для каждой определенной приложением области пространства, для которой требуются данные пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="e47bd-154">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="e47bd-155">Укажите регион пространства, в котором каждый объект Сурфацеобсервер будет предоставлять данные, вызвав либо Сетволумеассфере, Сетволумеасаксисалигнедбокс, Сетволумеасориентедбокс, либо SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="e47bd-155">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="e47bd-156">Можно переопределить область пространства в будущем, просто вызвав один из этих методов снова.</span><span class="sxs-lookup"><span data-stu-id="e47bd-156">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="e47bd-157">При вызове Сурфацеобсервер. Update () необходимо предоставить обработчик для каждой пространственной поверхности в регионе Сурфацеобсервер, для которого в системе пространственных сопоставлений есть новая информация.</span><span class="sxs-lookup"><span data-stu-id="e47bd-157">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="e47bd-158">Обработчик получает для одной пространственной поверхности:</span><span class="sxs-lookup"><span data-stu-id="e47bd-158">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="e47bd-159">Обработка изменений поверхности</span><span class="sxs-lookup"><span data-stu-id="e47bd-159">Handling Surface Changes</span></span>

<span data-ttu-id="e47bd-160">Существует несколько основных вариантов, которые необходимо решить.</span><span class="sxs-lookup"><span data-stu-id="e47bd-160">There are several main cases to handle.</span></span> <span data-ttu-id="e47bd-161">Добавленные & обновлены, которые могут использовать один и тот же путь к коду и удалены.</span><span class="sxs-lookup"><span data-stu-id="e47bd-161">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="e47bd-162">В добавленных & обновленных вариантах в примере мы добавим или получаем GameObject, представляющий эту сетку, из словаря, создадим Сурфацедата структуру с необходимыми компонентами, а затем вызываем Рекуестмешдатаасинк для заполнения GameObject данными сетки и расположение в сцене.</span><span class="sxs-lookup"><span data-stu-id="e47bd-162">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="e47bd-163">В удаленном варианте мы удаляем GameObject, представляющий эту сетку, из словаря и удалим ее.</span><span class="sxs-lookup"><span data-stu-id="e47bd-163">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="e47bd-164">Обработка данных готова</span><span class="sxs-lookup"><span data-stu-id="e47bd-164">Handling Data Ready</span></span>

<span data-ttu-id="e47bd-165">Обработчик Ондатареади получает объект Сурфацедата.</span><span class="sxs-lookup"><span data-stu-id="e47bd-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="e47bd-166">Ворлданчор, Мешфилтер и (необязательно) Мешколлидер объекты, которые он содержит, отражает Последнее состояние связанной пространственной поверхности.</span><span class="sxs-lookup"><span data-stu-id="e47bd-166">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="e47bd-167">При необходимости выполните анализ и (или) [обработку](spatial-mapping.md#mesh-processing) данных сетки, обратившись к элементу сетки объекта мешфилтер.</span><span class="sxs-lookup"><span data-stu-id="e47bd-167">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="e47bd-168">Отрисовка пространственной поверхности с помощью последней сети и (необязательно) используйте ее для физических конфликтов и райкастс.</span><span class="sxs-lookup"><span data-stu-id="e47bd-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="e47bd-169">Важно убедиться, что содержимое Сурфацедата не равно null.</span><span class="sxs-lookup"><span data-stu-id="e47bd-169">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="e47bd-170">Начать обработку обновлений</span><span class="sxs-lookup"><span data-stu-id="e47bd-170">Start processing on updates</span></span>

<span data-ttu-id="e47bd-171">Сурфацеобсервер. Update () следует вызывать при задержке, а не во всех кадрах.</span><span class="sxs-lookup"><span data-stu-id="e47bd-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="e47bd-172">Анализ сетки более высокого уровня: Спатиалундерстандинг</span><span class="sxs-lookup"><span data-stu-id="e47bd-172">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="e47bd-173"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Микседреалититулкит</a> — это набор полезных вспомогательных программ для holographic-приложений, созданных на основе интерфейсов API для в Holographic.</span><span class="sxs-lookup"><span data-stu-id="e47bd-173">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="e47bd-174">Пространственное понимание</span><span class="sxs-lookup"><span data-stu-id="e47bd-174">Spatial Understanding</span></span>

<span data-ttu-id="e47bd-175">При помещении голограмм в физический мир часто желательно выйти за пределы сетки и поверхностей пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="e47bd-175">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="e47bd-176">Когда размещение выполняется процедурно, желательно более высокий уровень понимания окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="e47bd-176">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="e47bd-177">Обычно это требует принятия решений о том, что такое этаж, потолк и стенки.</span><span class="sxs-lookup"><span data-stu-id="e47bd-177">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="e47bd-178">Кроме того, возможность оптимизации по набору ограничений на размещение позволяет определить наиболее подходящего физического расположения для holographic объектов.</span><span class="sxs-lookup"><span data-stu-id="e47bd-178">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="e47bd-179">Во время разработки Конкер и фрагментов асобо Studios столкнулись с этой проблемой, разрабатывая Поиск решения для комнаты для этой цели.</span><span class="sxs-lookup"><span data-stu-id="e47bd-179">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="e47bd-180">В каждой из этих игр были специфические потребности игр, но они являются общими основными ключевыми технологиями.</span><span class="sxs-lookup"><span data-stu-id="e47bd-180">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="e47bd-181">Библиотека Холотулкит. Спатиалундерстандинг инкапсулирует эту технологию, позволяя быстро находить пустые пробелы в стенах, размещать объекты в самом потолке, указывать место для размещения символа и множество других пространственных запросов.</span><span class="sxs-lookup"><span data-stu-id="e47bd-181">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="e47bd-182">Весь исходный код включен, что позволяет настроить его в своих целях и поделиться изменениями с сообществом.</span><span class="sxs-lookup"><span data-stu-id="e47bd-182">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="e47bd-183">Код для C++ поиска решения был заключен в БИБЛИОТЕКУ DLL UWP и предоставлен в Unity с помощью Drop в prefab, который содержится в микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="e47bd-183">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="e47bd-184">Основные сведения о модулях</span><span class="sxs-lookup"><span data-stu-id="e47bd-184">Understanding Modules</span></span>

<span data-ttu-id="e47bd-185">Существует три основных интерфейса, предоставляемых модулем: топология простых и пространственных запросов, форма для обнаружения объектов и поисковый запрос на размещение объектов для ограничений на размещение наборов объектов.</span><span class="sxs-lookup"><span data-stu-id="e47bd-185">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="e47bd-186">Каждый из них описан ниже.</span><span class="sxs-lookup"><span data-stu-id="e47bd-186">Each of these is described below.</span></span> <span data-ttu-id="e47bd-187">В дополнение к трем интерфейсам основного модуля можно использовать интерфейс приведения лучей, чтобы извлечь типы областей с тегами, а также можно скопировать пользовательскую сетку ватертигхт плайспаце.</span><span class="sxs-lookup"><span data-stu-id="e47bd-187">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="e47bd-188">Приведение лучей</span><span class="sxs-lookup"><span data-stu-id="e47bd-188">Ray Casting</span></span>

<span data-ttu-id="e47bd-189">После того как комната будет проверена и закончена, метки будут внутренне созданы для таких поверхностей, как этаж, потолк и стенки.</span><span class="sxs-lookup"><span data-stu-id="e47bd-189">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="e47bd-190">Функция "Плайспацерайкаст" принимает луч и возвращает, если луч конфликтует с известной поверхностью и, если да, сведения об этой поверхности в виде "Райкастресулт".</span><span class="sxs-lookup"><span data-stu-id="e47bd-190">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="e47bd-191">На внутреннем уровне райкаст вычисляются на основе вычисленного 8cm Куба Воксел представления плайспаце.</span><span class="sxs-lookup"><span data-stu-id="e47bd-191">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="e47bd-192">Каждый Воксел содержит набор элементов Surface с обработанными данными топологии (то есть сурфелс).</span><span class="sxs-lookup"><span data-stu-id="e47bd-192">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="e47bd-193">Сурфелс, содержащиеся в пересеченной ячейке Воксел, сравниваются с наиболее подходящим соответствием, используемым для поиска сведений о топологии.</span><span class="sxs-lookup"><span data-stu-id="e47bd-193">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="e47bd-194">Данные топологии содержат метки, возвращаемые в форме перечисления "Сурфацетипес", а также контактную зону для пересекающейся поверхности.</span><span class="sxs-lookup"><span data-stu-id="e47bd-194">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="e47bd-195">В примере Unity курсор приводится к каждому кадру.</span><span class="sxs-lookup"><span data-stu-id="e47bd-195">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="e47bd-196">Во – первых, от своих противоречией Unity.</span><span class="sxs-lookup"><span data-stu-id="e47bd-196">First, against Unity’s colliders.</span></span> <span data-ttu-id="e47bd-197">Во вторых, для представления о мировом представлении модуля.</span><span class="sxs-lookup"><span data-stu-id="e47bd-197">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="e47bd-198">И наконец, еще раз элементы пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e47bd-198">And finally, again UI elements.</span></span> <span data-ttu-id="e47bd-199">В этом приложении пользовательский интерфейс получает приоритет, далее понимание результата и, наконец, конфликтующие элементы Unity.</span><span class="sxs-lookup"><span data-stu-id="e47bd-199">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="e47bd-200">Сурфацетипе сообщается в виде текста рядом с курсором.</span><span class="sxs-lookup"><span data-stu-id="e47bd-200">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="e47bd-201">Тип поверхности ![обозначен рядом с курсором](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e47bd-201">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="e47bd-202">*Тип поверхности помечен рядом с курсором*</span><span class="sxs-lookup"><span data-stu-id="e47bd-202">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="e47bd-203">Запросы топологии</span><span class="sxs-lookup"><span data-stu-id="e47bd-203">Topology Queries</span></span>

<span data-ttu-id="e47bd-204">В библиотеке DLL диспетчер топологии обрабатывает метки среды.</span><span class="sxs-lookup"><span data-stu-id="e47bd-204">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="e47bd-205">Как упоминалось выше, большая часть данных хранится в сурфелс, содержащейся в томе Воксел.</span><span class="sxs-lookup"><span data-stu-id="e47bd-205">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="e47bd-206">Кроме того, структура "Плайспацеинфос" используется для хранения сведений о плайспаце, включая выравнивание по всему миру (Дополнительные сведения см. ниже), этаж и высоту потолка.</span><span class="sxs-lookup"><span data-stu-id="e47bd-206">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="e47bd-207">Эвристические методы используются для определения этажей, потолков и стен.</span><span class="sxs-lookup"><span data-stu-id="e47bd-207">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="e47bd-208">Например, крупнейшим является самая крупная и меньшая горизонтальная поверхность с более чем одной контактной областью m2.</span><span class="sxs-lookup"><span data-stu-id="e47bd-208">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="e47bd-209">Обратите внимание, что в процессе сканирования также используется путь к камере.</span><span class="sxs-lookup"><span data-stu-id="e47bd-209">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="e47bd-210">Подмножество запросов, предоставляемых диспетчером топологии, предоставляется через библиотеку DLL.</span><span class="sxs-lookup"><span data-stu-id="e47bd-210">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="e47bd-211">Доступны следующие запросы топологии.</span><span class="sxs-lookup"><span data-stu-id="e47bd-211">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="e47bd-212">Каждый запрос имеет набор параметров, относящихся к типу запроса.</span><span class="sxs-lookup"><span data-stu-id="e47bd-212">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="e47bd-213">В следующем примере пользователь указывает минимальную высоту, & ширину требуемого тома, минимальную высоту размещения выше пола и минимальный размер зазора перед томом.</span><span class="sxs-lookup"><span data-stu-id="e47bd-213">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="e47bd-214">Все измерения задаются в метрах.</span><span class="sxs-lookup"><span data-stu-id="e47bd-214">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="e47bd-215">Каждый из этих запросов принимает предварительно выделенный массив структур "Топологиресулт".</span><span class="sxs-lookup"><span data-stu-id="e47bd-215">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="e47bd-216">Параметр "Локатионкаунт" задает длину переданного массива.</span><span class="sxs-lookup"><span data-stu-id="e47bd-216">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="e47bd-217">Возвращаемое значение сообщает о количестве возвращенных расположений.</span><span class="sxs-lookup"><span data-stu-id="e47bd-217">The return value reports the number of returned locations.</span></span> <span data-ttu-id="e47bd-218">Это число никогда не превышает значение, переданное параметром "Локатионкаунт".</span><span class="sxs-lookup"><span data-stu-id="e47bd-218">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="e47bd-219">"Топологиресулт" содержит центральную точку возвращенного тома, направление (то есть нормальное) и размеры найденного пространства.</span><span class="sxs-lookup"><span data-stu-id="e47bd-219">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="e47bd-220">Обратите внимание, что в примере Unity каждый из этих запросов связан с кнопкой на панели виртуального интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e47bd-220">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="e47bd-221">Пример жестко кодирует параметры для каждого из этих запросов в разумные значения.</span><span class="sxs-lookup"><span data-stu-id="e47bd-221">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="e47bd-222">Дополнительные примеры см. в разделе SpaceVisualizer.cs в примере кода.</span><span class="sxs-lookup"><span data-stu-id="e47bd-222">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="e47bd-223">Запросы фигур</span><span class="sxs-lookup"><span data-stu-id="e47bd-223">Shape Queries</span></span>

<span data-ttu-id="e47bd-224">В библиотеке DLL анализатор форм ("ShapeAnalyzer_W") использует анализатор топологии для сопоставления с пользовательскими фигурами, определенными пользователем.</span><span class="sxs-lookup"><span data-stu-id="e47bd-224">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="e47bd-225">Образец Unity определяет набор фигур и предоставляет результаты из меню запросов в приложении на вкладке Shape. Цель состоит в том, что пользователь может определить собственные запросы фигур объектов и использовать их в соответствии с потребностями приложения.</span><span class="sxs-lookup"><span data-stu-id="e47bd-225">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="e47bd-226">Обратите внимание, что анализ фигур работает только на горизонтальных поверхностях.</span><span class="sxs-lookup"><span data-stu-id="e47bd-226">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="e47bd-227">Например, диван определяется поверхностью плоского места и плоской вершиной на диване.</span><span class="sxs-lookup"><span data-stu-id="e47bd-227">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="e47bd-228">Запрос Shape выполняет поиск двух поверхностей определенного размера, высоты и пропорций, при этом две поверхности Выровняйте и соединены.</span><span class="sxs-lookup"><span data-stu-id="e47bd-228">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="e47bd-229">Используя терминологию API, место в диване и задняя часть являются компонентами фигур, а требования к выравниванию — к ограничениям компонентов.</span><span class="sxs-lookup"><span data-stu-id="e47bd-229">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="e47bd-230">Пример запроса, определенный в примере Unity (ShapeDefinition.cs) для объектов "ситтабле", выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="e47bd-230">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="e47bd-231">Каждый запрос Shape определяется набором компонентов Shape, каждый из которых имеет набор ограничений компонента и набор ограничений фигуры, в котором перечисляются зависимости между компонентами.</span><span class="sxs-lookup"><span data-stu-id="e47bd-231">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="e47bd-232">Этот пример включает три ограничения в определении одного компонента и не имеет ограничений фигур между компонентами (так как существует только один компонент).</span><span class="sxs-lookup"><span data-stu-id="e47bd-232">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="e47bd-233">Напротив, фигура дивана имеет два компонента фигур и четыре ограничения фигуры.</span><span class="sxs-lookup"><span data-stu-id="e47bd-233">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="e47bd-234">Обратите внимание, что компоненты определяются по индексу в списке компонентов пользователя (в этом примере 0 и 1).</span><span class="sxs-lookup"><span data-stu-id="e47bd-234">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="e47bd-235">Функции-оболочки предоставляются в модуле Unity для простого создания пользовательских определений фигур.</span><span class="sxs-lookup"><span data-stu-id="e47bd-235">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="e47bd-236">Полный список ограничений для компонентов и фигур можно найти в "SpatialUnderstandingDll.cs" в структурах "Шапекомпонентконстраинт" и "Шапеконстраинт".</span><span class="sxs-lookup"><span data-stu-id="e47bd-236">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="e47bd-237">![фигурный прямоугольник находится на этой поверхности](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e47bd-237">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="e47bd-238">*Фигура прямоугольника находится на этой поверхности*</span><span class="sxs-lookup"><span data-stu-id="e47bd-238">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="e47bd-239">Поиск решения о размещении объектов</span><span class="sxs-lookup"><span data-stu-id="e47bd-239">Object Placement Solver</span></span>

<span data-ttu-id="e47bd-240">Поиск по месту размещения объектов можно использовать для обнаружения идеального расположения в физической комнате для размещения объектов.</span><span class="sxs-lookup"><span data-stu-id="e47bd-240">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="e47bd-241">Поиск решения позволяет найти оптимальное расположение с учетом правил и ограничений объекта.</span><span class="sxs-lookup"><span data-stu-id="e47bd-241">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="e47bd-242">Кроме того, запросы объектов сохраняются до тех пор, пока объект не будет удален с помощью вызовов "Solver_RemoveObject" или "Solver_RemoveAllObjects", что позволяет ограничить размещение нескольких объектов.</span><span class="sxs-lookup"><span data-stu-id="e47bd-242">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="e47bd-243">Запросы размещения объектов состоят из трех частей: тип размещения с параметрами, список правил и список ограничений.</span><span class="sxs-lookup"><span data-stu-id="e47bd-243">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="e47bd-244">Чтобы выполнить запрос, используйте следующий API.</span><span class="sxs-lookup"><span data-stu-id="e47bd-244">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="e47bd-245">Эта функция принимает имя объекта, определение размещения и список правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="e47bd-245">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="e47bd-246">C# Оболочки предоставляют вспомогательные функции конструирования для упрощения создания правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="e47bd-246">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="e47bd-247">Определение размещения содержит тип запроса, то есть один из следующих элементов.</span><span class="sxs-lookup"><span data-stu-id="e47bd-247">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
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

<span data-ttu-id="e47bd-248">Каждый из типов размещения имеет набор параметров, уникальных для данного типа.</span><span class="sxs-lookup"><span data-stu-id="e47bd-248">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="e47bd-249">Структура "Обжектплацементдефинитион" содержит набор статических вспомогательных функций для создания этих определений.</span><span class="sxs-lookup"><span data-stu-id="e47bd-249">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="e47bd-250">Например, чтобы найти место для размещения объекта в этаже, можно использовать следующую функцию.</span><span class="sxs-lookup"><span data-stu-id="e47bd-250">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="e47bd-251">общедоступная статическая Обжектплацементдефинитион Create_OnFloor (Vector3 Халфдимс) в дополнение к типу размещения можно предоставить набор правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="e47bd-251">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="e47bd-252">Правила не могут быть нарушены.</span><span class="sxs-lookup"><span data-stu-id="e47bd-252">Rules cannot be violated.</span></span> <span data-ttu-id="e47bd-253">Возможные расположения размещения, которые соответствуют типу и правилам, оптимизируются по набору ограничений, чтобы выбрать оптимальное расположение размещения.</span><span class="sxs-lookup"><span data-stu-id="e47bd-253">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="e47bd-254">Каждое из правил и ограничений можно создать с помощью предоставленных статических функций создания.</span><span class="sxs-lookup"><span data-stu-id="e47bd-254">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="e47bd-255">Ниже приведен пример функции конструирования правила и ограничения.</span><span class="sxs-lookup"><span data-stu-id="e47bd-255">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="e47bd-256">Приведенный ниже запрос на размещение объекта ищет место для размещения полугодового Куба на границе поверхности, от других ранее размещенных объектов и вблизи центра комнаты.</span><span class="sxs-lookup"><span data-stu-id="e47bd-256">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
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

<span data-ttu-id="e47bd-257">В случае успешного выполнения возвращается структура "Обжектплацементресулт", содержащая положение размещения, размеры и ориентацию.</span><span class="sxs-lookup"><span data-stu-id="e47bd-257">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="e47bd-258">Кроме того, размещение добавляется в внутренний список размещенных объектов библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="e47bd-258">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="e47bd-259">При последующих запросах на размещение этот объект учитывается.</span><span class="sxs-lookup"><span data-stu-id="e47bd-259">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="e47bd-260">Файл "LevelSolver.cs" в образце Unity содержит дополнительные примеры запросов.</span><span class="sxs-lookup"><span data-stu-id="e47bd-260">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="e47bd-261">![результаты размещения объектов](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e47bd-261">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="e47bd-262">*Рис. 3. синий прямоугольник, посвященный результату из трех мест в запросах к этаже от правил размещения камеры*</span><span class="sxs-lookup"><span data-stu-id="e47bd-262">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="e47bd-263">При решении для размещения нескольких объектов, необходимых для сценария уровня или приложения, сначала решите ненужные и крупные объекты, чтобы максимально эффективно обнаружить место.</span><span class="sxs-lookup"><span data-stu-id="e47bd-263">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="e47bd-264">Порядок размещения важен.</span><span class="sxs-lookup"><span data-stu-id="e47bd-264">Placement order is important.</span></span> <span data-ttu-id="e47bd-265">Если размещение объектов не найдено, попробуйте уменьшить количество ограниченных конфигураций.</span><span class="sxs-lookup"><span data-stu-id="e47bd-265">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="e47bd-266">Наличие набора резервных конфигураций крайне важно для поддержки функциональных возможностей во многих конфигурациях комнаты.</span><span class="sxs-lookup"><span data-stu-id="e47bd-266">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="e47bd-267">Процесс сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="e47bd-267">Room Scanning Process</span></span>

<span data-ttu-id="e47bd-268">Хотя решение для пространственного сопоставления, предоставляемое HoloLens, достаточно универсально для удовлетворения потребностей всего спектра проблемных пространств, модуль пространственного понимания был разработан для поддержки потребностей двух конкретных игр.</span><span class="sxs-lookup"><span data-stu-id="e47bd-268">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="e47bd-269">Его решение структурировано на основе определенного процесса и набора допущений, приведенных ниже.</span><span class="sxs-lookup"><span data-stu-id="e47bd-269">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="e47bd-270">Пользователь, плайспаце "Рисование" — на этапе сканирования пользователь перемещает и просматривает темпы воспроизведения, эффективно вырисуя области, которые должны быть добавлены.</span><span class="sxs-lookup"><span data-stu-id="e47bd-270">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="e47bd-271">Созданная сетка важна для предоставления отзывов пользователей на этом этапе.</span><span class="sxs-lookup"><span data-stu-id="e47bd-271">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="e47bd-272">Настройка домашних и офисных задвижок — функции запросов разрабатываются вокруг плоских поверхностей и стен в правой части.</span><span class="sxs-lookup"><span data-stu-id="e47bd-272">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="e47bd-273">Это мягкое ограничение.</span><span class="sxs-lookup"><span data-stu-id="e47bd-273">This is a soft limitation.</span></span> <span data-ttu-id="e47bd-274">Однако на этапе сканирования выполняется анализ основной оси для оптимизации тесселяции сетки вдоль основной и вспомогательной осей.</span><span class="sxs-lookup"><span data-stu-id="e47bd-274">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="e47bd-275">Прилагаемый файл SpatialUnderstanding.cs управляет процессом этапа сканирования.</span><span class="sxs-lookup"><span data-stu-id="e47bd-275">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="e47bd-276">Он вызывает следующие функции.</span><span class="sxs-lookup"><span data-stu-id="e47bd-276">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="e47bd-277">Поток сканирования, управляемый поведением "Спатиалундерстандинг", вызывает Инитскан, а затем Упдатескан каждый кадр.</span><span class="sxs-lookup"><span data-stu-id="e47bd-277">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="e47bd-278">Когда статистический запрос сообщает о разумном покрытии, пользователю разрешается аиртап вызывать Рекуестфиниш, чтобы обозначить окончание этапа сканирования.</span><span class="sxs-lookup"><span data-stu-id="e47bd-278">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="e47bd-279">Упдатескан будет вызываться до тех пор, пока не будет возвращено значение, указывающее, что библиотека DLL завершила обработку.</span><span class="sxs-lookup"><span data-stu-id="e47bd-279">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="e47bd-280">Общие сведения о сетке</span><span class="sxs-lookup"><span data-stu-id="e47bd-280">Understanding Mesh</span></span>

<span data-ttu-id="e47bd-281">Внутренняя библиотека DLL сохраняет плайспаце в виде сетки 8cm Воксел Cubes.</span><span class="sxs-lookup"><span data-stu-id="e47bd-281">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="e47bd-282">Во время первой части сканирования выполняется анализ основных компонентов, чтобы определить оси комнаты.</span><span class="sxs-lookup"><span data-stu-id="e47bd-282">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="e47bd-283">На внутреннем уровне он хранит свое Воксел пространство, выравниваемая по этим осям.</span><span class="sxs-lookup"><span data-stu-id="e47bd-283">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="e47bd-284">Сетка создается приблизительно каждую секунду путем извлечения isosurface из тома Воксел.</span><span class="sxs-lookup"><span data-stu-id="e47bd-284">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="e47bd-285">Созданная ![ная сеть создана на основе тома Воксел](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="e47bd-285">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="e47bd-286">*Созданная Сетка создана на основе тома Воксел*</span><span class="sxs-lookup"><span data-stu-id="e47bd-286">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e47bd-287">Поиск и устранение неисправностей</span><span class="sxs-lookup"><span data-stu-id="e47bd-287">Troubleshooting</span></span>
* <span data-ttu-id="e47bd-288">Убедитесь, что вы установили функцию [спатиалперцептион](#setting-the-spatialperception-capability)</span><span class="sxs-lookup"><span data-stu-id="e47bd-288">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="e47bd-289">При потере отслеживания следующее событие Онсурфацечанжед удалит все сетки.</span><span class="sxs-lookup"><span data-stu-id="e47bd-289">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="e47bd-290">Пространственное сопоставление в наборе средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e47bd-290">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="e47bd-291">Дополнительные сведения об использовании пространственного сопоставления с Mixed Reality Toolkit v2 см. в <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">разделе о поддержке пространственных</a> данных в документации по мртк.</span><span class="sxs-lookup"><span data-stu-id="e47bd-291">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="e47bd-292">См. также</span><span class="sxs-lookup"><span data-stu-id="e47bd-292">See also</span></span>
* [<span data-ttu-id="e47bd-293">Индекс MR 230: пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="e47bd-293">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="e47bd-294">Системы координат</span><span class="sxs-lookup"><span data-stu-id="e47bd-294">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="e47bd-295">Системы координат в Unity</span><span class="sxs-lookup"><span data-stu-id="e47bd-295">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="e47bd-296"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="e47bd-296"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="e47bd-297"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. Мешфилтер</a></span><span class="sxs-lookup"><span data-stu-id="e47bd-297"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="e47bd-298"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. Мешколлидер</a></span><span class="sxs-lookup"><span data-stu-id="e47bd-298"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="e47bd-299"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. Bounds</a></span><span class="sxs-lookup"><span data-stu-id="e47bd-299"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
