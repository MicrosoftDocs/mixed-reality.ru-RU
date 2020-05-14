---
title: Пространственные привязки в Unreal
description: Руководство по применению пространственных привязок в Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, пространственные привязки
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840143"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="a8541-104">Пространственные привязки в Unreal</span><span class="sxs-lookup"><span data-stu-id="a8541-104">Spatial Anchors in Unreal</span></span>

<span data-ttu-id="a8541-105">Пространственные привязки используются для размещения в реальных пространствах голограмм, которые сохраняются между сеансами работы с приложением.</span><span class="sxs-lookup"><span data-stu-id="a8541-105">Spatial anchors are used to persist holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="a8541-106">Эта возможность предоставляется в Unreal как элементы ARPin и использует для хранения хранилище привязок HoloLens, позволяя загружать их в последующих сеансах.</span><span class="sxs-lookup"><span data-stu-id="a8541-106">This gets surfaced through Unreal as ARPins and gets saved in the HoloLens’ anchor store to be loaded in future sessions.</span></span> 

<span data-ttu-id="a8541-107">Перед сохранением или загрузкой привязок обязательно убедитесь, что хранилище привязок подготовлено.</span><span class="sxs-lookup"><span data-stu-id="a8541-107">Before saving or loading anchors, first check that the anchor store is ready.</span></span>  <span data-ttu-id="a8541-108">Попытка вызвать любую из функций привязки в HoloLens без готовности хранилища завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="a8541-108">Attempting to call any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Хранилище пространственных привязок готово](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a><span data-ttu-id="a8541-110">Сохранение привязок</span><span class="sxs-lookup"><span data-stu-id="a8541-110">Save Anchors</span></span>

<span data-ttu-id="a8541-111">Когда в приложении появится компонент, который нужно прикрепить к положению в реальном мире, сохраните его в хранилище привязок с помощью следующей последовательности:</span><span class="sxs-lookup"><span data-stu-id="a8541-111">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Сохранение пространственных привязок](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="a8541-113">В этом примере мы порождаем субъект в известном расположении, создаем ARPin с этим значением расположения и именем, созданным на основе класса субъекта, затем добавляем этот субъект в ARPin и сохраняем указатель в хранилище привязок HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a8541-113">Here, we are spawning an actor at a known location, creating an ARPin with that location and a name based on the actor’s class, adding the actor to the ARPin, and saving the pin to the HoloLens anchor store.</span></span>  <span data-ttu-id="a8541-114">Нам необходимо выбрать уникальное имя привязки, поэтому в нашем примере к имени добавляется текущая метка времени.</span><span class="sxs-lookup"><span data-stu-id="a8541-114">The anchor name we choose must be unique, so in this example we append the current timestamp.</span></span>  <span data-ttu-id="a8541-115">Если привязка будет успешно сохранена в хранилище привязок, она станет доступна для проверки на портале устройств HoloLens в разделе System (Система) > Map manager (Диспетчер карт) > Anchor Files Saved On Device (Сохраненные на устройстве файлы привязок).</span><span class="sxs-lookup"><span data-stu-id="a8541-115">If the anchor successfully saves to the anchor store, it can be inspected in the HoloLens device portal under System > Map manager > Anchor Files Saved On Device.</span></span> 

## <a name="load-anchors"></a><span data-ttu-id="a8541-116">Загрузка привязок</span><span class="sxs-lookup"><span data-stu-id="a8541-116">Load Anchors</span></span>

<span data-ttu-id="a8541-117">При запуске приложения можно вызвать следующую схему, чтобы восстановить все компоненты в местах соответствующих привязок:</span><span class="sxs-lookup"><span data-stu-id="a8541-117">When an application starts, the following blueprint can be called to restore components to their anchor locations:</span></span>

![Загрузка пространственных привязок](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="a8541-119">В этом примере мы перебираем все привязки, сохраненные в хранилище привязок, порождаем субъект по его идентификатору и прикрепляем этот субъект к ARPin из хранилища привязок.</span><span class="sxs-lookup"><span data-stu-id="a8541-119">In this example, we iterate over all of the anchors in the anchor store, spawn an actor at identity, and pin that actor to the ARPin from the anchor store.</span></span>  <span data-ttu-id="a8541-120">Здесь важно порождать субъект по идентификатору, так как привязка отвечает за размещение голограммы в мире в том месте, где она была сохранена, поэтому любое преобразование на этом этапе добавит к нашей привязке ненужное смещение.</span><span class="sxs-lookup"><span data-stu-id="a8541-120">It is important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved, so any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="a8541-121">Идентификатор привязки также запрашивается, чтобы мы могли порождать разные субъекты в зависимости от сохраненного имени привязки.</span><span class="sxs-lookup"><span data-stu-id="a8541-121">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="remove-anchors"></a><span data-ttu-id="a8541-122">Удаление привязок</span><span class="sxs-lookup"><span data-stu-id="a8541-122">Remove Anchors</span></span> 

<span data-ttu-id="a8541-123">Завершив работу с привязками, вы можете очистить все хранилище привязок сразу или удалять из него отдельные привязки по отдельности, и удаленные привязки не будут включаться в будущие сеансы:</span><span class="sxs-lookup"><span data-stu-id="a8541-123">When done with an anchor, the entire anchor store can be cleared, or individual anchors can be removed from the anchor store so they are not included in future sessions:</span></span> 

![Удаление пространственных привязок](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a><span data-ttu-id="a8541-125">См. также статью</span><span class="sxs-lookup"><span data-stu-id="a8541-125">See also</span></span>
* [<span data-ttu-id="a8541-126">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="a8541-126">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="a8541-127">Системы координат</span><span class="sxs-lookup"><span data-stu-id="a8541-127">Coordinate systems</span></span>](coordinate-systems.md)
