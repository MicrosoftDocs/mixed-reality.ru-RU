---
title: Передача локальных привязок в DirectX
description: Объясняется, как синхронизировать два устройства HoloLens путем передачи пространственных привязок.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Synchronize, пространственный якорь, перемещение, многопользовательский режим, представление, сценарий, пошаговое руководство, пример кода, перенос, перенос локальной привязки, экспорт привязки, импорт привязки
ms.openlocfilehash: f961862c3c49872484683e264fb9c62b5d0b60ee
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437954"
---
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="18590-104">Передача локальных привязок в DirectX</span><span class="sxs-lookup"><span data-stu-id="18590-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="18590-105">В ситуациях, когда нельзя использовать <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>, передача локальных точек подключения позволяет одному устройству hololens экспортировать привязку, которая будет импортирована вторым устройством hololens.</span><span class="sxs-lookup"><span data-stu-id="18590-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="18590-106">Передача локальных привязок обеспечивает менее устойчивое отзыв, чем <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>, а устройства iOS и Android не поддерживаются этим подходом.</span><span class="sxs-lookup"><span data-stu-id="18590-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="18590-107">Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="18590-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="18590-108">Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="18590-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="18590-109">Передача пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="18590-109">Transferring spatial anchors</span></span>

<span data-ttu-id="18590-110">Вы можете передавать пространственные привязки между устройствами Windows Mixed Reality с помощью [спатиаланчортрансферманажер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="18590-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="18590-111">Этот API позволяет объединять привязку со всеми поддерживающими данными датчика, необходимыми для поиска точного места в мире, а затем импортировать этот пакет на другом устройстве.</span><span class="sxs-lookup"><span data-stu-id="18590-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="18590-112">После того, как приложение на втором устройстве импортировало эту привязку, каждое приложение может визуализировать голограммы с помощью этой системы координат общей пространственной привязки, которая затем будет отображаться в том же месте реального мира.</span><span class="sxs-lookup"><span data-stu-id="18590-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="18590-113">Обратите внимание, что пространственные привязки не могут перемещаться между разными типами устройств, например, пространственный якорь HoloLens может не размещаемые с помощью иммерсивного головного телефона.</span><span class="sxs-lookup"><span data-stu-id="18590-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="18590-114">Передаваемые привязки также несовместимы с устройствами iOS или Android.</span><span class="sxs-lookup"><span data-stu-id="18590-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="18590-115">Настройка приложения для использования возможности Спатиалперцептион</span><span class="sxs-lookup"><span data-stu-id="18590-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="18590-116">Приложению должно быть предоставлено разрешение на использование возможности Спатиалперцептион, прежде чем оно сможет использовать [спатиаланчортрансферманажер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="18590-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="18590-117">Это необходимо потому, что передача пространственной привязки включает в себя общий доступ к изображениям датчика, собранным со временем в результате этой привязки, которая может содержать конфиденциальные сведения.</span><span class="sxs-lookup"><span data-stu-id="18590-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="18590-118">Объявите эту возможность в файле Package. appxmanifest для приложения.</span><span class="sxs-lookup"><span data-stu-id="18590-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="18590-119">Вот пример.</span><span class="sxs-lookup"><span data-stu-id="18590-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="18590-120">Эта возможность поступает из пространства имен **uap2** .</span><span class="sxs-lookup"><span data-stu-id="18590-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="18590-121">Чтобы получить доступ к этому пространству имен в манифесте, включите его в качестве атрибута *кслмнс* в элемент &lt;пакета >.</span><span class="sxs-lookup"><span data-stu-id="18590-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="18590-122">Вот пример.</span><span class="sxs-lookup"><span data-stu-id="18590-122">Here's an example:</span></span>

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="18590-123">**Примечание.** Приложению потребуется запросить возможность во время выполнения, прежде чем он сможет получить доступ к API экспорта и импорта Спатиаланчор.</span><span class="sxs-lookup"><span data-stu-id="18590-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="18590-124">См. раздел [рекуестакцессасинк](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) в примерах ниже.</span><span class="sxs-lookup"><span data-stu-id="18590-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="18590-125">Сериализация данных привязки путем их экспорта с помощью Спатиаланчортрансферманажер</span><span class="sxs-lookup"><span data-stu-id="18590-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="18590-126">Вспомогательная функция включается в пример кода для экспорта (сериализации) [спатиаланчор](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) данных.</span><span class="sxs-lookup"><span data-stu-id="18590-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="18590-127">Этот API экспорта сериализует все привязки в коллекции пар "ключ-значение", связывающие строки с привязками.</span><span class="sxs-lookup"><span data-stu-id="18590-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

<span data-ttu-id="18590-128">Сначала необходимо настроить поток данных.</span><span class="sxs-lookup"><span data-stu-id="18590-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="18590-129">Это позволит нам получить 1.) Используйте Трекспортанчорсасинк, чтобы разместить данные в буфере, принадлежащем приложению, и 2.) чтение данных из экспортированного потока байтового буфера, который представляет собой поток данных WinRT, в собственный буфер памяти, который является стандартом std:: Vector&lt;байтом >.</span><span class="sxs-lookup"><span data-stu-id="18590-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="18590-130">Необходимо запросить разрешение на доступ к пространственным данным, включая привязки, которые экспортируются системой.</span><span class="sxs-lookup"><span data-stu-id="18590-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

<span data-ttu-id="18590-131">Если выполняется экспорт разрешений и привязок, можно прочитать поток данных.</span><span class="sxs-lookup"><span data-stu-id="18590-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="18590-132">Здесь также показано, как создать объект DataReader и InputStream, который будет использоваться для чтения данных.</span><span class="sxs-lookup"><span data-stu-id="18590-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

<span data-ttu-id="18590-133">После считывания байтов из потока можно сохранить их в собственном буфере данных, например так.</span><span class="sxs-lookup"><span data-stu-id="18590-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="18590-134">Десериализация данных привязки путем их импорта в систему с помощью Спатиаланчортрансферманажер</span><span class="sxs-lookup"><span data-stu-id="18590-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="18590-135">Вспомогательная функция включается в пример кода для загрузки ранее экспортированных данных.</span><span class="sxs-lookup"><span data-stu-id="18590-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="18590-136">Эта функция десериализации предоставляет коллекцию пар "ключ-значение", аналогичную предоставляемой Спатиаланчорсторе, за исключением того, что мы получили эти данные из другого источника, например сетевого сокета.</span><span class="sxs-lookup"><span data-stu-id="18590-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="18590-137">Эти данные можно обработать и причину, прежде чем сохранять их в автономном режиме, используя память в приложении или (если применимо) Спатиаланчорсторе приложения.</span><span class="sxs-lookup"><span data-stu-id="18590-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

<span data-ttu-id="18590-138">Сначала необходимо создать объекты потока для доступа к данным привязки.</span><span class="sxs-lookup"><span data-stu-id="18590-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="18590-139">Мы будем записывать данные из нашего буфера в системный буфер, поэтому мы создадим запись данных, которая записывает данные в поток данных в памяти, чтобы достичь нашей цели получения привязок из буфера байтов в систему как Спатиаланчорс.</span><span class="sxs-lookup"><span data-stu-id="18590-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="18590-140">Опять же, необходимо убедиться, что у приложения есть разрешение на экспорт данных пространственной привязки, которые могут включать в себя закрытые сведения о среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="18590-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="18590-141">Если доступ разрешен, можно записывать байты из буфера в поток системных данных.</span><span class="sxs-lookup"><span data-stu-id="18590-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

<span data-ttu-id="18590-142">Если бы мы смогли сохранить байты в потоке данных, мы можем попытаться импортировать эти данные с помощью Спатиаланчортрансферманажер.</span><span class="sxs-lookup"><span data-stu-id="18590-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

<span data-ttu-id="18590-143">Если данные могут быть импортированы, мы получаем представление сопоставления пар "ключ-значение", связывающее строки с привязками.</span><span class="sxs-lookup"><span data-stu-id="18590-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="18590-144">Мы можем загрузить его в собственную коллекцию данных в памяти и использовать эту коллекцию для поиска привязок, которые мы заинтересованы использовать.</span><span class="sxs-lookup"><span data-stu-id="18590-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

<span data-ttu-id="18590-145">**Примечание.** Так как вы можете импортировать привязку, это не обязательно означает, что ее можно использовать сразу.</span><span class="sxs-lookup"><span data-stu-id="18590-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="18590-146">Привязка может находиться в другой комнате или в другом физическом расположении. привязка не будет размещаемыеа, пока полученное устройство не получит достаточно визуальных сведений о среде, в которой была создана привязка, для восстановления положения привязки относительно известной текущей среды.</span><span class="sxs-lookup"><span data-stu-id="18590-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="18590-147">Реализация клиента должна попытаться найти привязку относительно локальной системы координат или рамки ссылки, прежде чем продолжить использовать ее для содержимого в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="18590-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="18590-148">Например, попробуйте нахождение привязки относительно текущей системы координат, пока привязка не начнет быть размещаемые.</span><span class="sxs-lookup"><span data-stu-id="18590-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="18590-149">Особые рекомендации</span><span class="sxs-lookup"><span data-stu-id="18590-149">Special Considerations</span></span>

<span data-ttu-id="18590-150">API [трекспортанчорсасинк](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) позволяет экспортировать несколько [спатиаланчорс](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) в один и тот же непрозрачный двоичный BLOB-объект.</span><span class="sxs-lookup"><span data-stu-id="18590-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="18590-151">Однако существует небольшая разница в том, какие данные будут включены в большой двоичный объект, в зависимости от того, экспортируется ли один Спатиаланчор или несколько Спатиаланчорс в одном вызове.</span><span class="sxs-lookup"><span data-stu-id="18590-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="18590-152">Экспорт одного Спатиаланчор</span><span class="sxs-lookup"><span data-stu-id="18590-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="18590-153">Большой двоичный объект содержит представление окружения в окружении Спатиаланчор, чтобы среду можно было распознать на устройстве, которое импортирует Спатиаланчор.</span><span class="sxs-lookup"><span data-stu-id="18590-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="18590-154">После завершения импорта новый Спатиаланчор будет доступен для устройства.</span><span class="sxs-lookup"><span data-stu-id="18590-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="18590-155">При условии, что пользователь недавно найдет в области привязки, он будет размещаемые и голограммами, прикрепленными к Спатиаланчор, могут быть подготовлены к просмотру.</span><span class="sxs-lookup"><span data-stu-id="18590-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="18590-156">Эти голограммы будут отображаться в том же физическом расположении, что и на исходном устройстве, в котором был экспортирован Спатиаланчор.</span><span class="sxs-lookup"><span data-stu-id="18590-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![Экспорт одного Спатиаланчор](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="18590-158">Экспорт нескольких Спатиаланчорс</span><span class="sxs-lookup"><span data-stu-id="18590-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="18590-159">Как и при экспорте одного Спатиаланчор, большой двоичный объект содержит представление окружения в области окружения всех заданных Спатиаланчорс.</span><span class="sxs-lookup"><span data-stu-id="18590-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="18590-160">Кроме того, BLOB-объект содержит сведения о соединениях между включаемыми Спатиаланчорс, если они находятся в одном и том же физическом пространстве.</span><span class="sxs-lookup"><span data-stu-id="18590-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="18590-161">Это означает, что если два ближайших Спатиаланчорс импортированы, то голограмма, прикрепленная к *второй* спатиаланчор, будет размещаемые, даже если устройство распознает только среду, окружающую *первый* спатиаланчор, так как достаточно данных для Преобразование вычислений между двумя Спатиаланчорсми было добавлено в большой двоичный объект.</span><span class="sxs-lookup"><span data-stu-id="18590-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="18590-162">Если два Спатиаланчорс были экспортированы по отдельности (два отдельных вызова Трекспортспатиаланчорс), то в большом двоичном объекте могут отсутствовать достаточные данные для голограмм, присоединенных к второй Спатиаланчор, чтобы размещаемые при обнаружении первого из них.</span><span class="sxs-lookup"><span data-stu-id="18590-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![Множественные привязки, экспортированные с помощью одного вызова Трекспортанчорсасинк](images/multipleanchors.png) ![Несколько привязок, экспортируемых с помощью отдельного вызова Трекспортанчорсасинк для каждой привязки](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="18590-165">Пример. Отправка данных привязки с помощью Windows:: Network:: Стреамсоккет</span><span class="sxs-lookup"><span data-stu-id="18590-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="18590-166">Здесь мы предоставляем пример того, как использовать экспортированные данные привязки, отправляя их по сети TCP.</span><span class="sxs-lookup"><span data-stu-id="18590-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="18590-167">Это происходит из Холографикспатиаланчортрансферсампле.</span><span class="sxs-lookup"><span data-stu-id="18590-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="18590-168">Класс Стреамсоккет WinRT использует библиотеку задач PPL.</span><span class="sxs-lookup"><span data-stu-id="18590-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="18590-169">В случае ошибок сети Эта ошибка возвращается к следующей задаче в цепочке с помощью повторно создаваемого исключения.</span><span class="sxs-lookup"><span data-stu-id="18590-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="18590-170">Исключение содержит значение HRESULT, указывающее состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="18590-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="18590-171">Используйте Windows:: Network:: Стреамсоккетлистенер с TCP для отправки экспортированных данных привязки</span><span class="sxs-lookup"><span data-stu-id="18590-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="18590-172">Создайте экземпляр сервера, который прослушивает соединение.</span><span class="sxs-lookup"><span data-stu-id="18590-172">Create a server instance that listens for a connection.</span></span>

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

<span data-ttu-id="18590-173">При получении соединения используйте подключение клиентского сокета для отправки данных привязки.</span><span class="sxs-lookup"><span data-stu-id="18590-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

<span data-ttu-id="18590-174">Теперь можно начать отправку потока данных, содержащего экспортированные данные привязки.</span><span class="sxs-lookup"><span data-stu-id="18590-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

<span data-ttu-id="18590-175">Прежде чем мы можем отправить сам поток, необходимо сначала отправить пакет заголовка.</span><span class="sxs-lookup"><span data-stu-id="18590-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="18590-176">Этот пакет заголовка должен иметь фиксированную длину, а также длину массива байтов, который является потоком привязки данных. в случае этого примера у нас нет других данных заголовка для отправки, поэтому заголовок имеет 4 байта и содержит 32-разрядное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="18590-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

<span data-ttu-id="18590-177">После отправки клиенту длины потока в байтах можно приступать к записи самого потока данных в поток сокета.</span><span class="sxs-lookup"><span data-stu-id="18590-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="18590-178">Это приведет к тому, что байты хранилища привязки будут отправлены клиенту.</span><span class="sxs-lookup"><span data-stu-id="18590-178">This will cause the anchor store bytes to get sent to the client.</span></span>

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

<span data-ttu-id="18590-179">Как отмечалось ранее в этом разделе, необходимо подготовиться к обработке исключений, содержащих сообщения о состоянии ошибок сети.</span><span class="sxs-lookup"><span data-stu-id="18590-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="18590-180">Для неожидаемых ошибок можно записать сведения об исключении в консоль отладки, например так.</span><span class="sxs-lookup"><span data-stu-id="18590-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="18590-181">Это даст нам представление о том, что случилось, если наш пример кода не может завершить соединение или не может завершить отправку данных привязки.</span><span class="sxs-lookup"><span data-stu-id="18590-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="18590-182">Используйте Windows:: Network:: Стреамсоккет с TCP для получения экспортированных данных привязки</span><span class="sxs-lookup"><span data-stu-id="18590-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="18590-183">Сначала необходимо подключиться к серверу.</span><span class="sxs-lookup"><span data-stu-id="18590-183">First, we have to connect to the server.</span></span> <span data-ttu-id="18590-184">В этом примере кода показано, как создать и настроить Стреамсоккет и создать объект DataReader, который можно использовать для получения сетевых данных с помощью подключения к сокету.</span><span class="sxs-lookup"><span data-stu-id="18590-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="18590-185">**Примечание.** Если вы запустите этот пример кода, убедитесь, что вы настроили и запустили сервер перед запуском клиента.</span><span class="sxs-lookup"><span data-stu-id="18590-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

<span data-ttu-id="18590-186">После подключения можно подождать, пока сервер отправит данные.</span><span class="sxs-lookup"><span data-stu-id="18590-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="18590-187">Это делается путем вызова LoadAsync для модуля чтения данных потока.</span><span class="sxs-lookup"><span data-stu-id="18590-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="18590-188">Первый набор получаемых байтов всегда должен быть пакетом заголовка, который указывает длину байт потока данных привязки, как описано в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="18590-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

<span data-ttu-id="18590-189">...</span><span class="sxs-lookup"><span data-stu-id="18590-189">...</span></span>

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

<span data-ttu-id="18590-190">После получения пакета заголовков мы понимаем, сколько байт данных привязки следует рассчитывать.</span><span class="sxs-lookup"><span data-stu-id="18590-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="18590-191">Мы можем перейти к чтению этих байтов из потока.</span><span class="sxs-lookup"><span data-stu-id="18590-191">We can proceed to read those bytes from the stream.</span></span>

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

<span data-ttu-id="18590-192">Вот наш код для получения потока данных привязки.</span><span class="sxs-lookup"><span data-stu-id="18590-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="18590-193">Опять же, мы сначала загружаем байты из потока. выполнение этой операции может занять некоторое время, так как Стреамсоккет ожидает получения этого объема байт из сети.</span><span class="sxs-lookup"><span data-stu-id="18590-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="18590-194">По завершении операции загрузки можно прочитать количество байтов.</span><span class="sxs-lookup"><span data-stu-id="18590-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="18590-195">Если было получено число байтов, которое мы предполагаем для потока данных привязки, можно импортировать данные привязки. в противном случае необходимо иметь некоторый вид ошибки.</span><span class="sxs-lookup"><span data-stu-id="18590-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="18590-196">Например, это может произойти, когда экземпляр сервера завершит работу, прежде чем он сможет завершить передачу потока данных, или сеть будет остановлена до того, как клиент сможет получить весь поток данных.</span><span class="sxs-lookup"><span data-stu-id="18590-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

<span data-ttu-id="18590-197">Опять же, необходимо подготовиться к обработке неизвестных ошибок сети.</span><span class="sxs-lookup"><span data-stu-id="18590-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="18590-198">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="18590-198">That's it!</span></span> <span data-ttu-id="18590-199">Теперь у вас должна быть достаточная информация, чтобы попытаться найти привязки, полученные по сети.</span><span class="sxs-lookup"><span data-stu-id="18590-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="18590-200">Опять же, обратите внимание, что у клиента должно быть достаточно визуальных данных отслеживания для успешного размещения привязки. Если он не работает немедленно, попробуйте выполнить обход в течение определенного временного решения.</span><span class="sxs-lookup"><span data-stu-id="18590-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="18590-201">Если он по-прежнему не работает, пошлите серверу больше привязок и используйте Сетевые подключения, чтобы согласовать его с клиентом.</span><span class="sxs-lookup"><span data-stu-id="18590-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="18590-202">Это можно сделать, загрузив Холографикспатиаланчортрансферсампле, настроив IP-адреса клиента и сервера и развернув их на клиентских и серверных устройствах HoloLens.</span><span class="sxs-lookup"><span data-stu-id="18590-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="18590-203">См. также</span><span class="sxs-lookup"><span data-stu-id="18590-203">See also</span></span>
* [<span data-ttu-id="18590-204">Библиотека параллельных шаблонов (PPL)</span><span class="sxs-lookup"><span data-stu-id="18590-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="18590-205">Windows. Networking. Стреамсоккет</span><span class="sxs-lookup"><span data-stu-id="18590-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="18590-206">Windows. Networking. Стреамсоккетлистенер</span><span class="sxs-lookup"><span data-stu-id="18590-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
