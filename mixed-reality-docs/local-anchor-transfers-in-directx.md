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
# <a name="local-anchor-transfers-in-directx"></a>Передача локальных привязок в DirectX

В ситуациях, когда нельзя использовать <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>, передача локальных точек подключения позволяет одному устройству hololens экспортировать привязку, которая будет импортирована вторым устройством hololens.

>[!NOTE]
>Передача локальных привязок обеспечивает менее устойчивое отзыв, чем <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>, а устройства iOS и Android не поддерживаются этим подходом.

>[!NOTE]
>Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

## <a name="transferring-spatial-anchors"></a>Передача пространственных привязок

Вы можете передавать пространственные привязки между устройствами Windows Mixed Reality с помощью [спатиаланчортрансферманажер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Этот API позволяет объединять привязку со всеми поддерживающими данными датчика, необходимыми для поиска точного места в мире, а затем импортировать этот пакет на другом устройстве. После того, как приложение на втором устройстве импортировало эту привязку, каждое приложение может визуализировать голограммы с помощью этой системы координат общей пространственной привязки, которая затем будет отображаться в том же месте реального мира.

Обратите внимание, что пространственные привязки не могут перемещаться между разными типами устройств, например, пространственный якорь HoloLens может не размещаемые с помощью иммерсивного головного телефона.  Передаваемые привязки также несовместимы с устройствами iOS или Android.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Настройка приложения для использования возможности Спатиалперцептион

Приложению должно быть предоставлено разрешение на использование возможности Спатиалперцептион, прежде чем оно сможет использовать [спатиаланчортрансферманажер](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Это необходимо потому, что передача пространственной привязки включает в себя общий доступ к изображениям датчика, собранным со временем в результате этой привязки, которая может содержать конфиденциальные сведения.

Объявите эту возможность в файле Package. appxmanifest для приложения. Вот пример.

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

Эта возможность поступает из пространства имен **uap2** . Чтобы получить доступ к этому пространству имен в манифесте, включите его в качестве атрибута *кслмнс* в элемент &lt;пакета >. Вот пример.

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**Примечание.** Приложению потребуется запросить возможность во время выполнения, прежде чем он сможет получить доступ к API экспорта и импорта Спатиаланчор. См. раздел [рекуестакцессасинк](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) в примерах ниже.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Сериализация данных привязки путем их экспорта с помощью Спатиаланчортрансферманажер

Вспомогательная функция включается в пример кода для экспорта (сериализации) [спатиаланчор](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) данных. Этот API экспорта сериализует все привязки в коллекции пар "ключ-значение", связывающие строки с привязками.

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

Сначала необходимо настроить поток данных. Это позволит нам получить 1.) Используйте Трекспортанчорсасинк, чтобы разместить данные в буфере, принадлежащем приложению, и 2.) чтение данных из экспортированного потока байтового буфера, который представляет собой поток данных WinRT, в собственный буфер памяти, который является стандартом std:: Vector&lt;байтом >.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

Необходимо запросить разрешение на доступ к пространственным данным, включая привязки, которые экспортируются системой.

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

Если выполняется экспорт разрешений и привязок, можно прочитать поток данных. Здесь также показано, как создать объект DataReader и InputStream, который будет использоваться для чтения данных.

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

После считывания байтов из потока можно сохранить их в собственном буфере данных, например так.

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Десериализация данных привязки путем их импорта в систему с помощью Спатиаланчортрансферманажер

Вспомогательная функция включается в пример кода для загрузки ранее экспортированных данных. Эта функция десериализации предоставляет коллекцию пар "ключ-значение", аналогичную предоставляемой Спатиаланчорсторе, за исключением того, что мы получили эти данные из другого источника, например сетевого сокета. Эти данные можно обработать и причину, прежде чем сохранять их в автономном режиме, используя память в приложении или (если применимо) Спатиаланчорсторе приложения.

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

Сначала необходимо создать объекты потока для доступа к данным привязки. Мы будем записывать данные из нашего буфера в системный буфер, поэтому мы создадим запись данных, которая записывает данные в поток данных в памяти, чтобы достичь нашей цели получения привязок из буфера байтов в систему как Спатиаланчорс.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Опять же, необходимо убедиться, что у приложения есть разрешение на экспорт данных пространственной привязки, которые могут включать в себя закрытые сведения о среде пользователя.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Если доступ разрешен, можно записывать байты из буфера в поток системных данных.

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

Если бы мы смогли сохранить байты в потоке данных, мы можем попытаться импортировать эти данные с помощью Спатиаланчортрансферманажер.

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

Если данные могут быть импортированы, мы получаем представление сопоставления пар "ключ-значение", связывающее строки с привязками. Мы можем загрузить его в собственную коллекцию данных в памяти и использовать эту коллекцию для поиска привязок, которые мы заинтересованы использовать.

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

**Примечание.** Так как вы можете импортировать привязку, это не обязательно означает, что ее можно использовать сразу. Привязка может находиться в другой комнате или в другом физическом расположении. привязка не будет размещаемыеа, пока полученное устройство не получит достаточно визуальных сведений о среде, в которой была создана привязка, для восстановления положения привязки относительно известной текущей среды. Реализация клиента должна попытаться найти привязку относительно локальной системы координат или рамки ссылки, прежде чем продолжить использовать ее для содержимого в реальном времени. Например, попробуйте нахождение привязки относительно текущей системы координат, пока привязка не начнет быть размещаемые.

## <a name="special-considerations"></a>Особые рекомендации

API [трекспортанчорсасинк](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) позволяет экспортировать несколько [спатиаланчорс](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) в один и тот же непрозрачный двоичный BLOB-объект. Однако существует небольшая разница в том, какие данные будут включены в большой двоичный объект, в зависимости от того, экспортируется ли один Спатиаланчор или несколько Спатиаланчорс в одном вызове.

### <a name="export-of-a-single-spatialanchor"></a>Экспорт одного Спатиаланчор

Большой двоичный объект содержит представление окружения в окружении Спатиаланчор, чтобы среду можно было распознать на устройстве, которое импортирует Спатиаланчор. После завершения импорта новый Спатиаланчор будет доступен для устройства. При условии, что пользователь недавно найдет в области привязки, он будет размещаемые и голограммами, прикрепленными к Спатиаланчор, могут быть подготовлены к просмотру. Эти голограммы будут отображаться в том же физическом расположении, что и на исходном устройстве, в котором был экспортирован Спатиаланчор.

![Экспорт одного Спатиаланчор](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Экспорт нескольких Спатиаланчорс

Как и при экспорте одного Спатиаланчор, большой двоичный объект содержит представление окружения в области окружения всех заданных Спатиаланчорс. Кроме того, BLOB-объект содержит сведения о соединениях между включаемыми Спатиаланчорс, если они находятся в одном и том же физическом пространстве. Это означает, что если два ближайших Спатиаланчорс импортированы, то голограмма, прикрепленная к *второй* спатиаланчор, будет размещаемые, даже если устройство распознает только среду, окружающую *первый* спатиаланчор, так как достаточно данных для Преобразование вычислений между двумя Спатиаланчорсми было добавлено в большой двоичный объект. Если два Спатиаланчорс были экспортированы по отдельности (два отдельных вызова Трекспортспатиаланчорс), то в большом двоичном объекте могут отсутствовать достаточные данные для голограмм, присоединенных к второй Спатиаланчор, чтобы размещаемые при обнаружении первого из них.

![Множественные привязки, экспортированные с помощью одного вызова Трекспортанчорсасинк](images/multipleanchors.png) ![Несколько привязок, экспортируемых с помощью отдельного вызова Трекспортанчорсасинк для каждой привязки](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Пример. Отправка данных привязки с помощью Windows:: Network:: Стреамсоккет

Здесь мы предоставляем пример того, как использовать экспортированные данные привязки, отправляя их по сети TCP. Это происходит из Холографикспатиаланчортрансферсампле.

Класс Стреамсоккет WinRT использует библиотеку задач PPL. В случае ошибок сети Эта ошибка возвращается к следующей задаче в цепочке с помощью повторно создаваемого исключения. Исключение содержит значение HRESULT, указывающее состояние ошибки.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Используйте Windows:: Network:: Стреамсоккетлистенер с TCP для отправки экспортированных данных привязки

Создайте экземпляр сервера, который прослушивает соединение.

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

При получении соединения используйте подключение клиентского сокета для отправки данных привязки.

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

Теперь можно начать отправку потока данных, содержащего экспортированные данные привязки.

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

Прежде чем мы можем отправить сам поток, необходимо сначала отправить пакет заголовка. Этот пакет заголовка должен иметь фиксированную длину, а также длину массива байтов, который является потоком привязки данных. в случае этого примера у нас нет других данных заголовка для отправки, поэтому заголовок имеет 4 байта и содержит 32-разрядное целое число без знака.

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

После отправки клиенту длины потока в байтах можно приступать к записи самого потока данных в поток сокета. Это приведет к тому, что байты хранилища привязки будут отправлены клиенту.

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

Как отмечалось ранее в этом разделе, необходимо подготовиться к обработке исключений, содержащих сообщения о состоянии ошибок сети. Для неожидаемых ошибок можно записать сведения об исключении в консоль отладки, например так. Это даст нам представление о том, что случилось, если наш пример кода не может завершить соединение или не может завершить отправку данных привязки.

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Используйте Windows:: Network:: Стреамсоккет с TCP для получения экспортированных данных привязки

Сначала необходимо подключиться к серверу. В этом примере кода показано, как создать и настроить Стреамсоккет и создать объект DataReader, который можно использовать для получения сетевых данных с помощью подключения к сокету.

**Примечание.** Если вы запустите этот пример кода, убедитесь, что вы настроили и запустили сервер перед запуском клиента.

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

После подключения можно подождать, пока сервер отправит данные. Это делается путем вызова LoadAsync для модуля чтения данных потока.

Первый набор получаемых байтов всегда должен быть пакетом заголовка, который указывает длину байт потока данных привязки, как описано в предыдущем разделе.

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

После получения пакета заголовков мы понимаем, сколько байт данных привязки следует рассчитывать. Мы можем перейти к чтению этих байтов из потока.

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

Вот наш код для получения потока данных привязки. Опять же, мы сначала загружаем байты из потока. выполнение этой операции может занять некоторое время, так как Стреамсоккет ожидает получения этого объема байт из сети.

По завершении операции загрузки можно прочитать количество байтов. Если было получено число байтов, которое мы предполагаем для потока данных привязки, можно импортировать данные привязки. в противном случае необходимо иметь некоторый вид ошибки. Например, это может произойти, когда экземпляр сервера завершит работу, прежде чем он сможет завершить передачу потока данных, или сеть будет остановлена до того, как клиент сможет получить весь поток данных.

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

Опять же, необходимо подготовиться к обработке неизвестных ошибок сети.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

Вот и все! Теперь у вас должна быть достаточная информация, чтобы попытаться найти привязки, полученные по сети. Опять же, обратите внимание, что у клиента должно быть достаточно визуальных данных отслеживания для успешного размещения привязки. Если он не работает немедленно, попробуйте выполнить обход в течение определенного временного решения. Если он по-прежнему не работает, пошлите серверу больше привязок и используйте Сетевые подключения, чтобы согласовать его с клиентом. Это можно сделать, загрузив Холографикспатиаланчортрансферсампле, настроив IP-адреса клиента и сервера и развернув их на клиентских и серверных устройствах HoloLens.

## <a name="see-also"></a>См. также
* [Библиотека параллельных шаблонов (PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows. Networking. Стреамсоккет](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows. Networking. Стреамсоккетлистенер](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
