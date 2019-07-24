---
title: Получение Холографикспаце
description: Описание API Холографикспаце, основной концепции для holographic-отрисовки и пространственного ввода.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Холографикспаце, CoreWindow, пространственный ввод, отрисовка, цепочка буферов, holographic кадров, цикл обновления, цикл игры, кадр ссылки, локатабилити, пример кода, пошаговое руководство
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525446"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="59c59-104">Получение Холографикспаце</span><span class="sxs-lookup"><span data-stu-id="59c59-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="59c59-105">Класс <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a> является порталом в holographic мире.</span><span class="sxs-lookup"><span data-stu-id="59c59-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="59c59-106">Он контролирует иммерсивное визуализацию, предоставляет данные камеры и предоставляет доступ к API-интерфейсам пространственной причины.</span><span class="sxs-lookup"><span data-stu-id="59c59-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="59c59-107">Вы создадите его для <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> приложения UWP или HWND приложения Win32.</span><span class="sxs-lookup"><span data-stu-id="59c59-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="59c59-108">Настройка holographic-дискового пространства</span><span class="sxs-lookup"><span data-stu-id="59c59-108">Set up the holographic space</span></span>

<span data-ttu-id="59c59-109">Создание объекта holographic — это первый шаг в создании приложения Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="59c59-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="59c59-110">Традиционные приложения Windows подготавливаются к цепочке переключения Direct3D, созданной для основного окна представления приложения.</span><span class="sxs-lookup"><span data-stu-id="59c59-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="59c59-111">Эта цепочка подкачки отображается на планшете с помощью интерфейса пользователя Holographic.</span><span class="sxs-lookup"><span data-stu-id="59c59-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="59c59-112">Чтобы сделать представление приложения более holographic, а не 2D-планшетом, создайте для его основного окна, а не цепочки буферов.</span><span class="sxs-lookup"><span data-stu-id="59c59-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="59c59-113">Представление holographic-кадров, созданных с помощью этого holographic-места, помещает приложение в полноэкранный режим отрисовки.</span><span class="sxs-lookup"><span data-stu-id="59c59-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="59c59-114">Для **приложения UWP** , [начиная с *шаблона приложения holographic DirectX 11 (Universal Windows)* ](creating-a-holographic-directx-project.md), найдите этот код в методе **сетвиндов** в аппвиев. cpp:</span><span class="sxs-lookup"><span data-stu-id="59c59-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="59c59-115">Для **приложения Win32** , [начиная с примера Win32 *басичолограм* ](creating-a-holographic-directx-project.md#creating-a-win32-project), рассмотрим **Приложение:: креатевиндовандхолографикспаце** , в котором приведен пример того, как создать HWND и преобразовать его в иммерсивное окно HWND, создав связанный <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">элемент Холографикспаце</a>:</span><span class="sxs-lookup"><span data-stu-id="59c59-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
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

<span data-ttu-id="59c59-116">Теперь, когда вы получили Холографикспаце для CoreWindowов UWP или Win32 HWND, вы будете использовать этот Холографикспаце для обработки holographic-камер, создания систем координат и работы с Holographic.</span><span class="sxs-lookup"><span data-stu-id="59c59-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="59c59-117">Текущий holographic-диск используется в нескольких местах шаблона DirectX:</span><span class="sxs-lookup"><span data-stu-id="59c59-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="59c59-118">Класс **DeviceResources** должен получить некоторую информацию из объекта холографикспаце, чтобы создать устройство Direct3D.</span><span class="sxs-lookup"><span data-stu-id="59c59-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="59c59-119">Это идентификатор адаптера DXGI, связанный с holographic-дисплеем.</span><span class="sxs-lookup"><span data-stu-id="59c59-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="59c59-120">Класс <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a> использует устройство Direct3D 11 приложения для создания ресурсов на основе устройств и управления ими, например задними буферами для каждой из holographic камер.</span><span class="sxs-lookup"><span data-stu-id="59c59-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="59c59-121">Если вы заинтересованы в том, какую функцию выполняет эта функция, вы найдете ее в DeviceResources. cpp.</span><span class="sxs-lookup"><span data-stu-id="59c59-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="59c59-122">Функция **DeviceResources:: инитиализеусингхолографикспаце** показывает, как получить адаптер путем поиска LUID — и как выбрать адаптер по умолчанию, если предпочтительный адаптер не указан.</span><span class="sxs-lookup"><span data-stu-id="59c59-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="59c59-123">В основном классе приложения для обновлений и отрисовки используется пространство с **аппвиев:: сетвиндов** или **app:: креатевиндовандхолографикспаце** .</span><span class="sxs-lookup"><span data-stu-id="59c59-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="59c59-124">В разделах ниже упоминаются имена функций из шаблона, например **аппвиев:: сетвиндов** , которые предполагают, что вы начали из шаблона приложения с шаблоном UWP, отображаемые фрагменты кода будут применяться одинаково в приложениях UWP и Win32.</span><span class="sxs-lookup"><span data-stu-id="59c59-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="59c59-125">Далее мы рассмотрим процесс установки, который **сесолографикспаце** отвечает за в классе аппмаин.</span><span class="sxs-lookup"><span data-stu-id="59c59-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="59c59-126">Подпишитесь на события камеры, создавайте и удаляйте ресурсы камеры</span><span class="sxs-lookup"><span data-stu-id="59c59-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="59c59-127">Содержимое вашего приложения живет в жизнь и просматривается с помощью одной или нескольких holographic камер, которые представляют различные перспективы сцены.</span><span class="sxs-lookup"><span data-stu-id="59c59-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="59c59-128">Теперь, когда у вас есть место, вы можете получить данные для более holographic камер.</span><span class="sxs-lookup"><span data-stu-id="59c59-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="59c59-129">Приложение должно реагировать на события **камерааддед** , создавая все ресурсы, относящиеся к этой камере, такие как представление целевого объекта отрисовки заднего буфера.</span><span class="sxs-lookup"><span data-stu-id="59c59-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="59c59-130">Этот код можно увидеть в функции **DeviceResources:: сесолографикспаце** , вызываемой **Аппвиев:: сетвиндов** до того, как приложение создаст все holographic кадров:</span><span class="sxs-lookup"><span data-stu-id="59c59-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="59c59-131">Приложение также должно отвечать на события **камераремовед** , освобождая ресурсы, созданные для этой камеры.</span><span class="sxs-lookup"><span data-stu-id="59c59-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="59c59-132">Из **DeviceResources:: сесолографикспаце**:</span><span class="sxs-lookup"><span data-stu-id="59c59-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="59c59-133">Обработчики событий должны выполнить некоторую работу, чтобы обеспечить плавное перетекание с помощью, чтобы приложение могло работать вообще.</span><span class="sxs-lookup"><span data-stu-id="59c59-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="59c59-134">Ознакомьтесь с кодом и комментариями для получения сведений: вы можете найти **онкамерааддед** и **онкамераремовед** в основном классе, чтобы понять, как в **DeviceResources**обрабатывается схема **m_cameraResources** .</span><span class="sxs-lookup"><span data-stu-id="59c59-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="59c59-135">Сейчас мы сосредоточены на Аппмаин и настройке, которые он делает для того, чтобы ваше приложение знало о holographic фотокамер.</span><span class="sxs-lookup"><span data-stu-id="59c59-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="59c59-136">Учитывая это, важно отметить следующие два требования:</span><span class="sxs-lookup"><span data-stu-id="59c59-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="59c59-137">Для обработчика событий **камерааддед** приложение может работать асинхронно, чтобы завершить создание ресурсов и загрузку ресурсов для новой камеры Holographic.</span><span class="sxs-lookup"><span data-stu-id="59c59-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="59c59-138">Приложения, которые используют более одного кадра для выполнения этой работы, должны запрашивать РБП и завершать РБП после асинхронной загрузки; [задачу PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) можно использовать для асинхронной работы.</span><span class="sxs-lookup"><span data-stu-id="59c59-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="59c59-139">Приложение должно убедиться, что оно готово к отображению на этой камере сразу после выхода из обработчика событий или после завершения периода отсрочки.</span><span class="sxs-lookup"><span data-stu-id="59c59-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="59c59-140">Выход из обработчика событий или завершение периода отсрочки сообщает системе, что ваше приложение готово к получению holographic с помощью включенной камеры.</span><span class="sxs-lookup"><span data-stu-id="59c59-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="59c59-141">Когда приложение получает событие **камераремовед** , оно должно освободить все ссылки на задний буфер и сразу же выйти из функции.</span><span class="sxs-lookup"><span data-stu-id="59c59-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="59c59-142">Сюда входят представления целевого объекта прорисовки и любой другой ресурс, который может содержать ссылку на [идксгиресаурце](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="59c59-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="59c59-143">Приложение также должно гарантировать, что задний буфер не присоединен в качестве целевого объекта отрисовки, как показано в **камераресаурцес:: релеасересаурцесфорбаккбуффер**.</span><span class="sxs-lookup"><span data-stu-id="59c59-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="59c59-144">Чтобы ускорить работу, приложение может освободить задний буфер, а затем запустить задачу для асинхронного завершения любой другой работы, необходимой для удаления этой камеры.</span><span class="sxs-lookup"><span data-stu-id="59c59-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="59c59-145">Шаблон holographic App содержит задачу PPL, которую можно использовать для этой цели.</span><span class="sxs-lookup"><span data-stu-id="59c59-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="59c59-146">Если вы хотите определить, когда в рамке отображается добавленная или удаленная камера, используйте свойства **холографикфраме** [аддедкамерас](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) и [ремоведкамерас](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .</span><span class="sxs-lookup"><span data-stu-id="59c59-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="59c59-147">Создание рамки ссылки для вашего holographic-содержимого</span><span class="sxs-lookup"><span data-stu-id="59c59-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="59c59-148">Содержимое вашего приложения должно быть размещено в пространственной [системе координат](coordinate-systems-in-directx.md) для подготовки к просмотру в холографикспаце.</span><span class="sxs-lookup"><span data-stu-id="59c59-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="59c59-149">Система предоставляет два основных кадра ссылок, которые можно использовать для создания системы координат для голограмм.</span><span class="sxs-lookup"><span data-stu-id="59c59-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="59c59-150">В Windows holographic есть два вида опорных кадра: справочные фреймы, присоединенные к устройству, и ссылки на кадры, которые остаются стационарными при перемещении устройства через среду пользователя.</span><span class="sxs-lookup"><span data-stu-id="59c59-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="59c59-151">Шаблон holographic App по умолчанию использует стационарный ссылочный фрейм. Это один из самых простых способов визуализации голограмм с блокировкой мира.</span><span class="sxs-lookup"><span data-stu-id="59c59-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="59c59-152">Стационарные опорные кадры предназначены для стабилизации положений в текущем расположении устройства.</span><span class="sxs-lookup"><span data-stu-id="59c59-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="59c59-153">Это означает, что более подробное смещение от устройства может немного отменяться в отношении среды пользователя, так как устройство узнает больше о пространстве вокруг него.</span><span class="sxs-lookup"><span data-stu-id="59c59-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="59c59-154">Существует два способа создания стационарной рамки ссылки: получение системы координат с [пространственного этапа](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)или использование <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">спатиаллокатор</a>по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="59c59-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="59c59-155">Если вы создаете приложение Windows Mixed Reality для впечатляющих головных телефонов, рекомендуемой отправной точкой является [пространственный этап](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), который также предоставляет сведения о возможностях надеты гарнитуры, которые проигрыватель.</span><span class="sxs-lookup"><span data-stu-id="59c59-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="59c59-156">Здесь мы покажем, как использовать <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">спатиаллокатор</a>по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="59c59-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="59c59-157">Пространственный локатор представляет устройство Windows Mixed Reality и отслеживает движение устройства и предоставляет системы координат, которые могут быть понятны по отношению к его расположению.</span><span class="sxs-lookup"><span data-stu-id="59c59-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="59c59-158">Из **аппмаин:: онхолографикдисплайисаваилаблечанжед**:</span><span class="sxs-lookup"><span data-stu-id="59c59-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="59c59-159">Создайте стационарный фрейм ссылки один раз при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="59c59-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="59c59-160">Это аналогично определению мировой системы координат, когда источник помещается в положение устройства при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="59c59-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="59c59-161">Этот ссылочный кадр не перемещается вместе с устройством.</span><span class="sxs-lookup"><span data-stu-id="59c59-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="59c59-162">Из **аппмаин:: сесолографикспаце**:</span><span class="sxs-lookup"><span data-stu-id="59c59-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="59c59-163">Все ссылочные фреймы имеют согласованный объект, что означает, что ось y указывает на "вверх" в отношении среды пользователя.</span><span class="sxs-lookup"><span data-stu-id="59c59-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="59c59-164">Так как в Windows используются "правильные" системы координат, направление оси – z совпадает с направлением "вперед", когда создается ссылочный фрейм.</span><span class="sxs-lookup"><span data-stu-id="59c59-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="59c59-165">Если для приложения требуется точное размещение отдельных голограмм, используйте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">спатиаланчор</a> , чтобы привязать отдельную голограмму к положению в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="59c59-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="59c59-166">Например, используйте пространственное привязку, когда пользователь указывает на точку, которая является специальным интересом.</span><span class="sxs-lookup"><span data-stu-id="59c59-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="59c59-167">Позиции привязки не отменяют смещение, но их можно скорректировать.</span><span class="sxs-lookup"><span data-stu-id="59c59-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="59c59-168">По умолчанию, когда привязка корректируется, она упрощает свою позицию в следующих нескольких кадрах после исправления.</span><span class="sxs-lookup"><span data-stu-id="59c59-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="59c59-169">В зависимости от приложения, когда это происходит, может потребоваться выполнить корректировку другим способом (например, отложив его до тех пор, пока не появится голограмма).</span><span class="sxs-lookup"><span data-stu-id="59c59-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="59c59-170">Свойства <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">равкурдинатесистем</a> и <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">равкурдинатесистемаджустед</a> позволяют выполнять эти настройки.</span><span class="sxs-lookup"><span data-stu-id="59c59-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="59c59-171">Реагирование на события изменения локатабилити</span><span class="sxs-lookup"><span data-stu-id="59c59-171">Respond to locatability changed events</span></span>

<span data-ttu-id="59c59-172">Для отрисовки голограмм, заблокированных в мире, устройство должно иметь возможность размещать себя в мире.</span><span class="sxs-lookup"><span data-stu-id="59c59-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="59c59-173">Это может быть не всегда возможно из-за условий окружающей среды. Если да, то пользователь может столкнуться с визуальным индикатором прерывания отслеживания.</span><span class="sxs-lookup"><span data-stu-id="59c59-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="59c59-174">Этот визуальный индикатор должен быть визуализирован с помощью ссылочных фреймов, присоединенных к устройству, а не по всему миру.</span><span class="sxs-lookup"><span data-stu-id="59c59-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="59c59-175">Приложение может запросить уведомления, если отслеживание прервано по какой-либо причине.</span><span class="sxs-lookup"><span data-stu-id="59c59-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="59c59-176">Зарегистрируйтесь на событие Локатабилитичанжед, чтобы определить, когда устройство может найти себя в мире изменений.</span><span class="sxs-lookup"><span data-stu-id="59c59-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="59c59-177">Из **аппмаин:: сесолографикспаце:**</span><span class="sxs-lookup"><span data-stu-id="59c59-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="59c59-178">Затем используйте это событие, чтобы определить, когда голограммы не могут быть отображены в нестационарном мире.</span><span class="sxs-lookup"><span data-stu-id="59c59-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="59c59-179">См. также</span><span class="sxs-lookup"><span data-stu-id="59c59-179">See also</span></span>
* [<span data-ttu-id="59c59-180">Отрисовка в DirectX</span><span class="sxs-lookup"><span data-stu-id="59c59-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="59c59-181">Системы координат в DirectX</span><span class="sxs-lookup"><span data-stu-id="59c59-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
