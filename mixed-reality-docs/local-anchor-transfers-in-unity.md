---
title: Передача локальных привязок в Unity
description: Переносите привязки между несколькими устройствами HoloLens в приложении Unity.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Совместное использование, привязка, Ворлданчор, MR совместное использование 250, Ворлданчортрансфербатч, Спатиалперцептион, перемещение, перенос локальной привязки, экспорт привязки, импорт привязки
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516134"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="53995-104">Передача локальных привязок в Unity</span><span class="sxs-lookup"><span data-stu-id="53995-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="53995-105">В ситуациях, когда нельзя использовать <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>, передача локальных точек подключения позволяет одному устройству hololens экспортировать привязку, которая будет импортирована вторым устройством hololens.</span><span class="sxs-lookup"><span data-stu-id="53995-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="53995-106">Передача локальных привязок обеспечивает менее устойчивое отзыв, чем <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>, а устройства iOS и Android не поддерживаются этим подходом.</span><span class="sxs-lookup"><span data-stu-id="53995-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="53995-107">Настройка возможности Спатиалперцептион</span><span class="sxs-lookup"><span data-stu-id="53995-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="53995-108">Чтобы приложение могла передавать пространственные привязки, необходимо включить возможность *спатиалперцептион* .</span><span class="sxs-lookup"><span data-stu-id="53995-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="53995-109">Как включить функцию *спатиалперцептион* :</span><span class="sxs-lookup"><span data-stu-id="53995-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="53995-110">В редакторе Unity откройте панель **"Параметры проигрывателя"** (измените > параметры проекта > Player).</span><span class="sxs-lookup"><span data-stu-id="53995-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="53995-111">Перейдите на вкладку **"Магазин Windows"** .</span><span class="sxs-lookup"><span data-stu-id="53995-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="53995-112">Разверните узел **"Параметры публикации"** и проверьте возможность **"спатиалперцептион** " в списке **"возможности"** .</span><span class="sxs-lookup"><span data-stu-id="53995-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="53995-113">Если вы уже экспортировали проект Unity в решение Visual Studio, необходимо либо экспортировать в новую папку, либо вручную [установить эту возможность в appxmanifest в Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="53995-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="53995-114">Перенос привязки</span><span class="sxs-lookup"><span data-stu-id="53995-114">Anchor Transfer</span></span>

<span data-ttu-id="53995-115">**Имен** *UnityEngine. XR. WSA. Общий доступ*</span><span class="sxs-lookup"><span data-stu-id="53995-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="53995-116">**Тип**: *ворлданчортрансфербатч*</span><span class="sxs-lookup"><span data-stu-id="53995-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="53995-117">Чтобы передать [ворлданчор](coordinate-systems-in-unity.md), необходимо установить привязку для передачи.</span><span class="sxs-lookup"><span data-stu-id="53995-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="53995-118">Пользователь одного объекта HoloLens сканирует свою среду и либо вручную, либо программно выбирает точку в пространстве, чтобы быть привязкой для общего интерфейса.</span><span class="sxs-lookup"><span data-stu-id="53995-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="53995-119">Данные, представляющие эту точку, можно затем сериализовать и передать на другие устройства, которые совместно используются в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="53995-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="53995-120">Затем каждое устройство десериализует данные привязки и пытается нахождение точки в пространстве.</span><span class="sxs-lookup"><span data-stu-id="53995-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="53995-121">Чтобы перемещение привязки работало, каждое устройство должно быть проверено в достаточном объеме среды, чтобы можно было идентифицировать точку, представленную привязкой.</span><span class="sxs-lookup"><span data-stu-id="53995-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="53995-122">Установка</span><span class="sxs-lookup"><span data-stu-id="53995-122">Setup</span></span>

<span data-ttu-id="53995-123">Пример кода на этой странице содержит несколько полей, которые необходимо инициализировать:</span><span class="sxs-lookup"><span data-stu-id="53995-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="53995-124">*GameObject рутгамеобжект* — это *GameObject* в Unity, на котором есть компонент *ворлданчор* .</span><span class="sxs-lookup"><span data-stu-id="53995-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="53995-125">Один пользователь в общем интерфейсе поместит этот *GameObject* и экспортирует данные другим пользователям.</span><span class="sxs-lookup"><span data-stu-id="53995-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="53995-126">*Ворлданчор гамерутанчор* — это *UnityEngine. XR. WSA. ворлданчор* , который находится на *рутгамеобжект*.</span><span class="sxs-lookup"><span data-stu-id="53995-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="53995-127">*Byte [] импортеддата* является массивом байтов для сериализованной привязки, получаемой каждым клиентом по сети.</span><span class="sxs-lookup"><span data-stu-id="53995-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a><span data-ttu-id="53995-128">Идет</span><span class="sxs-lookup"><span data-stu-id="53995-128">Exporting</span></span>

<span data-ttu-id="53995-129">Чтобы выполнить экспорт, нам нужно просто *ворлданчор* и знать, что именно мы его называю, что имеет смысл для принимающего приложения.</span><span class="sxs-lookup"><span data-stu-id="53995-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="53995-130">Один клиент в общем интерфейсе выполняет следующие действия по экспорту общей привязки:</span><span class="sxs-lookup"><span data-stu-id="53995-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="53995-131">Создание *ворлданчортрансфербатч*</span><span class="sxs-lookup"><span data-stu-id="53995-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="53995-132">Добавление *ворлданчорс* для перемещения</span><span class="sxs-lookup"><span data-stu-id="53995-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="53995-133">Начать экспорт</span><span class="sxs-lookup"><span data-stu-id="53995-133">Begin the export</span></span>
4. <span data-ttu-id="53995-134">Обрабатывает событие *онекспортдатааваилабле* , так как данные становятся доступными</span><span class="sxs-lookup"><span data-stu-id="53995-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="53995-135">Обрабатывает событие *онекспорткомплете*</span><span class="sxs-lookup"><span data-stu-id="53995-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="53995-136">Мы создадим *ворлданчортрансфербатч* , чтобы инкапсулировать, что мы будем передавать, а затем экспортировать в байты:</span><span class="sxs-lookup"><span data-stu-id="53995-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="53995-137">По мере того как данные становятся доступными, отправьте их клиенту или буферу в виде сегментов данных и отправьте их по своему усмотрению:</span><span class="sxs-lookup"><span data-stu-id="53995-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="53995-138">После завершения экспорта, если мы передавали данные и произошел сбой сериализации, сообщите клиенту об отмене данных.</span><span class="sxs-lookup"><span data-stu-id="53995-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="53995-139">Если сериализация выполнена успешно, сообщите клиенту, что все данные были переданы и импорт может начаться:</span><span class="sxs-lookup"><span data-stu-id="53995-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a><span data-ttu-id="53995-140">Падут</span><span class="sxs-lookup"><span data-stu-id="53995-140">Importing</span></span>

<span data-ttu-id="53995-141">После получения всех байтов от отправителя можно импортировать данные обратно в *ворлданчортрансфербатч* и заблокировать объект корневой игры в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="53995-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="53995-142">Примечание. в некоторых случаях импорт будет временно невозможен и необходимо повторить попытку:</span><span class="sxs-lookup"><span data-stu-id="53995-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

<span data-ttu-id="53995-143">После того как *GameObject* блокируется через вызов *lockobject* , он будет иметь *ворлданчор* , который сохранит его в той же физической позиции в мире, но может находиться в другом месте в пространстве координат Unity, чем другие пользователи.</span><span class="sxs-lookup"><span data-stu-id="53995-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

