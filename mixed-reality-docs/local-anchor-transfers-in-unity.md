---
title: Передача локального привязки в Unity
description: Перенос привязок между несколькими устройствами HoloLens в приложении Unity.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Общий доступ, привязки, WorldAnchor, MR совместное использование 250, WorldAnchorTransferBatch, SpatialPerception, передачи, перемещение локальной привязки, привязки экспорта, импорта привязки
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605056"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="b1437-104">Передача локального привязки в Unity</span><span class="sxs-lookup"><span data-stu-id="b1437-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="b1437-105">В ситуациях, когда невозможно использовать <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">привязки пространственных Azure</a>, передача локального привязки включить одно устройство HoloLens Экспорт привязки импортируемой второе устройство HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b1437-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="b1437-106">Передачи локального привязки позволяют менее надежны, отзыв привязки, чем <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">привязки пространственных Azure</a>, и устройства iOS и Android не поддерживаются, этот подход.</span><span class="sxs-lookup"><span data-stu-id="b1437-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="b1437-107">Настройка возможностей SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="b1437-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="b1437-108">В порядке передачи пространственных привязки, чтобы приложение *SpatialPerception* возможность должна быть включена.</span><span class="sxs-lookup"><span data-stu-id="b1437-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="b1437-109">Как включить *SpatialPerception* возможность:</span><span class="sxs-lookup"><span data-stu-id="b1437-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="b1437-110">Откройте в редакторе Unity **«Параметры проигрывателя»** области (Изменить > Параметры проекта > проигрывателя)</span><span class="sxs-lookup"><span data-stu-id="b1437-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="b1437-111">Щелкните **«Windows Store»** вкладку</span><span class="sxs-lookup"><span data-stu-id="b1437-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="b1437-112">Разверните **«Параметры публикации»** и проверьте **«SpatialPerception»** возможность **«Возможности»** списка</span><span class="sxs-lookup"><span data-stu-id="b1437-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="b1437-113">Если вы уже экспортировали проекта Unity в решение Visual Studio, необходимо будет либо экспорта в новую папку или вручную [задать эту возможность в манифест AppxManifest в Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="b1437-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="b1437-114">Передача привязки</span><span class="sxs-lookup"><span data-stu-id="b1437-114">Anchor Transfer</span></span>

<span data-ttu-id="b1437-115">**Пространство имен:** *UnityEngine.XR.WSA.Sharing*</span><span class="sxs-lookup"><span data-stu-id="b1437-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="b1437-116">**Тип**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="b1437-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="b1437-117">Для передачи [WorldAnchor](coordinate-systems-in-unity.md), один необходимо установить точку привязки будут передаваться.</span><span class="sxs-lookup"><span data-stu-id="b1437-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="b1437-118">Пользователь один HoloLens сканирует их среду и вручную или программными средствами выбирает точку в пространстве, чтобы служить в качестве привязки для общей работы.</span><span class="sxs-lookup"><span data-stu-id="b1437-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="b1437-119">Данные, представляющие этой точки можно сериализовать и передаются на других устройствах, которые находятся в системе работы с.</span><span class="sxs-lookup"><span data-stu-id="b1437-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="b1437-120">Каждое устройство затем десериализует привязки данных и пытается найти эту точку в пространстве.</span><span class="sxs-lookup"><span data-stu-id="b1437-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="b1437-121">В порядке привязки службы передачи для работы каждого устройства необходимо проверки достаточного среды таким образом, можно определить точки, представленной привязки.</span><span class="sxs-lookup"><span data-stu-id="b1437-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="b1437-122">Установка</span><span class="sxs-lookup"><span data-stu-id="b1437-122">Setup</span></span>

<span data-ttu-id="b1437-123">Пример кода, на этой странице содержит несколько полей, которые нужно инициализировать:</span><span class="sxs-lookup"><span data-stu-id="b1437-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="b1437-124">*Объект GameObject rootGameObject* — *GameObject* в Unity, которое имеет *WorldAnchor* компонентом.</span><span class="sxs-lookup"><span data-stu-id="b1437-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="b1437-125">Один пользователь в опытом разместит *GameObject* и экспортировать данные другим пользователям.</span><span class="sxs-lookup"><span data-stu-id="b1437-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="b1437-126">*WorldAnchor gameRootAnchor* — *UnityEngine.XR.WSA.WorldAnchor* на *rootGameObject*.</span><span class="sxs-lookup"><span data-stu-id="b1437-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="b1437-127">*Byte [] importedData* является массив байтов для сериализованного привязки, каждый клиент получает по сети.</span><span class="sxs-lookup"><span data-stu-id="b1437-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

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

### <a name="exporting"></a><span data-ttu-id="b1437-128">Экспорт</span><span class="sxs-lookup"><span data-stu-id="b1437-128">Exporting</span></span>

<span data-ttu-id="b1437-129">Чтобы экспортировать, требуется всего лишь *WorldAnchor* и знать, что мы назовем его таким образом, что имеет смысл для принимающего приложения.</span><span class="sxs-lookup"><span data-stu-id="b1437-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="b1437-130">Один клиент в общий интерфейс выполнит следующие действия для экспорта общей привязки:</span><span class="sxs-lookup"><span data-stu-id="b1437-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="b1437-131">Создание *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="b1437-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="b1437-132">Добавить *WorldAnchors* для передачи</span><span class="sxs-lookup"><span data-stu-id="b1437-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="b1437-133">Начать экспорт</span><span class="sxs-lookup"><span data-stu-id="b1437-133">Begin the export</span></span>
4. <span data-ttu-id="b1437-134">Обрабатывать *OnExportDataAvailable* события в качестве данных становится доступной</span><span class="sxs-lookup"><span data-stu-id="b1437-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="b1437-135">Обрабатывать *OnExportComplete* событий</span><span class="sxs-lookup"><span data-stu-id="b1437-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="b1437-136">Мы создадим *WorldAnchorTransferBatch* для инкапсуляции, что мы будет передачи и затем его экспорт в байтах:</span><span class="sxs-lookup"><span data-stu-id="b1437-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="b1437-137">Как данные становятся доступными, отправить клиенту или буфер байты, сегменты данных доступен и отправить с помощью любым способом требуемого:</span><span class="sxs-lookup"><span data-stu-id="b1437-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="b1437-138">По завершении экспорта, если мы передачи данных и сериализации не удалось, сообщите клиенту удалить данные.</span><span class="sxs-lookup"><span data-stu-id="b1437-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="b1437-139">Если сериализация выполнена успешно, сообщите клиенту, что все данные были переданы, и импорт можно запустить:</span><span class="sxs-lookup"><span data-stu-id="b1437-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

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

### <a name="importing"></a><span data-ttu-id="b1437-140">Импорт</span><span class="sxs-lookup"><span data-stu-id="b1437-140">Importing</span></span>

<span data-ttu-id="b1437-141">После получения всех байтов от отправителя, можно импортировать данные обратно в *WorldAnchorTransferBatch* и заблокировать наших корневой объект игр в одном месте.</span><span class="sxs-lookup"><span data-stu-id="b1437-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="b1437-142">Примечание: Импорт иногда быстро завершится ошибкой и необходимо повторить:</span><span class="sxs-lookup"><span data-stu-id="b1437-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

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

<span data-ttu-id="b1437-143">После *GameObject* заблокирована с помощью *LockObject* вызова, он будет иметь *WorldAnchor* которого будет хранить в физическое положение в мире, но он может находиться в другое расположение в Unity координатное пространство, чем для других пользователей.</span><span class="sxs-lookup"><span data-stu-id="b1437-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

