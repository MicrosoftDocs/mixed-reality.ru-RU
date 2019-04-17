---
title: Начало HolographicSpace
description: Описание API HolographicSpace, основное понятие для holographic отрисовки и пространственных входных данных.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, пространственных входных данных, Подготовка к просмотру, замены цепочки, holographic кадра, цикла обновления, цикл игры, системой отсчета координат, locatability, образцы кода и пошаговое руководство
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605083"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="e4240-104">Начало HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="e4240-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="e4240-105"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> класс — это окно в holographic мир.</span><span class="sxs-lookup"><span data-stu-id="e4240-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="e4240-106">Он управляет впечатляющие визуализации, предоставляет данные камеры и предоставляет доступ к пространственных обоснование на основе API-интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="e4240-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="e4240-107">Вы создадите одно для приложения универсальной платформы Windows <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> или приложение Win32 HWND.</span><span class="sxs-lookup"><span data-stu-id="e4240-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="e4240-108">Настройка holographic пространства</span><span class="sxs-lookup"><span data-stu-id="e4240-108">Set up the holographic space</span></span>

<span data-ttu-id="e4240-109">Создание объекта holographic пространства является первым шагом в создании приложения Windows смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="e4240-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="e4240-110">Традиционные приложения Windows отрисовки для цепочки буферов Direct3D, созданные для окна core их представления приложения.</span><span class="sxs-lookup"><span data-stu-id="e4240-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="e4240-111">Этой цепочки буферов отображается баннер в пользовательском Интерфейсе holographic.</span><span class="sxs-lookup"><span data-stu-id="e4240-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="e4240-112">Чтобы сделать представление приложения holographic вместо того чтобы 2D баннер, создайте holographic пространство для окна core вместо цепочки буферов.</span><span class="sxs-lookup"><span data-stu-id="e4240-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="e4240-113">Представления holographic кадров, созданные этой holographic пространства позволяет предоставить ваше приложение в режиме полноэкранной отрисовке.</span><span class="sxs-lookup"><span data-stu-id="e4240-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="e4240-114">Для **приложения универсальной платформы Windows** [начиная с *Holographic приложение DirectX 11 (универсальные Windows) шаблона*](creating-a-holographic-directx-project.md), этот код в **SetWindow** метод в AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="e4240-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="e4240-115">Для **приложение Win32** [начиная с *BasicHologram* пример Win32](creating-a-holographic-directx-project.md#creating-a-win32-project), рассмотрим **App::CreateWindowAndHolographicSpace** для Пример того, как создать HWND и затем преобразовать его в иммерсивных HWND, создав связанным <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="e4240-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="e4240-116">Теперь, когда полученный HolographicSpace для UWP CoreWindow или Win32 HWND, HolographicSpace используется для обработки holographic камеры, создание системы координат и выполнения holographic отрисовки.</span><span class="sxs-lookup"><span data-stu-id="e4240-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="e4240-117">Текущее holographic пространство используется в нескольких местах в шаблоне DirectX:</span><span class="sxs-lookup"><span data-stu-id="e4240-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="e4240-118">**DeviceResources** классу необходимо получить сведения из объекта HolographicSpace для создания устройства Direct3D.</span><span class="sxs-lookup"><span data-stu-id="e4240-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="e4240-119">Это идентификатор адаптера DXGI, связанные с отображением holographic.</span><span class="sxs-lookup"><span data-stu-id="e4240-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="e4240-120"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> класс использует устройство Direct3D 11 вашего приложения для создания и управления ресурсами на основе устройств, включая задние буферы для каждой holographic камеры.</span><span class="sxs-lookup"><span data-stu-id="e4240-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="e4240-121">Если вы хотите увидеть, что эта функция делает за кулисами, вы найдете его в DeviceResources.cpp.</span><span class="sxs-lookup"><span data-stu-id="e4240-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="e4240-122">Функция **DeviceResources::InitializeUsingHolographicSpace** показано, как получить адаптер, посмотрев на LUID — и о выборе адаптера по умолчанию, при указании не основной адаптер.</span><span class="sxs-lookup"><span data-stu-id="e4240-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="e4240-123">Основной класс приложения использует holographic пространство из **AppView::SetWindow** или **App::CreateWindowAndHolographicSpace** для обновления и подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="e4240-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="e4240-124">Хотя в следующих разделах упомянуть имена функций из шаблона, такие как **AppView::SetWindow** , предполагается, что был запущен из holographic шаблон приложения UWP, фрагменты кода, вы увидите будут применяться одинаково для приложений универсальной платформы Windows и Win32.</span><span class="sxs-lookup"><span data-stu-id="e4240-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="e4240-125">Далее мы подробно рассмотрим настройку обработки, **SetHolographicSpace** отвечает за в классе AppMain.</span><span class="sxs-lookup"><span data-stu-id="e4240-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="e4240-126">Подписка на события камеры, создание и удаление ресурсов камеры</span><span class="sxs-lookup"><span data-stu-id="e4240-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="e4240-127">Holographic содержимое своего приложения проживает в его holographic пространство, а также просмотреть с помощью одного или нескольких holographic камеры, которые представляют различные перспективы на сцене.</span><span class="sxs-lookup"><span data-stu-id="e4240-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="e4240-128">Теперь, когда у вас есть holographic пространство, вы можете получать данные для holographic камеры.</span><span class="sxs-lookup"><span data-stu-id="e4240-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="e4240-129">Приложение должно реагировать на них **CameraAdded** события, создавая все ресурсы, относящиеся к этой камере как представление целевого объекта прорисовки задний буфер.</span><span class="sxs-lookup"><span data-stu-id="e4240-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="e4240-130">Вы увидите этот код в **DeviceResources::SetHolographicSpace** функции, вызванных **AppView::SetWindow** перед созданием приложения каких-либо holographic кадров:</span><span class="sxs-lookup"><span data-stu-id="e4240-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="e4240-131">Приложение также должно реагировать на них **CameraRemoved** события по освобождения ресурсов, которые были созданы для этой камеры.</span><span class="sxs-lookup"><span data-stu-id="e4240-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="e4240-132">Из **DeviceResources::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="e4240-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="e4240-133">Обработчики событий необходимо выполнить некоторую работу для обеспечения holographic отрисовки, потока, и поэтому, когда приложение может отображать вообще.</span><span class="sxs-lookup"><span data-stu-id="e4240-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="e4240-134">Чтение кода и комментариев, Дополнительные сведения: вы можете поискать **OnCameraAdded** и **OnCameraRemoved** в вашей основной класс, чтобы понять, как **m_cameraResources** карта — это обрабатывается **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="e4240-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="e4240-135">Прямо сейчас, сосредоточены на AppMain и настройкой на предоставление приложению возможности знать о holographic камеры.</span><span class="sxs-lookup"><span data-stu-id="e4240-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="e4240-136">С учетом этого очень важно принять во внимание следующие два требования:</span><span class="sxs-lookup"><span data-stu-id="e4240-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="e4240-137">Для **CameraAdded** обработчик событий, приложение может работать асинхронно для завершения создания ресурсов и загрузка ресурсов для нового holographic камеры.</span><span class="sxs-lookup"><span data-stu-id="e4240-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="e4240-138">Приложения, которые принимают более одного кадра, чтобы завершить эту работу следует запрашивать отсрочки и выполнить задержка, после загрузки асинхронно; [задач PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) может использоваться для выполнения асинхронной работы.</span><span class="sxs-lookup"><span data-stu-id="e4240-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="e4240-139">Приложению необходимо убедиться, что она готова для отрисовки к этой камере, прямо сейчас, при выходе из обработчика событий или при завершении задержка.</span><span class="sxs-lookup"><span data-stu-id="e4240-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="e4240-140">Выходе из обработчика событий или завершением задержка сообщает системе, что приложение теперь будет готова к приему holographic кадры с камерой, что включены.</span><span class="sxs-lookup"><span data-stu-id="e4240-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="e4240-141">Когда приложение получит **CameraRemoved** событие, он должен освободить все ссылки на задний буфер и выхода, функцию правой кнопкой мыши мышью.</span><span class="sxs-lookup"><span data-stu-id="e4240-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="e4240-142">Сюда входят представления целевого объекта отрисовки и любой другой ресурс, который может содержать ссылку на [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="e4240-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="e4240-143">Приложение необходимо также убедиться, что задний буфер не подключен как целевой объект отрисовки, как показано в **CameraResources::ReleaseResourcesForBackBuffer**.</span><span class="sxs-lookup"><span data-stu-id="e4240-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="e4240-144">Для ускорения процесса вместе, приложение можно освободить задний буфер, а затем запустите задачу, чтобы асинхронно выполнить другую работу, необходимую для того, камеры, чтобы.</span><span class="sxs-lookup"><span data-stu-id="e4240-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="e4240-145">Шаблон holographic приложения включает в себя задачу PPL, который можно использовать для этой цели.</span><span class="sxs-lookup"><span data-stu-id="e4240-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="e4240-146">Если вы хотите определить, когда отображается добавляемых или удаляемых камеры кадра, используйте **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) и [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) свойства.</span><span class="sxs-lookup"><span data-stu-id="e4240-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="e4240-147">Создание для ссылок для holographic содержимого</span><span class="sxs-lookup"><span data-stu-id="e4240-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="e4240-148">Содержимое приложения должно размещаться в [Пространственные системы координат](coordinate-systems-in-directx.md) для отображения в HolographicSpace.</span><span class="sxs-lookup"><span data-stu-id="e4240-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="e4240-149">Система предоставляет два Первичное эталонное of кадров, которые можно использовать для установки в системе координат для вашей голограммы.</span><span class="sxs-lookup"><span data-stu-id="e4240-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="e4240-150">Существует два вида опорных кадров в Windows Holographic: ссылки на кадры, подключенным к устройству и опорными кадрами, которые должно оставаться неподвижным, как это устройство окажется через среду.</span><span class="sxs-lookup"><span data-stu-id="e4240-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="e4240-151">В шаблоне holographic приложения используется кадр стационарные ссылку по умолчанию; Это одна из самых простых способов для подготовки к просмотру голограммы заблокирован в мире.</span><span class="sxs-lookup"><span data-stu-id="e4240-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="e4240-152">Стационарные опорными кадрами предназначены для стабилизации позиций практически текущее расположение устройства.</span><span class="sxs-lookup"><span data-stu-id="e4240-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="e4240-153">Это означает, что координаты от устройства могут немного смещения по отношению к среде пользователя как устройство сторона узнает больше о пространство вокруг него.</span><span class="sxs-lookup"><span data-stu-id="e4240-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="e4240-154">Существует два способа создания стационарной системой отсчета координат: получить систему координат из [пространственных этап](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), или используйте значение по умолчанию <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="e4240-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="e4240-155">Если вы создаете приложение Windows смешанной реальности для иммерсивную, рекомендуемые начальной точкой является [пространственных этап](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), которой также приводится информация о возможностях иммерсивных гарнитура, надеты на руку проигрывателем.</span><span class="sxs-lookup"><span data-stu-id="e4240-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="e4240-156">Здесь мы покажем, как использовать значение по умолчанию <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="e4240-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="e4240-157">Пространственные локатора представляет устройство Windows Mixed Reality и отслеживает движение устройства и предоставляет системы координат, которые могут быть поняты относительно его расположение.</span><span class="sxs-lookup"><span data-stu-id="e4240-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="e4240-158">Из **AppMain::OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="e4240-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="e4240-159">После создания фрейма стационарные ссылку при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="e4240-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="e4240-160">Это аналогично определение мировая система координат, к серверу-источнику, помещаются в позиции устройства при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="e4240-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="e4240-161">Этот кадр ссылки не перемещаются вместе с устройства.</span><span class="sxs-lookup"><span data-stu-id="e4240-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="e4240-162">Из **AppMain::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="e4240-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="e4240-163">Все опорными кадрами, тяжести выровнены, это означает, что ось y указывает «up» по отношению к среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="e4240-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="e4240-164">Так как Windows использует «правостороннюю» системы координат, направление оси z — совпадает с «forward» направление устройства направлена в том случае, когда создается фрейм ссылку.</span><span class="sxs-lookup"><span data-stu-id="e4240-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="e4240-165">Если вашему приложению требуется точное расположение отдельных голограммы, использовать <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> нулевые отдельных голограмма в позицию в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="e4240-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="e4240-166">Например можно используйте привязку Пространственные, когда пользователь указывает точку, чтобы наибольший интерес.</span><span class="sxs-lookup"><span data-stu-id="e4240-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="e4240-167">Не переместятся позиций привязки, но они могут быть изменены.</span><span class="sxs-lookup"><span data-stu-id="e4240-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="e4240-168">По умолчанию при изменении привязки, например, тем, что повышает его положение в месте по кадрам, далее несколько после исправления.</span><span class="sxs-lookup"><span data-stu-id="e4240-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="e4240-169">В зависимости от приложения в этом случае может потребоваться обрабатывать корректировки иным образом (например, дожидаясь, пока она выходит за пределы представления).</span><span class="sxs-lookup"><span data-stu-id="e4240-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="e4240-170"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> свойство и <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> события включить эти настройки.</span><span class="sxs-lookup"><span data-stu-id="e4240-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="e4240-171">Реагирование на события locatability изменен</span><span class="sxs-lookup"><span data-stu-id="e4240-171">Respond to locatability changed events</span></span>

<span data-ttu-id="e4240-172">Визуализации заблокирован world голограммы требуется устройства могли выполнять поиск самого в мире.</span><span class="sxs-lookup"><span data-stu-id="e4240-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="e4240-173">Это не всегда возможно из-за условий эксплуатации, и если да, пользователь может ожидать визуальное отслеживание прерывания.</span><span class="sxs-lookup"><span data-stu-id="e4240-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="e4240-174">Это визуальное должен визуализироваться с помощью опорных кадров, подключенным к устройству, а не бланк во всем мире.</span><span class="sxs-lookup"><span data-stu-id="e4240-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="e4240-175">Теперь приложение можно настроить уведомления об Если отслеживания прерывается по любой причине.</span><span class="sxs-lookup"><span data-stu-id="e4240-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="e4240-176">Зарегистрируйте событие LocatabilityChanged обнаруживать устройства возможность обнаружения сам изменяется в мире.</span><span class="sxs-lookup"><span data-stu-id="e4240-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="e4240-177">Из **AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="e4240-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="e4240-178">Затем используйте это событие, чтобы определить, когда голограммы невозможно стационарные во всем мире.</span><span class="sxs-lookup"><span data-stu-id="e4240-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4240-179">См. также</span><span class="sxs-lookup"><span data-stu-id="e4240-179">See also</span></span>
* [<span data-ttu-id="e4240-180">Подготовка к просмотру в DirectX</span><span class="sxs-lookup"><span data-stu-id="e4240-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="e4240-181">Системы координат в DirectX</span><span class="sxs-lookup"><span data-stu-id="e4240-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
