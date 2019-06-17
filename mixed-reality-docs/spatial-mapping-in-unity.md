---
title: Пространственное сопоставление в Unity
description: Подготовка к просмотру и несовместимости с реальных геометрического объекта вокруг вас в Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, пространственное сопоставление, модуль подготовки отчетов, collider, сетки, сканирование, компонент
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148652"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="ffa9e-104">Пространственное сопоставление в Unity</span><span class="sxs-lookup"><span data-stu-id="ffa9e-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="ffa9e-105">В этом разделе описывается использование [пространственное сопоставление](spatial-mapping.md) в проекте Unity извлечение треугольников, представляющие поверхности в мир вокруг устройства HoloLens, для размещения, перекрытия, анализа комнаты и многое другое.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="ffa9e-106">Unity обеспечивает полную поддержку пространственное сопоставление, который предоставляется разработчикам одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="ffa9e-107">Пространственные сопоставление компоненты, доступные в MixedRealityToolkit, которые предоставляют удобный и быстрого пути по началу работы с пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="ffa9e-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="ffa9e-108">Пространственное сопоставление более низкого уровня API-интерфейсы, которые предоставить полный управления и включить определенные настройки более сложных приложений</span><span class="sxs-lookup"><span data-stu-id="ffa9e-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="ffa9e-109">Чтобы использовать пространственное сопоставление в приложении, spatialPerception возможность должен задаваться в вашей AppxManifest.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="ffa9e-110">Настройка возможностей SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="ffa9e-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="ffa9e-111">Чтобы приложение для работы с данными пространственное сопоставление должна быть включена возможность SpatialPerception.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="ffa9e-112">Как включить возможность SpatialPerception:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="ffa9e-113">Откройте в редакторе Unity **«Параметры проигрывателя»** области (Изменить > Параметры проекта > проигрывателя)</span><span class="sxs-lookup"><span data-stu-id="ffa9e-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="ffa9e-114">Щелкните **«Windows Store»** вкладку</span><span class="sxs-lookup"><span data-stu-id="ffa9e-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="ffa9e-115">Разверните **«Параметры публикации»** и проверьте **«SpatialPerception»** возможность **«Возможности»** списка</span><span class="sxs-lookup"><span data-stu-id="ffa9e-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="ffa9e-116">Обратите внимание, что если вы уже экспортировали проекта Unity в решение Visual Studio, необходимо будет либо экспорта в новую папку или вручную [задать эту возможность в манифест AppxManifest в Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="ffa9e-117">Пространственное сопоставление также требуется maxversiontested укажите из по крайней мере 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="ffa9e-118">В Visual Studio щелкните правой кнопкой мыши **Package.appxmanifest** в обозревателе решений и выберите **Просмотр кода**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="ffa9e-119">Найти ввод строки **TargetDeviceFamily** и измените **maxversiontested укажите = «10.0.10240.0»** для **maxversiontested укажите = «10.0.10586.0»**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="ffa9e-120">**Сохранить** Package.appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="ffa9e-121">Приступая к работе с компонентами Unity встроенные пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="ffa9e-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="ffa9e-122">Unity предоставляет два компонента для простого добавления пространственное сопоставление в приложение, **визуализации пространственных сопоставление** и **пространственных сопоставление Collider**.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="ffa9e-123">Модуль подготовки отчетов пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="ffa9e-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="ffa9e-124">Для визуализации сетки пространственное сопоставление позволяет пространственных сопоставления модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Пространственное сопоставление модуля подготовки отчетов в Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="ffa9e-126">Пространственное сопоставление Collider</span><span class="sxs-lookup"><span data-stu-id="ffa9e-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="ffa9e-127">Пространственные Collider сопоставления позволяет holographic содержимое (или символ) взаимодействие, например физики, при этом пространственное сопоставление сети.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Пространственное сопоставление Collider в Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="ffa9e-129">С помощью встроенных пространственное сопоставление компонентов</span><span class="sxs-lookup"><span data-stu-id="ffa9e-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="ffa9e-130">Если вы хотите визуализировать и взаимодействовать с физические можно добавить оба компонента в приложение.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="ffa9e-131">Чтобы использовать эти два компонента в приложении Unity:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="ffa9e-132">Выберите GameObject в центре области, в котором вы хотите обнаружить пространственных поверхности сетки.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="ffa9e-133">В окне инспектора **добавить компонент** > **XR** > **пространственных сопоставление Collider** или **пространственный индекс Модуль подготовки отчетов сопоставление**.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="ffa9e-134">Можно найти дополнительные сведения о том, как использовать эти компоненты в <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">сайт документации по Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="ffa9e-135">Помимо встроенных пространственное сопоставление компонентов</span><span class="sxs-lookup"><span data-stu-id="ffa9e-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="ffa9e-136">Эти компоненты сделать его и перетащите легко приступить к работе с пространственными сопоставление.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="ffa9e-137"> Если вы хотите пойти дальше, существует два основных способа для изучения:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="ffa9e-138">Для собственной обработки сетки более низкого уровня, см. ниже разделе о сценарии низкого уровня пространственного сопоставления API.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="ffa9e-139">Чтобы сделать более высокого уровня сетки анализа, см. ниже разделе о библиотеке SpatialUnderstanding в <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="ffa9e-140">С помощью Unity пространственных сопоставление интерфейса API низкого уровня</span><span class="sxs-lookup"><span data-stu-id="ffa9e-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="ffa9e-141">Если вам требуется больший контроль, чем вы получаете от пространственных сопоставление модуля подготовки отчетов и пространственных Collider сопоставление компонентов, можно использовать сценарий низкого уровня пространственного сопоставление интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="ffa9e-142">**Пространство имен:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="ffa9e-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="ffa9e-143">**Типы**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="ffa9e-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="ffa9e-144">Ниже приводится объяснение того предлагаемые потока для приложения, использующего пространственное сопоставление интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="ffa9e-145">Настройка SurfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="ffa9e-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="ffa9e-146">Создайте экземпляр одного объекта SurfaceObserver для каждого региона, определяемые приложением пространства, которое требуется пространственное сопоставление данных для.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="ffa9e-147">Укажите регион, предоставляющий данные для каждого объекта SurfaceObserver путем вызова SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox или SetVolumeAsFrustum пространства.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="ffa9e-148">Можно переопределить область пространства в будущем, просто вызвав один из следующих методов.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="ffa9e-149">При вызове SurfaceObserver.Update(), необходимо создать обработчик для каждого пространственного рабочей области в регионе SurfaceObserver пространства, система пространственное сопоставление имеет сведения о новых.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="ffa9e-150">Обработчик получает для одного пространственного рабочей области:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="ffa9e-151">Обработка изменений на поверхности</span><span class="sxs-lookup"><span data-stu-id="ffa9e-151">Handling Surface Changes</span></span>

<span data-ttu-id="ffa9e-152">Существует несколько основных вариантов для обработки.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-152">There are several main cases to handle.</span></span> <span data-ttu-id="ffa9e-153">Добавить & Updated, который можно использовать те же кода путь "и" удалено.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="ffa9e-154">В случаях Added & Updated в примере, мы добавить или получить, представляющий объект GameObject, это mesh из словаря, создание структуры SurfaceData необходимые компоненты, а затем вызовите RequestMeshDataAsync для заполнения GameObject с данными сетки и Поместите в сцене.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="ffa9e-155">В случае, удалено удалите объект GameObject, представляющий этой сетчатой структурой из словаря и удалите его.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

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

### <a name="handling-data-ready"></a><span data-ttu-id="ffa9e-156">Обработка готовность данных</span><span class="sxs-lookup"><span data-stu-id="ffa9e-156">Handling Data Ready</span></span>

<span data-ttu-id="ffa9e-157">OnDataReady обработчик получает объект SurfaceData.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="ffa9e-158">WorldAnchor, MeshFilter и (необязательно MeshCollider объекты, содержащиеся в ней) отражают последнее состояние связанного пространственных поверхности.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="ffa9e-159">При необходимости выполнять анализ и/или [обработки](spatial-mapping.md#mesh-processing) сетки данных, доступ к члену сетки MeshFilter объекта.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="ffa9e-160">Отрисовать область пространственных с последней сетки и (при необходимости) использовать ее для конфликтов физики и raycasts.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="ffa9e-161">Важно, чтобы убедиться, что содержимое SurfaceData не равны null.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="ffa9e-162">Начать обрабатывать обновления</span><span class="sxs-lookup"><span data-stu-id="ffa9e-162">Start processing on updates</span></span>

<span data-ttu-id="ffa9e-163">SurfaceObserver.Update() должен быть вызван на задержку, а не в каждом кадре.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="ffa9e-164">Анализ более высокого уровня сетки. SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="ffa9e-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="ffa9e-165"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> содержится ряд полезных вспомогательных кода для holographic разработки приложений, построенных на основе holographic API-интерфейсов Unity.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="ffa9e-166">Пространственные понимание</span><span class="sxs-lookup"><span data-stu-id="ffa9e-166">Spatial Understanding</span></span>

<span data-ttu-id="ffa9e-167">При помещении голограммы в физическом мире часто желательно переход за пределы пространственное сопоставление mesh и взглянуть на плоскости.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="ffa9e-168">После завершения процедурному размещения более высокий уровень понимания окружающую среду является предпочтительным.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="ffa9e-169">Обычно для этого требуется принимать решения о том, что функция floor, ceiling и стены.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="ffa9e-170">Кроме того, возможность оптимизации на основе набора ограничений на размещение для определения наиболее желательно физических расположений для holographic объектов.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="ffa9e-171">Во время разработки Young Conker и фрагментов Asobo Studios сталкиваются этой проблемы головной фрагмент, разработка поиск места для этой цели.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="ffa9e-172">Каждый из этих игр имел игр потребностями, но они совместно core пространственных основные сведения о технологии.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="ffa9e-173">HoloToolkit.SpatialUnderstanding, библиотека инкапсулирует эта технология позволяет вам быстро найти свободное место на стене, поместите объекты на потолке, определить поместить символ средством обработки и множество других запросов пространственных понимание.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="ffa9e-174">Весь исходный код включается, позволяя настраивать его под свои нужды и поделиться с сообществом улучшений.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="ffa9e-175">Код для C++ средства поиска решения в оболочку в библиотеку dll для универсальной платформы Windows и предоставлена для Unity с помощью перетаскивания в содержащихся в MixedRealityToolkit prefab.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="ffa9e-176">Основные сведения о модулях</span><span class="sxs-lookup"><span data-stu-id="ffa9e-176">Understanding Modules</span></span>

<span data-ttu-id="ffa9e-177">Существует три основных интерфейсов, предоставляемую модулем: топология для простой поверхность и пространственных запросов, фигуры, для обнаружения объектов и поиска решения для размещения объекта для размещения на основе ограничений наборов объектов.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="ffa9e-178">Ниже описан каждый из них.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-178">Each of these is described below.</span></span> <span data-ttu-id="ffa9e-179">Помимо три интерфейса основной модуль интерфейсом Рэй приведения может использоваться для извлечения с тегами поверхности типов и пользовательских watertight playspace сетки может быть скопирован обратно.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="ffa9e-180">Рэй приведения</span><span class="sxs-lookup"><span data-stu-id="ffa9e-180">Ray Casting</span></span>

<span data-ttu-id="ffa9e-181">После комнате были сканирования и финализации, метки внутренне создаются для поверхности: floor, ceiling и стены.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="ffa9e-182">«PlayspaceRaycast», функция принимает луча и возвращает Если луч конфликтует с известных поверхность и если да, сведения, которые отображаются в виде «RaycastResult».</span><span class="sxs-lookup"><span data-stu-id="ffa9e-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

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

<span data-ttu-id="ffa9e-183">На внутреннем уровне raycast вычисляется с представлением playspace voxel вычисляемый 8cm, в кубе.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="ffa9e-184">Каждый voxel содержит набор поверхности элементами и данными обработанные топологии (также называемые surfels).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="ffa9e-185">Сравниваются surfels, содержащихся в ячейке пересекаемых voxel, наиболее подходящий, используемый для поиска сведений о топологии.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="ffa9e-186">Эти данные топологии содержит такой параметр, возвращается в виде перечисления «SurfaceTypes», а также контактную зону поверхности пересекаемых.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="ffa9e-187">В этом примере Unity курсора приводит луча каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="ffa9e-188">Во-первых от Unity colliders.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="ffa9e-189">Во-вторых по представлению модуль общее представление о мире.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="ffa9e-190">И наконец, еще раз элементы пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-190">And finally, again UI elements.</span></span> <span data-ttu-id="ffa9e-191">В этом приложении пользовательского интерфейса получает приоритет, далее понимание результат и, наконец, Unity colliders.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="ffa9e-192">SurfaceType сообщается как текст рядом с курсором.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="ffa9e-193">![Тип поверхности помечен рядом с курсором](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ffa9e-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="ffa9e-194">*Тип поверхности помечен рядом с курсором*</span><span class="sxs-lookup"><span data-stu-id="ffa9e-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="ffa9e-195">Топология запросов</span><span class="sxs-lookup"><span data-stu-id="ffa9e-195">Topology Queries</span></span>

<span data-ttu-id="ffa9e-196">В этой библиотеке DLL диспетчера топологии обрабатывает пометки среды.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="ffa9e-197">Как упоминалось выше, большая часть данных хранится в surfels, содержащихся в voxel тома.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="ffa9e-198">Кроме того структура «PlaySpaceInfos» используется для хранения сведений о playspace, включая выравнивание по всему миру (Дополнительные сведения об этом ниже), floor и ceiling высоты.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="ffa9e-199">Эвристики для определения floor, ceiling и стены.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="ffa9e-200">Например максимальный и минимальный горизонтальный поверхности с более чем 1 m2 контактную зону считается ближайшее снизу целое.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="ffa9e-201">Обратите внимание на то, что путь камеры во время сканирования также используется в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="ffa9e-202">Подмножество запросов, предоставляемых диспетчера топологии предоставляются посредством библиотеки dll.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="ffa9e-203">Ниже приведены запросы предоставляемого топологии.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="ffa9e-204">Каждый из запросов имеет набор параметров, зависящие от типа запроса.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="ffa9e-205">В следующем примере пользователь указывает минимальную высоту и ширину нужного тома, высота минимальное размещения выше ближайшее снизу целое и минимальный объем зазор перед тома.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="ffa9e-206">Все измерения, в метрах.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="ffa9e-207">Каждый из запросов принимает предварительно выделить массив структур «TopologyResult».</span><span class="sxs-lookup"><span data-stu-id="ffa9e-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="ffa9e-208">Параметр «locationCount» задает длину переданный массив.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="ffa9e-209">Возвращаемое значение сообщает количество возвращаемых расположений.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="ffa9e-210">Это число больше никогда не переданный в параметре «locationCount».</span><span class="sxs-lookup"><span data-stu-id="ffa9e-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="ffa9e-211">«TopologyResult» содержит центральную позицию возвращаемого тома, разворота направления (т. е. обычные) и размеры найден пространства.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="ffa9e-212">Обратите внимание, что в образце Unity, каждый из этих запросов связанного к кнопке панели виртуального пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="ffa9e-213">Пример жестких коды параметры для каждого из этих запросов, приемлемые значения.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="ffa9e-214">См. в разделе SpaceVisualizer.cs в образце кода Дополнительные примеры.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="ffa9e-215">Запросы фигуры</span><span class="sxs-lookup"><span data-stu-id="ffa9e-215">Shape Queries</span></span>

<span data-ttu-id="ffa9e-216">Внутри библиотеки dll анализатор фигуры («ShapeAnalyzer_W») использует анализатор топологии для сравнения пользовательские фигуры, определенные пользователем.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="ffa9e-217">В примере Unity определяет набор фигур и предоставляет доступ к результатам out через меню "запрос в приложении", на вкладке фигуры. Намерение — что пользователь может определить собственные запросы объектов фигуры и пользоваться из них, по мере необходимости приложением.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="ffa9e-218">Обратите внимание на то, что анализ фигуры работает на горизонтальной поверхностях только.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="ffa9e-219">Диване, например, определяется области неструктурированных рабочих мест и плоский вверху диване обратно.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="ffa9e-220">Запроса shape выполняет поиск двух областей определенного размера, высоту и аспект диапазона, с помощью двух областей выравнивается и подключен.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="ffa9e-221">С помощью API-интерфейсы терминология, рабочих диване мест и возврата верхней являются компонентами фигуры и требований к выравниванию — ограниченность компонентов фигуры.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="ffa9e-222">Ниже приведен пример запроса, определенные в образце Unity (ShapeDefinition.cs), для объектов «sittable».</span><span class="sxs-lookup"><span data-stu-id="ffa9e-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

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

<span data-ttu-id="ffa9e-223">Каждый запрос фигуры определяется ряд компонентов фигуры, каждая из которых набор ограничений компонента и набор ограничений фигуры которой список зависимостей между компонентами.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="ffa9e-224">Этот пример включает три ограничения в определении один компонент и нет ограничений фигуры между компонентами (так как существует только один компонент).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="ffa9e-225">Напротив диване фигура имеет два компонента фигуры и четыре ограничения фигуры.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="ffa9e-226">Обратите внимание на то, что компоненты идентифицируются по их индекс в списке компонентов пользователя (0 и 1 в этом примере).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="ffa9e-227">Функции-оболочки предоставляются в модуле Unity для упрощенного создания пользовательской фигуры определений.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="ffa9e-228">Полный список ограничений компонента и фигуры можно найти в «SpatialUnderstandingDll.cs» в «ShapeComponentConstraint» и «ShapeConstraint» структуры.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="ffa9e-229">![Прямоугольник находится в этой рабочей области](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ffa9e-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="ffa9e-230">*Прямоугольник находится в этой рабочей области*</span><span class="sxs-lookup"><span data-stu-id="ffa9e-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="ffa9e-231">Поиск решения для размещения объекта</span><span class="sxs-lookup"><span data-stu-id="ffa9e-231">Object Placement Solver</span></span>

<span data-ttu-id="ffa9e-232">Поиска решения для размещения объекта можно использовать для обозначения идеальный расположений в физических комнаты для размещения ваших объектов.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="ffa9e-233">Средство поиска решения будет найти наиболее подходит расположение, заданное объектом правила и ограничения.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="ffa9e-234">Кроме того запросы объектов действовать, пока объект удаляется с «Solver_RemoveObject» или «Solver_RemoveAllObjects» вызовов, позволяя ограниченное размещение нескольких объектов.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="ffa9e-235">Объекты размещения запросы состоят из трех частей: тип размещения с параметрами, список правил и список ограничений.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="ffa9e-236">Чтобы выполнить запрос, используйте следующий интерфейс API.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-236">To run a query, use the following API.</span></span>

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

<span data-ttu-id="ffa9e-237">Эта функция принимает имя объекта, определение размещения и список правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="ffa9e-238">C# Оболочки предоставляет конструкции вспомогательные функции для упрощения создания правила и ограничения.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="ffa9e-239">Определение размещения содержит тип запроса — то есть одно из следующих.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-239">The placement definition contains the query type – that is, one of the following.</span></span>

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

<span data-ttu-id="ffa9e-240">Каждый из типов размещения имеет набор параметров, уникальный в тип.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="ffa9e-241">Структура «ObjectPlacementDefinition» содержит набор статических вспомогательных функций для создания этих определений.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="ffa9e-242">Например чтобы найти место для размещения объекта в процессе установки, можно использовать следующую функцию.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="ffa9e-243">общедоступный статический ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) в дополнение к тип размещения, можно предоставить набор правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="ffa9e-244">Правила не может быть нарушено.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-244">Rules cannot be violated.</span></span> <span data-ttu-id="ffa9e-245">Возможное размещение расположения, которые удовлетворяют типа и правила, затем оптимизируются с набором ограничений для выбора расположения оптимальное размещение.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="ffa9e-246">Каждый из правила и ограничения могут создаваться предоставленный создания статических функций.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="ffa9e-247">Ниже приведен пример правила и ограничения создания такой функции.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="ffa9e-248">Под объектом размещения запросов ищет поместить половину измерения куба на края поверхности, от других ранее разместить объекты и рядом с центром комнаты.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

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

<span data-ttu-id="ffa9e-249">В случае успешного выполнения «ObjectPlacementResult» структуру, содержащую позиции размещения, размеры и ориентации возвращается.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="ffa9e-250">Кроме того размещение добавляется внутренний список размещенных объектов для библиотеки dll.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="ffa9e-251">Размещение последующие запросы будут учитывать этот объект.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="ffa9e-252">Файл «LevelSolver.cs» в образце Unity содержит дополнительные примеры запросов.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="ffa9e-253">![Результаты размещение объекта](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ffa9e-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="ffa9e-254">*Рис. 3. Синий поля, как результат из три места, на площадке запросы с малой от правил позиции камеры*</span><span class="sxs-lookup"><span data-stu-id="ffa9e-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="ffa9e-255">Решения для расположения размещения нескольких объектов, необходимые для уровня или приложение сценария, следует сначала разрешить незаменимым и больших объектов, в порядке, чтобы обеспечить максимальную вероятность того, что можно найти пробел.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="ffa9e-256">Важен порядок размещения.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-256">Placement order is important.</span></span> <span data-ttu-id="ffa9e-257">Если не удается найти объект размещения, попробуйте менее ограниченного конфигураций.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="ffa9e-258">Набор настроек резервирования важно для поддержки функциональности в конфигурациях с много места.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="ffa9e-259">Процесс сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="ffa9e-259">Room Scanning Process</span></span>

<span data-ttu-id="ffa9e-260">Хотя решение пространственное сопоставление, предоставляемые HoloLens предназначен быть универсальными, в соответствии с потребностями весь спектр пространства состояний, пространственных основные сведения о модуле была создана для поддержки потребностей два игр.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="ffa9e-261">Свое решение рассматриваются специфические идентификаторы процессов и набор предположений, представлены ниже.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="ffa9e-262">Управляемая playspace «Рисование» — во время фазы сканирования пользователем пользователь перемещает и ищет вокруг играет темпе, эффективно закрашивание области, которые должны быть включены.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="ffa9e-263">Отзыв пользователя на этом этапе важно созданный сетки.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="ffa9e-264">Улице домашней или установке office — запрос, который функции разрабатываются на основе плоскими поверхностями и стены под прямым углом.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="ffa9e-265">Это мягкое ограничение.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-265">This is a soft limitation.</span></span> <span data-ttu-id="ffa9e-266">Однако во время фазы сканирования анализа основной оси выполняется для оптимизации тесселяции сетки на основной и вспомогательной оси.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="ffa9e-267">Включаемый файл SpatialUnderstanding.cs управляет процессом сканирования этапа.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="ffa9e-268">Он вызывает следующие функции.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-268">It calls the following functions.</span></span>

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

<span data-ttu-id="ffa9e-269">Сканирования потока, обусловленных «SpatialUnderstanding» поведение вызывает InitScan, а затем UpdateScan каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="ffa9e-270">При разумным покрытия отчете статистики запроса, пользователь может airtap для вызова RequestFinish для указания на конец фазы сканирования.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="ffa9e-271">UpdateScan по-прежнему вызываться, пока он не возвращаемое значение указывает, что библиотека dll завершило обработку.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="ffa9e-272">Основные сведения о сети</span><span class="sxs-lookup"><span data-stu-id="ffa9e-272">Understanding Mesh</span></span>

<span data-ttu-id="ffa9e-273">Основные сведения о dll хранятся playspace как сетка 8cm размера voxel кубов.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="ffa9e-274">Во время начальной части сканирования завершения анализа основного компонента для определения осей комнаты.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="ffa9e-275">Внутри он хранит пространства voxel, выровненным по этим осям.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="ffa9e-276">Сетка создается приблизительно каждую секунду путем извлечения isosurface voxel тома.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="ffa9e-277">![Созданный сетки, полученные из тома voxel](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="ffa9e-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="ffa9e-278">*Созданный сетки, полученные из тома voxel*</span><span class="sxs-lookup"><span data-stu-id="ffa9e-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="ffa9e-279">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="ffa9e-279">Troubleshooting</span></span>
* <span data-ttu-id="ffa9e-280">Убедитесь, вы задали [SpatialPerception](#setting-the-spatialperception-capability) возможностей</span><span class="sxs-lookup"><span data-stu-id="ffa9e-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="ffa9e-281">При потере отслеживания следующего события OnSurfaceChanged приведет к удалению всех сеток.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="ffa9e-282">Пространственное сопоставление в наборе средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="ffa9e-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="ffa9e-283">Дополнительные сведения об использовании пространственных сопоставление со смешанной реальности Toolkit v2, см. в разделе <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">разделе пространственных Awareness</a> MRTK документов.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffa9e-284">См. также</span><span class="sxs-lookup"><span data-stu-id="ffa9e-284">See also</span></span>
* [<span data-ttu-id="ffa9e-285">230. Пространство в смешанной реальности: пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="ffa9e-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="ffa9e-286">Системы координат</span><span class="sxs-lookup"><span data-stu-id="ffa9e-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="ffa9e-287">Системы координат в Unity</span><span class="sxs-lookup"><span data-stu-id="ffa9e-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="ffa9e-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="ffa9e-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="ffa9e-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="ffa9e-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="ffa9e-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="ffa9e-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="ffa9e-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="ffa9e-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
