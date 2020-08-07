---
title: Локальные пространственные привязки в Unreal
description: Руководство по применению пространственных привязок в Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, пространственные привязки
ms.openlocfilehash: b102d506b1d670291c3b97ca34d277e2597af043
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376052"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="d8759-104">Локальные пространственные привязки в Unreal</span><span class="sxs-lookup"><span data-stu-id="d8759-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="d8759-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="d8759-105">Overview</span></span>

<span data-ttu-id="d8759-106">Пространственные привязки используются для размещения в реальных пространствах голограмм, которые сохраняются между сеансами работы с приложением.</span><span class="sxs-lookup"><span data-stu-id="d8759-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="d8759-107">Они предоставляются в Unreal в виде элементов **ARPin** и сохраняются в хранилище привязок HoloLens, которое загружается в последующих сеансах.</span><span class="sxs-lookup"><span data-stu-id="d8759-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="d8759-108">Локальные привязки идеально подходят для тех случаев, когда подключение к Интернету отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d8759-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8759-109">Локальные привязки хранятся на устройстве, а пространственные привязки Azure сохраняются в облаке.</span><span class="sxs-lookup"><span data-stu-id="d8759-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="d8759-110">Если вы хотите использовать облачные службы Azure для хранения привязок, мы предоставляем документ, который поможем вам в интеграции [Пространственных привязок Azure](unreal-azure-spatial-anchors.md).</span><span class="sxs-lookup"><span data-stu-id="d8759-110">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="d8759-111">Обратите внимание, что вы можете использовать локальные привязки и привязки Azure в одном проекте без каких-либо конфликтов.</span><span class="sxs-lookup"><span data-stu-id="d8759-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="d8759-112">Проверка хранилища привязок</span><span class="sxs-lookup"><span data-stu-id="d8759-112">Checking the anchor store</span></span>

<span data-ttu-id="d8759-113">Перед сохранением или загрузкой привязок обязательно убедитесь, что хранилище привязок подготовлено.</span><span class="sxs-lookup"><span data-stu-id="d8759-113">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="d8759-114">Попытка вызвать любую из функций привязки в HoloLens при неготовности хранилища завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="d8759-114">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Хранилище пространственных привязок готово](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="d8759-116">Сохранение привязок</span><span class="sxs-lookup"><span data-stu-id="d8759-116">Saving anchors</span></span>

<span data-ttu-id="d8759-117">Когда в приложении появится компонент, который нужно прикрепить к положению в реальном мире, сохраните его в хранилище привязок с помощью следующей последовательности:</span><span class="sxs-lookup"><span data-stu-id="d8759-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Сохранение пространственных привязок](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="d8759-119">Порядок действий:</span><span class="sxs-lookup"><span data-stu-id="d8759-119">Breaking this down:</span></span>
1. <span data-ttu-id="d8759-120">Породите субъект в известном расположении.</span><span class="sxs-lookup"><span data-stu-id="d8759-120">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="d8759-121">Создайте элемент **ARPin** с этим расположением и именем, основанным на классе субъекта.</span><span class="sxs-lookup"><span data-stu-id="d8759-121">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="d8759-122">Добавьте соответствующий субъект в **ARPin** и сохраните полученный элемент в хранилище привязок HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d8759-122">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="d8759-123">Для привязки необходимо выбрать уникальное имя, поэтому в нашем примере к имени добавляется текущая метка времени.</span><span class="sxs-lookup"><span data-stu-id="d8759-123">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="d8759-124">Привязка, успешно сохраненная в хранилище, становится доступной для проверки на портале устройства HoloLens в разделе **System > Map manager > Anchor Files Saved On Device** (Система > Диспетчер карт > Сохраненные на устройстве файлы привязок).</span><span class="sxs-lookup"><span data-stu-id="d8759-124">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="d8759-125">Загрузка привязок</span><span class="sxs-lookup"><span data-stu-id="d8759-125">Loading anchors</span></span>

<span data-ttu-id="d8759-126">При запуске приложения можно вызвать следующую схему, чтобы восстановить все компоненты в местах соответствующих привязок:</span><span class="sxs-lookup"><span data-stu-id="d8759-126">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![Загрузка пространственных привязок](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="d8759-128">Порядок действий:</span><span class="sxs-lookup"><span data-stu-id="d8759-128">Breaking this down:</span></span>
1. <span data-ttu-id="d8759-129">Выполните перечисленные ниже шаги для всех привязок в хранилище.</span><span class="sxs-lookup"><span data-stu-id="d8759-129">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="d8759-130">Породите субъект без преобразований.</span><span class="sxs-lookup"><span data-stu-id="d8759-130">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="d8759-131">Прикрепите субъект к элементу **ARPin** из хранилища привязок.</span><span class="sxs-lookup"><span data-stu-id="d8759-131">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="d8759-132">Здесь важно порождать субъект без преобразований, так как привязка отвечает за размещение голограммы в мире в том месте, где она была сохранена.</span><span class="sxs-lookup"><span data-stu-id="d8759-132">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="d8759-133">Любое преобразование на этом этапе добавит к нашей привязке ненужное смещение.</span><span class="sxs-lookup"><span data-stu-id="d8759-133">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="d8759-134">Идентификатор привязки также запрашивается, чтобы мы могли порождать разные субъекты в зависимости от сохраненного имени привязки.</span><span class="sxs-lookup"><span data-stu-id="d8759-134">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="d8759-135">Удаление привязок</span><span class="sxs-lookup"><span data-stu-id="d8759-135">Removing anchors</span></span> 

<span data-ttu-id="d8759-136">Когда вы закончите с привязкой, то можете очистить отдельные привязки или очистить все хранилище привязок с помощью компонентов **Remove ARPin from WMRAnchor Store** (Удаление ARPin из хранилища WMRAnchor) и **Remove All ARPins from WMRAnchor Store** (Удаление всех элементов ARPin из хранилища WMRAnchor).</span><span class="sxs-lookup"><span data-stu-id="d8759-136">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![Удаление пространственных привязок](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="d8759-138">Имейте в виду, что функциональность пространственных привязок находится пока в стадии бета-версии, поэтому стоит возвращаться сюда время от времени за новой информацией.</span><span class="sxs-lookup"><span data-stu-id="d8759-138">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8759-139">См. также статью</span><span class="sxs-lookup"><span data-stu-id="d8759-139">See also</span></span>
* [<span data-ttu-id="d8759-140">Пространственные привязки Azure</span><span class="sxs-lookup"><span data-stu-id="d8759-140">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="d8759-141">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="d8759-141">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="d8759-142">Системы координат</span><span class="sxs-lookup"><span data-stu-id="d8759-142">Coordinate systems</span></span>](coordinate-systems.md)
