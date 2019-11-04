---
title: Создание хост-приложения holographic с удаленным взаимодействием
description: Создание удаленного содержимого узла с удаленным удаленным доступом для удаленного взаимодействия, которое отображается на удаленном компьютере, можно передать в HoloLens 2. В этой статье описывается, как это можно сделать.
author: bethau
ms.author: bethau
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие с holographic
ms.openlocfilehash: e296e5847849bb87f76a7187c3f8ea36a1d681e1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434310"
---
# <a name="writing-a-holographic-remoting-host-app"></a><span data-ttu-id="8ebf8-105">Создание хост-приложения holographic с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="8ebf8-105">Writing a Holographic Remoting host app</span></span>

>[!IMPORTANT]
><span data-ttu-id="8ebf8-106">В этом документе описывается создание ведущего приложения для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-106">This document describes the creation of a host application for HoloLens 2.</span></span> <span data-ttu-id="8ebf8-107">Ведущее приложение для **HoloLens (1-го поколения)** должно использовать пакет NuGet версии **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-107">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="8ebf8-108">Это подразумевает, что ведущие приложения, написанные для HoloLens 2, несовместимы с HoloLens 1 и наоборот.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-108">This implies that host applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="8ebf8-109">Документацию по HoloLens 1 можно найти [здесь](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="8ebf8-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="8ebf8-110">Создав удаленное содержимое удаленного приложения с удаленным удаленным доступом, которое будет передаваться на удаленный компьютер, можно передать в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-110">By creating a Holographic Remoting host app remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="8ebf8-111">В этой статье описывается, как это можно сделать.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="8ebf8-112">Весь код на этой странице и рабочих проектах можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="8ebf8-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="8ebf8-113">Holographic удаленное взаимодействие позволяет приложению ориентироваться на HoloLens 2 с holographic-содержимым, размещенным на настольном компьютере или на устройстве UWP, например на Xbox One, что обеспечивает доступ к дополнительным системным ресурсам и делает возможным интеграцию удаленных [иммерсивное представлений](app-views.md) в существующие программное обеспечение для настольных ПК.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-113">Holographic remoting allows an app to target HoloLens 2 with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="8ebf8-114">Удаленное приложение узла удаленного взаимодействия получает поток входных данных от HoloLens 2, визуализирует содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-114">A remoting host app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="8ebf8-115">Подключение устанавливается с использованием стандартного Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="8ebf8-116">Holographic удаленное взаимодействие добавляется в приложение для настольных систем или UWP через пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="8ebf8-117">Требуется дополнительный код, который обрабатывает соединение и готовится к просмотру в режиме погружения.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="8ebf8-118">Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="8ebf8-119">Приложение проигрывателя может сообщать о задержке в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8ebf8-120">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="8ebf8-120">Prerequisites</span></span>

<span data-ttu-id="8ebf8-121">Хорошей отправной точкой является работа рабочего стола на основе DirectX или приложения UWP, предназначенного для API Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="8ebf8-122">Дополнительные сведения см. в статье [Общие сведения о разработке DirectX](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8ebf8-122">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="8ebf8-123">[ C++ Шаблон "holographic проект](creating-a-holographic-directx-project.md) " является хорошей отправной точкой.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-123">The [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="8ebf8-124">Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span><span class="sxs-lookup"><span data-stu-id="8ebf8-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="8ebf8-125">Использование [однопотокового подразделения](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-125">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="8ebf8-126">При использовании C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) по умолчанию используется многопотоковое подразделение.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="8ebf8-127">Получение пакета NuGet для удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="8ebf8-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="8ebf8-128">Чтобы добавить пакет NuGet в проект в Visual Studio, необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="8ebf8-129">Откройте проект в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="8ebf8-130">Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**</span><span class="sxs-lookup"><span data-stu-id="8ebf8-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="8ebf8-131">На появившейся панели нажмите кнопку **Обзор** и найдите "holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="8ebf8-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="8ebf8-132">Выберите **Microsoft. Holographic. удаленное взаимодействие**, обязательно выберите последнюю версию **2. x. x** и нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="8ebf8-133">Если откроется диалоговое окно **предварительного просмотра** , нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="8ebf8-134">Следующее появившееся диалоговое окно — это лицензионное соглашение.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="8ebf8-135">Нажмите кнопку **я принимаю** , чтобы принять условия лицензионного соглашения.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="8ebf8-136">Версия **1. x. x** пакета NuGet по-прежнему доступна для разработчиков, желающих выбрать HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="8ebf8-137">Дополнительные сведения см. в разделе [Добавление удаленного взаимодействия holographic (HoloLens (1-й общий))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="8ebf8-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="8ebf8-138">Создание удаленного контекста</span><span class="sxs-lookup"><span data-stu-id="8ebf8-138">Create the remote context</span></span>

<span data-ttu-id="8ebf8-139">В качестве первого шага приложение должно создать удаленный контекст.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-139">As a first step the application should create a remote context.</span></span>

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
><span data-ttu-id="8ebf8-140">Holographic удаленное взаимодействие выполняется путем замены среды выполнения Windows Mixed Reality, которая является частью Windows, на среду выполнения с удаленным взаимодействием.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="8ebf8-141">Это делается во время создания удаленного контекста.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="8ebf8-142">По этой причине любой вызов любого API Windows Mixed Reality перед созданием удаленного контекста может привести к непредвиденному поведению.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="8ebf8-143">Рекомендуемый подход состоит в том, чтобы создать удаленный контекст как можно раньше перед взаимодействием с любым API смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="8ebf8-144">Никогда не смешивать объекты, созданные или полученные через API Windows Mixed Reality до вызова Креатеремотеконтекст с объектами, созданными или полученными позже.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="8ebf8-145">После этого необходимо создать новый Holographic.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="8ebf8-146">Указывать CoreWindow не требуется.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="8ebf8-147">Классические приложения, не имеющие CoreWindow, могут просто передавать ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="8ebf8-148">Подключение к устройству</span><span class="sxs-lookup"><span data-stu-id="8ebf8-148">Connect to the device</span></span>

<span data-ttu-id="8ebf8-149">После того как ведущее приложение готово к отрисовке содержимого, можно установить подключение к устройству.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-149">Once the host app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="8ebf8-150">Соединение может быть выполнено одним из двух способов.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="8ebf8-151">Ведущее приложение подключается к проигрывателю, работающему на устройстве.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-151">The host app connects to the player running on the device.</span></span>
2) <span data-ttu-id="8ebf8-152">Проигрыватель, выполняющийся на устройстве, подключается к ведущему приложению.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-152">The player running on the device connects to the host app.</span></span>

<span data-ttu-id="8ebf8-153">Чтобы установить подключение из ведущего приложения к HoloLens 2, вызовите метод ```Connect``` в удаленном контексте, указав имя узла и порт.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-153">To establish a connection from the host app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="8ebf8-154">Порт, используемый проигрывателем удаленного взаимодействия (holographic), — **8265**.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

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
><span data-ttu-id="8ebf8-155">Как и любой C++другой ```Connect``` API/WinRT может вызывать исключение WinRT:: hresult_error, которое необходимо обработать.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="8ebf8-156">Чтобы избежать использования [ C++](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) проекции языка/WinRT, можно добавить файл ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h```, расположенный в пакете NuGet удаленного взаимодействия с удаленным доступом.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-156">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="8ebf8-157">Он содержит объявления базовых COM-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="8ebf8-158">Однако рекомендуется использовать C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="8ebf8-159">Прослушивание входящих подключений в ведущем приложении можно выполнить, вызвав метод ```Listen```.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-159">Listening for incoming connections on the host app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="8ebf8-160">Во время этого вызова можно указать как порт подтверждения, так и порт транспорта.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="8ebf8-161">Порт подтверждения используется для первоначального подтверждения.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="8ebf8-162">Затем данные пересылаются через порт транспорта.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-162">The data is then send over the transport port.</span></span> <span data-ttu-id="8ebf8-163">По умолчанию используются **8265** и **8266** .</span><span class="sxs-lookup"><span data-stu-id="8ebf8-163">By default **8265** and **8266** are used.</span></span>

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
><span data-ttu-id="8ebf8-164">```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` в пакете NuGet содержит подробную документацию по API, предоставляемому с помощью holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="8ebf8-165">Обработка событий, связанных с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="8ebf8-165">Handling Remoting specific events</span></span>

<span data-ttu-id="8ebf8-166">Удаленный контекст предоставляет три события, которые важны для отслеживания состояния соединения.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="8ebf8-167">Подключено: активируется при успешном установлении подключения к устройству.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="8ebf8-168">Ondisconnectо: активируется, если установленное соединение закрыто или не удалось установить подключение.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
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
3) <span data-ttu-id="8ebf8-169">Идет ожидание: при прослушивании входящих подключений начинается.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="8ebf8-170">Кроме того, состояние соединения можно запросить с помощью свойства ```ConnectionState``` в удаленном контексте.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="8ebf8-171">Обработка событий речи</span><span class="sxs-lookup"><span data-stu-id="8ebf8-171">Handling speech events</span></span>

<span data-ttu-id="8ebf8-172">С помощью удаленного речевого интерфейса можно зарегистрировать речевые триггеры в HoloLens 2 и удаленно выполнять их в ведущем приложении.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the host application.</span></span>

<span data-ttu-id="8ebf8-173">Этот дополнительный элемент необходим для отслеживания состояния удаленного распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="8ebf8-174">Сначала необходимо получить удаленный речевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="8ebf8-175">С помощью асинхронного вспомогательного метода можно инициализировать удаленный голос.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="8ebf8-176">Это необходимо сделать асинхронно, так как инициализация может занять значительное время.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="8ebf8-177">[Параллельные и асинхронные операции C++с/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) объясняет, как создавать асинхронные C++функции с помощью/винрт.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

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

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="8ebf8-178">Существует два способа указания фраз для распознавания.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="8ebf8-179">Спецификация внутри XML-файла грамматики речи.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="8ebf8-180">Дополнительные сведения см. [в статье Создание базовой грамматики XML](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .</span><span class="sxs-lookup"><span data-stu-id="8ebf8-180">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="8ebf8-181">Укажите, передав их в векторе словаря в ```ApplyParameters```.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="8ebf8-182">Внутри обратного вызова Онрекогнизедспич можно обработать события речи:</span><span class="sxs-lookup"><span data-stu-id="8ebf8-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

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

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="8ebf8-183">Предварительный просмотр потокового содержимого на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="8ebf8-183">Preview streamed content locally</span></span>

<span data-ttu-id="8ebf8-184">Чтобы отобразить то же содержимое в ведущем приложении, которое отправляется на устройство, можно использовать ```OnSendFrame```ное событие удаленного контекста.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-184">To display the same content in the host app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="8ebf8-185">Событие ```OnSendFrame``` активируется каждый раз, когда библиотека holographic Remote Remoting отправляет текущий кадр на удаленное устройство.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="8ebf8-186">Это идеальное время для получения содержимого, а также Блит его в окно рабочего стола или UWP.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

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

## <a name="optional-custom-data-channels"></a><span data-ttu-id="8ebf8-187">Необязательно: пользовательские каналы данных</span><span class="sxs-lookup"><span data-stu-id="8ebf8-187">Optional: Custom data channels</span></span>

<span data-ttu-id="8ebf8-188">Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное соединение.</span><span class="sxs-lookup"><span data-stu-id="8ebf8-188">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="8ebf8-189">Дополнительные сведения см. в разделе [пользовательские каналы данных](holographic-remoting-custom-data-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="8ebf8-189">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ebf8-190">См. также</span><span class="sxs-lookup"><span data-stu-id="8ebf8-190">See Also</span></span>
* [<span data-ttu-id="8ebf8-191">Написание пользовательского приложения для удаленного взаимодействия holographic</span><span class="sxs-lookup"><span data-stu-id="8ebf8-191">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="8ebf8-192">Пользовательские каналы данных с голографическим удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="8ebf8-192">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="8ebf8-193">Установление безопасного подключения с помощью удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="8ebf8-193">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="8ebf8-194">Устранение неполадок и ограничения удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="8ebf8-194">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="8ebf8-195">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="8ebf8-195">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="8ebf8-196">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="8ebf8-196">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
