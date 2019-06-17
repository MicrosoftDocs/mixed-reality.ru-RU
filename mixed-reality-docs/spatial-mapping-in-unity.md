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
# <a name="spatial-mapping-in-unity"></a>Пространственное сопоставление в Unity

В этом разделе описывается использование [пространственное сопоставление](spatial-mapping.md) в проекте Unity извлечение треугольников, представляющие поверхности в мир вокруг устройства HoloLens, для размещения, перекрытия, анализа комнаты и многое другое.

Unity обеспечивает полную поддержку пространственное сопоставление, который предоставляется разработчикам одним из следующих способов:
1. Пространственные сопоставление компоненты, доступные в MixedRealityToolkit, которые предоставляют удобный и быстрого пути по началу работы с пространственное сопоставление
2. Пространственное сопоставление более низкого уровня API-интерфейсы, которые предоставить полный управления и включить определенные настройки более сложных приложений

Чтобы использовать пространственное сопоставление в приложении, spatialPerception возможность должен задаваться в вашей AppxManifest.

## <a name="setting-the-spatialperception-capability"></a>Настройка возможностей SpatialPerception

Чтобы приложение для работы с данными пространственное сопоставление должна быть включена возможность SpatialPerception.

Как включить возможность SpatialPerception:
1. Откройте в редакторе Unity **«Параметры проигрывателя»** области (Изменить > Параметры проекта > проигрывателя)
2. Щелкните **«Windows Store»** вкладку
3. Разверните **«Параметры публикации»** и проверьте **«SpatialPerception»** возможность **«Возможности»** списка

Обратите внимание, что если вы уже экспортировали проекта Unity в решение Visual Studio, необходимо будет либо экспорта в новую папку или вручную [задать эту возможность в манифест AppxManifest в Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

Пространственное сопоставление также требуется maxversiontested укажите из по крайней мере 10.0.10586.0:
1. В Visual Studio щелкните правой кнопкой мыши **Package.appxmanifest** в обозревателе решений и выберите **Просмотр кода**
2. Найти ввод строки **TargetDeviceFamily** и измените **maxversiontested укажите = «10.0.10240.0»** для **maxversiontested укажите = «10.0.10586.0»**
3. **Сохранить** Package.appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Приступая к работе с компонентами Unity встроенные пространственное сопоставление

Unity предоставляет два компонента для простого добавления пространственное сопоставление в приложение, **визуализации пространственных сопоставление** и **пространственных сопоставление Collider**.

### <a name="spatial-mapping-renderer"></a>Модуль подготовки отчетов пространственное сопоставление

Для визуализации сетки пространственное сопоставление позволяет пространственных сопоставления модуля подготовки отчетов.

![Пространственное сопоставление модуля подготовки отчетов в Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Пространственное сопоставление Collider

Пространственные Collider сопоставления позволяет holographic содержимое (или символ) взаимодействие, например физики, при этом пространственное сопоставление сети.

![Пространственное сопоставление Collider в Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>С помощью встроенных пространственное сопоставление компонентов

Если вы хотите визуализировать и взаимодействовать с физические можно добавить оба компонента в приложение.

Чтобы использовать эти два компонента в приложении Unity:
1. Выберите GameObject в центре области, в котором вы хотите обнаружить пространственных поверхности сетки.
2. В окне инспектора **добавить компонент** > **XR** > **пространственных сопоставление Collider** или **пространственный индекс Модуль подготовки отчетов сопоставление**.

Можно найти дополнительные сведения о том, как использовать эти компоненты в <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">сайт документации по Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Помимо встроенных пространственное сопоставление компонентов

Эти компоненты сделать его и перетащите легко приступить к работе с пространственными сопоставление.  Если вы хотите пойти дальше, существует два основных способа для изучения:
* Для собственной обработки сетки более низкого уровня, см. ниже разделе о сценарии низкого уровня пространственного сопоставления API.
* Чтобы сделать более высокого уровня сетки анализа, см. ниже разделе о библиотеке SpatialUnderstanding в <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>С помощью Unity пространственных сопоставление интерфейса API низкого уровня

Если вам требуется больший контроль, чем вы получаете от пространственных сопоставление модуля подготовки отчетов и пространственных Collider сопоставление компонентов, можно использовать сценарий низкого уровня пространственного сопоставление интерфейсов API.

**Пространство имен:** *UnityEngine.XR.WSA*<br>
**Типы**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

Ниже приводится объяснение того предлагаемые потока для приложения, использующего пространственное сопоставление интерфейсов API.

### <a name="set-up-the-surfaceobservers"></a>Настройка SurfaceObserver(s)

Создайте экземпляр одного объекта SurfaceObserver для каждого региона, определяемые приложением пространства, которое требуется пространственное сопоставление данных для.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

Укажите регион, предоставляющий данные для каждого объекта SurfaceObserver путем вызова SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox или SetVolumeAsFrustum пространства. Можно переопределить область пространства в будущем, просто вызвав один из следующих методов.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

При вызове SurfaceObserver.Update(), необходимо создать обработчик для каждого пространственного рабочей области в регионе SurfaceObserver пространства, система пространственное сопоставление имеет сведения о новых. Обработчик получает для одного пространственного рабочей области:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>Обработка изменений на поверхности

Существует несколько основных вариантов для обработки. Добавить & Updated, который можно использовать те же кода путь "и" удалено.
* В случаях Added & Updated в примере, мы добавить или получить, представляющий объект GameObject, это mesh из словаря, создание структуры SurfaceData необходимые компоненты, а затем вызовите RequestMeshDataAsync для заполнения GameObject с данными сетки и Поместите в сцене.
* В случае, удалено удалите объект GameObject, представляющий этой сетчатой структурой из словаря и удалите его.

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

### <a name="handling-data-ready"></a>Обработка готовность данных

OnDataReady обработчик получает объект SurfaceData. WorldAnchor, MeshFilter и (необязательно MeshCollider объекты, содержащиеся в ней) отражают последнее состояние связанного пространственных поверхности. При необходимости выполнять анализ и/или [обработки](spatial-mapping.md#mesh-processing) сетки данных, доступ к члену сетки MeshFilter объекта. Отрисовать область пространственных с последней сетки и (при необходимости) использовать ее для конфликтов физики и raycasts. Важно, чтобы убедиться, что содержимое SurfaceData не равны null.

### <a name="start-processing-on-updates"></a>Начать обрабатывать обновления

SurfaceObserver.Update() должен быть вызван на задержку, а не в каждом кадре.

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>Анализ более высокого уровня сетки. SpatialUnderstanding

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> содержится ряд полезных вспомогательных кода для holographic разработки приложений, построенных на основе holographic API-интерфейсов Unity.

### <a name="spatial-understanding"></a>Пространственные понимание

При помещении голограммы в физическом мире часто желательно переход за пределы пространственное сопоставление mesh и взглянуть на плоскости. После завершения процедурному размещения более высокий уровень понимания окружающую среду является предпочтительным. Обычно для этого требуется принимать решения о том, что функция floor, ceiling и стены. Кроме того, возможность оптимизации на основе набора ограничений на размещение для определения наиболее желательно физических расположений для holographic объектов.

Во время разработки Young Conker и фрагментов Asobo Studios сталкиваются этой проблемы головной фрагмент, разработка поиск места для этой цели. Каждый из этих игр имел игр потребностями, но они совместно core пространственных основные сведения о технологии. HoloToolkit.SpatialUnderstanding, библиотека инкапсулирует эта технология позволяет вам быстро найти свободное место на стене, поместите объекты на потолке, определить поместить символ средством обработки и множество других запросов пространственных понимание.

Весь исходный код включается, позволяя настраивать его под свои нужды и поделиться с сообществом улучшений. Код для C++ средства поиска решения в оболочку в библиотеку dll для универсальной платформы Windows и предоставлена для Unity с помощью перетаскивания в содержащихся в MixedRealityToolkit prefab.

### <a name="understanding-modules"></a>Основные сведения о модулях

Существует три основных интерфейсов, предоставляемую модулем: топология для простой поверхность и пространственных запросов, фигуры, для обнаружения объектов и поиска решения для размещения объекта для размещения на основе ограничений наборов объектов. Ниже описан каждый из них. Помимо три интерфейса основной модуль интерфейсом Рэй приведения может использоваться для извлечения с тегами поверхности типов и пользовательских watertight playspace сетки может быть скопирован обратно.

### <a name="ray-casting"></a>Рэй приведения

После комнате были сканирования и финализации, метки внутренне создаются для поверхности: floor, ceiling и стены. «PlayspaceRaycast», функция принимает луча и возвращает Если луч конфликтует с известных поверхность и если да, сведения, которые отображаются в виде «RaycastResult».

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

На внутреннем уровне raycast вычисляется с представлением playspace voxel вычисляемый 8cm, в кубе. Каждый voxel содержит набор поверхности элементами и данными обработанные топологии (также называемые surfels). Сравниваются surfels, содержащихся в ячейке пересекаемых voxel, наиболее подходящий, используемый для поиска сведений о топологии. Эти данные топологии содержит такой параметр, возвращается в виде перечисления «SurfaceTypes», а также контактную зону поверхности пересекаемых.

В этом примере Unity курсора приводит луча каждого кадра. Во-первых от Unity colliders. Во-вторых по представлению модуль общее представление о мире. И наконец, еще раз элементы пользовательского интерфейса. В этом приложении пользовательского интерфейса получает приоритет, далее понимание результат и, наконец, Unity colliders. SurfaceType сообщается как текст рядом с курсором.

![Тип поверхности помечен рядом с курсором](images/su-raycastresults-300px.jpg)<br>
*Тип поверхности помечен рядом с курсором*

### <a name="topology-queries"></a>Топология запросов

В этой библиотеке DLL диспетчера топологии обрабатывает пометки среды. Как упоминалось выше, большая часть данных хранится в surfels, содержащихся в voxel тома. Кроме того структура «PlaySpaceInfos» используется для хранения сведений о playspace, включая выравнивание по всему миру (Дополнительные сведения об этом ниже), floor и ceiling высоты. Эвристики для определения floor, ceiling и стены. Например максимальный и минимальный горизонтальный поверхности с более чем 1 m2 контактную зону считается ближайшее снизу целое. Обратите внимание на то, что путь камеры во время сканирования также используется в этом процессе.

Подмножество запросов, предоставляемых диспетчера топологии предоставляются посредством библиотеки dll. Ниже приведены запросы предоставляемого топологии.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Каждый из запросов имеет набор параметров, зависящие от типа запроса. В следующем примере пользователь указывает минимальную высоту и ширину нужного тома, высота минимальное размещения выше ближайшее снизу целое и минимальный объем зазор перед тома. Все измерения, в метрах.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Каждый из запросов принимает предварительно выделить массив структур «TopologyResult». Параметр «locationCount» задает длину переданный массив. Возвращаемое значение сообщает количество возвращаемых расположений. Это число больше никогда не переданный в параметре «locationCount».

«TopologyResult» содержит центральную позицию возвращаемого тома, разворота направления (т. е. обычные) и размеры найден пространства.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Обратите внимание, что в образце Unity, каждый из этих запросов связанного к кнопке панели виртуального пользовательского интерфейса. Пример жестких коды параметры для каждого из этих запросов, приемлемые значения. См. в разделе SpaceVisualizer.cs в образце кода Дополнительные примеры.

### <a name="shape-queries"></a>Запросы фигуры

Внутри библиотеки dll анализатор фигуры («ShapeAnalyzer_W») использует анализатор топологии для сравнения пользовательские фигуры, определенные пользователем. В примере Unity определяет набор фигур и предоставляет доступ к результатам out через меню "запрос в приложении", на вкладке фигуры. Намерение — что пользователь может определить собственные запросы объектов фигуры и пользоваться из них, по мере необходимости приложением.

Обратите внимание на то, что анализ фигуры работает на горизонтальной поверхностях только. Диване, например, определяется области неструктурированных рабочих мест и плоский вверху диване обратно. Запроса shape выполняет поиск двух областей определенного размера, высоту и аспект диапазона, с помощью двух областей выравнивается и подключен. С помощью API-интерфейсы терминология, рабочих диване мест и возврата верхней являются компонентами фигуры и требований к выравниванию — ограниченность компонентов фигуры.

Ниже приведен пример запроса, определенные в образце Unity (ShapeDefinition.cs), для объектов «sittable».

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

Каждый запрос фигуры определяется ряд компонентов фигуры, каждая из которых набор ограничений компонента и набор ограничений фигуры которой список зависимостей между компонентами. Этот пример включает три ограничения в определении один компонент и нет ограничений фигуры между компонентами (так как существует только один компонент).

Напротив диване фигура имеет два компонента фигуры и четыре ограничения фигуры. Обратите внимание на то, что компоненты идентифицируются по их индекс в списке компонентов пользователя (0 и 1 в этом примере).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Функции-оболочки предоставляются в модуле Unity для упрощенного создания пользовательской фигуры определений. Полный список ограничений компонента и фигуры можно найти в «SpatialUnderstandingDll.cs» в «ShapeComponentConstraint» и «ShapeConstraint» структуры.

![Прямоугольник находится в этой рабочей области](images/su-shapequery-300px.jpg)<br>
*Прямоугольник находится в этой рабочей области*

### <a name="object-placement-solver"></a>Поиск решения для размещения объекта

Поиска решения для размещения объекта можно использовать для обозначения идеальный расположений в физических комнаты для размещения ваших объектов. Средство поиска решения будет найти наиболее подходит расположение, заданное объектом правила и ограничения. Кроме того запросы объектов действовать, пока объект удаляется с «Solver_RemoveObject» или «Solver_RemoveAllObjects» вызовов, позволяя ограниченное размещение нескольких объектов. Объекты размещения запросы состоят из трех частей: тип размещения с параметрами, список правил и список ограничений. Чтобы выполнить запрос, используйте следующий интерфейс API.

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

Эта функция принимает имя объекта, определение размещения и список правил и ограничений. C# Оболочки предоставляет конструкции вспомогательные функции для упрощения создания правила и ограничения. Определение размещения содержит тип запроса — то есть одно из следующих.

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

Каждый из типов размещения имеет набор параметров, уникальный в тип. Структура «ObjectPlacementDefinition» содержит набор статических вспомогательных функций для создания этих определений. Например чтобы найти место для размещения объекта в процессе установки, можно использовать следующую функцию. общедоступный статический ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) в дополнение к тип размещения, можно предоставить набор правил и ограничений. Правила не может быть нарушено. Возможное размещение расположения, которые удовлетворяют типа и правила, затем оптимизируются с набором ограничений для выбора расположения оптимальное размещение. Каждый из правила и ограничения могут создаваться предоставленный создания статических функций. Ниже приведен пример правила и ограничения создания такой функции.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

Под объектом размещения запросов ищет поместить половину измерения куба на края поверхности, от других ранее разместить объекты и рядом с центром комнаты.

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

В случае успешного выполнения «ObjectPlacementResult» структуру, содержащую позиции размещения, размеры и ориентации возвращается. Кроме того размещение добавляется внутренний список размещенных объектов для библиотеки dll. Размещение последующие запросы будут учитывать этот объект. Файл «LevelSolver.cs» в образце Unity содержит дополнительные примеры запросов.

![Результаты размещение объекта](images/su-objectplacement-1000px.jpg)<br>
*Рис. 3. Синий поля, как результат из три места, на площадке запросы с малой от правил позиции камеры*

Решения для расположения размещения нескольких объектов, необходимые для уровня или приложение сценария, следует сначала разрешить незаменимым и больших объектов, в порядке, чтобы обеспечить максимальную вероятность того, что можно найти пробел. Важен порядок размещения. Если не удается найти объект размещения, попробуйте менее ограниченного конфигураций. Набор настроек резервирования важно для поддержки функциональности в конфигурациях с много места.

### <a name="room-scanning-process"></a>Процесс сканирования комнаты

Хотя решение пространственное сопоставление, предоставляемые HoloLens предназначен быть универсальными, в соответствии с потребностями весь спектр пространства состояний, пространственных основные сведения о модуле была создана для поддержки потребностей два игр. Свое решение рассматриваются специфические идентификаторы процессов и набор предположений, представлены ниже.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

Управляемая playspace «Рисование» — во время фазы сканирования пользователем пользователь перемещает и ищет вокруг играет темпе, эффективно закрашивание области, которые должны быть включены. Отзыв пользователя на этом этапе важно созданный сетки. Улице домашней или установке office — запрос, который функции разрабатываются на основе плоскими поверхностями и стены под прямым углом. Это мягкое ограничение. Однако во время фазы сканирования анализа основной оси выполняется для оптимизации тесселяции сетки на основной и вспомогательной оси. Включаемый файл SpatialUnderstanding.cs управляет процессом сканирования этапа. Он вызывает следующие функции.

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

Сканирования потока, обусловленных «SpatialUnderstanding» поведение вызывает InitScan, а затем UpdateScan каждого кадра. При разумным покрытия отчете статистики запроса, пользователь может airtap для вызова RequestFinish для указания на конец фазы сканирования. UpdateScan по-прежнему вызываться, пока он не возвращаемое значение указывает, что библиотека dll завершило обработку.

### <a name="understanding-mesh"></a>Основные сведения о сети

Основные сведения о dll хранятся playspace как сетка 8cm размера voxel кубов. Во время начальной части сканирования завершения анализа основного компонента для определения осей комнаты. Внутри он хранит пространства voxel, выровненным по этим осям. Сетка создается приблизительно каждую секунду путем извлечения isosurface voxel тома. 

![Созданный сетки, полученные из тома voxel](images/su-custommesh.jpg)<br>
*Созданный сетки, полученные из тома voxel*

## <a name="troubleshooting"></a>Устранение неполадок
* Убедитесь, вы задали [SpatialPerception](#setting-the-spatialperception-capability) возможностей
* При потере отслеживания следующего события OnSurfaceChanged приведет к удалению всех сеток.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Пространственное сопоставление в наборе средств для смешанной реальности
Дополнительные сведения об использовании пространственных сопоставление со смешанной реальности Toolkit v2, см. в разделе <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">разделе пространственных Awareness</a> MRTK документов.

## <a name="see-also"></a>См. также
* [230. Пространство в смешанной реальности: пространственное сопоставление](holograms-230.md)
* [Системы координат](coordinate-systems.md)
* [Системы координат в Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
