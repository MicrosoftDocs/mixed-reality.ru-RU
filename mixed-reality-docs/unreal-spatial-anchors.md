---
title: Пространственные привязки в Unreal
description: Руководство по применению пространственных привязок в Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, пространственные привязки
ms.openlocfilehash: 1100704cae40de1997eb869bfc6c82bba3d0dc6e
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428728"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="08f06-104">Пространственные привязки в Unreal</span><span class="sxs-lookup"><span data-stu-id="08f06-104">Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="08f06-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="08f06-105">Overview</span></span>

<span data-ttu-id="08f06-106">Пространственные привязки используются для размещения в реальных пространствах голограмм, которые сохраняются между сеансами работы с приложением.</span><span class="sxs-lookup"><span data-stu-id="08f06-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="08f06-107">Они предоставляются в Unreal в виде элементов **ARPin** и сохраняются в хранилище привязок HoloLens, которое загружается в последующих сеансах.</span><span class="sxs-lookup"><span data-stu-id="08f06-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> 

## <a name="checking-the-anchor-store"></a><span data-ttu-id="08f06-108">Проверка хранилища привязок</span><span class="sxs-lookup"><span data-stu-id="08f06-108">Checking the anchor store</span></span>

<span data-ttu-id="08f06-109">Перед сохранением или загрузкой привязок обязательно убедитесь, что хранилище привязок подготовлено.</span><span class="sxs-lookup"><span data-stu-id="08f06-109">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="08f06-110">Попытка вызвать любую из функций привязки в HoloLens при неготовности хранилища завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="08f06-110">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Хранилище пространственных привязок готово](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="08f06-112">Сохранение привязок</span><span class="sxs-lookup"><span data-stu-id="08f06-112">Saving anchors</span></span>

<span data-ttu-id="08f06-113">Когда в приложении появится компонент, который нужно прикрепить к положению в реальном мире, сохраните его в хранилище привязок с помощью следующей последовательности:</span><span class="sxs-lookup"><span data-stu-id="08f06-113">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Сохранение пространственных привязок](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="08f06-115">Порядок действий:</span><span class="sxs-lookup"><span data-stu-id="08f06-115">Breaking this down:</span></span>
1. <span data-ttu-id="08f06-116">Породите субъект в известном расположении.</span><span class="sxs-lookup"><span data-stu-id="08f06-116">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="08f06-117">Создайте элемент **ARPin** с этим расположением и именем, основанным на классе субъекта.</span><span class="sxs-lookup"><span data-stu-id="08f06-117">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="08f06-118">Добавьте соответствующий субъект в **ARPin** и сохраните полученный элемент в хранилище привязок HoloLens.</span><span class="sxs-lookup"><span data-stu-id="08f06-118">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="08f06-119">Для привязки необходимо выбрать уникальное имя, поэтому в нашем примере к имени добавляется текущая метка времени.</span><span class="sxs-lookup"><span data-stu-id="08f06-119">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="08f06-120">Привязка, успешно сохраненная в хранилище, становится доступной для проверки на портале устройства HoloLens в разделе **System > Map manager > Anchor Files Saved On Device** (Система > Диспетчер карт > Сохраненные на устройстве файлы привязок).</span><span class="sxs-lookup"><span data-stu-id="08f06-120">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="08f06-121">Загрузка привязок</span><span class="sxs-lookup"><span data-stu-id="08f06-121">Loading anchors</span></span>

<span data-ttu-id="08f06-122">При запуске приложения можно вызвать следующую схему, чтобы восстановить все компоненты в местах соответствующих привязок:</span><span class="sxs-lookup"><span data-stu-id="08f06-122">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![Загрузка пространственных привязок](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="08f06-124">Порядок действий:</span><span class="sxs-lookup"><span data-stu-id="08f06-124">Breaking this down:</span></span>
1. <span data-ttu-id="08f06-125">Выполните перечисленные ниже шаги для всех привязок в хранилище.</span><span class="sxs-lookup"><span data-stu-id="08f06-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="08f06-126">Породите субъект без преобразований.</span><span class="sxs-lookup"><span data-stu-id="08f06-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="08f06-127">Прикрепите субъект к элементу **ARPin** из хранилища привязок.</span><span class="sxs-lookup"><span data-stu-id="08f06-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="08f06-128">Здесь важно порождать субъект без преобразований, так как привязка отвечает за размещение голограммы в мире в том месте, где она была сохранена.</span><span class="sxs-lookup"><span data-stu-id="08f06-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="08f06-129">Любое преобразование на этом этапе добавит к нашей привязке ненужное смещение.</span><span class="sxs-lookup"><span data-stu-id="08f06-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="08f06-130">Идентификатор привязки также запрашивается, чтобы мы могли порождать разные субъекты в зависимости от сохраненного имени привязки.</span><span class="sxs-lookup"><span data-stu-id="08f06-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="08f06-131">Удаление привязок</span><span class="sxs-lookup"><span data-stu-id="08f06-131">Removing anchors</span></span> 

<span data-ttu-id="08f06-132">Когда вы закончите с привязкой, то можете очистить отдельные привязки или очистить все хранилище привязок с помощью компонентов **Remove ARPin from WMRAnchor Store** (Удаление ARPin из хранилища WMRAnchor) и **Remove All ARPins from WMRAnchor Store** (Удаление всех элементов ARPin из хранилища WMRAnchor).</span><span class="sxs-lookup"><span data-stu-id="08f06-132">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![Удаление пространственных привязок](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="08f06-134">Имейте в виду, что функциональность пространственных привязок находится пока в стадии бета-версии, поэтому стоит возвращаться сюда время от времени за новой информацией.</span><span class="sxs-lookup"><span data-stu-id="08f06-134">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="08f06-135">См. также статью</span><span class="sxs-lookup"><span data-stu-id="08f06-135">See also</span></span>
* [<span data-ttu-id="08f06-136">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="08f06-136">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="08f06-137">Системы координат</span><span class="sxs-lookup"><span data-stu-id="08f06-137">Coordinate systems</span></span>](coordinate-systems.md)
