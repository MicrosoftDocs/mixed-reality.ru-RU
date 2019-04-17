---
title: Системы координат в DirectX
description: Объясняет, как использовать Windows Mixed Reality пространственных указатели, опорными кадрами, пространственных привязки и системы координат, как использовать SpatialStage, способ обработки потери отслеживания, как сохранять и загружать привязки и как изображение стабилизации.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Смешанной реальности, пространственных локатора, пространственной кадра, пространственные системы координат, пространственных рабочей области, пример кода, стабилизацию изображения, пространственные привязки, пространственного хранилища привязки, отслеживания потери, пошаговое руководство
ms.openlocfilehash: c8cdb39cbf4634edb4ed0a595381fc70f1388ce4
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605153"
---
# <a name="coordinate-systems-in-directx"></a>Системы координат в DirectX

[Системы координат](coordinate-systems.md) формируют основу для пространственных основные сведения о предлагаемых интерфейсы API Windows смешанной реальности.

Современные сидели VR или устройств виртуальной Реальности единого места установки одной основной системы координат для представления отслеживаемых пространства. Устройства Windows Mixed Reality например HoloLens предназначены для использования в крупных средах неопределенным, с устройством, обнаружения и изучения окружающей среды, как пользователь просматривает вокруг. Это позволяет устройству для адаптации к непрерывно улучшать знания о комнаты пользователя, но результаты в системах координат, которые приводят к изменению их связь друг с другом в течение всего приложения. Windows Mixed Reality поддерживает широкий спектр устройств, от за кресло иммерсивную через подключенные world опорными кадрами.

>[!NOTE]
>Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).  Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.

## <a name="spatial-coordinate-systems-in-windows"></a>Пространственные системы координат в Windows

Тип core, используемый делать выводы о реальных системами координат в Windows является <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>. Экземпляр этого типа представляет произвольный систему координат и предоставляет метод для получения матрицы преобразования, который можно использовать для преобразования между двумя системами координат, не понимая подробнее.

Методы, которые возвращают Пространственные сведения представлены в виде точек, лучи или тома в окружения пользователя, будет принимать параметр SpatialCoordinateSystem позволяет решить система координат, в котором он особенно полезен для этих координаты должны быть возвращены. Единицы измерения для эти координаты всегда будет в метрах.

SpatialCoordinateSystem имеет динамический связь с другими системами координат, включая те, которые представляют положение устройства. В любой момент времени устройство может быть возможность найти некоторые системы координат и не разрешать этого другим. Для большинства систем координат приложение должно представлять Готово к обработке периодов времени, в течение которого не удается найти.

Приложения не следует создавать SpatialCoordinateSystems напрямую — скорее они занимают через интерфейсы API восприятие. Существует три основных источника системами координат в API-интерфейсы восприятие, каждая из которых сопоставлена понятие, которое описано в статье [системы координат](coordinate-systems.md) страницы:
* Чтобы получить стационарной системой отсчета координат, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> или получить из текущего <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.
* Чтобы получить пространственных привязки, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.
* Чтобы получить вложенное отсчета координат, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.

Все системы координат, возвращаемые этими объектами являются для правши с + y вверх + x справа и + z назад. Направление, в котором можно запомнить точек оси z — карточкой слева или справа в направлении положительного x и curling их в направлении y положительные. Направление, в котором указывают ваши пальцы (к вам или от вас), — это направление, в котором указывает положительная ось z в этой системе координат. На следующем рисунке показаны эти две системы координат.

![Левую и правую систем координат](images/left-hand-right-hand.gif)<br>
*Левую и правую систем координат*

Для начальной загрузки в SpatialCoordinateSystem, в соответствии с положением HoloLens, использовать <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> класс, чтобы создать либо присоединяемых или стационарные отсчета координат, как описано в следующих разделах.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Поместите голограммы мира с помощью пространственных этапа

Система координат для непрозрачного иммерсивную смешанной реальности Windows осуществляется с помощью статического <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> свойство. Этот API предоставляет в системе координат, сведения о ли установлен проигрыватель или мобильных устройств, граница безопасной области для прогулке по, если игрок мобильных устройств и сведения об ли гарнитура является направленным. Имеется также обработчик событий для обновлений в пространственных рабочую область.

Во-первых мы для получения пространственных рабочей области и Подпишитесь на обновления к нему. 

Код для **пространственных этапа инициализации**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

В методе OnCurrentChanged ваше приложение должно проверять пространственных рабочей области и соответствующим образом обновить интерфейс работы с проигрывателем. В этом примере мы предоставляем визуализации границ рабочей области, а также начальное положение, указанное пользователем, а также диапазон этого этапа, представления и диапазон перемещения свойств. Мы также связываться с нашего собственного стационарные системы координат, если не может поступать в рабочей области.


Код для **пространственных этап обновления**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

Набор вершины, определяющие границе рабочей области, указанные в порядке по часовой стрелке. Оболочка Windows Mixed Reality рисует барьер, расположенным на границе, приближается к пользователю. Вы можете triangularize области неанализируемой по своему усмотрению. Чтобы triangularize рабочей области можно использовать следующий алгоритм.


Код для **triangularization пространственных рабочей области**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Поместите голограммы мира с помощью стационарной системой отсчета координат

[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) класс представляет кадр сослаться на него, [остается на месте](coordinate-systems.md#stationary-frame-of-reference) относительно окружения пользователя, как пользователь перемещается. Это подразумевает определяет приоритеты хранения координаты стабильной рядом с устройства. Один ключа SpatialStationaryFrameOfReference используется в качестве базовой мировая система координат в механизм визуализации при отрисовке голограммы.

Чтобы получить SpatialStationaryFrameOfReference, используйте [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) класса и вызове [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).

С Windows Holographic код шаблона приложения:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Стационарные опорными кадрами призваны обеспечить наилучшее позиции относительно общего пространства. Отдельные позиции, в рамках этого окна ссылок могут немного неверно. Это нормально, так как устройство сторона узнает больше о среде.
* Если требуется точное расположение отдельных голограммы, SpatialAnchor следует использовать для привязки отдельных голограмма в позицию в реальном мире — например, точку пользователь указывает наибольший интерес. Позиции привязки не переместятся, но может быть исправлено. привязка будет использовать исправленный позиции, начиная в следующем фрейме, после исправления.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Поместите голограммы мира с помощью пространственных привязки

[Пространственные привязки](coordinate-systems.md#spatial-anchors) являются отличным способом поместить голограммы в определенном месте в реальном мире, в системе обеспечение привязки остается на месте со временем. В этом разделе объясняется, как создать и использовать привязку, а также способы работы с данными для привязки.

Вы можете создать SpatialAnchor в любой позиции и ориентации в SpatialCoordinateSystem по своему выбору. Устройство необходимо иметь возможность найти этой системы координат на данный момент и система не должен иметь достиг ограничения пространственных якорей.

После определения система координат SpatialAnchor постоянно изменяется, чтобы сохранить точное положение и ориентацию его исходное расположение. Затем можно использовать этот SpatialAnchor для подготовки к просмотру голограммы, которые будут отображаться предопределенной в окружения пользователя точное положение.

Последствия изменения, которые храните привязки в месте обостряются, как расстояние от увеличения привязки. Таким образом следует избегать отрисовки содержимого относительно привязкой, более 3 м от начала эту привязку.

[Система CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) свойство получает системы координат, которая позволяет размещать содержимое относительно привязки, с реалистичной анимации, когда устройство корректирует точное расположение привязки.

Используйте [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) свойства и соответствующие [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) событий самостоятельно управлять следующие поправки.

### <a name="persist-and-share-spatial-anchors"></a>Сохранять и совместно использовать Пространственные привязки

Можно сохранить локально с помощью SpatialAnchor [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) класса, а затем получите его обратно в сеансе будущих приложений на одном устройстве HoloLens.

С помощью <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a>, можно создать привязку надежные облачные из локального SpatialAnchor, который приложения можно найти в нескольких HoloLens, iOS и устройств Android.  Совместное использование общих пространственных привязки на нескольких устройствах, каждый пользователь может видеть содержимое отображается относительно эту привязку, в том же физическом расположении.  Это позволяет выполнять публикацию в режиме реального времени.

Можно также использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a> для асинхронной голограмма сохраняемости на устройствах Android, iOS и HoloLens.  По электронной почте на привязку пространственных надежные облачные, несколько устройств можно наблюдать за же материализованных голограмма со временем, даже если эти устройства не существуют друг с другом в то же время.

Чтобы приступить к работе, создания общих возможностей в приложении HoloLens, изучите 5-минутные <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">быстрого запуска Azure пространственных привязки HoloLens</a>.

После того, как приступить к работе с пространственными привязки Azure, вы можете затем <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">создать и найдите привязки на HoloLens</a>.  Доступны пошаговые руководства для <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android и iOS</a> также, что позволяет совместно использовать же привязки на всех устройствах.

### <a name="create-spatialanchors-for-holographic-content"></a>Создание SpatialAnchors holographic содержимого

Этот пример кода, мы изменили Windows Holographic привязывает шаблон приложения для создания, когда **Pressed** обнаружении жеста. Затем куба помещается у привязки во время прохода отрисовки.

Так как вспомогательный класс поддерживает несколько привязок, будет расположен столько кубы, так как нам нужно, использование этого образца кода!

Обратите внимание, что идентификаторы для привязки кое-что управления в приложении. В этом примере мы создали схему именования, который выполняется последовательно в зависимости от количества привязки, хранящихся в коллекции приложений якорей.

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Асинхронно загрузки и кэширования, SpatialAnchorStore

Давайте посмотрим, как написать класс SampleSpatialAnchorHelper, которая помогает обрабатывать этот сохраняемости, включая:
* Хранить коллекцию привязок в памяти, индексированных по ключу Platform::String.
* Загружает привязки из SpatialAnchorStore системы, который хранится отдельно от локальной коллекции в памяти.
* Идет сохранение локальной коллекции в памяти якорей SpatialAnchorStore при выборе этого приложения.

Вот как можно сохранить [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) объекты в [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

При запуске класса запрашивается SpatialAnchorStore асинхронно. Это включает системы ввода-вывода, как API загружает хранилище привязки, и этот API выполняется асинхронный таким образом, чтобы ввод-вывод является без блокировки.

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

Вам будет предоставлена SpatialAnchorStore, который можно использовать для сохранения привязки. Это IMapView, связывающий значениями ключа, которые представляют собой строки, со значениями данных, которые являются SpatialAnchors. В нашем примере кода мы сохраните его в переменную-член закрытого класса, доступном через открытую функцию нашего вспомогательного класса.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>Не забудьте подключить события приостановки и возобновления для сохранения и загрузки в хранилище привязки.

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>Сохранить содержимое в хранилище привязки

Когда система приостанавливает приложение, необходимо сохранить ваши Пространственные привязки в хранилище привязки. Также можно сохранить привязки в хранилище привязки в других случаях, как найти необходимые для реализации вашего приложения.

Когда вы будете готовы повторить сохранение SpatialAnchorStore привязки в памяти, можно организовать цикл по коллекции и попробуйте сохранить каждого из них.

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Загрузить содержимое из хранилища привязки, когда приложение возобновляет работу

Когда приложение возобновляет работу, или в любое другое время, необходимые для вашего приложения implementaiton, вы можете восстановить привязки, которые ранее были сохранены в AnchorStore, передавая их из магазина привязки IMapView собственную базу данных в памяти по SpatialAnchors.

Чтобы восстановить привязки из SpatialAnchorStore, восстановите каждого из них, которые вас интересуют к собственной коллекции в памяти.

Вам потребуется собственную базу данных в памяти по SpatialAnchors; какой-либо способ связать с SpatialAnchors, создаваемой строки. В нашем примере кода мы решили использовать Windows::Foundation::Collections::IMap для хранения привязки, что позволяет легко использовать то же значение ключа и данных для SpatialAnchorStore.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Это привязка, восстанавливается может оказаться может быть найдена прямо сейчас. Например возможно, привязку в другой комнате или вообще другой построения. Привязки, полученные из AnchorStore должны тестироваться для locatability перед их использованием.

<br>

>[!NOTE]
>В этом примере кода мы получить все ссылки из AnchorStore. Это не является обязательным; приложение может точно так же выбирать определенные подмножества привязки с помощью строковых значений ключей, которые важны для вашей реализации.

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>Очистить хранилище привязки, при необходимости

В некоторых случаях необходимо очистить состояние приложения и записывать новые данные. Вот как это сделать с помощью [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

С помощью наших вспомогательного класса, почти ненужные оболочка для функции очистки. Мы решили сделать это в наш пример реализации, поскольку наши вспомогательный класс является выдается ответственность объекта-владельца экземпляра SpatialAnchorStore.

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Пример. Относящиеся к системы координат кадра стационарные ссылки привязки системы координат

Предположим, у вас есть привязки, что вы хотите что-то в системе координат вашей привязки связаны с SpatialStationaryReferenceFrame, который вы уже используете для большинства других содержимого. Можно использовать [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) для получения преобразование из системы координат точку привязки, кадра стационарные ссылки:

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

Это полезно для вас двумя способами:
1. Он сообщает, что вы, если два ссылаются на кадры можно воспринимать относительно друг друга, и;
2. Если Да, предоставляет преобразование для перехода непосредственно из одной системы координат в другую.

Имея эту информацию вы понимаете пространственного отношения между объектами между двумя опорными кадрами.

Для подготовки к просмотру, можно часто получить лучшие результаты путем группирования объектов в соответствии с их исходным блоком ссылку или привязки. Выполните отдельном проходе рисования для каждой группы. Представление матрицы является более точным для объектов с преобразованиями модели, которые создаются первоначально с помощью той же системе координат.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Создание голограммы, используя устройство подключено для ссылок

Бывают случаи, когда, в который требуется визуализировать голограмма, [остается прикрепленным](coordinate-systems.md#attached-frame-of-reference) расположение устройства, например панель с отладкой сведения или информационное сообщение, когда устройство находится только возможность определить, ориентация и не его положение в пространстве. Для этого мы используем присоединенного отсчета координат.

Класс SpatialLocatorAttachedFrameOfReference определяет системы координат, которые являются относительно устройства, а не в реальной жизни. Он содержит заголовок предопределенной относительно окружения пользователя, на которые указывает в направлении пользователь был с выходом во время создания кадра ссылку. После этого для всех направлениях в этой системой отсчета координат относительны этот заголовок, фиксированный, даже при повороте устройства.

Для HoloLens начало системы координат данного кадра находится в центре поворот головы пользователя, таким образом, чтобы его положение не зависит от головного поворота. Приложение может указать смещение относительно этой точки, чтобы изменить расположение голограммы глазах у пользователя.

Чтобы получить SpatialLocatorAttachedFrameOfReference, используйте класс SpatialLocator и вызвать CreateAttachedFrameOfReferenceAtCurrentHeading.

Обратите внимание на то, что это относится к устройствам весь диапазон из Windows смешанной реальности.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Используйте фрейм ссылки, связанные с устройством

Эти разделы поговорим о мы изменили в Windows Holographic шаблон приложения, чтобы включить устройство подключено для ссылок с помощью этого API. Обратите внимание, что это «вложенных» голограмма тесно связаны стационарным или привязанные голограммы также может использоваться, когда устройство находится временно не удается найти его положение в мире.

Во-первых мы изменили шаблона для хранения SpatialLocatorAttachedFrameOfReference вместо SpatialStationaryFrameOfReference:

Из **HolographicTagAlongSampleMain.h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Из **HolographicTagAlongSampleMain.cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Во время обновления теперь мы получаем систему координат с отметкой времени, полученные с прогнозированием кадра.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Получить позу пространственных указатель, а затем следуйте взглядом пользователя

Мы хотим, чтобы наш пример голограмма следовать пользователя [помощи](gaze.md)подобно тому, как holographic оболочки могут проследовать по взглядом пользователя. Для этого нам нужно получить SpatialPointerPose из той же отметкой времени.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Этот SpatialPointerPose содержит сведения, необходимые для размещения голограмма согласно [пользователя текущего заголовка](gaze,-gestures,-and-motion-controllers-in-directx.md).

Из соображений удобства пользователя мы используем линейную интерполяцию («lerp») для сглаживания изменения позиции, таким образом, чтобы она выполнялась в течение времени. Это более удобны для пользователя, чем блокировка голограмма для их взглядом. Lerping, положение tag-along голограмма также позволяет стабилизировать голограмма по гашение перемещения; Если мы не сделает этого гашение, пользователь мог видеть голограмма нарушение синхронизации из-за то, что обычно считаются долог перемещений головы пользователя.

Из **StationaryQuadRenderer::PositionHologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>В случае отладки панели можно изменить положение голограмма off на сторону немного, чтобы он не мешали представления. Ниже приведен пример того, как это может выполнить.

Для **StationaryQuadRenderer::PositionHologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>Поворот голограмма для сталкиваются с камеры

Не достаточно, чтобы просто поместите голограмма, который в данном случае является quad; Мы также необходимо повернуть объект столкнуться пользователь. Обратите внимание на то, что происходит этот вращение в абсолютном пространстве, так как этот тип биллбординга позволяет голограмма остаются частью среды пользователя. Биллбординга пространстве представления не ваттными, так как она блокируется для ориентацией экрана; в этом случае также пришлось бы выполнять интерполяцию между левым и правым представление матрицы для получения преобразование элемент с объявлением пространства представления, которое не нарушает стерео отрисовки. Здесь мы Повернуть на осях X и Z, чтобы пользователь.

Из **StationaryQuadRenderer::Update**:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>Визуализации присоединенного голограмма

В этом примере мы также решили отрисовки голограмма в системе координат SpatialLocatorAttachedReferenceFrame, являющийся мы как расположены голограмма. (Если бы решили просто для подготовки к просмотру с помощью другой системы координат, необходимо получить преобразование из системы координат рамки устройство подключено ссылку на эту систему координат).

Из **HolographicTagAlongSampleMain::Render**:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

Вот и все! Она будет теперь «отслеживаются» позицию 2 м перед направление взглядом пользователя.

>[!NOTE]
>Кроме того, в этом примере загружает дополнительное содержимое — см. в разделе StationaryQuadRenderer.cpp.

## <a name="handling-tracking-loss"></a>Обработка отслеживание потери

Если устройство не может найти сам в мире, приложение интерфейсы «отслеживания потери». Приложения Windows Mixed Reality должны иметь возможность обрабатывать перебоев в системе позиционные отслеживания. Можно просмотреть эти нарушений в работе и создания ответов с помощью LocatabilityChanged событие по умолчанию SpatialLocator.

Из **AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Когда приложение получает событие LocatabilityChanged, можно изменить поведение, при необходимости. Например, в состоянии PositionalTrackingInhibited, приложение можно приостановить нормальной работы и отображения [tag-along голограмма](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) , выводит предупреждающее сообщение.

Windows Holographic шаблон приложения поставляется с уже созданным LocatabilityChanged обработчик. По умолчанию отображается предупреждение в консоли отладки при недоступности позиционные отслеживания. Можно добавить код в этот обработчик для предоставления ответа при необходимости из вашего приложения.

Из **AppMain.cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>Пространственное сопоставление

[Пространственное сопоставление](spatial-mapping-in-directx.md) API-интерфейсов использования систем координат, чтобы получить преобразования модели для поверхности сетки.

## <a name="see-also"></a>См. также
* [Системы координат](coordinate-systems.md)
* [Пространственные привязки](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure пространственных привязки</a>
* [Взглядом, жесты и контроллеры движения в DirectX](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [Пространственное сопоставление в DirectX](spatial-mapping-in-directx.md)
