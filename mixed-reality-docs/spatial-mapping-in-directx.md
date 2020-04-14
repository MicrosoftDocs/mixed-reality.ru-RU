---
title: Пространственное сопоставление в DirectX
description: Объясняет, как реализовать пространственное сопоставление в приложении DirectX. Сюда входит подробное описание примера приложения пространственного сопоставления, которое входит в состав пакета SDK для универсальная платформа Windows.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, пространственное сопоставление, среда, взаимодействие, DirectX, WinRT, API, пример кода, UWP, пакет SDK, пошаговое руководство
ms.openlocfilehash: b3ef74a7e11e0e73fce47e4c7193ace42ffe7c20
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277502"
---
# <a name="spatial-mapping-in-directx"></a>Пространственное сопоставление в DirectX

В этом разделе описывается реализация [пространственного сопоставления](spatial-mapping.md) в приложении DirectX. Сюда входит подробное описание примера приложения пространственного сопоставления, которое входит в состав пакета SDK для универсальная платформа Windows.

В этом разделе используется код из примера кода UWP для [холографикспатиалмаппинг](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .

>[!NOTE]
>Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

## <a name="device-support"></a>Поддержка устройств

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Функциями</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></td>
    </tr>
     <tr>
        <td>пространственное сопоставление</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a>Общие сведения о разработке DirectX

При разработке собственного приложения для пространственного сопоставления используются интерфейсы API в пространстве имен [Windows. восприятие. пространственный.](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) Эти API предоставляют полный контроль над функциями пространственного сопоставления, как и непосредственно аналогично API-интерфейсам пространственного сопоставления, предоставляемым [Unity](spatial-mapping-in-unity.md).

### <a name="perception-apis"></a>API-интерфейсы восприятия

Ниже приведены основные типы, предоставляемые для разработки пространственных сопоставлений.
* [Спатиалсурфацеобсервер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) предоставляет сведения о поверхностях в указанных в приложении областях пространства рядом с пользователем в виде объектов спатиалсурфацеинфо.
* [Спатиалсурфацеинфо](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) описывает одну пространственно екстантную поверхность, включая уникальный идентификатор, связанный том и время последнего изменения. Он предоставит Спатиалсурфацемеш асинхронно после запроса.
* [Спатиалсурфацемешоптионс](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) содержит параметры, используемые для настройки объектов спатиалсурфацемеш, запрошенных из спатиалсурфацеинфо.
* [Спатиалсурфацемеш](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) представляет данные сетки для отдельной пространственной поверхности. Данные для позиций вершин, нормалей вершин и индексов треугольников содержатся в объектах-членах Спатиалсурфацемешбуффер.
* [Спатиалсурфацемешбуффер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) заключает в оболочку один тип данных сетки.

При разработке приложения с использованием этих API основная последовательность программ будет выглядеть следующим образом (как показано в примере приложения, описанном ниже):
- **Настройка Спатиалсурфацеобсервер**
  - Вызовите [рекуестакцессасинк](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), чтобы убедиться, что пользователь предоставил разрешение на использование возможностей пространственного сопоставления устройства.
  - Создайте экземпляр объекта Спатиалсурфацеобсервер.
  - Вызовите [сетбаундингволумес](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) , чтобы указать области пространства, в которых требуется получить сведения о пространственных поверхностях. Вы можете изменить эти регионы в будущем, просто вызвав эту функцию еще раз. Каждый регион указывается с помощью [спатиалбаундингволуме](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).
  - Зарегистрируйтесь на событие [обсерведсурфацесчанжед](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , которое будет срабатывать каждый раз, когда доступна новая информация о пространственных областях в указанных регионах.
- **Обработка событий Обсерведсурфацесчанжед**
  - В обработчике событий вызовите [жетобсерведсурфацес](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) , чтобы получить карту объектов спатиалсурфацеинфо. С помощью этой схемы можно обновить записи, для которых существуют пространственные поверхности [в среде пользователя](spatial-mapping.md#mesh-caching).
  - Для каждого объекта Спатиалсурфацеинфо можно запросить [трижетбаундс](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) , чтобы определить пространственные экстенты поверхности, выраженные в [пространственной системе координат](coordinate-systems.md) по вашему выбору.
  - Если вы решили запросить сетку для пространственной поверхности, вызовите [трикомпутелатестмешасинк](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx). Вы можете указать параметры, задающие нужную плотность треугольников, и формат возвращаемых данных сетки.
- **Сетка приема и обработки**
  - Каждый вызов Трикомпутелатестмешасинк будет айснчронаусли возвращать один объект Спатиалсурфацемеш.
  - Из этого объекта можно получить доступ к содержащимся объектам Спатиалсурфацемешбуффер, чтобы получить доступ к индексам треугольника, позициям вершин и (при запросе) нормалям вершин сетки. Эти данные будут в формате, непосредственно совместимом с [API-интерфейсами Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) , используемыми для отрисовки сеток.
  - Здесь приложение может при необходимости выполнять анализ или [обработку](spatial-mapping.md#mesh-processing) данных сетки, а также использовать их для [визуализации](spatial-mapping.md#rendering) и создания физических [райкастинг и конфликтов](spatial-mapping.md#raycasting-and-collision).
  - Важно отметить, что необходимо применить шкалу к позициям вершин сетки (например, в шейдере вершин, используемом для отрисовки сеток), чтобы преобразовать их из оптимизированных целых единиц, в которых они хранятся в буфере, на метры. Эту шкалу можно получить, вызвав [вертекспоситионскале](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).

### <a name="troubleshooting"></a>Диагностика
* Не забудьте масштабировать позиции вершин сетки в шейдере вершин, используя шкалу, возвращенную [спатиалсурфацемеш. вертекспоситионскале](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Пример пошагового руководства по коду пространственного сопоставления

Пример кода для [пространственного сопоставления holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) включает в себя код, который можно использовать для начала загрузки сеток поверхности в приложение, включая инфраструктуру для управления и визуализации сеток поверхности.

Теперь мы пошаговым инструкциями по добавлению функции сопоставления поверхности в приложение DirectX. Этот код можно добавить в проект [шаблона приложения Windows holographic](creating-a-holographic-directx-project.md) . Кроме того, можно выполнить действия, просмотрев приведенный выше пример кода. Этот пример кода основан на шаблоне приложения Windows Holographic.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Настройка приложения для использования возможности Спатиалперцептион

Приложение должно иметь возможность использовать функцию пространственного сопоставления. Это необходимо потому, что пространственный сетчатый объект представляет собой представление среды пользователя, которое может считаться частными данными. Объявите эту возможность в файле Package. appxmanifest для приложения. Пример:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

Эта возможность поступает из пространства имен **uap2** . Чтобы получить доступ к этому пространству имен в манифесте, включите его в качестве атрибута *кслмнс* в элемент &lt;пакета >. Пример:

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Проверка поддержки функции пространственного сопоставления

Windows Mixed Reality поддерживает широкий спектр устройств, включая устройства, которые не поддерживают пространственное сопоставление. Если приложение может использовать пространственное сопоставление или должно использовать пространственное сопоставление для обеспечения функциональности, оно должно проверить, поддерживается ли пространственное сопоставление, прежде чем пытаться его использовать. Например, если для приложения смешанной реальности требуется пространственное сопоставление, оно должно отображать это сообщение, если пользователь пытается запустить его на устройстве без пространственного сопоставления. Кроме того, приложение может визуализировать собственную виртуальную среду вместо среды пользователя, предоставляя возможности, аналогичные тому, что произойдет, если было доступно пространственное сопоставление. В любом событии этот API позволяет приложению знать, когда не будет получать данные пространственного сопоставления и реагировать соответствующим образом.

Чтобы проверить наличие поддержки пространственного сопоставления на текущем устройстве, убедитесь, что контракт UWP имеет уровень 4 или выше и затем вызовите Спатиалсурфацеобсервер:: support (). Вот как это сделать в контексте примера кода [пространственного пространственного сопоставления](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) . Поддержка проверяется непосредственно перед запросом доступа.

API Спатиалсурфацеобсервер:: support () доступен начиная с пакета SDK версии 15063. При необходимости перецелевой проект до версии платформы 15063 перед использованием этого API.

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

Обратите внимание, что если контракт UWP меньше уровня 4, приложение должно продолжать работу так, как будто устройство поддерживает пространственное сопоставление.

### <a name="request-access-to-spatial-mapping-data"></a>Запрос доступа к данным пространственного сопоставления

Приложение должно запросить разрешение на доступ к данным пространственного сопоставления, прежде чем пытаться создать любые наблюдатели Surface. Ниже приведен пример, основанный на нашем примере кода сопоставления Surface, с дополнительными сведениями, приведенными далее на этой странице.

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

### <a name="create-a-surface-observer"></a>Создание наблюдателя Surface

Пространство имен **Windows::P ерцептион:: spatial::** Surfaces включает класс [спатиалсурфацеобсервер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) , который следит за одним или несколькими томами, указанными в [спатиалкурдинатесистем](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx). Используйте экземпляр [спатиалсурфацеобсервер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) для доступа к данным сетки Surface в режиме реального времени.

Из **аппмаин. h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Как отмечалось в предыдущем разделе, необходимо запросить доступ к данным пространственного сопоставления, прежде чем приложение сможет его использовать. Этот доступ предоставляется автоматически на HoloLens.

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

Далее необходимо настроить наблюдатель поверхности для наблюдения за конкретным ограничивающим томом. Здесь мы наблюдаем поле, 20x20x5 измерительные приборы, центрированные по отношению к координатам системы координат.

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

Обратите внимание, что вместо этого можно задать несколько ограничивающих томов.

*Это псевдокод:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

Также можно использовать другие ограничивающие фигуры, такие как представление фрустум, или ограничивающий прямоугольник, не выравниваемая по осям.

*Это псевдокод:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Если приложение должно выполнять какие-либо действия, если данные сопоставления поверхности недоступны, можно написать код для реагирования на случай, когда [спатиалперцептионакцессстатус](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) не **разрешен** (например, он не будет разрешен) на компьютерах с подключенными устройствами, так как эти устройства не имеют оборудования для пространственного сопоставления. Для этих устройств следует использовать пространственный этап для получения сведений о среде пользователя и конфигурации устройства.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Инициализация и обновление коллекции сеток поверхности

Если наблюдатель Surface был успешно создан, мы можем приступить к инициализации коллекции посети Surface. Здесь мы используем API модели извлечения для немедленного получения текущего набора наблюдаемых поверхностей:

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

Существует также модель push-уведомлений, доступная для получения данных о сетке поверхности. Вы можете разрабатывать приложение для использования только модели извлечения, если выбрать, в этом случае вы будете опрашивать данные каждые часто, например, один раз в кадре или в течение определенного периода времени, как во время настройки игры. В этом случае приведенный выше код является необходимым.

В нашем примере кода мы решили продемонстрировать использование обеих моделей для воспитательный целей. Здесь мы подписались на событие, чтобы получить актуальные данные о сетке поверхности всякий раз, когда система распознает изменение.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Наш пример кода также настроен для реагирования на эти события. Давайте подробно рассмотрим, как это сделать.

**Примечание.** Это может быть не самым эффективным способом для работы приложения с данными сетки. Этот код написан для ясности и не оптимизирован.

Данные сетки поверхности предоставляются в карте только для чтения, в которой хранятся объекты [спатиалсурфацеинфо](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) с использованием [Platform:: GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) в качестве значений ключа.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Для обработки этих данных сначала мы рассмотрим значения ключей, которых нет в нашей коллекции. Сведения о том, как данные хранятся в нашем примере приложения, будут представлены далее в этом разделе.

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

Также необходимо удалить сети Surface, которые находятся в коллекции посетей, но больше нет в коллекции систем. Для этого необходимо сделать что-то на противоположное, что было показано для добавления и обновления сеток; Мы выполним цикл по сбору нашего приложения и проверяем, есть ли **идентификатор GUID** в коллекции системы. Если он отсутствует в системной коллекции, мы удалим его из нашей.

Из нашего обработчика событий в Аппмаин. cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

Реализация удаления сетки в Реалтимесурфацемешрендерер. cpp:

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Получение и использование буферов данных для сетки поверхности

Получение сведений о сетке поверхности было так же простым, как извлечение коллекции данных и обработка обновлений в этой коллекции. Теперь мы подробно рассмотрим, как можно использовать данные.

В нашем примере кода мы решили использовать сетки Surface для отрисовки. Это распространенный сценарий для окклудингных голограмм, стоящих за реальными областями. Можно также визуализировать сетки или визуализировать обработанные версии, чтобы увидеть, какие области комнаты просматриваются, прежде чем приступить к работе с функциями приложения или игры.

Пример кода запускает процесс при получении обновлений сетки Surface из обработчика событий, описанного в предыдущем разделе. Важной строкой кода в этой функции является вызов обновления *сетки*поверхности: на этот раз мы уже обработали сведения о сетке, и мы будем получать данные об вершинах и индексах, которые будут использоваться, как видно.

Из Реалтимесурфацемешрендерер. cpp:

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

Наш пример кода разработан таким образом, что класс данных **сурфацемеш**обрабатывает обработку и отрисовку данных в сети. Эти сетки — это то, что **реалтимесурфацемешрендерер** на самом деле сохраняет карту. У каждого из них есть ссылка на Спатиалсурфацемеш, и мы используем его в любой момент, когда нам нужно получить доступ к вершинной сетке или буферу индексов или получить преобразование для сетки. Сейчас мы помечаем сетку как требующую обновления.

Из Сурфацемеш. cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

В следующий раз, когда сетка получит запрос на прорисовку, сначала будет проверяться флаг. Если требуется обновление, буферы вершин и индексов будут обновлены на GPU.

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

Сначала мы получаем необработанные буферы данных:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Затем мы создадим буферы устройств Direct3D с данными сетки, предоставляемыми HoloLens:

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

**Примечание.** Для вспомогательной функции Креатедиректксбуффер, используемой в предыдущем фрагменте, см. пример кода сопоставления Surface: Сурфацемеш. cpp, Жетдатафромибуффер. h. Теперь создание ресурса устройства завершено, и сетка считается загруженной и готова к обновлению и визуализации.

### <a name="update-and-render-surface-meshes"></a>Обновление и отрисовка сеток поверхности

Наш класс Сурфацемеш имеет специализированную функцию Update. Каждый [спатиалсурфацемеш](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) имеет собственное преобразование, и в нашем примере используется текущая система координат для **спатиалстатионариреференцефраме** , чтобы получить преобразование. Затем он обновляет буфер констант модели на GPU.

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

Когда вы намерены приступить к отрисовке сеток Surface, мы выполняем некоторые подготовительные действия перед отрисовкой коллекции. Мы настроили конвейер шейдера для текущей конфигурации подготовки к просмотру и настроили этап ассемблера входных данных. Обратите внимание, что класс модуля поддержки holographic Camera **камераресаурцес. cpp** уже настроил буфер констант представления/проекции прямо сейчас.

Из **реалтимесурфацемешрендерер:: Render**:

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

По завершении этого цикла мы рассмотрим наши сети и поговорю, что каждый из них будет нарисован. **Примечание.** Этот пример кода не оптимизирован для использования какого-либо рода фрустумного отбора, но эту функцию следует включить в приложение.

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

Отдельные сети отвечают за настройку буферов вершин и индексов, а также буфера констант и преобразования модели. Как и в случае вращающегося куба в шаблоне приложения Windows holographic, мы подготавливаем буферы стереоскопик с помощью создания экземпляров.

Из **сурфацемеш::D RAW**:

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

### <a name="rendering-choices-with-surface-mapping"></a>Отрисовка вариантов с помощью сопоставления поверхности

Пример кода сопоставления Surface предлагает код для отрисовки данных в виде сетки поверхности перекрытия, а также для отображения данных в сетке поверхности на экране. Выбор пути зависит от приложения. В этом документе мы рассмотрим обе конфигурации.

**Отрисовка буферов перекрытия для holographic Effect**

Начните с очистки представления целевого объекта прорисовки для текущей виртуальной камеры.

Из Аппмаин. cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Это этап предварительной отрисовки. Здесь мы создадим буфер перекрытия, запросив для модуля подготовки к сетке глубину прорисовки только глубины. В этой конфигурации мы не подключим представление целевого объекта прорисовки, и модуль визуализации сетки задает для этапа Шейдер пикселей значение **nullptr** , чтобы GPU не проводился для рисования пикселей. Геометрия будет помещена в буфер глубины, а графический конвейер будет останавливаться.

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

Мы можем нарисовать голограммы с дополнительным тестом глубины по отношению к буферу сопоставления поверхности перекрытия. В этом примере кода выполняется отрисовка пикселов в Кубе по другому цвету, если они находятся за поверхностью.

Из Аппмаин. cpp:

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

На основе кода из СпеЦиалеффектпикселшадер. HLSL:

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

**Примечание.** Для нашей подпрограммы **гасердепслесс** см. пример кода сопоставления Surface: спеЦиалеффектпикселшадер. HLSL.

**Отображение данных сетки поверхности для отображения**

Кроме того, можно просто нарисовать сетки Surface в экранных буферах вывода. Мы решили нарисовать полные лица с освещением, но вы можете рисовать каркасную схему, обработать сетки перед отрисовкой, применить текстурную карту и т. д.

Здесь наш пример кода указывает, что модуль подготовки сетки рисует коллекцию. На этот раз мы не будем указывать проход только по глубине, поэтому он присоединяет шейдер пикселей и завершает конвейер отрисовки, используя целевые объекты, которые мы указали для текущей виртуальной камеры.

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>См. также:
* [Создание голографического проекта в DirectX](creating-a-holographic-directx-project.md)
* [API Windows. восприятие. пространственный](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
