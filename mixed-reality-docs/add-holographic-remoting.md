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
# <a name="add-holographic-remoting"></a><span data-ttu-id="563cf-104">Добавление holographic удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="563cf-104">Add holographic remoting</span></span>

> [!NOTE]
> <span data-ttu-id="563cf-105">Дополнительные рекомендации, относящиеся к HoloLens 2 [ожидается в ближайшее время](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="563cf-105">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="563cf-106">Добавление holographic удаленного взаимодействия на рабочий стол или приложение универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="563cf-106">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="563cf-107">Эта страница описывает способы добавления Holographic удаленного взаимодействия на рабочий стол или приложение универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="563cf-107">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="563cf-108">Holographic удаленное взаимодействие позволяет вашему приложению для HoloLens holographic содержимого, размещенного на настольном Компьютере или на устройстве универсальной платформы Windows, таких как Xbox One, благодаря доступу к больше системных ресурсов, а также что позволяет интегрировать удаленного [иммерсивных представления](app-views.md) в desktop существующего программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="563cf-108">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="563cf-109">В приложении узла удаленного взаимодействия получает потока входных данных от HoloLens и отрисовывает содержимое в виде виртуального иммерсивных выполняет потоковую передачу содержимого кадров, вернитесь к HoloLens.</span><span class="sxs-lookup"><span data-stu-id="563cf-109">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="563cf-110">Соединение устанавливается с помощью стандартных Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="563cf-110">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="563cf-111">Чтобы использовать удаленное взаимодействие, используется пакет NuGet, чтобы добавить на рабочий стол или приложение универсальной платформы Windows holographic удаленного взаимодействия и написать код для обработки подключения и для подготовки к просмотру в иммерсивных представлении.</span><span class="sxs-lookup"><span data-stu-id="563cf-111">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="563cf-112">Вспомогательные библиотеки включаются в образце кода, который упрощает задачу обработки подключения устройства.</span><span class="sxs-lookup"><span data-stu-id="563cf-112">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="563cf-113">Типичный удаленное подключение будет иметь маленький 50 мс.</span><span class="sxs-lookup"><span data-stu-id="563cf-113">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="563cf-114">Приложение проигрывателя может сообщать задержки в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="563cf-114">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="563cf-115">Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="563cf-115">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="563cf-116">Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.</span><span class="sxs-lookup"><span data-stu-id="563cf-116">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="563cf-117">Получение удаленных пакетов NuGet</span><span class="sxs-lookup"><span data-stu-id="563cf-117">Get the remoting NuGet packages</span></span>

<span data-ttu-id="563cf-118">Выполните следующие действия, чтобы получить пакет NuGet для holographic удаленного взаимодействия и добавьте ссылку из проекта:</span><span class="sxs-lookup"><span data-stu-id="563cf-118">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="563cf-119">Перейдите к своему проекту в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="563cf-119">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="563cf-120">Щелкните правой кнопкой мыши узел проекта и выберите **управление пакетами NuGet...**</span><span class="sxs-lookup"><span data-stu-id="563cf-120">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="563cf-121">В появившейся панели щелкните **Обзор** и выполните поиск «Holographic удаленного взаимодействия».</span><span class="sxs-lookup"><span data-stu-id="563cf-121">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="563cf-122">Выберите **Microsoft.Holographic.Remoting** и нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="563cf-122">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="563cf-123">Если **предварительной версии** откроется диалоговое окно, нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="563cf-123">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="563cf-124">Далее открывшемся является лицензионного соглашения.</span><span class="sxs-lookup"><span data-stu-id="563cf-124">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="563cf-125">Щелкните **я принимаю** принять условия лицензионного соглашения.</span><span class="sxs-lookup"><span data-stu-id="563cf-125">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="563cf-126">Создание HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="563cf-126">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="563cf-127">Во-первых мы должны экземпляра HolographicStreamerHelpers.</span><span class="sxs-lookup"><span data-stu-id="563cf-127">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="563cf-128">Добавьте к классу, который будет обрабатывать удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="563cf-128">Add this to the class that will be handling remoting.</span></span>

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="563cf-129">Кроме того, потребуется отслеживать состояние подключения.</span><span class="sxs-lookup"><span data-stu-id="563cf-129">You'll also need to track connection state.</span></span> <span data-ttu-id="563cf-130">Если вы хотите отображении предварительного просмотра, необходимо иметь текстуру, скопируйте его.</span><span class="sxs-lookup"><span data-stu-id="563cf-130">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="563cf-131">Вы также должны несколько вещей, такие как блокировка состояния подключения некоторые способ хранения IP-адрес HoloLens и так далее.</span><span class="sxs-lookup"><span data-stu-id="563cf-131">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="563cf-132">Инициализировать HolographicStreamerHelpers и подключитесь к HoloLens</span><span class="sxs-lookup"><span data-stu-id="563cf-132">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="563cf-133">Чтобы подключиться к устройству HoloLens, создайте экземпляр HolographicStreamerHelpers и подключитесь к целевой IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="563cf-133">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="563cf-134">Необходимо будет задать размер кадра видео в соответствии с HoloLens отображаемых ширины и высоты, так как библиотека Holographic удаленного взаимодействия ожидает разрешения кодировщик и декодер должны в точности совпадать.</span><span class="sxs-lookup"><span data-stu-id="563cf-134">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

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

<span data-ttu-id="563cf-135">Подключение к устройству является асинхронным.</span><span class="sxs-lookup"><span data-stu-id="563cf-135">The device connection is asynchronous.</span></span> <span data-ttu-id="563cf-136">Отключите потребностями приложения для предоставления обработчики событий для подключения, и кадра отправлять события.</span><span class="sxs-lookup"><span data-stu-id="563cf-136">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="563cf-137">Событие OnConnected можно обновить пользовательский Интерфейс, начинается подготовка для просмотра и так далее.</span><span class="sxs-lookup"><span data-stu-id="563cf-137">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="563cf-138">В нашем примере кода для настольных систем Мы обновляем заголовок окна с сообщением «подключенных».</span><span class="sxs-lookup"><span data-stu-id="563cf-138">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="563cf-139">OnDisconnected событие можно обработать повторное подключение, обновление элементов пользовательского интерфейса и т. д.</span><span class="sxs-lookup"><span data-stu-id="563cf-139">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="563cf-140">В этом примере мы повторного подключения при возникновении временного сбоя.</span><span class="sxs-lookup"><span data-stu-id="563cf-140">In this example, we reconnect if there is a transient failure.</span></span>

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

<span data-ttu-id="563cf-141">Когда компонент удаленного взаимодействия готов к отправке кадр, приложения предоставляется возможность сделать его копию в SendFrameEvent.</span><span class="sxs-lookup"><span data-stu-id="563cf-141">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="563cf-142">Здесь мы копируем кадр для цепочки буферов, чтобы его можно отобразить в окне предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="563cf-142">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

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

### <a name="render-holographic-content"></a><span data-ttu-id="563cf-143">Визуализации holographic содержимого</span><span class="sxs-lookup"><span data-stu-id="563cf-143">Render holographic content</span></span>

<span data-ttu-id="563cf-144">Для отображения содержимого с помощью удаленного взаимодействия, настройке виртуального IFrameworkView внутри рабочего стола или приложение универсальной платформы Windows и обработать holographic кадры из удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="563cf-144">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="563cf-145">Все интерфейсы API Windows Holographic, используется так же, как это представление, но оно настроено несколько иначе.</span><span class="sxs-lookup"><span data-stu-id="563cf-145">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="563cf-146">Вместо того чтобы создавать их самостоятельно, holographic компоненты пространства и речи поступать из вашего класса HolographicRemotingHelpers:</span><span class="sxs-lookup"><span data-stu-id="563cf-146">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="563cf-147">Вместо использования цикла обновления внутри метода Run, предоставляют делений обновлений из главного цикла рабочего стола или приложение универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="563cf-147">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="563cf-148">Это позволяет рабочий стол или приложение UWP оставаться в системе управления обработкой сообщения.</span><span class="sxs-lookup"><span data-stu-id="563cf-148">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="563cf-149">Метод Tick() представление holographic приложений завершает одну итерацию обновления, draw, присутствует цикла.</span><span class="sxs-lookup"><span data-stu-id="563cf-149">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

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

<span data-ttu-id="563cf-150">Обновление представления holographic приложения, визуализации и присутствует цикл именно то как при работе на HoloLens — за исключением того, что у вас есть доступ к гораздо больший объем системных ресурсов на настольном Компьютере.</span><span class="sxs-lookup"><span data-stu-id="563cf-150">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="563cf-151">Можно визуализации множества треугольников дополнительные, имеют несколько проходов рисования, выполните дополнительные физики и применяют x64 рабочие процессы для загрузки содержимого, которая требует больше, чем 2 ГБ ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="563cf-151">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="563cf-152">Отключение и завершение удаленного сеанса</span><span class="sxs-lookup"><span data-stu-id="563cf-152">Disconnect and end the remote session</span></span>

<span data-ttu-id="563cf-153">Для отключения - например, когда пользователь нажимает кнопку пользовательского интерфейса для отключения - вызвать Disconnect() HolographicStreamerHelpers и затем освободить объект.</span><span class="sxs-lookup"><span data-stu-id="563cf-153">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

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

## <a name="get-the-remoting-player"></a><span data-ttu-id="563cf-154">Получить проигрыватель удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="563cf-154">Get the remoting player</span></span>

<span data-ttu-id="563cf-155">Windows Holographic проигрыватель удаленного взаимодействия предоставляется в магазине приложений Windows как конечную точку для удаленного взаимодействия узла приложений для подключения к.</span><span class="sxs-lookup"><span data-stu-id="563cf-155">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="563cf-156">Чтобы получить Windows Holographic проигрыватель удаленного взаимодействия, посетить магазин приложений Windows из вашей HoloLens поиска для удаленного взаимодействия и скачайте приложение.</span><span class="sxs-lookup"><span data-stu-id="563cf-156">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="563cf-157">Проигрыватель удаленного взаимодействия включает функцию для отображения статистики на экране, что может оказаться полезным при отладке приложений удаленного взаимодействия узла.</span><span class="sxs-lookup"><span data-stu-id="563cf-157">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="563cf-158">Примечания и ресурсы</span><span class="sxs-lookup"><span data-stu-id="563cf-158">Notes and resources</span></span>

<span data-ttu-id="563cf-159">Представление holographic приложения будет нужен способ обеспечить приложению устройства Direct3D, при этом должен использоваться для инициализации holographic пространства.</span><span class="sxs-lookup"><span data-stu-id="563cf-159">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="563cf-160">Приложение должно использовать это устройство Direct3D на копирование и отображение окна предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="563cf-160">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="563cf-161">**Пример кода:** Полный пример кода Holographic удаленного взаимодействия доступна, который включает представление holographic приложений, совместимую с удаленного взаимодействия и удаленного взаимодействия размещения проектов для рабочего стола Win32, DirectX для универсальной платформы Windows и UWP с помощью XAML.</span><span class="sxs-lookup"><span data-stu-id="563cf-161">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="563cf-162">Чтобы получить его, перейдите сюда:</span><span class="sxs-lookup"><span data-stu-id="563cf-162">To get it, go here:</span></span>
* [<span data-ttu-id="563cf-163">Образец Windows Holographic кода для удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="563cf-163">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="563cf-164">**Примечание отладки.** Библиотека Holographic удаленного взаимодействия может создавать исключения первого шанса.</span><span class="sxs-lookup"><span data-stu-id="563cf-164">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="563cf-165">Эти исключения могут быть видны в сеансы, в зависимости от Visual Studio параметры исключений, которые активны во время отладки.</span><span class="sxs-lookup"><span data-stu-id="563cf-165">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="563cf-166">Эти исключения перехватываются внутренне библиотекой Holographic удаленного взаимодействия и можно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="563cf-166">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
