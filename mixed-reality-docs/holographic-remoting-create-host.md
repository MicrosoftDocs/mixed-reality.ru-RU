---
title: Создание хост-приложения holographic с удаленным взаимодействием
description: Создание удаленного содержимого узла с удаленным удаленным доступом для удаленного взаимодействия, которое отображается на удаленном компьютере, можно передать в HoloLens 2. В этой статье описывается, как это можно сделать.
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: 6b0f92fce1099ec98d87100e015de9442bff6bd2
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122023"
---
# <a name="writing-a-holographic-remoting-host-app"></a>Создание хост-приложения holographic с удаленным взаимодействием

>[!IMPORTANT]
>В этом документе описывается создание ведущего приложения для HoloLens 2. Ведущее приложение для **HoloLens (1-го поколения)** должно использовать пакет NuGet версии **1. x. x**. Это подразумевает, что ведущие приложения, написанные для HoloLens 2, несовместимы с HoloLens 1 и наоборот. Документацию по HoloLens 1 можно найти [здесь](add-holographic-remoting.md).

Создав удаленное содержимое удаленного приложения с удаленным удаленным доступом, которое будет передаваться на удаленный компьютер, можно передать в HoloLens 2. В этой статье описывается, как это можно сделать. Весь код на этой странице и рабочих проектах можно найти в репозитории [GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Holographic удаленное взаимодействие позволяет приложению ориентироваться на HoloLens 2 с holographic-содержимым, размещенным на настольном компьютере или на устройстве UWP, например на Xbox One, что обеспечивает доступ к дополнительным системным ресурсам и делает возможным интеграцию удаленных [иммерсивное представлений](app-views.md) в существующие программное обеспечение для настольных ПК. Удаленное приложение узла удаленного взаимодействия получает поток входных данных от HoloLens 2, визуализирует содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens 2. Подключение устанавливается с использованием стандартного Wi-Fi. Holographic удаленное взаимодействие добавляется в приложение для настольных систем или UWP через пакет NuGet. Требуется дополнительный код, который обрабатывает соединение и готовится к просмотру в режиме погружения.

Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки. Приложение проигрывателя может сообщать о задержке в режиме реального времени.

## <a name="prerequisites"></a>Предварительные требования

Хорошей отправной точкой является работа рабочего стола на основе DirectX или приложения UWP, предназначенного для API Windows Mixed Reality. Дополнительные сведения см. в статье [Общие сведения о разработке DirectX](directx-development-overview.md). [ C++ Шаблон "holographic проект](creating-a-holographic-directx-project.md) " является хорошей отправной точкой.

>[!IMPORTANT]
>Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments). Использование однопотокового [подразделения](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения. При использовании C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) по умолчанию используется многопотоковое подразделение.



## <a name="get-the-holographic-remoting-nuget-package"></a>Получение пакета NuGet для удаленного взаимодействия с holographic

Чтобы добавить пакет NuGet в проект в Visual Studio, необходимо выполнить следующие действия.
1. Откройте проект в Visual Studio.
2. Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**
3. На появившейся панели нажмите кнопку **Обзор** и найдите "holographic Remoting".
4. Выберите **Microsoft. Holographic. удаленное взаимодействие**, обязательно выберите последнюю версию **2. x. x** и нажмите кнопку **установить**.
5. Если откроется диалоговое окно **предварительного просмотра** , нажмите кнопку **ОК**.
6. Следующее появившееся диалоговое окно — это лицензионное соглашение. Нажмите кнопку **я принимаю** , чтобы принять условия лицензионного соглашения.

>[!NOTE]
>Версия **1. x. x** пакета NuGet по-прежнему доступна для разработчиков, желающих выбрать HoloLens 1. Дополнительные сведения см. в разделе [Добавление удаленного взаимодействия holographic (HoloLens (1-й общий))](add-holographic-remoting.md).

## <a name="create-the-remote-context"></a>Создание удаленного контекста

В качестве первого шага приложение должно создать удаленный контекст.

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>Holographic удаленное взаимодействие выполняется путем замены среды выполнения Windows Mixed Reality, которая является частью Windows, на среду выполнения с удаленным взаимодействием. Это делается во время создания удаленного контекста. По этой причине любой вызов любого API Windows Mixed Reality перед созданием удаленного контекста может привести к непредвиденному поведению. Рекомендуемый подход состоит в том, чтобы создать удаленный контекст как можно раньше перед взаимодействием с любым API смешанной реальности. Никогда не смешивать объекты, созданные или полученные через API Windows Mixed Reality до вызова Креатеремотеконтекст с объектами, созданными или полученными позже.

После этого необходимо создать новый Holographic. Указывать CoreWindow не требуется. Классические приложения, у которых нет CoreWindowа, могут просто передать ```nullptr```.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Подключение к устройству

После того как ведущее приложение готово к отрисовке содержимого, можно установить подключение к устройству.

Соединение может быть выполнено одним из двух способов.
1) Ведущее приложение подключается к проигрывателю, работающему на устройстве.
2) Проигрыватель, выполняющийся на устройстве, подключается к ведущему приложению.

Чтобы установить соединение между ведущим приложением и HoloLens 2, вызовите ```Connect``` метод в удаленном контексте, указав имя узла и порт. Порт, используемый проигрывателем удаленного взаимодействия (holographic), — **8265**.

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Как и в C++случае любого ```Connect``` API/WinRT, может возникнуть исключение WinRT:: hresult_error, который необходимо обработать.

>[!TIP]
>Чтобы избежать использования [ C++](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/) проекции языка/WinRT, ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` можно добавить файл, расположенный в пакете NuGet удаленного взаимодействия с удаленным доступом. Он содержит объявления базовых COM-интерфейсов. Однако рекомендуется использовать C++/WinRT.

Прослушивание входящих подключений в ведущем приложении можно выполнить, вызвав ```Listen``` метод. Во время этого вызова можно указать как порт подтверждения, так и порт транспорта. Порт подтверждения используется для первоначального подтверждения. Затем данные пересылаются через порт транспорта. По умолчанию используются **8265** и **8266** .

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>В ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` пакете NuGet содержится подробная документация по API, предоставляемому с помощью holographic Remoting.

## <a name="handling-remoting-specific-events"></a>Обработка событий, связанных с удаленным взаимодействием

Удаленный контекст предоставляет три события, которые важны для отслеживания состояния соединения.
1) Подключено: Активируется при успешном установлении подключения к устройству.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) Отключено: Активируется, если установленное соединение закрыто или не удалось установить подключение.
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) Ожидание: При ожидании запуска входящих подключений.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

Кроме того, состояние соединения можно запросить с помощью ```ConnectionState``` свойства в удаленном контексте.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Обработка событий речи

С помощью удаленного речевого интерфейса можно зарегистрировать речевые триггеры в HoloLens 2 и удаленно выполнять их в ведущем приложении.

Этот дополнительный элемент необходим для отслеживания состояния удаленного распознавания речи.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

Сначала необходимо получить удаленный речевой интерфейс.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

С помощью асинхронного вспомогательного метода можно инициализировать удаленный голос. Это необходимо сделать асинхронно, так как инициализация может занять значительное время. [Параллельные и асинхронные операции C++с/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) объясняет, как создавать асинхронные C++функции с помощью/винрт.

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleHostMain> sampleHostMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleHostMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleHostMain = sampleHostMainWeak.lock())
            {
                sampleHostMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"en-US", grammarFile, dictionary);
}
```

Существует два способа указания фраз для распознавания.
1) Спецификация внутри XML-файла грамматики речи. Дополнительные сведения см. [в статье Создание базовой грамматики XML](https://docs.microsoft.com/en-us/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .
2) Укажите, передав их в векторе словаря в ```ApplyParameters```.

Внутри обратного вызова Онрекогнизедспич можно обработать события речи:

```cpp
void SampleHostMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>Предварительный просмотр потокового содержимого на локальном компьютере

Чтобы отобразить то же содержимое в ведущем приложении, которое отправляется на устройство ```OnSendFrame``` , можно использовать событие удаленного контекста. ```OnSendFrame``` Событие активируется каждый раз, когда в удаленной библиотеке holographic текущий кадр отправляется на удаленное устройство. Это идеальное время для получения содержимого, а также Блит его в окно рабочего стола или UWP.

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="optional-custom-data-channels"></a>Дополнительно Пользовательские каналы данных

Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное соединение. Дополнительные сведения см. в разделе [пользовательские каналы данных](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>См. также
* [Написание пользовательского приложения для удаленного взаимодействия holographic](holographic-remoting-create-player.md)
* [Пользовательские каналы данных с голографическим удаленным взаимодействием](holographic-remoting-custom-data-channels.md)
* [Установление безопасного подключения с помощью удаленного взаимодействия с holographic](holographic-remoting-secure-connection.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление о конфиденциальности Майкрософт](https://go.microsoft.com/fwlink/?LinkId=521839)
