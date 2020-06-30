---
title: Пространственное сопоставление в Unreal
description: Руководство по применению пространственного сопоставления в Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, пространственное сопоставление
ms.openlocfilehash: ffa57749cd96e240ac4812f950f4e13a6dbc68bd
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720410"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="f988f-104">Пространственное сопоставление в Unreal</span><span class="sxs-lookup"><span data-stu-id="f988f-104">Spatial Mapping in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="f988f-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="f988f-105">Overview</span></span>
<span data-ttu-id="f988f-106">Пространственное сопоставление позволяет помещать объекты на поверхности в физическом мире, показывая мир вокруг устройства HoloLens. За счет этого голограммы кажутся пользователю более реалистичными.</span><span class="sxs-lookup"><span data-stu-id="f988f-106">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="f988f-107">Кроме того, пространственное сопоставление обеспечивает привязку объектов в мире пользователя, пользуясь признаками глубины из реального мира. Это помогает создать у пользователя впечатление, что голограммы физически находятся в одном с ним пространстве. Если голограммы будут висеть в воздухе или перемещаться, ощущения пользователя будут не столь реалистичными.</span><span class="sxs-lookup"><span data-stu-id="f988f-107">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="f988f-108">При размещении объектов в пространстве нужно по возможности ориентироваться на комфорт.</span><span class="sxs-lookup"><span data-stu-id="f988f-108">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="f988f-109">Дополнительные сведения о качестве пространственного сопоставления, размещении объектов, загораживании, отрисовке и других аспектах см. в разделе справки "[Пространственное сопоставление](spatial-mapping.md)".</span><span class="sxs-lookup"><span data-stu-id="f988f-109">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="f988f-110">Включение пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="f988f-110">Enabling Spatial Mapping</span></span>

<span data-ttu-id="f988f-111">Чтобы включить пространственное сопоставление для HoloLens:</span><span class="sxs-lookup"><span data-stu-id="f988f-111">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="f988f-112">Выберите **Edit > Project Settings** (Правка > Параметры проекта) и прокрутите вниз до раздела **Platforms** (Платформы).</span><span class="sxs-lookup"><span data-stu-id="f988f-112">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="f988f-113">Выберите **HoloLens** и установите флажок **Spatial Perception** (Пространственное восприятие).</span><span class="sxs-lookup"><span data-stu-id="f988f-113">Select **HoloLens** and check **Spatial Perception**.</span></span>

<span data-ttu-id="f988f-114">Чтобы включить пространственное сопоставление (по умолчанию оно выключено) и отладить сетку **MRMesh** в игре для HoloLens:</span><span class="sxs-lookup"><span data-stu-id="f988f-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="f988f-115">Откройте компонент **ARSessionConfig** и разверните раздел **ARSettings > World Mapping** (Параметры дополненной реальности > Сопоставление мира).</span><span class="sxs-lookup"><span data-stu-id="f988f-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="f988f-116">Установите флажок **Generate Mesh Data from Tracked Geometry** (Генерировать данные сетки по отслеживаемой геометрии), который предписывает подключаемому модулю HoloLens начать асинхронную регистрацию данных пространственного сопоставления с выводом в Unreal посредством сетки **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="f988f-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="f988f-117">Установите флажок **Render Mesh Data in Wireframe** (Отрисовывать данные сетки в виде каркасной модели), чтобы контур каждого треугольника сетки **MRMesh** показывался белым цветом.</span><span class="sxs-lookup"><span data-stu-id="f988f-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Хранилище пространственных привязок готово](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="f988f-119">Пространственное сопоставление во время выполнения</span><span class="sxs-lookup"><span data-stu-id="f988f-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="f988f-120">Изменить логику пространственного сопоставления во время выполнения можно путем настройки следующих параметров:</span><span class="sxs-lookup"><span data-stu-id="f988f-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="f988f-121">Выберите **Edit > Project Settings** (Правка > Параметры проекта), прокрутите вниз до раздела **Platforms** (Платформы) и выберите **HoloLens > Spatial Mapping** (HoloLens > Пространственное сопоставление):</span><span class="sxs-lookup"><span data-stu-id="f988f-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Параметры пространственных привязок для проекта](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="f988f-123">Параметр **Max Triangles Per Cubic Meter** (Максимальное число треугольников на кубический метр) задает плотность треугольников в сетке пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="f988f-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="f988f-124">Параметр **Spatial Meshing Volume Size** (Размер объема для пространственных сеток) задает размер куба вокруг игрока, в пределах которого будут отрисовываться и обновляться данные пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="f988f-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="f988f-125">Если предполагается, что приложение будет выполняться в обширном пространстве, следует указать в этом поле достаточно большое значение, чтобы оно лучше соответствовало пространству реального мира.</span><span class="sxs-lookup"><span data-stu-id="f988f-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="f988f-126">Если же приложению нужны голограммы только на поверхностях рядом с пользователем, значение в этом поле может быть небольшим.</span><span class="sxs-lookup"><span data-stu-id="f988f-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="f988f-127">По мере перемещения пользователя по игровому миру вместе с ним перемещается и пространство для пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="f988f-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="f988f-128">Работа с сеткой MRMesh</span><span class="sxs-lookup"><span data-stu-id="f988f-128">Working with MRMesh</span></span>
<span data-ttu-id="f988f-129">Чтобы получить доступ к сетке **MRMesh** во время выполнения:</span><span class="sxs-lookup"><span data-stu-id="f988f-129">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="f988f-130">Добавьте к субъекту Blueprint компонент **ARTrackableNotify**.</span><span class="sxs-lookup"><span data-stu-id="f988f-130">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![AR Trackable Notify для пространственных привязок](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="f988f-132">Выберите компонент **ARTrackableNotify** и в панели **Details** (Сведения) разверните раздел **Events** (События).</span><span class="sxs-lookup"><span data-stu-id="f988f-132">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="f988f-133">Нажмите кнопку **+** на событиях, мониторинг которых требуется вести.</span><span class="sxs-lookup"><span data-stu-id="f988f-133">Click the **+** button on the events you want to monitor.</span></span> 

![События пространственных привязок](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="f988f-135">В данном случае ведется мониторинг события **On Add Tracked Geometry** (При добавлении отслеживаемой геометрии), которое ведет поиск действительных мировых сеток, соответствующих данным пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="f988f-135">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="f988f-136">Полный список событий можно найти в API объекта [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="f988f-136">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="f988f-137">Изменить материал сетки можно в графе событий схемы или в коде на C++.</span><span class="sxs-lookup"><span data-stu-id="f988f-137">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="f988f-138">На приведенном ниже снимке экрана показан вариант действий с графом событий схемы.</span><span class="sxs-lookup"><span data-stu-id="f988f-138">The screenshot below shows the Blueprint route:</span></span> 

![Пример пространственных привязок](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="f988f-140">В коде на C++ можно подписаться на делегат `OnTrackableAdded`, позволяющий получить объект `ARTrackedGeometry`, как только он станет доступным. Пример соответствующего кода показан ниже.</span><span class="sxs-lookup"><span data-stu-id="f988f-140">In C++, you can subscribe to the `OnTrackableAdded` delegate to get the `ARTrackedGeometry` as soon as it is available, shown in the code below.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="f988f-141">Файл build.cs проекта **ДОЛЖЕН** содержать модуль **AugmentedReality** в списке **PublicDependencyModuleNames**.</span><span class="sxs-lookup"><span data-stu-id="f988f-141">The project’s build.cs file **MUST** have **AugmentedReality** in the **PublicDependencyModuleNames** list.</span></span>
> - <span data-ttu-id="f988f-142">Через него включаются заголовочные файлы **ARBlueprintLibrary.h** и **MRMeshComponent.h**, что позволяет исследовать компонент **MRMesh** объекта **UARTrackedGeometry**.</span><span class="sxs-lookup"><span data-stu-id="f988f-142">This includes **ARBlueprintLibrary.h** and **MRMeshComponent.h**, which lets you inspect the **MRMesh** component of the **UARTrackedGeometry**.</span></span> 

![Код C++ для событий пространственных привязок](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="f988f-144">Пространственное сопоставление — не единственный тип данных, которые передаются в качестве поверхностей через объекты **ARTrackedGeometry**.</span><span class="sxs-lookup"><span data-stu-id="f988f-144">Spatial mapping is not the only type of data that gets surfaced through **ARTrackedGeometries**.</span></span> <span data-ttu-id="f988f-145">Чтобы убедиться, что данная геометрия относится к пространственному сопоставлению, можно проверить, что `EARObjectClassification` имеет значение `World`.</span><span class="sxs-lookup"><span data-stu-id="f988f-145">You can check that the `EARObjectClassification` is `World`, which means this is spatial mapping geometry.</span></span> 

<span data-ttu-id="f988f-146">Существуют аналогичные делегаты для событий обновления и удаления:</span><span class="sxs-lookup"><span data-stu-id="f988f-146">There are similar delegates for updated and removed events:</span></span> 
- `AddOnTrackableUpdatedDelegate_Handle` 
- <span data-ttu-id="f988f-147">`AddOnTrackableRemovedDelegate_Handle`.</span><span class="sxs-lookup"><span data-stu-id="f988f-147">`AddOnTrackableRemovedDelegate_Handle`.</span></span> 

<span data-ttu-id="f988f-148">Полный список событий можно найти в API объекта [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="f988f-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="f988f-149">См. также статью</span><span class="sxs-lookup"><span data-stu-id="f988f-149">See also</span></span>
* [<span data-ttu-id="f988f-150">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="f988f-150">Spatial mapping</span></span>](spatial-mapping.md)
