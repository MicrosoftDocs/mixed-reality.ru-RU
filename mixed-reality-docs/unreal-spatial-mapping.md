---
title: Пространственное сопоставление в Unreal
description: Руководство по применению пространственного сопоставления в Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, пространственное сопоставление
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840083"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="51963-104">Пространственное сопоставление в Unreal</span><span class="sxs-lookup"><span data-stu-id="51963-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="51963-105">Чтобы включить пространственное сопоставление в HoloLens, установите флажок Spatial Perception (Пространственное восприятие) в разделе Project Settings (Параметры проекта) > Platform (Платформа) > HoloLens > Capabilities (Возможности) редактора Unreal.</span><span class="sxs-lookup"><span data-stu-id="51963-105">To enable spatial mapping on HoloLens, ensure that the “Spatial Perception” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="51963-106">Чтобы применить пространственное сопоставление в игре на HoloLens, включите параметр Generate Mesh Data from Tracked Geometry (Генерировать данные сетки из отслеживаемой геометрии) в ARSessionConfig.</span><span class="sxs-lookup"><span data-stu-id="51963-106">To opt into using spatial mapping in a HoloLens game, enable the “Generate Mesh Data from Tracked Geometry” in the ARSessionConfig.</span></span>  <span data-ttu-id="51963-107">После этого подключаемый модуль HoloLens будет асинхронно получать данные пространственного сопоставления и выводить их в Unreal в виде MRMesh.</span><span class="sxs-lookup"><span data-stu-id="51963-107">The HoloLens plugin will then asynchronously get spatial mapping data and surface it to Unreal through the MRMesh.</span></span> 

![Хранилище пространственных привязок готово](images/unreal-spatialmapping-arsettings.PNG)

<span data-ttu-id="51963-109">Чтобы отслеживать отладочную визуализацию сетки пространственных сопоставлений, установите флажок Render Mesh Data in Wireframe (Визуализировать данные сетки в каркасе) в ARSessionConfig, чтобы для каждого треугольника MRMesh отображался белый контурный каркас.</span><span class="sxs-lookup"><span data-stu-id="51963-109">To see a debug visualization of the spatial mapping mesh, enable the “Render Mesh Data in Wireframe” checkbox in the ARSessionConfig to see a white wireframe outline of every triangle in the MRMesh.</span></span> 

<span data-ttu-id="51963-110">В разделе Project Settings (Параметры проекта) > Platform (Платформа) > HoloLens > Spatial Mapping (Пространственное сопоставление) можно изменить следующие параметры, чтобы изменить поведение пространственного сопоставления в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="51963-110">In Project Settings > Platform > HoloLens > Spatial Mapping, the following parameters can be modified to update spatial mapping’s runtime behavior:</span></span> 

![Параметры пространственных привязок для проекта](images/unreal-spatialmapping-projectsettings.PNG)

<span data-ttu-id="51963-112">Max Triangles Per Cubic Meter (Максимальное число треугольников на кубический метр) изменяет плотность треугольников в сетке пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="51963-112">Max Triangles Per Cubic Meter will update the density of the triangles in the spatial mapping mesh.</span></span>  <span data-ttu-id="51963-113">Spatial Meshing Volume Size (Размер объема для пространственных сеток) указывает размер куба вокруг игрока, в пределах которого будут отображаться и обновляться данные пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="51963-113">Spatial Meshing Volume Size indicates the size of the cube around the player to render and update spatial mapping data.</span></span>  <span data-ttu-id="51963-114">Если предполагается, что среда выполнения для приложения будет очень большой, в этом поле следует указать большое значение, чтобы оно лучше соответствовало реальному пространству.</span><span class="sxs-lookup"><span data-stu-id="51963-114">If the expected application runtime environment is expected to be large, this field may need to be large to match the real-world space.</span></span>  <span data-ttu-id="51963-115">И наоборот, если приложению нужны голограммы только на поверхностях рядом с пользователем, в этом поле можно указать небольшое значение.</span><span class="sxs-lookup"><span data-stu-id="51963-115">Conversely, if the application only needs to place holograms on surfaces immediately around the user, this field can be smaller.</span></span>  <span data-ttu-id="51963-116">По мере перемещения пользователя по игровому миру вместе с ним перемещается и пространство для пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="51963-116">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

<span data-ttu-id="51963-117">Чтобы использовать элемент MRMesh во время выполнения, добавьте к субъекту Blueprint (Схема) компонент AR Trackable Notify (Оповещение об отслеживаемой дополненной реальности).</span><span class="sxs-lookup"><span data-stu-id="51963-117">To get access to the MRMesh at runtime, first add an AR Trackable Notify Component to a Blueprint actor:</span></span> 

![AR Trackable Notify для пространственных привязок](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="51963-119">Затем перейдите к сведениям об этом компоненте и зелеными кнопками "+" выберите события для отслеживания.</span><span class="sxs-lookup"><span data-stu-id="51963-119">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span> 

![События пространственных привязок](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="51963-121">В этом случае мы отслеживаем событие On Add Tracked Geometry (При добавлении отслеживаемой геометрии), чтобы контролировать допустимые сетки, соответствующие данным пространственного сопоставления, и изменять материал этих сеток:</span><span class="sxs-lookup"><span data-stu-id="51963-121">In this case we monitor the On Add Tracked Geometry event looking for valid world meshes which correspond to spatial mapping data, and change the mesh’s material:</span></span> 

![Пример пространственных привязок](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="51963-123">В C++ можно подписаться на делегат OnTrackableAdded, чтобы получать элементы ARTrackedGeometry по мере доступности.</span><span class="sxs-lookup"><span data-stu-id="51963-123">In C++, we can subscribe to the OnTrackableAdded delegate to get the ARTrackedGeometry as soon as it is available.</span></span>  <span data-ttu-id="51963-124">Существуют аналогичные делегаты для событий обновления и удаления: AddOnTrackableUpdatedDelegate_Handle и AddOnTrackableRemovedDelegate_Handle.</span><span class="sxs-lookup"><span data-stu-id="51963-124">There are similar delegates for updated and removed events: AddOnTrackableUpdatedDelegate_Handle and AddOnTrackableRemovedDelegate_Handle.</span></span> 

![Код C++ для событий пространственных привязок](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="51963-126">В файле проекта Build.cs элемент AugmentedReality должен входить в список PublicDependencyModuleNames, чтобы добавить ARBlueprintLibrary.h и MRMesh для проверки компонента MRMesh в элементе UARTrackedGeometry.</span><span class="sxs-lookup"><span data-stu-id="51963-126">The project’s build.cs must have “AugmentedReality” in the PublicDependencyModuleNames list to include “ARBlueprintLibrary.h” and “MRMesh” to inspect the MRMesh component of the UARTrackedGeometry.</span></span> 

<span data-ttu-id="51963-127">Пространственное сопоставление — это не единственный тип данных, который предоставляется через ARTrackedGeometries, поэтому сначала мы проверяем соответствие EARObjectClassification и World, что подтверждает наличие геометрии пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="51963-127">Spatial mapping is not the only type of data that gets surfaced through ARTrackedGeometries, so we first check that the EARObjectClassification is World, which indicates that this is spatial mapping geometry.</span></span> 

## <a name="see-also"></a><span data-ttu-id="51963-128">См. также статью</span><span class="sxs-lookup"><span data-stu-id="51963-128">See also</span></span>
* [<span data-ttu-id="51963-129">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="51963-129">Spatial mapping</span></span>](spatial-mapping.md)
