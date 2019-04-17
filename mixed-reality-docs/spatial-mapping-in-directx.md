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
# <a name="spatial-mapping-in-directx"></a>Пространственное сопоставление в DirectX

В этом разделе описывается реализация [пространственное сопоставление](spatial-mapping.md) в вашем приложении DirectX. Сюда входят подробные сведения о работе пространственное сопоставление пример приложения, который входит в состав пакета SDK универсальной платформы Windows.

В этом разделе используется код из [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) пример кода для универсальной платформы Windows.

>[!NOTE]
>Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).  Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.

## <a name="directx-development-overview"></a>Общие сведения о разработке DirectX

Разработка приложения в машинном коде для пространственное сопоставление использует интерфейсы API, в разделе [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) пространства имен. Эти API обеспечивают полный контроль над пространственное сопоставление функций, аналогично непосредственно к пространственное сопоставление API-интерфейсы, предоставляемые [Unity](spatial-mapping-in-unity.md).

### <a name="perception-apis"></a>API-интерфейсы восприятие

Далее приведены основные типы для разработки пространственное сопоставление.
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) предоставляет сведения о поверхности в регионах, определяемый приложением, места рядом пользователя в форме объектов SpatialSurfaceInfo.
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) описывает единую для объекта пространственных поверхность, включая уникальный идентификатор, ограничивающий тома и время последнего изменения. Он предоставит SpatialSurfaceMesh асинхронно по запросу.
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) содержит параметры, используемые для настройки объектов SpatialSurfaceMesh, запрашиваемых SpatialSurfaceInfo.
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) представляет данные сетки для пространственного единую поверхность. Данные для позиции вершин, нормали вершины и индексы треугольников содержатся в объектах-членах SpatialSurfaceMeshBuffer.
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) заключает в оболочку одного типа данных сетки.

При разработке приложения с помощью этих API, простой программы последовательность будет выглядеть (как показано в примере приложения, описанные ниже):
- **Настройка вашей SpatialSurfaceObserver**
  - Вызовите [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), чтобы убедиться, что пользователь предоставил разрешения для приложения для использования пространственных сопоставление возможностей устройства.
  - Создание экземпляра объекта SpatialSurfaceObserver.
  - Вызовите [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) для указания области пространства, в котором нужно получить сведения о пространственных поверхности. Просто вызывайте эту функцию снова, вы можете изменять эти регионы в будущем. Каждая область указывается с помощью [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).
  - Зарегистрируйтесь для [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) событие, которое будет срабатывать при поступлении новой информации о пространственных поверхности в области пространства, которые вы указали.
- **Обработка событий ObservedSurfacesChanged**
  - В обработчике событий, вызовите [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) для получения карты SpatialSurfaceInfo объектов. Используя эту карту, можно обновить записи какие Пространственные поверхностей [существует в среде пользователя](spatial-mapping.md#mesh-caching).
  - Для каждого объекта SpatialSurfaceInfo можно выполнить запрос [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) для определения пространственного экстенты рабочей области, выраженное в [Пространственные системы координат](coordinate-systems.md) по своему выбору.
  - Если вы решите запроса сетки для пространственного поверхности, вызовите [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx). Может предоставлять параметры, указывающие требуемый плотность треугольники и формат возвращаемого сетки данных.
- **Получать и обрабатывать сетки**
  - Каждый вызов aysnchronously TryComputeLatestMeshAsync будет возвращать один объект SpatialSurfaceMesh.
  - Из этого объекта можно получить доступ к содержащиеся объекты SpatialSurfaceMeshBuffer для доступа к индексов треугольников, позиции вершин и (при запросе) нормалей вершин сетки. Эти данные будут в формате, полностью совместима с [интерфейсы API Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) используемой для визуализации сетки.
  - Отсюда приложения при необходимости можно выполнять анализ или [обработки](spatial-mapping.md#mesh-processing) сетки данных и использовать его для [отрисовки](spatial-mapping.md#rendering) и физики [точные точки для отслеживания и расчет столкновений](spatial-mapping.md#raycasting-and-collision).
  - Один важный момент, следует отметить том, что масштабируемый необходимо применить к позиции вершин сетки (например, в шейдер вершин, используемой для визуализации сетки), преобразовываемый оптимизированного целое число единиц, в которых они хранятся в буфере, на счетчики. Этой шкалы можно получить, вызвав [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).

### <a name="troubleshooting"></a>Устранение неполадок
* Не забудьте масштабировать позиции вершин сетки в шейдере вершин по масштабу, возвращенный [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Пошаговое руководство по примеру кода пространственных сопоставления

[Holographic пространственных сопоставление](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) образец кода содержит код, который можно использовать для начала загрузки поверхности сетки в приложении, включая инфраструктуру для управления и поверхностью отрисовки сетки.

Теперь мы рассмотрим добавление поверхности возможности сопоставления в приложении DirectX. Можно добавить этот код, чтобы ваши [Windows Holographic шаблон приложения](creating-a-holographic-directx-project.md) проектом или могут следить за действиями просмотра в образце кода, упомянутых выше. Этот пример кода основан на Windows Holographic шаблон приложения.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Настройка приложения для использования возможности spatialPerception

Приложения должны иметь возможность использовать Пространственные возможности сопоставления. Это необходимо, поскольку пространственный сетки является представлением среды пользователя, который может рассматриваться как закрытые данные. Объявите данную возможность в файле package.appxmanifest для вашего приложения. Ниже приведен пример:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

Возможность поступает из **uap2** пространства имен. Чтобы получить доступ к этому пространству имен в манифесте, включить его как *xlmns* атрибут в &lt;пакета > элемента. Ниже приведен пример:

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Проверьте наличие поддержки функция пространственное сопоставление

Смешанная реальность Windows поддерживает широкий спектр устройств, включая устройства, которые не поддерживают пространственное сопоставление. Если приложение можно использовать пространственное сопоставление или необходимо использовать пространственное сопоставление для обеспечения функциональности, оно должно проверить, чтобы убедиться в том, что пространственное сопоставление поддерживается перед попыткой его использования. Например если пространственное сопоставление требуется приложением смешанной реальности, отобразится сообщение об ошибке, если пользователь пытается его запуск на устройстве без пространственное сопоставление. Или, возможно, приложение может отображать собственной виртуальной среде, вместо среду, предоставляя функциональность, аналогичную что произойдет, если доступны пространственное сопоставление. В любом случае этот API позволяет вашему приложению, которые следует учитывать при его не получить пространственное сопоставление данных и реагировать соответствующим образом.

Чтобы проверить текущее устройство для поддержки пространственное сопоставление, сначала убедитесь, что контракт универсальной платформы Windows находится на уровне 4 или более поздней версии и затем вызвать SpatialSurfaceObserver::IsSupported(). Вот как можно сделать это в контексте [Holographic пространственных сопоставление](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) пример кода. Поддержка проверяется так же, прежде чем запрашивать доступ.

SpatialSurfaceObserver::IsSupported() API доступна, начиная с пакета SDK версии 15063. При необходимости изменить целевую платформу проекта, чтобы версия платформы 15063 перед использованием этого API.

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

Обратите внимание, что если контракт UWP меньше, чем уровень 4, приложения должна продолжаться, как если бы устройства позволяют делать пространственное сопоставление.

### <a name="request-access-to-spatial-mapping-data"></a>Запрос на доступ к данным пространственное сопоставление

Приложение должно запросить разрешение на доступ к пространственное сопоставление данных перед попыткой создания любой поверхности наблюдателей. Ниже приведен пример, основываясь на наш пример поверхность сопоставления кода с более подробными сведениями, предоставляемые позже на этой странице:

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

### <a name="create-a-surface-observer"></a>Создание поверхности наблюдателя

**Windows::Perception::Spatial::Surfaces** пространство имен включает [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) класс, который обнаруживает один или несколько томов, указанных в [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx). Используйте [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) экземпляра для доступа к данным сетки поверхности в режиме реального времени.

Из **AppMain.h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Как отмечалось в предыдущем разделе, необходимо запросить доступ к данным пространственное сопоставление, прежде чем приложение может использовать его. Такой доступ предоставляется автоматически в HoloLens.

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

Далее необходимо настроить поверхности наблюдателя для наблюдения за определенный ограничивающий том. Здесь мы заметили, поле, то есть 20 x 20 x 5 метров, начало системы координат.

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

Обратите внимание на то, можно задать несколько томов ограничивающий вместо этого.

*Это псевдокод:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

Можно также использовать другие ограничивающий фигуры — например усеченная или краю ограничивающий прямоугольник, который не оси.

*Это псевдокод:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Если вашему приложению необходим действия по-разному при поверхности сопоставления данные недоступны, можно написать код для реагирования на случай где [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) не **разрешено** — например, он не сможет на ПК с иммерсивных устройствами, подключить, так как эти устройства нет оборудования для пространственное сопоставление. Для этих устройств позволив пространственных рабочей области, сведения о среде и конфигурации устройства пользователя.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Инициализация и обновление коллекции сетки поверхности

Если поверхности наблюдатель был успешно создан, можно переходить к инициализации нашей коллекции сетки поверхности. Здесь мы используем API модели по запросу для получения текущего набора наблюдаемых поверхностей прямо сейчас:

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

Имеется также для получения данных сетки поверхности модели принудительной отправки. Можно разрабатывать приложения для использования только модели по запросу, если выбран, в этом случае необходимо будет запрашивать данные времени — скажем, один раз за кадр - или определенный период времени, например, во время установки игры. Если Да, приведенный выше код является то, что вам нужно.

В нашем примере мы выбрали для демонстрации использования обеих моделей воспитательный целях. Здесь мы подписаться на событие для получения данных в актуальном состоянии сетки поверхности всякий раз, когда система распознает изменения.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Наш пример кода также настраивается реагировать на эти события. Давайте рассмотрим, как это сделать.

**ПРИМЕЧАНИЕ.** Это может оказаться самым эффективным способом для вашего приложения для обработки данных сетки. Этот код написан для ясности и не оптимизирован.

Сетки поверхности данные предоставлены в карту только для чтения, в которой хранятся [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) объектов с помощью [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) как ключевые значения.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Для обработки этих данных, мы сначала выполняют для значений ключей, которые отсутствуют в нашей коллекции. Получите сведения о том, как данные хранятся в нашем примере далее в этом разделе.

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

Нам также нужно удалить поверхности сетки, которые в нашей коллекции сетки поверхности, но которых нет в коллекции системных больше. Чтобы сделать это, необходимо сделать что-то вроде противоположностью что мы только что показали за добавление и обновление сетки; Мы цикл по коллекции наше приложение и проверьте правильность **Guid** у нас есть в коллекции системы. Если он не находится в коллекции системных, мы удалите его из нас.

Из в AppMain.cpp наш обработчик событий:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

Реализация сетки очистки в RealtimeSurfaceMeshRenderer.cpp:

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Получить и использовать буферы данных сетки поверхности

Получение сведений сетки поверхности был так же просто, как получение коллекции данных и обработки обновления для этой коллекции. Теперь мы перейдем в подробности о том, как можно использовать данные.

В нашем примере мы решили использовать поверхности сетки для подготовки к просмотру. Это распространенный сценарий для occluding голограммы за реальных поверхности. Вы можете также отображают сетки или отрисовки обработанные их версии., для представления пользователю область просматриваются комнате, прежде чем начать предоставление функциональных возможностей приложений или игр.

Пример кода запускает процесс, при получении обновлений сетки поверхности из обработчика событий от описанного в предыдущем разделе. Важные строки кода в этой функции является вызов для обновления поверхности *mesh*: к этому моменту мы уже обработаны info сетки, и мы должны получить данные вершин и индексов для использования по мы усмотрению.

From RealtimeSurfaceMeshRenderer.cpp:

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

Наш пример кода предназначен, чтобы класс данных **SurfaceMesh**, обработка и вывод данных сетки дескрипторов. Эти сетки являются что **RealtimeSurfaceMeshRenderer** фактически хранит карту. Каждый из них имеет ссылку на SpatialSurfaceMesh, она поступила и мы используем его каждый раз, когда нам нужно получить доступ к сети буферы вершин или индекса, или получить преобразования для сетки. Сейчас мы флаг сетки как требующие обновления.

Из SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

При очередном сетки просят нарисовать сам себя, она проверяет флаг сначала. Если требуется обновление, буферы вершин и индексов будет обновляться в GPU.

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

Во-первых мы запросов буферы необработанные данные:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Затем создаем буферы устройства Direct3D с сетки данных, предоставляемых HoloLens:

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

**ПРИМЕЧАНИЕ.** Вспомогательная функция CreateDirectXBuffer, используемых в предыдущем фрагменте кода см. в образце кода поверхность сопоставления: SurfaceMesh.cpp GetDataFromIBuffer.h. Теперь завершении создания ресурсов устройства и сети считается загружены и готовы для обновления и визуализации.

### <a name="update-and-render-surface-meshes"></a>Обновление и отрисовки поверхности сетки

Наш класс SurfaceMesh имеется функция специализированные обновления. Каждый [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) имеет свои собственные преобразования, а в нашем примере использует текущую систему координат для наших **SpatialStationaryReferenceFrame** получения преобразование. Затем он обновляет буфера констант модель в графическом Процессоре.

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

Когда все готово для отрисовки поверхности сетки, делается некоторые подготовительную работу перед отображением в коллекцию. Мы настраиваем конвейер шейдера для текущей конфигурации подготовки к просмотру, и мы настраиваем стадии ассемблера входных данных. Обратите внимание, что вспомогательный класс holographic камеры **CameraResources.cpp** уже настроил буфера констант/проекция представления к этому моменту.

Из **RealtimeSurfaceMeshRenderer::Render**:

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

После этого, мы цикл по нашей сеток и сообщить каждого из них нарисовать сам себя. **ПРИМЕЧАНИЕ.** Этот пример кода не оптимизированы для использования любого вида поверхности пирамиды обзора, но следует включать эту функцию в вашем приложении.

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

Отдельных сеток несут ответственность за настройки буфера вершин и индексов, stride и буфер констант преобразования модели. Как и в случае с вращающегося куба в шаблоне приложения с Windows Holographic, мы визуализируем stereoscopic буферов, с помощью создания экземпляров.

Из **SurfaceMesh::Draw**:

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

### <a name="rendering-choices-with-surface-mapping"></a>Подготовка к просмотру вариантов в поверхность сопоставления

В образце кода поверхность сопоставления предоставляет код для подготовки к просмотру только для перекрытия данных сетки поверхности, а также для отображения на экране поверхности сетки данных. Какой путь выбран - или - зависит от приложения. Мы рассмотрим обе конфигурации в этом документе.

**Подготовка к просмотру перекрытия буферов для holographic эффекта**

Для начала сняв целевой объект прорисовки для текущей виртуальной камеры.

Из AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Это цикл «предвизуализации». Здесь мы создадим в буфер перекрытия запросив сетки модуля подготовки отчетов к просмотру только глубины. В этой конфигурации не Присоединяйте представления целевого объекта прорисовки и модуль подготовки отчетов сетки задает уровень построителя текстур пикселей **nullptr** таким образом, чтобы GPU не беспокоится Рисование пикселей. Геометрия будет растровое буфер глубины, и существует остановит графического конвейера.

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

Можно провести голограммы с тестами дополнительный глубины для буфера перекрытия область сопоставления. В этом примере кода мы построить пикселей на кубе другим цветом, если они находятся позади рабочую область.

Из AppMain.cpp:

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

На основе кода из SpecialEffectPixelShader.hlsl:

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

**Примечание.** Для наших **GatherDepthLess** подпрограммы, см. в образце кода поверхность сопоставления: SpecialEffectPixelShader.hlsl.

**Данные отрисовки поверхности сетки для отображения**

Можно также просто провести поверхности сетки в стерео отображения буферы. Мы выбрали для рисования полный лиц с помощью освещение, но вы можете рисования каркас, обрабатывать сеток перед отрисовкой, применить текстурной карты и т. д.

Здесь наш пример кода указывает модуль подготовки отчетов сетка для рисования в коллекцию. Это время мы не указываем только для глубина прохода, поэтому он будет прикрепление шейдера пикселей и выполнения конвейера отрисовки, с помощью целевых объектов, которые мы указали для текущей виртуальной камеры.

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

## <a name="see-also"></a>См. также
* [Создание проекта holographic DirectX](creating-a-holographic-directx-project.md)
* [Windows.Perception.Spatial API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
