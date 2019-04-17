---
title: Добавление holographic удаленного взаимодействия
description: В этой статье описывается использование Holographic удаленного взаимодействия для подготовки к просмотру голограммы для HoloLens по сети.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, голограммы, holographic удаленного взаимодействия, удаленной визуализации, визуализации, HoloLens, голограммы удаленной сети
ms.openlocfilehash: 4726c6af43fe1b89fc8298e459a1af9dfa5fc667
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605126"
---
# <a name="add-holographic-remoting"></a>Добавление holographic удаленного взаимодействия

> [!NOTE]
> Дополнительные рекомендации, относящиеся к HoloLens 2 [ожидается в ближайшее время](index.md#news-and-notes).

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Добавление holographic удаленного взаимодействия на рабочий стол или приложение универсальной платформы Windows

Эта страница описывает способы добавления Holographic удаленного взаимодействия на рабочий стол или приложение универсальной платформы Windows.

Holographic удаленное взаимодействие позволяет вашему приложению для HoloLens holographic содержимого, размещенного на настольном Компьютере или на устройстве универсальной платформы Windows, таких как Xbox One, благодаря доступу к больше системных ресурсов, а также что позволяет интегрировать удаленного [иммерсивных представления](app-views.md) в desktop существующего программного обеспечения. В приложении узла удаленного взаимодействия получает потока входных данных от HoloLens и отрисовывает содержимое в виде виртуального иммерсивных выполняет потоковую передачу содержимого кадров, вернитесь к HoloLens. Соединение устанавливается с помощью стандартных Wi-Fi. Чтобы использовать удаленное взаимодействие, используется пакет NuGet, чтобы добавить на рабочий стол или приложение универсальной платформы Windows holographic удаленного взаимодействия и написать код для обработки подключения и для подготовки к просмотру в иммерсивных представлении. Вспомогательные библиотеки включаются в образце кода, который упрощает задачу обработки подключения устройства.

Типичный удаленное подключение будет иметь маленький 50 мс. Приложение проигрывателя может сообщать задержки в режиме реального времени.

>[!NOTE]
>Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).  Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.

### <a name="get-the-remoting-nuget-packages"></a>Получение удаленных пакетов NuGet

Выполните следующие действия, чтобы получить пакет NuGet для holographic удаленного взаимодействия и добавьте ссылку из проекта:
1. Перейдите к своему проекту в Visual Studio.
2. Щелкните правой кнопкой мыши узел проекта и выберите **управление пакетами NuGet...**
3. В появившейся панели щелкните **Обзор** и выполните поиск «Holographic удаленного взаимодействия».
4. Выберите **Microsoft.Holographic.Remoting** и нажмите кнопку **установить**.
5. Если **предварительной версии** откроется диалоговое окно, нажмите кнопку **ОК**.
6. Далее открывшемся является лицензионного соглашения. Щелкните **я принимаю** принять условия лицензионного соглашения.

### <a name="create-the-holographicstreamerhelpers"></a>Создание HolographicStreamerHelpers

Во-первых мы должны экземпляра HolographicStreamerHelpers. Добавьте к классу, который будет обрабатывать удаленного взаимодействия.

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Кроме того, потребуется отслеживать состояние подключения. Если вы хотите отображении предварительного просмотра, необходимо иметь текстуру, скопируйте его. Вы также должны несколько вещей, такие как блокировка состояния подключения некоторые способ хранения IP-адрес HoloLens и так далее.

```
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Инициализировать HolographicStreamerHelpers и подключитесь к HoloLens

Чтобы подключиться к устройству HoloLens, создайте экземпляр HolographicStreamerHelpers и подключитесь к целевой IP-адрес. Необходимо будет задать размер кадра видео в соответствии с HoloLens отображаемых ширины и высоты, так как библиотека Holographic удаленного взаимодействия ожидает разрешения кодировщик и декодер должны в точности совпадать.

```
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

Подключение к устройству является асинхронным. Отключите потребностями приложения для предоставления обработчики событий для подключения, и кадра отправлять события.

Событие OnConnected можно обновить пользовательский Интерфейс, начинается подготовка для просмотра и так далее. В нашем примере кода для настольных систем Мы обновляем заголовок окна с сообщением «подключенных».

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

OnDisconnected событие можно обработать повторное подключение, обновление элементов пользовательского интерфейса и т. д. В этом примере мы повторного подключения при возникновении временного сбоя.

```
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

Когда компонент удаленного взаимодействия готов к отправке кадр, приложения предоставляется возможность сделать его копию в SendFrameEvent. Здесь мы копируем кадр для цепочки буферов, чтобы его можно отобразить в окне предварительного просмотра.

```
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>Визуализации holographic содержимого

Для отображения содержимого с помощью удаленного взаимодействия, настройке виртуального IFrameworkView внутри рабочего стола или приложение универсальной платформы Windows и обработать holographic кадры из удаленного взаимодействия. Все интерфейсы API Windows Holographic, используется так же, как это представление, но оно настроено несколько иначе.

Вместо того чтобы создавать их самостоятельно, holographic компоненты пространства и речи поступать из вашего класса HolographicRemotingHelpers:

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Вместо использования цикла обновления внутри метода Run, предоставляют делений обновлений из главного цикла рабочего стола или приложение универсальной платформы Windows. Это позволяет рабочий стол или приложение UWP оставаться в системе управления обработкой сообщения.

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Метод Tick() представление holographic приложений завершает одну итерацию обновления, draw, присутствует цикла.

```
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

Обновление представления holographic приложения, визуализации и присутствует цикл именно то как при работе на HoloLens — за исключением того, что у вас есть доступ к гораздо больший объем системных ресурсов на настольном Компьютере. Можно визуализации множества треугольников дополнительные, имеют несколько проходов рисования, выполните дополнительные физики и применяют x64 рабочие процессы для загрузки содержимого, которая требует больше, чем 2 ГБ ОЗУ.

### <a name="disconnect-and-end-the-remote-session"></a>Отключение и завершение удаленного сеанса

Для отключения - например, когда пользователь нажимает кнопку пользовательского интерфейса для отключения - вызвать Disconnect() HolographicStreamerHelpers и затем освободить объект.

```
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>Получить проигрыватель удаленного взаимодействия

Windows Holographic проигрыватель удаленного взаимодействия предоставляется в магазине приложений Windows как конечную точку для удаленного взаимодействия узла приложений для подключения к. Чтобы получить Windows Holographic проигрыватель удаленного взаимодействия, посетить магазин приложений Windows из вашей HoloLens поиска для удаленного взаимодействия и скачайте приложение. Проигрыватель удаленного взаимодействия включает функцию для отображения статистики на экране, что может оказаться полезным при отладке приложений удаленного взаимодействия узла.

## <a name="notes-and-resources"></a>Примечания и ресурсы

Представление holographic приложения будет нужен способ обеспечить приложению устройства Direct3D, при этом должен использоваться для инициализации holographic пространства. Приложение должно использовать это устройство Direct3D на копирование и отображение окна предварительного просмотра.

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Пример кода:** Полный пример кода Holographic удаленного взаимодействия доступна, который включает представление holographic приложений, совместимую с удаленного взаимодействия и удаленного взаимодействия размещения проектов для рабочего стола Win32, DirectX для универсальной платформы Windows и UWP с помощью XAML. Чтобы получить его, перейдите сюда:
* [Образец Windows Holographic кода для удаленного взаимодействия](https://github.com/Microsoft/HoloLensCompanionKit/)

**Примечание отладки.** Библиотека Holographic удаленного взаимодействия может создавать исключения первого шанса. Эти исключения могут быть видны в сеансы, в зависимости от Visual Studio параметры исключений, которые активны во время отладки. Эти исключения перехватываются внутренне библиотекой Holographic удаленного взаимодействия и можно игнорировать.
