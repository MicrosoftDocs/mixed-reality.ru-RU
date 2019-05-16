---
title: Системы координат в DirectX
description: Объясняет, как использовать Windows Mixed Reality пространственных указатели, опорными кадрами, пространственных привязки и системы координат, как использовать SpatialStage, способ обработки потери отслеживания, как сохранять и загружать привязки и как изображение стабилизации.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Смешанной реальности, пространственных локатора, пространственной кадра, пространственные системы координат, пространственных рабочей области, пример кода, стабилизацию изображения, пространственные привязки, пространственного хранилища привязки, отслеживания потери, пошаговое руководство
ms.openlocfilehash: 5a48e0a829ba8647718e28ec20760d8a764b13fe
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628975"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="79921-104">Системы координат в DirectX</span><span class="sxs-lookup"><span data-stu-id="79921-104">Coordinate systems in DirectX</span></span>

<span data-ttu-id="79921-105">[Системы координат](coordinate-systems.md) формируют основу для пространственных основные сведения о предлагаемых интерфейсы API Windows смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="79921-105">[Coordinate systems](coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="79921-106">Современные сидели VR или устройств виртуальной Реальности единого места установки одной основной системы координат для представления отслеживаемых пространства.</span><span class="sxs-lookup"><span data-stu-id="79921-106">Today's seated VR or single-room VR devices establish one primary coordinate system to represent their tracked space.</span></span> <span data-ttu-id="79921-107">Устройства Windows Mixed Reality например HoloLens предназначены для использования в крупных средах неопределенным, с устройством, обнаружения и изучения окружающей среды, как пользователь просматривает вокруг.</span><span class="sxs-lookup"><span data-stu-id="79921-107">Windows Mixed Reality devices such as HoloLens are designed to be used throughout large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="79921-108">Это позволяет устройству для адаптации к непрерывно улучшать знания о комнаты пользователя, но результаты в системах координат, которые приводят к изменению их связь друг с другом в течение всего приложения.</span><span class="sxs-lookup"><span data-stu-id="79921-108">This allows the device to adapt to continually-improving knowledge about the user's rooms, but results in coordinate systems that will change their relationship to one another through the lifetime of the app.</span></span> <span data-ttu-id="79921-109">Windows Mixed Reality поддерживает широкий спектр устройств, от за кресло иммерсивную через подключенные world опорными кадрами.</span><span class="sxs-lookup"><span data-stu-id="79921-109">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="79921-110">Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="79921-110">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="79921-111">Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.</span><span class="sxs-lookup"><span data-stu-id="79921-111">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="79921-112">Пространственные системы координат в Windows</span><span class="sxs-lookup"><span data-stu-id="79921-112">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="79921-113">Тип core, используемый делать выводы о реальных системами координат в Windows является <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span><span class="sxs-lookup"><span data-stu-id="79921-113">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="79921-114">Экземпляр этого типа представляет произвольный систему координат и предоставляет метод для получения матрицы преобразования, который можно использовать для преобразования между двумя системами координат, не понимая подробнее.</span><span class="sxs-lookup"><span data-stu-id="79921-114">An instance of this type represents an arbitrary coordinate system and provides a method to get a transformation matrix that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="79921-115">Методы, которые возвращают Пространственные сведения представлены в виде точек, лучи или тома в окружения пользователя, будет принимать параметр SpatialCoordinateSystem позволяет решить система координат, в котором он особенно полезен для этих координаты должны быть возвращены.</span><span class="sxs-lookup"><span data-stu-id="79921-115">Methods that return spatial information, represented as points, rays, or volumes in the user's surroundings, will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="79921-116">Единицы измерения для эти координаты всегда будет в метрах.</span><span class="sxs-lookup"><span data-stu-id="79921-116">The units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="79921-117">SpatialCoordinateSystem имеет динамический связь с другими системами координат, включая те, которые представляют положение устройства.</span><span class="sxs-lookup"><span data-stu-id="79921-117">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="79921-118">В любой момент времени устройство может быть возможность найти некоторые системы координат и не разрешать этого другим.</span><span class="sxs-lookup"><span data-stu-id="79921-118">At any point in time, the device may be able to locate some coordinate systems and not others.</span></span> <span data-ttu-id="79921-119">Для большинства систем координат приложение должно представлять Готово к обработке периодов времени, в течение которого не удается найти.</span><span class="sxs-lookup"><span data-stu-id="79921-119">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="79921-120">Приложения не следует создавать SpatialCoordinateSystems напрямую — скорее они занимают через интерфейсы API восприятие.</span><span class="sxs-lookup"><span data-stu-id="79921-120">Your application should not create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="79921-121">Существует три основных источника системами координат в API-интерфейсы восприятие, каждая из которых сопоставлена понятие, которое описано в статье [системы координат](coordinate-systems.md) страницы:</span><span class="sxs-lookup"><span data-stu-id="79921-121">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](coordinate-systems.md) page:</span></span>
* <span data-ttu-id="79921-122">Чтобы получить стационарной системой отсчета координат, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> или получить из текущего <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="79921-122">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="79921-123">Чтобы получить пространственных привязки, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span><span class="sxs-lookup"><span data-stu-id="79921-123">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="79921-124">Чтобы получить вложенное отсчета координат, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="79921-124">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="79921-125">Все системы координат, возвращаемые этими объектами являются для правши с + y вверх + x справа и + z назад.</span><span class="sxs-lookup"><span data-stu-id="79921-125">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="79921-126">Направление, в котором можно запомнить точек оси z — карточкой слева или справа в направлении положительного x и curling их в направлении y положительные.</span><span class="sxs-lookup"><span data-stu-id="79921-126">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="79921-127">Направление, в котором указывают ваши пальцы (к вам или от вас), — это направление, в котором указывает положительная ось z в этой системе координат.</span><span class="sxs-lookup"><span data-stu-id="79921-127">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="79921-128">На следующем рисунке показаны эти две системы координат.</span><span class="sxs-lookup"><span data-stu-id="79921-128">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="79921-129">![Левую и правую систем координат](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="79921-129">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="79921-130">*Левую и правую систем координат*</span><span class="sxs-lookup"><span data-stu-id="79921-130">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="79921-131">Для начальной загрузки в SpatialCoordinateSystem, в соответствии с положением HoloLens, использовать <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> класс, чтобы создать либо присоединяемых или стационарные отсчета координат, как описано в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="79921-131">To bootstrap into a SpatialCoordinateSystem based on the position of a HoloLens, use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference, as described in the sections below.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="79921-132">Поместите голограммы мира с помощью пространственных этапа</span><span class="sxs-lookup"><span data-stu-id="79921-132">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="79921-133">Система координат для непрозрачного иммерсивную смешанной реальности Windows осуществляется с помощью статического <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> свойство.</span><span class="sxs-lookup"><span data-stu-id="79921-133">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="79921-134">Этот API предоставляет в системе координат, сведения о ли установлен проигрыватель или мобильных устройств, граница безопасной области для прогулке по, если игрок мобильных устройств и сведения об ли гарнитура является направленным.</span><span class="sxs-lookup"><span data-stu-id="79921-134">This API provides a coordinate system, information about whether the player is seated or mobile, the boundary of a safe area for walking around if the player is mobile, and an indication of whether or not the headset is directional.</span></span> <span data-ttu-id="79921-135">Имеется также обработчик событий для обновлений в пространственных рабочую область.</span><span class="sxs-lookup"><span data-stu-id="79921-135">There is also an event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="79921-136">Во-первых мы для получения пространственных рабочей области и Подпишитесь на обновления к нему.</span><span class="sxs-lookup"><span data-stu-id="79921-136">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="79921-137">Код для **пространственных этапа инициализации**</span><span class="sxs-lookup"><span data-stu-id="79921-137">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="79921-138">В методе OnCurrentChanged ваше приложение должно проверять пространственных рабочей области и соответствующим образом обновить интерфейс работы с проигрывателем.</span><span class="sxs-lookup"><span data-stu-id="79921-138">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience accordingly.</span></span> <span data-ttu-id="79921-139">В этом примере мы предоставляем визуализации границ рабочей области, а также начальное положение, указанное пользователем, а также диапазон этого этапа, представления и диапазон перемещения свойств.</span><span class="sxs-lookup"><span data-stu-id="79921-139">In this example, we provide a visualization of the stage boundary, as well as the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="79921-140">Мы также связываться с нашего собственного стационарные системы координат, если не может поступать в рабочей области.</span><span class="sxs-lookup"><span data-stu-id="79921-140">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="79921-141">Код для **пространственных этап обновления**</span><span class="sxs-lookup"><span data-stu-id="79921-141">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="79921-142">Набор вершины, определяющие границе рабочей области, указанные в порядке по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="79921-142">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="79921-143">Оболочка Windows Mixed Reality рисует барьер, расположенным на границе, приближается к пользователю. Вы можете triangularize области неанализируемой по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="79921-143">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it; you may wish to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="79921-144">Чтобы triangularize рабочей области можно использовать следующий алгоритм.</span><span class="sxs-lookup"><span data-stu-id="79921-144">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="79921-145">Код для **triangularization пространственных рабочей области**</span><span class="sxs-lookup"><span data-stu-id="79921-145">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="79921-146">Поместите голограммы мира с помощью стационарной системой отсчета координат</span><span class="sxs-lookup"><span data-stu-id="79921-146">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="79921-147">[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) класс представляет кадр сослаться на него, [остается на месте](coordinate-systems.md#stationary-frame-of-reference) относительно окружения пользователя, как пользователь перемещается.</span><span class="sxs-lookup"><span data-stu-id="79921-147">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="79921-148">Это подразумевает определяет приоритеты хранения координаты стабильной рядом с устройства.</span><span class="sxs-lookup"><span data-stu-id="79921-148">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="79921-149">Один ключа SpatialStationaryFrameOfReference используется в качестве базовой мировая система координат в механизм визуализации при отрисовке голограммы.</span><span class="sxs-lookup"><span data-stu-id="79921-149">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="79921-150">Чтобы получить SpatialStationaryFrameOfReference, используйте [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) класса и вызове [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span><span class="sxs-lookup"><span data-stu-id="79921-150">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="79921-151">С Windows Holographic код шаблона приложения:</span><span class="sxs-lookup"><span data-stu-id="79921-151">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="79921-152">Стационарные опорными кадрами призваны обеспечить наилучшее позиции относительно общего пространства.</span><span class="sxs-lookup"><span data-stu-id="79921-152">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="79921-153">Отдельные позиции, в рамках этого окна ссылок могут немного неверно.</span><span class="sxs-lookup"><span data-stu-id="79921-153">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="79921-154">Это нормально, так как устройство сторона узнает больше о среде.</span><span class="sxs-lookup"><span data-stu-id="79921-154">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="79921-155">Если требуется точное расположение отдельных голограммы, SpatialAnchor следует использовать для привязки отдельных голограмма в позицию в реальном мире — например, точку пользователь указывает наибольший интерес.</span><span class="sxs-lookup"><span data-stu-id="79921-155">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="79921-156">Позиции привязки не переместятся, но может быть исправлено. привязка будет использовать исправленный позиции, начиная в следующем фрейме, после исправления.</span><span class="sxs-lookup"><span data-stu-id="79921-156">Anchor positions do not drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="79921-157">Поместите голограммы мира с помощью пространственных привязки</span><span class="sxs-lookup"><span data-stu-id="79921-157">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="79921-158">[Пространственные привязки](coordinate-systems.md#spatial-anchors) являются отличным способом поместить голограммы в определенном месте в реальном мире, в системе обеспечение привязки остается на месте со временем.</span><span class="sxs-lookup"><span data-stu-id="79921-158">[Spatial anchors](coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="79921-159">В этом разделе объясняется, как создать и использовать привязку, а также способы работы с данными для привязки.</span><span class="sxs-lookup"><span data-stu-id="79921-159">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="79921-160">Вы можете создать SpatialAnchor в любой позиции и ориентации в SpatialCoordinateSystem по своему выбору.</span><span class="sxs-lookup"><span data-stu-id="79921-160">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="79921-161">Устройство необходимо иметь возможность найти этой системы координат на данный момент и система не должен иметь достиг ограничения пространственных якорей.</span><span class="sxs-lookup"><span data-stu-id="79921-161">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="79921-162">После определения система координат SpatialAnchor постоянно изменяется, чтобы сохранить точное положение и ориентацию его исходное расположение.</span><span class="sxs-lookup"><span data-stu-id="79921-162">Once defined, the coordinate system of a SpatialAnchor adjusts continually to retain the precise position and orientation of its initial location.</span></span> <span data-ttu-id="79921-163">Затем можно использовать этот SpatialAnchor для подготовки к просмотру голограммы, которые будут отображаться предопределенной в окружения пользователя точное положение.</span><span class="sxs-lookup"><span data-stu-id="79921-163">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="79921-164">Последствия изменения, которые храните привязки в месте обостряются, как расстояние от увеличения привязки.</span><span class="sxs-lookup"><span data-stu-id="79921-164">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="79921-165">Таким образом следует избегать отрисовки содержимого относительно привязкой, более 3 м от начала эту привязку.</span><span class="sxs-lookup"><span data-stu-id="79921-165">Therefore, you should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="79921-166">[Система CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) свойство получает системы координат, которая позволяет размещать содержимое относительно привязки, с реалистичной анимации, когда устройство корректирует точное расположение привязки.</span><span class="sxs-lookup"><span data-stu-id="79921-166">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="79921-167">Используйте [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) свойства и соответствующие [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) событий самостоятельно управлять следующие поправки.</span><span class="sxs-lookup"><span data-stu-id="79921-167">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="79921-168">Сохранять и совместно использовать Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="79921-168">Persist and share spatial anchors</span></span>

<span data-ttu-id="79921-169">Можно сохранить локально с помощью SpatialAnchor [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) класса, а затем получите его обратно в сеансе будущих приложений на одном устройстве HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79921-169">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="79921-170">С помощью <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a>, можно создать привязку надежные облачные из локального SpatialAnchor, который приложения можно найти в нескольких HoloLens, iOS и устройств Android.</span><span class="sxs-lookup"><span data-stu-id="79921-170">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="79921-171">Совместное использование общих пространственных привязки на нескольких устройствах, каждый пользователь может видеть содержимое отображается относительно эту привязку, в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="79921-171">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="79921-172">Это позволяет выполнять публикацию в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="79921-172">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="79921-173">Можно также использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a> для асинхронной голограмма сохраняемости на устройствах Android, iOS и HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79921-173">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="79921-174">По электронной почте на привязку пространственных надежные облачные, несколько устройств можно наблюдать за же материализованных голограмма со временем, даже если эти устройства не существуют друг с другом в то же время.</span><span class="sxs-lookup"><span data-stu-id="79921-174">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="79921-175">Чтобы приступить к работе, создания общих возможностей в приложении HoloLens, изучите 5-минутные <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">быстрого запуска Azure пространственных привязки HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="79921-175">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="79921-176">После того, как приступить к работе с пространственными привязки Azure, вы можете затем <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">создать и найдите привязки на HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="79921-176">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="79921-177">Доступны пошаговые руководства для <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android и iOS</a> также, что позволяет совместно использовать же привязки на всех устройствах.</span><span class="sxs-lookup"><span data-stu-id="79921-177">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="79921-178">Создание SpatialAnchors holographic содержимого</span><span class="sxs-lookup"><span data-stu-id="79921-178">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="79921-179">Этот пример кода, мы изменили Windows Holographic привязывает шаблон приложения для создания, когда **Pressed** обнаружении жеста.</span><span class="sxs-lookup"><span data-stu-id="79921-179">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="79921-180">Затем куба помещается у привязки во время прохода отрисовки.</span><span class="sxs-lookup"><span data-stu-id="79921-180">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="79921-181">Так как вспомогательный класс поддерживает несколько привязок, будет расположен столько кубы, так как нам нужно, использование этого образца кода!</span><span class="sxs-lookup"><span data-stu-id="79921-181">Since multiple anchors are supported by the helper class, we can place as many cubes as we want using this code sample!</span></span>

<span data-ttu-id="79921-182">Обратите внимание, что идентификаторы для привязки кое-что управления в приложении.</span><span class="sxs-lookup"><span data-stu-id="79921-182">Note that the IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="79921-183">В этом примере мы создали схему именования, который выполняется последовательно в зависимости от количества привязки, хранящихся в коллекции приложений якорей.</span><span class="sxs-lookup"><span data-stu-id="79921-183">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="79921-184">Асинхронно загрузки и кэширования, SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="79921-184">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="79921-185">Давайте посмотрим, как написать класс SampleSpatialAnchorHelper, которая помогает обрабатывать этот сохраняемости, включая:</span><span class="sxs-lookup"><span data-stu-id="79921-185">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="79921-186">Хранить коллекцию привязок в памяти, индексированных по ключу Platform::String.</span><span class="sxs-lookup"><span data-stu-id="79921-186">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="79921-187">Загружает привязки из SpatialAnchorStore системы, который хранится отдельно от локальной коллекции в памяти.</span><span class="sxs-lookup"><span data-stu-id="79921-187">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="79921-188">Идет сохранение локальной коллекции в памяти якорей SpatialAnchorStore при выборе этого приложения.</span><span class="sxs-lookup"><span data-stu-id="79921-188">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="79921-189">Вот как можно сохранить [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) объекты в [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="79921-189">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="79921-190">При запуске класса запрашивается SpatialAnchorStore асинхронно.</span><span class="sxs-lookup"><span data-stu-id="79921-190">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="79921-191">Это включает системы ввода-вывода, как API загружает хранилище привязки, и этот API выполняется асинхронный таким образом, чтобы ввод-вывод является без блокировки.</span><span class="sxs-lookup"><span data-stu-id="79921-191">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="79921-192">Вам будет предоставлена SpatialAnchorStore, который можно использовать для сохранения привязки.</span><span class="sxs-lookup"><span data-stu-id="79921-192">You will be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="79921-193">Это IMapView, связывающий значениями ключа, которые представляют собой строки, со значениями данных, которые являются SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="79921-193">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="79921-194">В нашем примере кода мы сохраните его в переменную-член закрытого класса, доступном через открытую функцию нашего вспомогательного класса.</span><span class="sxs-lookup"><span data-stu-id="79921-194">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="79921-195">Не забудьте подключить события приостановки и возобновления для сохранения и загрузки в хранилище привязки.</span><span class="sxs-lookup"><span data-stu-id="79921-195">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="79921-196">Сохранить содержимое в хранилище привязки</span><span class="sxs-lookup"><span data-stu-id="79921-196">Save content to the anchor store</span></span>

<span data-ttu-id="79921-197">Когда система приостанавливает приложение, необходимо сохранить ваши Пространственные привязки в хранилище привязки.</span><span class="sxs-lookup"><span data-stu-id="79921-197">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="79921-198">Также можно сохранить привязки в хранилище привязки в других случаях, как найти необходимые для реализации вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="79921-198">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="79921-199">Когда вы будете готовы повторить сохранение SpatialAnchorStore привязки в памяти, можно организовать цикл по коллекции и попробуйте сохранить каждого из них.</span><span class="sxs-lookup"><span data-stu-id="79921-199">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="79921-200">Загрузить содержимое из хранилища привязки, когда приложение возобновляет работу</span><span class="sxs-lookup"><span data-stu-id="79921-200">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="79921-201">Когда приложение возобновляет работу, или в любое другое время, необходимые для вашего приложения implementaiton, вы можете восстановить привязки, которые ранее были сохранены в AnchorStore, передавая их из магазина привязки IMapView собственную базу данных в памяти по SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="79921-201">When your app resumes, or at any other time necessary for your app's implementaiton, you can restore anchors that were previously saved to the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors.</span></span>

<span data-ttu-id="79921-202">Чтобы восстановить привязки из SpatialAnchorStore, восстановите каждого из них, которые вас интересуют к собственной коллекции в памяти.</span><span class="sxs-lookup"><span data-stu-id="79921-202">To restore anchors from the SpatialAnchorStore, restore each one that you are interested in to your own in-memory collection.</span></span>

<span data-ttu-id="79921-203">Вам потребуется собственную базу данных в памяти по SpatialAnchors; какой-либо способ связать с SpatialAnchors, создаваемой строки.</span><span class="sxs-lookup"><span data-stu-id="79921-203">You need your own in-memory database of SpatialAnchors; some way to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="79921-204">В нашем примере кода мы решили использовать Windows::Foundation::Collections::IMap для хранения привязки, что позволяет легко использовать то же значение ключа и данных для SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="79921-204">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="79921-205">Это привязка, восстанавливается может оказаться может быть найдена прямо сейчас.</span><span class="sxs-lookup"><span data-stu-id="79921-205">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="79921-206">Например возможно, привязку в другой комнате или вообще другой построения.</span><span class="sxs-lookup"><span data-stu-id="79921-206">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="79921-207">Привязки, полученные из AnchorStore должны тестироваться для locatability перед их использованием.</span><span class="sxs-lookup"><span data-stu-id="79921-207">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="79921-208">В этом примере кода мы получить все ссылки из AnchorStore.</span><span class="sxs-lookup"><span data-stu-id="79921-208">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="79921-209">Это не является обязательным; приложение может точно так же выбирать определенные подмножества привязки с помощью строковых значений ключей, которые важны для вашей реализации.</span><span class="sxs-lookup"><span data-stu-id="79921-209">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="79921-210">Очистить хранилище привязки, при необходимости</span><span class="sxs-lookup"><span data-stu-id="79921-210">Clear the anchor store, when needed</span></span>

<span data-ttu-id="79921-211">В некоторых случаях необходимо очистить состояние приложения и записывать новые данные.</span><span class="sxs-lookup"><span data-stu-id="79921-211">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="79921-212">Вот как это сделать с помощью [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="79921-212">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="79921-213">С помощью наших вспомогательного класса, почти ненужные оболочка для функции очистки.</span><span class="sxs-lookup"><span data-stu-id="79921-213">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="79921-214">Мы решили сделать это в наш пример реализации, поскольку наши вспомогательный класс является выдается ответственность объекта-владельца экземпляра SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="79921-214">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="79921-215">Пример. Относящиеся к системы координат кадра стационарные ссылки привязки системы координат</span><span class="sxs-lookup"><span data-stu-id="79921-215">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="79921-216">Предположим, у вас есть привязки, что вы хотите что-то в системе координат вашей привязки связаны с SpatialStationaryReferenceFrame, который вы уже используете для большинства других содержимого.</span><span class="sxs-lookup"><span data-stu-id="79921-216">Let's say that you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame that you’re already using for most of your other content.</span></span> <span data-ttu-id="79921-217">Можно использовать [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) для получения преобразование из системы координат точку привязки, кадра стационарные ссылки:</span><span class="sxs-lookup"><span data-stu-id="79921-217">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to obtain a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="79921-218">Это полезно для вас двумя способами:</span><span class="sxs-lookup"><span data-stu-id="79921-218">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="79921-219">Он сообщает, что вы, если два ссылаются на кадры можно воспринимать относительно друг друга, и;</span><span class="sxs-lookup"><span data-stu-id="79921-219">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="79921-220">Если Да, предоставляет преобразование для перехода непосредственно из одной системы координат в другую.</span><span class="sxs-lookup"><span data-stu-id="79921-220">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="79921-221">Имея эту информацию вы понимаете пространственного отношения между объектами между двумя опорными кадрами.</span><span class="sxs-lookup"><span data-stu-id="79921-221">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="79921-222">Для подготовки к просмотру, можно часто получить лучшие результаты путем группирования объектов в соответствии с их исходным блоком ссылку или привязки.</span><span class="sxs-lookup"><span data-stu-id="79921-222">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="79921-223">Выполните отдельном проходе рисования для каждой группы.</span><span class="sxs-lookup"><span data-stu-id="79921-223">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="79921-224">Представление матрицы является более точным для объектов с преобразованиями модели, которые создаются первоначально с помощью той же системе координат.</span><span class="sxs-lookup"><span data-stu-id="79921-224">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="79921-225">Создание голограммы, используя устройство подключено для ссылок</span><span class="sxs-lookup"><span data-stu-id="79921-225">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="79921-226">Бывают случаи, когда, в который требуется визуализировать голограмма, [остается прикрепленным](coordinate-systems.md#attached-frame-of-reference) расположение устройства, например панель с отладкой сведения или информационное сообщение, когда устройство находится только возможность определить, ориентация и не его положение в пространстве.</span><span class="sxs-lookup"><span data-stu-id="79921-226">There are times when you want to render a hologram that [remains attached](coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="79921-227">Для этого мы используем присоединенного отсчета координат.</span><span class="sxs-lookup"><span data-stu-id="79921-227">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="79921-228">Класс SpatialLocatorAttachedFrameOfReference определяет системы координат, которые являются относительно устройства, а не в реальной жизни.</span><span class="sxs-lookup"><span data-stu-id="79921-228">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="79921-229">Он содержит заголовок предопределенной относительно окружения пользователя, на которые указывает в направлении пользователь был с выходом во время создания кадра ссылку.</span><span class="sxs-lookup"><span data-stu-id="79921-229">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="79921-230">После этого для всех направлениях в этой системой отсчета координат относительны этот заголовок, фиксированный, даже при повороте устройства.</span><span class="sxs-lookup"><span data-stu-id="79921-230">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="79921-231">Для HoloLens начало системы координат данного кадра находится в центре поворот головы пользователя, таким образом, чтобы его положение не зависит от головного поворота.</span><span class="sxs-lookup"><span data-stu-id="79921-231">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="79921-232">Приложение может указать смещение относительно этой точки, чтобы изменить расположение голограммы глазах у пользователя.</span><span class="sxs-lookup"><span data-stu-id="79921-232">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="79921-233">Чтобы получить SpatialLocatorAttachedFrameOfReference, используйте класс SpatialLocator и вызвать CreateAttachedFrameOfReferenceAtCurrentHeading.</span><span class="sxs-lookup"><span data-stu-id="79921-233">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="79921-234">Обратите внимание на то, что это относится к устройствам весь диапазон из Windows смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="79921-234">Note that this applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="79921-235">Используйте фрейм ссылки, связанные с устройством</span><span class="sxs-lookup"><span data-stu-id="79921-235">Use a reference frame attached to the device</span></span>

<span data-ttu-id="79921-236">Эти разделы поговорим о мы изменили в Windows Holographic шаблон приложения, чтобы включить устройство подключено для ссылок с помощью этого API.</span><span class="sxs-lookup"><span data-stu-id="79921-236">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="79921-237">Обратите внимание, что это «вложенных» голограмма тесно связаны стационарным или привязанные голограммы также может использоваться, когда устройство находится временно не удается найти его положение в мире.</span><span class="sxs-lookup"><span data-stu-id="79921-237">Note that this "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="79921-238">Во-первых мы изменили шаблона для хранения SpatialLocatorAttachedFrameOfReference вместо SpatialStationaryFrameOfReference:</span><span class="sxs-lookup"><span data-stu-id="79921-238">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="79921-239">Из **HolographicTagAlongSampleMain.h**:</span><span class="sxs-lookup"><span data-stu-id="79921-239">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="79921-240">Из **HolographicTagAlongSampleMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="79921-240">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="79921-241">Во время обновления теперь мы получаем систему координат с отметкой времени, полученные с прогнозированием кадра.</span><span class="sxs-lookup"><span data-stu-id="79921-241">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="79921-242">Получить позу пространственных указатель, а затем следуйте взглядом пользователя</span><span class="sxs-lookup"><span data-stu-id="79921-242">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="79921-243">Мы хотим, чтобы наш пример голограмма следовать пользователя [помощи](gaze.md)подобно тому, как holographic оболочки могут проследовать по взглядом пользователя.</span><span class="sxs-lookup"><span data-stu-id="79921-243">We want our example hologram to follow the user's [gaze](gaze.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="79921-244">Для этого нам нужно получить SpatialPointerPose из той же отметкой времени.</span><span class="sxs-lookup"><span data-stu-id="79921-244">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="79921-245">Этот SpatialPointerPose содержит сведения, необходимые для размещения голограмма согласно [пользователя текущего заголовка](gaze-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="79921-245">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="79921-246">Из соображений удобства пользователя мы используем линейную интерполяцию («lerp») для сглаживания изменения позиции, таким образом, чтобы она выполнялась в течение времени.</span><span class="sxs-lookup"><span data-stu-id="79921-246">For reasons of user comfort, we use linear interpolation ("lerp") to smooth the change in position such that it occurs over a period of time.</span></span> <span data-ttu-id="79921-247">Это более удобны для пользователя, чем блокировка голограмма для их взглядом.</span><span class="sxs-lookup"><span data-stu-id="79921-247">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="79921-248">Lerping, положение tag-along голограмма также позволяет стабилизировать голограмма по гашение перемещения; Если мы не сделает этого гашение, пользователь мог видеть голограмма нарушение синхронизации из-за то, что обычно считаются долог перемещений головы пользователя.</span><span class="sxs-lookup"><span data-stu-id="79921-248">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement; if we did not do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="79921-249">Из **StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="79921-249">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="79921-250">В случае отладки панели можно изменить положение голограмма off на сторону немного, чтобы он не мешали представления.</span><span class="sxs-lookup"><span data-stu-id="79921-250">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it does not obstruct your view.</span></span> <span data-ttu-id="79921-251">Ниже приведен пример того, как это может выполнить.</span><span class="sxs-lookup"><span data-stu-id="79921-251">Here's an example of how you might do that.</span></span>

<span data-ttu-id="79921-252">Для **StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="79921-252">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="79921-253">Поворот голограмма для сталкиваются с камеры</span><span class="sxs-lookup"><span data-stu-id="79921-253">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="79921-254">Не достаточно, чтобы просто поместите голограмма, который в данном случае является quad; Мы также необходимо повернуть объект столкнуться пользователь.</span><span class="sxs-lookup"><span data-stu-id="79921-254">It is not enough to simply position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="79921-255">Обратите внимание на то, что происходит этот вращение в абсолютном пространстве, так как этот тип биллбординга позволяет голограмма остаются частью среды пользователя.</span><span class="sxs-lookup"><span data-stu-id="79921-255">Note that this rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="79921-256">Биллбординга пространстве представления не ваттными, так как она блокируется для ориентацией экрана; в этом случае также пришлось бы выполнять интерполяцию между левым и правым представление матрицы для получения преобразование элемент с объявлением пространства представления, которое не нарушает стерео отрисовки.</span><span class="sxs-lookup"><span data-stu-id="79921-256">View-space billboarding is not as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices in order to acquire a view-space billboard transform that does not disrupt stereo rendering.</span></span> <span data-ttu-id="79921-257">Здесь мы Повернуть на осях X и Z, чтобы пользователь.</span><span class="sxs-lookup"><span data-stu-id="79921-257">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="79921-258">Из **StationaryQuadRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="79921-258">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="79921-259">Визуализации присоединенного голограмма</span><span class="sxs-lookup"><span data-stu-id="79921-259">Render the attached hologram</span></span>

<span data-ttu-id="79921-260">В этом примере мы также решили отрисовки голограмма в системе координат SpatialLocatorAttachedReferenceFrame, являющийся мы как расположены голограмма.</span><span class="sxs-lookup"><span data-stu-id="79921-260">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="79921-261">(Если бы решили просто для подготовки к просмотру с помощью другой системы координат, необходимо получить преобразование из системы координат рамки устройство подключено ссылку на эту систему координат).</span><span class="sxs-lookup"><span data-stu-id="79921-261">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="79921-262">Из **HolographicTagAlongSampleMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="79921-262">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="79921-263">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="79921-263">That's it!</span></span> <span data-ttu-id="79921-264">Она будет теперь «отслеживаются» позицию 2 м перед направление взглядом пользователя.</span><span class="sxs-lookup"><span data-stu-id="79921-264">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="79921-265">Кроме того, в этом примере загружает дополнительное содержимое — см. в разделе StationaryQuadRenderer.cpp.</span><span class="sxs-lookup"><span data-stu-id="79921-265">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="79921-266">Обработка отслеживание потери</span><span class="sxs-lookup"><span data-stu-id="79921-266">Handling tracking loss</span></span>

<span data-ttu-id="79921-267">Если устройство не может найти сам в мире, приложение интерфейсы «отслеживания потери».</span><span class="sxs-lookup"><span data-stu-id="79921-267">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="79921-268">Приложения Windows Mixed Reality должны иметь возможность обрабатывать перебоев в системе позиционные отслеживания.</span><span class="sxs-lookup"><span data-stu-id="79921-268">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="79921-269">Можно просмотреть эти нарушений в работе и создания ответов с помощью LocatabilityChanged событие по умолчанию SpatialLocator.</span><span class="sxs-lookup"><span data-stu-id="79921-269">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="79921-270">Из **AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="79921-270">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="79921-271">Когда приложение получает событие LocatabilityChanged, можно изменить поведение, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="79921-271">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="79921-272">Например, в состоянии PositionalTrackingInhibited, приложение можно приостановить нормальной работы и отображения [tag-along голограмма](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) , выводит предупреждающее сообщение.</span><span class="sxs-lookup"><span data-stu-id="79921-272">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="79921-273">Windows Holographic шаблон приложения поставляется с уже созданным LocatabilityChanged обработчик.</span><span class="sxs-lookup"><span data-stu-id="79921-273">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="79921-274">По умолчанию отображается предупреждение в консоли отладки при недоступности позиционные отслеживания.</span><span class="sxs-lookup"><span data-stu-id="79921-274">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="79921-275">Можно добавить код в этот обработчик для предоставления ответа при необходимости из вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="79921-275">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="79921-276">Из **AppMain.cpp:**</span><span class="sxs-lookup"><span data-stu-id="79921-276">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="79921-277">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="79921-277">Spatial mapping</span></span>

<span data-ttu-id="79921-278">[Пространственное сопоставление](spatial-mapping-in-directx.md) API-интерфейсов использования систем координат, чтобы получить преобразования модели для поверхности сетки.</span><span class="sxs-lookup"><span data-stu-id="79921-278">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="79921-279">См. также</span><span class="sxs-lookup"><span data-stu-id="79921-279">See also</span></span>
* [<span data-ttu-id="79921-280">Системы координат</span><span class="sxs-lookup"><span data-stu-id="79921-280">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="79921-281">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="79921-281">Spatial anchors</span></span>](spatial-anchors.md)
* <span data-ttu-id="79921-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a></span><span class="sxs-lookup"><span data-stu-id="79921-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="79921-283">HEAD и глаз взглядом в DirectX</span><span class="sxs-lookup"><span data-stu-id="79921-283">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="79921-284">Руки и контроллеры движения в DirectX</span><span class="sxs-lookup"><span data-stu-id="79921-284">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="79921-285">Пространственное сопоставление в DirectX</span><span class="sxs-lookup"><span data-stu-id="79921-285">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
