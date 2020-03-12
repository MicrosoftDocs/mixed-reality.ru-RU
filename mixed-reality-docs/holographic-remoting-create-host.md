---
title: Создание удаленного приложения holographic с удаленным взаимодействием
description: Создав удаленное содержимое удаленного приложения с удаленным удаленным доступом, которое будет отображаться на удаленном компьютере, можно передать потоковую передачу в HoloLens 2. В этой статье описывается, как это можно сделать.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: 76e37499fd32a82e6846c6c7cac1a292ef6b553a
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092309"
---
# <a name="writing-a-holographic-remoting-remote-app"></a>Создание удаленного приложения holographic с удаленным взаимодействием

>[!IMPORTANT]
>В этом документе описывается создание удаленного приложения для HoloLens 2. Удаленные приложения для **HoloLens (1-го поколения)** должны использовать пакет NuGet версии **1. x. x**. Это означает, что удаленные приложения, написанные для HoloLens 2, несовместимы с HoloLens 1 и наоборот. Документацию по HoloLens 1 можно найти [здесь](add-holographic-remoting.md).

При создании удаленного приложения с удаленным удаленным доступом удаленное содержимое, отображаемое на удаленном компьютере, можно передать в HoloLens 2. В этой статье описывается, как это можно сделать. Весь код на этой странице и рабочих проектах можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Holographic удаленное взаимодействие позволяет приложению ориентироваться на HoloLens 2 с holographic-содержимым, отображаемым на настольном компьютере или на устройстве UWP, например Xbox One, что обеспечивает доступ к дополнительным системным ресурсам и делает возможным интеграцию удаленных [иммерсивного представлений](app-views.md) в существующее программное обеспечение для настольного ПК. Удаленное приложение получает поток входных данных из HoloLens 2, отображает содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens 2. Подключение устанавливается с использованием стандартного Wi-Fi. Holographic удаленное взаимодействие добавляется в приложение для настольных систем или UWP через пакет NuGet. Требуется дополнительный код, который обрабатывает соединение и готовится к просмотру в режиме погружения.

Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки. Приложение проигрывателя может сообщать о задержке в режиме реального времени.

## <a name="prerequisites"></a>Предварительные требования

Хорошей отправной точкой является работа рабочего стола на основе DirectX или приложения UWP, предназначенного для API Windows Mixed Reality. Дополнительные сведения см. в статье [Общие сведения о разработке DirectX](directx-development-overview.md). [ C++ Шаблон "holographic проект](creating-a-holographic-directx-project.md) " является хорошей отправной точкой.

>[!IMPORTANT]
>Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments). Использование [однопотокового подразделения](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения. При использовании C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) многопотоковое подразделение является значением по умолчанию.



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

После этого необходимо создать новый Holographic. Указывать CoreWindow не требуется. Классические приложения, не имеющие CoreWindow, могут просто передавать ```nullptr```.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Подключение к устройству

Когда удаленное приложение будет готово к отрисовке содержимого, можно установить подключение к устройству.

Соединение может быть выполнено одним из двух способов.
1) Удаленное приложение подключается к проигрывателю, работающему на устройстве.
2) Проигрыватель, выполняющийся на устройстве, подключается к удаленному приложению.

Чтобы установить соединение между удаленным приложением и HoloLens 2, вызовите метод ```Connect``` в удаленном контексте, указав имя узла и порт. Порт, используемый проигрывателем удаленного взаимодействия (holographic), — **8265**.

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
>Как и в C++случае любого API/WinRT, ```Connect``` может вызывать исключение WinRT:: hresult_error, которое необходимо обработать.

>[!TIP]
>Чтобы избежать использования [ C++](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) проекции языка/WinRT, можно добавить файл ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h```, расположенный в пакете NuGet удаленного взаимодействия с удаленным доступом. Он содержит объявления базовых COM-интерфейсов. Однако рекомендуется использовать C++/WinRT.

Прослушивание входящих подключений в удаленном приложении можно выполнить, вызвав метод ```Listen```. Во время этого вызова можно указать как порт подтверждения, так и порт транспорта. Порт подтверждения используется для первоначального подтверждения. Затем данные пересылаются через порт транспорта. По умолчанию используются **8265** и **8266** .

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
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` в пакете NuGet содержит подробную документацию по API, предоставляемому с помощью holographic Remoting.

## <a name="handling-remoting-specific-events"></a>Обработка событий, связанных с удаленным взаимодействием

Удаленный контекст предоставляет три события, которые важны для отслеживания состояния соединения.
1) Подключено: активируется при успешном установлении подключения к устройству.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) Ondisconnectо: активируется, если установленное соединение закрыто или не удалось установить подключение.
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
3) Идет ожидание: при прослушивании входящих подключений начинается.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

Кроме того, состояние соединения можно запросить с помощью свойства ```ConnectionState``` в удаленном контексте.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Обработка событий речи

С помощью удаленного речевого интерфейса можно зарегистрировать речевые триггеры в HoloLens 2 и удаленно взаимодействовать с удаленным приложением.

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

С помощью асинхронного вспомогательного метода можно инициализировать удаленный голос. Это необходимо сделать асинхронно, так как инициализация может занять значительное время. [Параллельные и асинхронные операции C++с/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) объясняет, как создавать асинхронные C++функции с помощью/винрт.

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
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

Существует два способа указания фраз для распознавания.
1) Спецификация внутри XML-файла грамматики речи. Дополнительные сведения см. [в статье Создание базовой грамматики XML](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .
2) Укажите, передав их в векторе словаря в ```ApplyParameters```.

Внутри обратного вызова Онрекогнизедспич можно обработать события речи:

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
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

Чтобы отобразить то же содержимое в удаленном приложении, которое отправляется на устройство, можно использовать ```OnSendFrame```ное событие удаленного контекста. Событие ```OnSendFrame``` активируется каждый раз, когда библиотека holographic Remote Remoting отправляет текущий кадр на удаленное устройство. Это идеальное время для получения содержимого, а также Блит его в окно рабочего стола или UWP.

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

## <a name="depth-reprojection"></a>Репроектная глубина

Начиная с версии [2.1.0](holographic-remoting-version-history.md#v2.1.0), holographic удаленное взаимодействие поддерживает [репроекцию с глубиной](hologram-stability.md#reprojection). Для этого в дополнение к буферу цвета также требуется потоковая передача буфера глубины из удаленного приложения в HoloLens 2. По умолчанию буфер глубины передается по потоку в половину разрешения буфера цвета. Это можно изменить следующим образом:

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

Обратите внимание, что перед установкой соединения с HoloLens 2 необходимо вызвать ```ConfigureDepthVideoStream```. Лучшее место будет сразу после создания удаленного контекста. Возможные значения: Full, половина и Quarter. Значение по умолчанию — половина разрешения. Помните, что использование буфера глубины полного разрешения также влияет на требования к пропускной способности и должно учитывать максимальное значение пропускной способности, предоставленное для ```CreateRemoteContext```.

При настройке разрешения необходимо также зафиксировать буфер глубины с помощью [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

Чтобы проверить, распределялись ли в HoloLens 2 более глубокое переработка, вы можете включить визуализатор глубины с помощью портала устройств. Дополнительные сведения см. в разделе [Проверка глубины правильно настроена](hologram-stability.md#verifying-depth-is-set-correctly) .

## <a name="optional-custom-data-channels"></a>Необязательно: пользовательские каналы данных

Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное соединение. Дополнительные сведения см. в разделе [пользовательские каналы данных](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>См. также
* [Написание пользовательского приложения для удаленного взаимодействия holographic](holographic-remoting-create-player.md)
* [Пользовательские каналы данных с голографическим удаленным взаимодействием](holographic-remoting-custom-data-channels.md)
* [Установление безопасного подключения с помощью удаленного взаимодействия с holographic](holographic-remoting-secure-connection.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление о конфиденциальности Майкрософт](https://go.microsoft.com/fwlink/?LinkId=521839)
