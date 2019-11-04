---
title: Написание пользовательского плеера holographic
description: Создав настраиваемое приложение для удаленного взаимодействия holographic, вы можете создать пользовательское приложение, способное отображать содержимое, отображаемое на удаленном компьютере, в HoloLens 2. В этой статье описывается, как это можно сделать.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: 982a3f42014d8f5eb9ba181247fee9825fb78371
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434321"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="87c62-105">Написание пользовательского приложения для удаленного взаимодействия holographic</span><span class="sxs-lookup"><span data-stu-id="87c62-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="87c62-106">В этом документе описывается создание пользовательского приложения проигрывателя для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="87c62-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="87c62-107">Пользовательские проигрыватели, написанные для HoloLens 2, несовместимы с ведущими приложениями, написанными для HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="87c62-107">Custom players written for HoloLens 2 are not compatible with host applications written for HoloLens 1.</span></span> <span data-ttu-id="87c62-108">Это означает, что оба приложения должны использовать пакет NuGet версии **2. x. x**.</span><span class="sxs-lookup"><span data-stu-id="87c62-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="87c62-109">Создав настраиваемое приложение для удаленного взаимодействия holographic, вы можете создать пользовательское приложение, способное отображать [иммерсивное представление](app-views.md) с удаленного компьютера в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="87c62-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="87c62-110">В этой статье описывается, как это можно сделать.</span><span class="sxs-lookup"><span data-stu-id="87c62-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="87c62-111">Весь код на этой странице и рабочих проектах можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="87c62-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="87c62-112">С помощью плеера holographic в приложении можно отображать holographic-содержимое, [Отображаемое](rendering.md) на настольном компьютере или на устройстве UWP, например Xbox One, что позволяет получить доступ к дополнительным системным ресурсам.</span><span class="sxs-lookup"><span data-stu-id="87c62-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="87c62-113">Приложение holographic Remoting, которое выполняет потоковую передачу данных, передает входные данные в хост-приложение holographic с удаленным взаимодействием и получает иммерсивное представление в виде видео-и звукового потока.</span><span class="sxs-lookup"><span data-stu-id="87c62-113">A Holographic Remoting player app streams input data to a Holographic Remoting host application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="87c62-114">Подключение устанавливается с использованием стандартного Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="87c62-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="87c62-115">Чтобы создать приложение проигрывателя, вы будете использовать пакет NuGet для добавления удаленного взаимодействия holographic в ваше приложение UWP и написать код для управления подключением и отображения иммерсивного представления.</span><span class="sxs-lookup"><span data-stu-id="87c62-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="87c62-116">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="87c62-116">Prerequisites</span></span>

<span data-ttu-id="87c62-117">Хорошей отправной точкой является рабочее приложение UWP на основе DirectX, которое уже предназначено для API Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="87c62-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="87c62-118">Дополнительные сведения см. в статье [Общие сведения о разработке DirectX](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="87c62-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="87c62-119">Если у вас нет существующего приложения и вы хотите начать с самого начала, [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md) является хорошей отправной точкой.</span><span class="sxs-lookup"><span data-stu-id="87c62-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="87c62-120">Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span><span class="sxs-lookup"><span data-stu-id="87c62-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="87c62-121">Использование [однопотокового аппартмент](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="87c62-121">The use of a [single-threaded appartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="87c62-122">При использовании C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) по умолчанию используется многопотоковое подразделение.</span><span class="sxs-lookup"><span data-stu-id="87c62-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="87c62-123">Получение пакета NuGet для удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="87c62-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="87c62-124">Чтобы добавить пакет NuGet в проект в Visual Studio, необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="87c62-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="87c62-125">Откройте проект в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87c62-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="87c62-126">Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**</span><span class="sxs-lookup"><span data-stu-id="87c62-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="87c62-127">На появившейся панели нажмите кнопку **Обзор** и найдите "holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="87c62-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="87c62-128">Выберите **Microsoft. Holographic. удаленное взаимодействие**, обязательно выберите последнюю версию **2. x. x** и нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="87c62-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="87c62-129">Если откроется диалоговое окно **предварительного просмотра** , нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="87c62-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="87c62-130">Следующее появившееся диалоговое окно — это лицензионное соглашение.</span><span class="sxs-lookup"><span data-stu-id="87c62-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="87c62-131">Нажмите кнопку **я принимаю** , чтобы принять условия лицензионного соглашения.</span><span class="sxs-lookup"><span data-stu-id="87c62-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="87c62-132">```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` в пакете NuGet содержит подробную документацию по API, предоставляемому с помощью holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="87c62-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="87c62-133">Изменение Package. appxmanifest приложения</span><span class="sxs-lookup"><span data-stu-id="87c62-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="87c62-134">Чтобы приложение было осведомлено о Microsoft. Holographic. Аппремотинг. dll, добавленном пакетом NuGet, необходимо выполнить следующие действия над проектом.</span><span class="sxs-lookup"><span data-stu-id="87c62-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="87c62-135">В обозреватель решений щелкните правой кнопкой мыши файл **Package. appxmanifest** и выберите **Открыть с помощью...**</span><span class="sxs-lookup"><span data-stu-id="87c62-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="87c62-136">Выберите **Редактор XML (текстовый)** и нажмите кнопку ОК.</span><span class="sxs-lookup"><span data-stu-id="87c62-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="87c62-137">Добавьте следующие строки в файл и сохраните</span><span class="sxs-lookup"><span data-stu-id="87c62-137">Add the following lines to the file and save</span></span>
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a><span data-ttu-id="87c62-138">Создание контекста проигрывателя</span><span class="sxs-lookup"><span data-stu-id="87c62-138">Create the player context</span></span>

<span data-ttu-id="87c62-139">В качестве первого шага приложение должно создать контекст проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="87c62-139">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting host and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="87c62-140">Holographic удаленное взаимодействие выполняется путем замены среды выполнения Windows Mixed Reality, которая является частью Windows, на среду выполнения с удаленным взаимодействием.</span><span class="sxs-lookup"><span data-stu-id="87c62-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="87c62-141">Это делается во время создания контекста проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="87c62-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="87c62-142">По этой причине любой вызов любого API Windows Mixed Reality перед созданием контекста проигрывателя может привести к непредвиденному поведению.</span><span class="sxs-lookup"><span data-stu-id="87c62-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="87c62-143">Рекомендуемый подход состоит в том, чтобы создать контекст проигрывателя как можно раньше перед взаимодействием с любым API смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="87c62-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="87c62-144">Никогда не смешивать объекты, созданные или полученные через API Windows Mixed Reality до вызова ```PlayerContext::Create()``` с объектами, созданными или полученными позже.</span><span class="sxs-lookup"><span data-stu-id="87c62-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create()``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="87c62-145">Далее можно создать Холографикспаце, вызвав [холографикспаце. креатефоркоревиндов](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span><span class="sxs-lookup"><span data-stu-id="87c62-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a><span data-ttu-id="87c62-146">Подключение к узлу</span><span class="sxs-lookup"><span data-stu-id="87c62-146">Connect to the host</span></span>

<span data-ttu-id="87c62-147">После того как приложение игрока готово к отрисовке содержимого, можно установить подключение к узлу.</span><span class="sxs-lookup"><span data-stu-id="87c62-147">Once the player app is ready for rendering content a connection to the host can be established.</span></span>

<span data-ttu-id="87c62-148">Соединение может быть установлено одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="87c62-148">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="87c62-149">Приложение проигрывателя, работающее в HoloLens 2, подключается к ведущему приложению.</span><span class="sxs-lookup"><span data-stu-id="87c62-149">The player app running on HoloLens 2 connects to the host app.</span></span>
2) <span data-ttu-id="87c62-150">Ведущее приложение подключается к приложению проигрывателя, работающему в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="87c62-150">The host app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="87c62-151">Чтобы подключиться из приложения проигрывателя к узлу, вызовите метод ```Connect``` в контексте проигрывателя, указав имя узла и порт.</span><span class="sxs-lookup"><span data-stu-id="87c62-151">To connect from the player app to the host call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="87c62-152">Порт по умолчанию — **8265**.</span><span class="sxs-lookup"><span data-stu-id="87c62-152">The default port is **8265**.</span></span>

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
><span data-ttu-id="87c62-153">Как и любой C++другой ```Connect``` API/WinRT может вызывать исключение WinRT:: hresult_error, которое необходимо обработать.</span><span class="sxs-lookup"><span data-stu-id="87c62-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="87c62-154">Прослушивание входящих подключений в приложении проигрывателя можно выполнить, вызвав метод ```Listen```.</span><span class="sxs-lookup"><span data-stu-id="87c62-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="87c62-155">Во время этого вызова можно указать как порт подтверждения, так и порт транспорта.</span><span class="sxs-lookup"><span data-stu-id="87c62-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="87c62-156">Порт подтверждения используется для первоначального подтверждения.</span><span class="sxs-lookup"><span data-stu-id="87c62-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="87c62-157">Затем данные пересылаются через порт транспорта.</span><span class="sxs-lookup"><span data-stu-id="87c62-157">The data is then send over the transport port.</span></span> <span data-ttu-id="87c62-158">По умолчанию используются номер порта **8265** и **8266** .</span><span class="sxs-lookup"><span data-stu-id="87c62-158">By default port number **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a><span data-ttu-id="87c62-159">Обработка событий, связанных с подключением</span><span class="sxs-lookup"><span data-stu-id="87c62-159">Handling connection related events</span></span>

<span data-ttu-id="87c62-160">```PlayerContext``` предоставляет три события для отслеживания состояния соединения.</span><span class="sxs-lookup"><span data-stu-id="87c62-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="87c62-161">Подключено: активируется при успешном установлении соединения с узлом.</span><span class="sxs-lookup"><span data-stu-id="87c62-161">OnConnected: Triggered when a connection to the host has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="87c62-162">Ondisconnectо: активируется, если установленное соединение прерывается или не удалось установить подключение.</span><span class="sxs-lookup"><span data-stu-id="87c62-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
><span data-ttu-id="87c62-163">Возможные значения ```ConnectionFailureReason``` задокументированы в [файле](#idl)```Microsoft.Holographic.AppRemoting.idl```.</span><span class="sxs-lookup"><span data-stu-id="87c62-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="87c62-164">Идет ожидание: при прослушивании входящих подключений начинается.</span><span class="sxs-lookup"><span data-stu-id="87c62-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="87c62-165">Кроме того, состояние соединения можно запросить с помощью свойства ```ConnectionState``` в контексте проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="87c62-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="87c62-166">Отобразить удаленно визуализированный кадр</span><span class="sxs-lookup"><span data-stu-id="87c62-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="87c62-167">Чтобы отобразить удаленно визуализированное содержимое, вызовите ```PlayerContext::BlitRemoteFrame()``` при подготовке к просмотру [холографикфраме](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="87c62-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame()``` while rendering a [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="87c62-168">```BlitRemoteFrame()``` требует, чтобы задний буфер для текущего Холографикфраме был привязан как целевой объект рендеринга.</span><span class="sxs-lookup"><span data-stu-id="87c62-168">```BlitRemoteFrame()``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="87c62-169">Задний буфер можно получить из [холографиккамерарендерингпараметерс](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) с помощью свойства [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .</span><span class="sxs-lookup"><span data-stu-id="87c62-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="87c62-170">При вызове ```BlitRemoteFrame()``` копирует последний полученный кадр из ведущего приложения в буфер обмена Холографикфраме.</span><span class="sxs-lookup"><span data-stu-id="87c62-170">When called, ```BlitRemoteFrame()``` copies the latest received frame from the host application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="87c62-171">Кроме того, устанавливается набор фокусных точек, если удаленное приложение указало фокус-точку во время отрисовки удаленного кадра.</span><span class="sxs-lookup"><span data-stu-id="87c62-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="87c62-172">```PlayerContext::BlitRemoteFrame()``` потенциально перезаписывает фокусную точку для текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="87c62-172">```PlayerContext::BlitRemoteFrame()``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="87c62-173">Чтобы задать резервную точку фокусировки, вызовите метод [холографиккамерарендерингпараметерс:: сетфокуспоинт](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) перед ```PlayerContext::BlitRemoteFrame()```.</span><span class="sxs-lookup"><span data-stu-id="87c62-173">To specifiy a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame()```.</span></span> 
>- <span data-ttu-id="87c62-174">Чтобы перезаписать удаленную точку фокусировки, вызовите [холографиккамерарендерингпараметерс:: сетфокуспоинт](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) после ```PlayerContext::BlitRemoteFrame()```.</span><span class="sxs-lookup"><span data-stu-id="87c62-174">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame()```.</span></span>

<span data-ttu-id="87c62-175">При успешном выполнении ```BlitRemoteFrame()``` возвращает ```BlitResult::Success_Color```.</span><span class="sxs-lookup"><span data-stu-id="87c62-175">On success, ```BlitRemoteFrame()``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="87c62-176">В противном случае возвращается причина сбоя:</span><span class="sxs-lookup"><span data-stu-id="87c62-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="87c62-177">```BlitResult::Failed_NoRemoteFrameAvailable```: сбой, так как нет доступных удаленных кадров.</span><span class="sxs-lookup"><span data-stu-id="87c62-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="87c62-178">```BlitResult::Failed_NoCamera```: сбой, так как отсутствует камера.</span><span class="sxs-lookup"><span data-stu-id="87c62-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="87c62-179">```BlitResult::Failed_RemoteFrameTooOld```: не выполнено, так как удаленная рамка устарела (см. свойство Плайерконтекст:: Блитремотефраметимеаут).</span><span class="sxs-lookup"><span data-stu-id="87c62-179">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

## <span data-ttu-id="87c62-180">Необязательно: Set Блитремотефраметимеаут<a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="87c62-180">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="87c62-181">```PlayerContext::BlitRemoteFrameTimout``` поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="87c62-181">```PlayerContext::BlitRemoteFrameTimout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="87c62-182">Свойство ```PlayerContext::BlitRemoteFrameTimeout``` указывает промежуток времени, в течение которого удаленная рамка повторно используется, если не получена новая Удаленная рамка.</span><span class="sxs-lookup"><span data-stu-id="87c62-182">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="87c62-183">Типичный вариант использования заключается в том, чтобы включить время ожидания Блитремотефраме для отображения пустого экрана, если новые кадры не будут получены в течение определенного промежутка времени.</span><span class="sxs-lookup"><span data-stu-id="87c62-183">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="87c62-184">Если параметр включен, можно также использовать тип возвращаемого значения метода ```BlitRemoteFrame```, чтобы переключиться на локально визуализированное резервное содержимое.</span><span class="sxs-lookup"><span data-stu-id="87c62-184">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="87c62-185">Чтобы включить время ожидания, задайте для свойства значение длительности, равное или больше 100 мс.</span><span class="sxs-lookup"><span data-stu-id="87c62-185">To enable the timeout, set the property value to a duration equal or greater than 100ms.</span></span> <span data-ttu-id="87c62-186">Чтобы отключить время ожидания, присвойте свойству нулевую длительность.</span><span class="sxs-lookup"><span data-stu-id="87c62-186">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="87c62-187">Если время ожидания включено и в течение заданного периода не получена Удаленная рамка, Блитремотефраме завершается ошибкой и возвращает ```Failed_RemoteFrameTooOld``` до тех пор, пока не будет получена новая Удаленная рамка.</span><span class="sxs-lookup"><span data-stu-id="87c62-187">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="87c62-188">Необязательно: получение статистики о последней удаленной рамке</span><span class="sxs-lookup"><span data-stu-id="87c62-188">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="87c62-189">Чтобы диагностировать проблемы с производительностью или сетью, можно получить статистику о последнем удаленном кадре с помощью свойства ```PlayerContext::LastFrameStatistics```.</span><span class="sxs-lookup"><span data-stu-id="87c62-189">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="87c62-190">Статистика обновляется во время вызова [холографикфраме::P ресентусингкуррентпредиктион](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span><span class="sxs-lookup"><span data-stu-id="87c62-190">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="87c62-191">Дополнительные сведения см. в документации по ```PlayerFrameStatistics``` в [файле](#idl)```Microsoft.Holographic.AppRemoting.idl```.</span><span class="sxs-lookup"><span data-stu-id="87c62-191">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="87c62-192">Необязательно: пользовательские каналы данных</span><span class="sxs-lookup"><span data-stu-id="87c62-192">Optional: Custom data channels</span></span>

<span data-ttu-id="87c62-193">Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное соединение.</span><span class="sxs-lookup"><span data-stu-id="87c62-193">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="87c62-194">Дополнительные сведения см. в разделе [пользовательские каналы данных](holographic-remoting-custom-data-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="87c62-194">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="87c62-195">См. также</span><span class="sxs-lookup"><span data-stu-id="87c62-195">See Also</span></span>
* [<span data-ttu-id="87c62-196">Создание хост-приложения holographic с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="87c62-196">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="87c62-197">Пользовательские каналы данных с голографическим удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="87c62-197">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="87c62-198">Установление безопасного подключения с помощью удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="87c62-198">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="87c62-199">Устранение неполадок и ограничения удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="87c62-199">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="87c62-200">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="87c62-200">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="87c62-201">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="87c62-201">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
