---
title: Передача локального привязки в DirectX
description: Описаны способы синхронизации двух устройств HoloLens, передавая пространственных привязки.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, синхронизировать, пространственных привязки, перемещение, многопользовательскую, просмотреть, сценарии, пошаговое руководство, образцы кода, передачи, передачи локального привязки, привязки экспорта и импорта привязки
ms.openlocfilehash: 5d03f4bfa764b9948ec4718bce86127cfcc3e303
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605066"
---
# <a name="local-anchor-transfers-in-directx"></a>Передача локального привязки в DirectX

В ситуациях, когда невозможно использовать <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">привязки пространственных Azure</a>, передача локального привязки включить одно устройство HoloLens Экспорт привязки импортируемой второе устройство HoloLens.

>[!NOTE]
>Передачи локального привязки позволяют менее надежны, отзыв привязки, чем <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">привязки пространственных Azure</a>, и устройства iOS и Android не поддерживаются, этот подход.

>[!NOTE]
>Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).  Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.

## <a name="transferring-spatial-anchors"></a>Передача пространственных привязки

Пространственные привязки можно передавать между устройствами Windows Mixed Reality с помощью [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Этот API позволяет формировать привязки всех датчиков информацию, необходимые для поиска, шифрованию в мире, а затем импортировать этот пакет на другом устройстве. После импорта в приложение на втором устройстве эту привязку каждого приложения можно визуализировать с помощью голограммы, которые совместно системы координат пространственных привязки, который затем будет отображаться в том же месте в реальном мире.

Обратите внимание, что Пространственные привязки не могут передавать между различных типов устройств, например привязку пространственных HoloLens может быть не может быть найдена иммерсивных гарнитуры.  Перенесенные привязки также не совместимы с устройства iOS или Android.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Настройка приложения для использования возможности spatialPerception

Приложение должно быть предоставлено разрешение использовать возможности spatialPerception, прежде чем он сможет использовать [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Это необходимо, поскольку передача пространственных привязки включает совместное использование образов датчиков, собранных за период времени в ближайших эту привязку, которая может включать конфиденциальные сведения.

Объявите данную возможность в файле package.appxmanifest для вашего приложения. Ниже приведен пример:

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

Возможность поступает из **uap2** пространства имен. Чтобы получить доступ к этому пространству имен в манифесте, включить его как *xlmns* атрибут в &lt;пакета > элемента. Ниже приведен пример:

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**ПРИМЕЧАНИЕ.** Вашему приложению потребуется запросить возможность во время выполнения, прежде чем он может обращаться к SpatialAnchor экспорта и импорта API-интерфейсы. См. в разделе [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) в приведенных ниже примерах.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Сериализация привязки данных путем их экспорта с SpatialAnchorTransferManager

Вспомогательная функция включается в образце кода для экспорта (сериализация) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) данных. Этот API экспорта сериализует все привязки в коллекцию пар "ключ значение", сопоставление строк с помощью привязки.

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

Во-первых нам нужно настроить поток данных. Это позволит нам 1.) Используйте TryExportAnchorsAsync поместить данные в буфере, принадлежащих приложению, а 2). чтение данных из потока буфера экспортированного байтов — это поток данных WinRT - в нашей буфер памяти, который представляет std::vector&lt;байтов >.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

Нам нужно запросить разрешение на доступ к пространственных данных, включая привязки, которые экспортируются в системе.

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

Если мы получаем разрешение и экспортируются привязки, можно выполнить чтение потока данных. Здесь также показано, как создать DataReader и InputStream, мы будем использовать для чтения данных.

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

После мы байтов, считанных из потока, их можно сохранить для нашего собственного буфера данных следующим образом.

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Десериализации привязки данных, импортируйте ее в систему, используя SpatialAnchorTransferManager

Вспомогательная функция включена в пример кода для загрузки ранее экспортированные данные. Эта функция десериализации предоставляет коллекцию пар ключ значение, подобно тому как предоставляет SpatialAnchorStore -, за исключением того, что у нас есть эти данные из другого источника, например к сетевому сокету. Можно обработать и выводы о эти данные перед их сохранением в автономном режиме, с использованием памяти в приложении, или (если применимо) SpatialAnchorStore вашего приложения.

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

Во-первых необходимо создать поток объектов для доступа к данным привязки. Мы будет записывать данные из наших буфера в буфер системы, поэтому мы создадим DataWriter, который записывает в поток данных в памяти для достижения нашей цели получения привязки из буфер байтов в систему как SpatialAnchors.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Опять же нам нужно убедиться, что приложение имеет разрешения на экспорт пространственных привязки данных, которая может включать закрытые данные об среду.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Если доступ разрешен, можно написать байты из буфера в поток данных системы.

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

Если мы выполнены успешно при записи байтов в поток данных, мы стараемся Импорт данных с помощью SpatialAnchorTransferManager.

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

Если данные невозможно импортировать, мы получаем представление карты пар "ключ значение", сопоставление строк с привязки. Мы можно загрузить это в нашей коллекции данных в памяти и использовать для поиска элементов привязки, что нас интересует с помощью этой коллекции.

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

**ПРИМЕЧАНИЕ.** Только потому, что можно импортировать привязку, не обязательно означает, что можно использовать ее прямо сейчас. Привязка может находиться в другой комнате или другое физическое местоположение полностью; привязка не будет может быть найдена, пока устройство, которое его получили имеет достаточно visual сведений о среде создания привязки, для восстановления привязка позиции относительно известных текущей среды. Реализация клиента следует попробовать расположить привязки по отношению к вашей локальной системе координат или фрейм ссылку перед переходом на попытаться использовать его для содержимого в реальном времени. Например попробуйте поиск привязки относительно текущую систему координат, периодически до привязки начинает искать.

## <a name="special-considerations"></a>Особые замечания

[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API позволяет использовать несколько [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) для экспорта в том же непрозрачный двоичный объект blob. Однако есть небольшая разница в том, какие данные, будет включать большой двоичный объект, в зависимости от экспортировать SpatialAnchor одного или нескольких SpatialAnchors за один вызов.

### <a name="export-of-a-single-spatialanchor"></a>Экспорт одной SpatialAnchor

Большой двоичный объект содержит представление среды вблизи SpatialAnchor таким образом, чтобы среду можно распознать на устройство, которое импортирует SpatialAnchor. После завершения импорта новой SpatialAnchor будут доступны устройству. Если пользователь недавно был ближайшие привязки, она может быть найдена и голограммы, подключенный к SpatialAnchor могут быть визуализированы. Эти голограммы будут отображаться в одном месте, они были на исходном устройстве, которое экспортирован SpatialAnchor.

![Экспорт одной SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Экспорт нескольких SpatialAnchors

Как экспорта одного SpatialAnchor большой двоичный объект содержит представление среды вблизи все указанного SpatialAnchors. Кроме того большой двоичный объект содержит сведения о соединениях между SpatialAnchors включены, если они находятся в том же физическом пространстве. Это означает, что если импортируются два рядом SpatialAnchors, голограмма прикрепляется к *второй* SpatialAnchor будет может быть найдена, даже если устройство только определяет окружающей среды *первый* SpatialAnchor, так как недостаточно данных для вычисления преобразования между двумя SpatialAnchors был включен в большой двоичный объект. Если два SpatialAnchors были экспортированы по отдельности (два отдельных вызовов TryExportSpatialAnchors) может не потребоваться находится достаточно данных, включенные в большой двоичный объект для голограммы присоединен к второй SpatialAnchor как может быть найдена при первой.

![Несколько привязок, экспортированные с помощью одного вызова TryExportAnchorsAsync](images/multipleanchors.png) ![Несколько привязок, экспортированные с помощью отдельного вызова TryExportAnchorsAsync для каждой привязки](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Пример. Отправка данных привязки, с помощью Windows::Networking::StreamSocket

Здесь мы предлагаем пример демонстрирует использование экспортированных привязки данных, отправляя ему в сети TCP. Пример взят из HolographicSpatialAnchorTransferSample.

В классе WinRT StreamSocket используется библиотека задач PPL. В случае ошибки сети то возвращается ошибка к следующей задаче в цепочке, используя исключение, которое выдается повторно. Исключение содержит значение HRESULT, указывающее состояние ошибки.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Использовать Windows::Networking::StreamSocketListener с TCP для отправки экспортированного привязки данных

Создайте экземпляр сервера, который ожидает передачи данных для подключения.

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

При получении соединения и использовать подключение сокета клиента для отправки данных привязки.

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

Теперь мы можем начать для отправки потока данных, содержащий экспортированные привязки данных.

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

Прежде чем мы можем отправлять сам поток, мы сначала необходимо отправить пакет заголовка. Этот пакет заголовок должен иметь фиксированную длину, и он также должен указывать длина переменной массив байтов, который является поток данных привязки; в случае в этом примере у нас нет других данных заголовка для отправки так что заголовка является длиной 4 байта и содержит 32-разрядное целое число без знака.

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

После отправки клиенту длину потока, в байтах, можно переходить к записи сам поток данных в поток сокета. В результате привязки хранилища байтов, отправляемых клиенту.

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

Как отмечалось ранее в этом разделе, мы должны быть готовы обрабатывать исключения, содержащий сообщений о состоянии ошибки сети. Для ошибок, не ожидаются, мы можем написать сведения об исключении в консоль отладки следующим образом. Это даст нам понять, что произошло, если наш пример кода не удалось выполнить подключение, или в том случае, если это не удалось завершить отправку привязки данных.

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Используйте Windows::Networking::StreamSocket с TCP для получения экспортированного привязки данных

Во-первых нам нужно подключиться к серверу. В этом примере кода показано, как создать и настроить StreamSocket и создание объекта DataReader, можно использовать для получения данных по сети, используя подключение к сокету.

**ПРИМЕЧАНИЕ.** Если запустить этот пример кода, убедитесь, что описана настройка и запуск сервера перед запуском клиента.

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

Когда соединение, мы можем подождать сервера для отправки данных. Это делается путем вызова LoadAsync для чтения потока данных.

Первый набор байтов, которые мы получаем всегда должно быть заголовок пакета, который указывает, что поток данных привязки байт, как описано в предыдущем разделе.

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

...

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

После получения заголовок пакета, мы знаем, сколько байтов привязки данных, стоит ожидать. Можно переходить к этих байтов, считанных из потока.

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

Вот наш код для получения потока привязки данных. Опять же мы сначала загрузит байты из потока; Эта операция может занять некоторое время как StreamSocket будет ожидать получения, количество байтов из сети.

После завершения операции загрузки, мы прочитали это количество байтов. Если мы получили число байтов, ожидается, что для потока данных привязки, мы продолжим и импорт данных привязки; в противном случае необходимо были внесены определенные ошибки. Например это может произойти при завершении работы экземпляра сервера, прежде чем можно было завершить отправки потока данных, или сеть перестает работать, прежде чем клиент получил в поток данных.

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

Опять же мы должны быть готовы обрабатывать неизвестные сетевые ошибки.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

Вот и все! Теперь должен иметь достаточно информации, чтобы попробовать расположить привязки, полученных по сети. Обратите внимание, что клиент должен иметь достаточно данных visual отслеживания для пространства успешно найти точку привязки. Если это не поможет прямо сейчас, попробуйте прогулке по некоторое время. Если это не помогло, иметь сервер Отправка дополнительные привязки и использование сети согласиться на тот, который работает для клиента. Это можно испытать, загрузка HolographicSpatialAnchorTransferSample, настройку клиента и сервера IP-адресов и развернув его на устройствах HoloLens клиентом и сервером.

## <a name="see-also"></a>См. также
* [Библиотека параллельных шаблонов (PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows.Networking.StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows.Networking.StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
