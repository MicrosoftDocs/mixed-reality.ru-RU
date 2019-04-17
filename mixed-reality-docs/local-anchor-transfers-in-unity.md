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
# <a name="local-anchor-transfers-in-unity"></a>Передача локального привязки в Unity

В ситуациях, когда невозможно использовать <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">привязки пространственных Azure</a>, передача локального привязки включить одно устройство HoloLens Экспорт привязки импортируемой второе устройство HoloLens.

>[!NOTE]
>Передачи локального привязки позволяют менее надежны, отзыв привязки, чем <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">привязки пространственных Azure</a>, и устройства iOS и Android не поддерживаются, этот подход.

### <a name="setting-the-spatialperception-capability"></a>Настройка возможностей SpatialPerception

В порядке передачи пространственных привязки, чтобы приложение *SpatialPerception* возможность должна быть включена.

Как включить *SpatialPerception* возможность:
1. Откройте в редакторе Unity **«Параметры проигрывателя»** области (Изменить > Параметры проекта > проигрывателя)
2. Щелкните **«Windows Store»** вкладку
3. Разверните **«Параметры публикации»** и проверьте **«SpatialPerception»** возможность **«Возможности»** списка

>[!NOTE]
>Если вы уже экспортировали проекта Unity в решение Visual Studio, необходимо будет либо экспорта в новую папку или вручную [задать эту возможность в манифест AppxManifest в Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Передача привязки

**Пространство имен:** *UnityEngine.XR.WSA.Sharing*<br>
**Тип**: *WorldAnchorTransferBatch*

Для передачи [WorldAnchor](coordinate-systems-in-unity.md), один необходимо установить точку привязки будут передаваться. Пользователь один HoloLens сканирует их среду и вручную или программными средствами выбирает точку в пространстве, чтобы служить в качестве привязки для общей работы. Данные, представляющие этой точки можно сериализовать и передаются на других устройствах, которые находятся в системе работы с. Каждое устройство затем десериализует привязки данных и пытается найти эту точку в пространстве. В порядке привязки службы передачи для работы каждого устройства необходимо проверки достаточного среды таким образом, можно определить точки, представленной привязки.

### <a name="setup"></a>Установка

Пример кода, на этой странице содержит несколько полей, которые нужно инициализировать:
1. *Объект GameObject rootGameObject* — *GameObject* в Unity, которое имеет *WorldAnchor* компонентом. Один пользователь в опытом разместит *GameObject* и экспортировать данные другим пользователям.
2. *WorldAnchor gameRootAnchor* — *UnityEngine.XR.WSA.WorldAnchor* на *rootGameObject*.
3. *Byte [] importedData* является массив байтов для сериализованного привязки, каждый клиент получает по сети.

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

### <a name="exporting"></a>Экспорт

Чтобы экспортировать, требуется всего лишь *WorldAnchor* и знать, что мы назовем его таким образом, что имеет смысл для принимающего приложения. Один клиент в общий интерфейс выполнит следующие действия для экспорта общей привязки:
1. Создание *WorldAnchorTransferBatch*
2. Добавить *WorldAnchors* для передачи
3. Начать экспорт
4. Обрабатывать *OnExportDataAvailable* события в качестве данных становится доступной
5. Обрабатывать *OnExportComplete* событий

Мы создадим *WorldAnchorTransferBatch* для инкапсуляции, что мы будет передачи и затем его экспорт в байтах:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

Как данные становятся доступными, отправить клиенту или буфер байты, сегменты данных доступен и отправить с помощью любым способом требуемого:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

По завершении экспорта, если мы передачи данных и сериализации не удалось, сообщите клиенту удалить данные. Если сериализация выполнена успешно, сообщите клиенту, что все данные были переданы, и импорт можно запустить:

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

### <a name="importing"></a>Импорт

После получения всех байтов от отправителя, можно импортировать данные обратно в *WorldAnchorTransferBatch* и заблокировать наших корневой объект игр в одном месте. Примечание: Импорт иногда быстро завершится ошибкой и необходимо повторить:

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

После *GameObject* заблокирована с помощью *LockObject* вызова, он будет иметь *WorldAnchor* которого будет хранить в физическое положение в мире, но он может находиться в другое расположение в Unity координатное пространство, чем для других пользователей.

