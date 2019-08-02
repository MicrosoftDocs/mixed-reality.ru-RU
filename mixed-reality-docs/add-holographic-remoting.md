---
title: Добавление удаленного взаимодействия holographic
description: Объясняется, как с помощью удаленного взаимодействия holographic визуализировать голограммы в HoloLens по сети.
author: MikeRiches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality, голограммы, удаленное взаимодействие, удаленная визуализация, подготовка к просмотру сети, HoloLens, удаленные голограммы
ms.openlocfilehash: 71a763b0660867bf910c0dcecb5fba921f19d068
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712430"
---
# <a name="add-holographic-remoting-hololens-1"></a>Добавление удаленного взаимодействия с holographic (HoloLens 1)

>[!IMPORTANT]
>В этом документе описывается создание ведущего приложения для HoloLens 1. Ведущее приложение для **HoloLens 1** должно использовать пакет NuGet версии **1. x. x**. Это подразумевает, что ведущие приложения, написанные для HoloLens 1, несовместимы с HoloLens 2 и наоборот.

## <a name="hololens-2"></a>HoloLens 2

Разработчики HoloLens, использующие holographic удаленное взаимодействие, должны обновить свои приложения, чтобы они были совместимы с HoloLens 2. Для этого требуется новая версия пакета NuGet удаленного взаимодействия Holographic. Если приложение, использующее пакет NuGet для удаленного взаимодействия с номером версии, меньшим 2.0.0.0, пытается подключиться к удаленному проигрывателю holographic с помощью HoloLens 2, произойдет сбой подключения.

>[!NOTE]
>Рекомендации, относящиеся к HoloLens 2, можно найти [здесь](holographic-remoting-create-host.md).


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Добавление удаленного взаимодействия holographic в приложение для настольных компьютеров или UWP

На этой странице описывается добавление удаленного взаимодействия holographic в приложение для настольных компьютеров или приложений UWP.

Holographic удаленное взаимодействие позволяет приложению ориентироваться на HoloLens с holographic-содержимым, размещенным на настольном компьютере или на устройстве UWP, например на Xbox One, что обеспечивает доступ к дополнительным системным ресурсам и делает возможным интеграцию удаленных [иммерсивного представлений](app-views.md) в существующее программное обеспечение для настольных ПК. Удаленное приложение узла удаленного взаимодействия получает поток входных данных от HoloLens, отображает содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens. Подключение устанавливается с использованием стандартного Wi-Fi. Для использования удаленного взаимодействия вы будете использовать пакет NuGet для добавления удаленного взаимодействия с настольным компьютером или приложением UWP и написания кода для обработки подключения и визуализации в режиме погружения. Вспомогательные библиотеки включены в пример кода, который упрощает задачу обработки подключения устройства.

Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки. Приложение проигрывателя может сообщать о задержке в режиме реального времени.

>[!NOTE]
>Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

### <a name="get-the-remoting-nuget-packages"></a>Получение пакетов NuGet для удаленного взаимодействия

Выполните следующие действия, чтобы получить пакет NuGet для удаленного взаимодействия holographic и добавить ссылку из проекта:
1. Перейдите к проекту в Visual Studio.
2. Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**
3. На появившейся панели нажмите кнопку **Обзор** и найдите "holographic Remoting".
4. Выберите **Microsoft. Holographic. удаленное взаимодействие** и нажмите кнопку **установить**.
5. Если откроется диалоговое окно **предварительного просмотра** , нажмите кнопку **ОК**.
6. Следующее появившееся диалоговое окно — это лицензионное соглашение. Нажмите кнопку **я принимаю** , чтобы принять условия лицензионного соглашения.

### <a name="create-the-holographicstreamerhelpers"></a>Создание Холографикстреамерхелперс

Сначала нам нужен экземпляр Холографикстреамерхелперс. Добавьте его в класс, который будет обрабатывать удаленное взаимодействие.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Кроме того, необходимо будет отслеживанию состояния соединения. Если вы хотите подготовить к просмотру предварительную версию, необходимо иметь текстуру для копирования. Кроме того, необходимо выполнить несколько действий, например блокировку состояния подключения, способ хранения IP-адреса HoloLens и т. д.

```cpp
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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Инициализация Холографикстреамерхелперс и подключение к HoloLens

Чтобы подключиться к устройству HoloLens, создайте экземпляр Холографикстреамерхелперс и подключитесь к целевому IP-адресу. Необходимо задать размер видеокадра в соответствии с шириной и высотой HoloLens, так как библиотека holographic Remoting предполагает, что декодеры и разрешения кодировщика будут точно соответствовать.

```cpp
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

Подключение устройства является асинхронным. Приложение должно предоставить обработчики событий для событий подключения, отключения и отправки кадров.

Событие onconnected может обновлять пользовательский интерфейс, начинать отрисовку и т. д. В нашем примере кода для настольной системы мы обновляем заголовок окна с сообщением "Connected" (подключено).

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

Событие OnDisconnection может поддерживать повторное подключение, обновления пользовательского интерфейса и т. д. В этом примере мы выполним повторное подключение при наличии временного сбоя.

```cpp
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

Когда компонент удаленного взаимодействия готов отправить кадр, приложение предоставляет возможность создать его копию в Сендфрамивент. Здесь мы копируем фрейм в цепочку буферов, чтобы мы могли отобразить ее в окне предварительного просмотра.

```cpp
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

### <a name="render-holographic-content"></a>Прорисовка с holographic содержимым

Для отображения содержимого с помощью удаленного взаимодействия вы настраиваете виртуальные IFrameworkView в приложении для настольных систем или приложения UWP и обрабатываюте holographic-пакеты с удаленного взаимодействия. Все API-интерфейсы Windows holographic аналогичны этому представлению, но настраиваются немного иначе.

Вместо того, чтобы создавать их самостоятельно, компоненты holographic и речи берутся из класса Холографикремотингхелперс:

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Вместо того чтобы использовать цикл обновления в методе Run, вы предоставляете обновления тактов из основного цикла рабочего стола или приложения UWP. Это позволяет рабочему столу или приложению UWP оставаться в управлении обработкой сообщений.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Метод Tick () в представлении приложения holographic завершает одну итерацию обновления, прорисовки, представления цикла.

```cpp
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

Цикл обновления, подготовки к просмотру и представления с помощью приложения holographic точно такой же, как и при работе в HoloLens, за исключением того, что у вас есть доступ к гораздо большей части системных ресурсов на настольном компьютере. Вы можете визуализировать больше треугольников, увеличить число проходов рисования, сделать более физикой и использовать процессы x64 для загрузки содержимого, которое требует более 2 ГБ ОЗУ.

### <a name="disconnect-and-end-the-remote-session"></a>Отключение и завершение удаленного сеанса

Для отключения, например, когда пользователь нажимает кнопку пользовательского интерфейса для отключения команды Disconnect () на Холографикстреамерхелперс, а затем освобождает объект.

```cpp
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

## <a name="get-the-remoting-player"></a>Получение проигрывателя удаленного взаимодействия

Проигрыватель удаленного взаимодействия Windows holographic предлагается в магазине приложений Windows в качестве конечной точки для подключения приложений узла удаленного взаимодействия. Чтобы получить проигрыватель удаленного взаимодействия Windows holographic, перейдите в магазин приложений Windows из HoloLens, найдите удаленное взаимодействие и скачайте приложение. Проигрыватель удаленного взаимодействия включает функцию для отображения статистики на экране, которая может быть полезной при отладке приложений удаленного узла.

## <a name="notes-and-resources"></a>Заметки и ресурсы

В представлении с holographic приложений потребуется способ предоставить приложению Direct3D-устройство, которое должно использоваться для инициализации Holographic. Приложение должно использовать это устройство Direct3D для копирования и вывода кадра предварительного просмотра.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Пример кода:** Доступен полный пример кода с удаленным взаимодействием holographic, включающий представление приложения holographic, совместимое с удаленным взаимодействием и проектами удаленного взаимодействия для настольных приложений Win32, UWP DirectX и UWP с XAML. Чтобы получить его, перейдите по следующему адресу:
* [Пример Windows holographic для удаленного взаимодействия](https://github.com/Microsoft/HoloLensCompanionKit/)

**Примечание к отладке:** Библиотека holographic Remoting может создавать исключения с первого шанса. Эти исключения могут отображаться в сеансах отладки в зависимости от параметров исключений Visual Studio, которые активны в момент времени. Эти исключения захватываются внутри библиотеки holographic Remoting и могут быть пропущены.
