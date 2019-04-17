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
# <a name="getting-a-holographicspace"></a>Начало HolographicSpace

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> класс — это окно в holographic мир. Он управляет впечатляющие визуализации, предоставляет данные камеры и предоставляет доступ к пространственных обоснование на основе API-интерфейсы. Вы создадите одно для приложения универсальной платформы Windows <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> или приложение Win32 HWND.

## <a name="set-up-the-holographic-space"></a>Настройка holographic пространства

Создание объекта holographic пространства является первым шагом в создании приложения Windows смешанной реальности. Традиционные приложения Windows отрисовки для цепочки буферов Direct3D, созданные для окна core их представления приложения. Этой цепочки буферов отображается баннер в пользовательском Интерфейсе holographic. Чтобы сделать представление приложения holographic вместо того чтобы 2D баннер, создайте holographic пространство для окна core вместо цепочки буферов. Представления holographic кадров, созданные этой holographic пространства позволяет предоставить ваше приложение в режиме полноэкранной отрисовке.

Для **приложения универсальной платформы Windows** [начиная с *Holographic приложение DirectX 11 (универсальные Windows) шаблона*](creating-a-holographic-directx-project.md), этот код в **SetWindow** метод в AppView.cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Для **приложение Win32** [начиная с *BasicHologram* пример Win32](creating-a-holographic-directx-project.md#creating-a-win32-project), рассмотрим **App::CreateWindowAndHolographicSpace** для Пример того, как создать HWND и затем преобразовать его в иммерсивных HWND, создав связанным <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:
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

Теперь, когда полученный HolographicSpace для UWP CoreWindow или Win32 HWND, HolographicSpace используется для обработки holographic камеры, создание системы координат и выполнения holographic отрисовки. Текущее holographic пространство используется в нескольких местах в шаблоне DirectX:
* **DeviceResources** классу необходимо получить сведения из объекта HolographicSpace для создания устройства Direct3D. Это идентификатор адаптера DXGI, связанные с отображением holographic. <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> класс использует устройство Direct3D 11 вашего приложения для создания и управления ресурсами на основе устройств, включая задние буферы для каждой holographic камеры. Если вы хотите увидеть, что эта функция делает за кулисами, вы найдете его в DeviceResources.cpp.
* Функция **DeviceResources::InitializeUsingHolographicSpace** показано, как получить адаптер, посмотрев на LUID — и о выборе адаптера по умолчанию, при указании не основной адаптер.
* Основной класс приложения использует holographic пространство из **AppView::SetWindow** или **App::CreateWindowAndHolographicSpace** для обновления и подготовки к просмотру.

>[!NOTE]
>Хотя в следующих разделах упомянуть имена функций из шаблона, такие как **AppView::SetWindow** , предполагается, что был запущен из holographic шаблон приложения UWP, фрагменты кода, вы увидите будут применяться одинаково для приложений универсальной платформы Windows и Win32.

Далее мы подробно рассмотрим настройку обработки, **SetHolographicSpace** отвечает за в классе AppMain.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Подписка на события камеры, создание и удаление ресурсов камеры

Holographic содержимое своего приложения проживает в его holographic пространство, а также просмотреть с помощью одного или нескольких holographic камеры, которые представляют различные перспективы на сцене. Теперь, когда у вас есть holographic пространство, вы можете получать данные для holographic камеры.

Приложение должно реагировать на них **CameraAdded** события, создавая все ресурсы, относящиеся к этой камере как представление целевого объекта прорисовки задний буфер. Вы увидите этот код в **DeviceResources::SetHolographicSpace** функции, вызванных **AppView::SetWindow** перед созданием приложения каких-либо holographic кадров:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

Приложение также должно реагировать на них **CameraRemoved** события по освобождения ресурсов, которые были созданы для этой камеры.

Из **DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Обработчики событий необходимо выполнить некоторую работу для обеспечения holographic отрисовки, потока, и поэтому, когда приложение может отображать вообще. Чтение кода и комментариев, Дополнительные сведения: вы можете поискать **OnCameraAdded** и **OnCameraRemoved** в вашей основной класс, чтобы понять, как **m_cameraResources** карта — это обрабатывается **DeviceResources**.

Прямо сейчас, сосредоточены на AppMain и настройкой на предоставление приложению возможности знать о holographic камеры. С учетом этого очень важно принять во внимание следующие два требования:

1. Для **CameraAdded** обработчик событий, приложение может работать асинхронно для завершения создания ресурсов и загрузка ресурсов для нового holographic камеры. Приложения, которые принимают более одного кадра, чтобы завершить эту работу следует запрашивать отсрочки и выполнить задержка, после загрузки асинхронно; [задач PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) может использоваться для выполнения асинхронной работы. Приложению необходимо убедиться, что она готова для отрисовки к этой камере, прямо сейчас, при выходе из обработчика событий или при завершении задержка. Выходе из обработчика событий или завершением задержка сообщает системе, что приложение теперь будет готова к приему holographic кадры с камерой, что включены.

2. Когда приложение получит **CameraRemoved** событие, он должен освободить все ссылки на задний буфер и выхода, функцию правой кнопкой мыши мышью. Сюда входят представления целевого объекта отрисовки и любой другой ресурс, который может содержать ссылку на [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). Приложение необходимо также убедиться, что задний буфер не подключен как целевой объект отрисовки, как показано в **CameraResources::ReleaseResourcesForBackBuffer**. Для ускорения процесса вместе, приложение можно освободить задний буфер, а затем запустите задачу, чтобы асинхронно выполнить другую работу, необходимую для того, камеры, чтобы. Шаблон holographic приложения включает в себя задачу PPL, который можно использовать для этой цели.

>[!NOTE]
>Если вы хотите определить, когда отображается добавляемых или удаляемых камеры кадра, используйте **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) и [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) свойства.

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Создание для ссылок для holographic содержимого

Содержимое приложения должно размещаться в [Пространственные системы координат](coordinate-systems-in-directx.md) для отображения в HolographicSpace. Система предоставляет два Первичное эталонное of кадров, которые можно использовать для установки в системе координат для вашей голограммы.

Существует два вида опорных кадров в Windows Holographic: ссылки на кадры, подключенным к устройству и опорными кадрами, которые должно оставаться неподвижным, как это устройство окажется через среду. В шаблоне holographic приложения используется кадр стационарные ссылку по умолчанию; Это одна из самых простых способов для подготовки к просмотру голограммы заблокирован в мире.

Стационарные опорными кадрами предназначены для стабилизации позиций практически текущее расположение устройства. Это означает, что координаты от устройства могут немного смещения по отношению к среде пользователя как устройство сторона узнает больше о пространство вокруг него. Существует два способа создания стационарной системой отсчета координат: получить систему координат из [пространственных этап](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), или используйте значение по умолчанию <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>. Если вы создаете приложение Windows смешанной реальности для иммерсивную, рекомендуемые начальной точкой является [пространственных этап](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), которой также приводится информация о возможностях иммерсивных гарнитура, надеты на руку проигрывателем. Здесь мы покажем, как использовать значение по умолчанию <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.

Пространственные локатора представляет устройство Windows Mixed Reality и отслеживает движение устройства и предоставляет системы координат, которые могут быть поняты относительно его расположение.

Из **AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

После создания фрейма стационарные ссылку при запуске приложения. Это аналогично определение мировая система координат, к серверу-источнику, помещаются в позиции устройства при запуске приложения. Этот кадр ссылки не перемещаются вместе с устройства.

Из **AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Все опорными кадрами, тяжести выровнены, это означает, что ось y указывает «up» по отношению к среде пользователя. Так как Windows использует «правостороннюю» системы координат, направление оси z — совпадает с «forward» направление устройства направлена в том случае, когда создается фрейм ссылку.

>[!NOTE]
>Если вашему приложению требуется точное расположение отдельных голограммы, использовать <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> нулевые отдельных голограмма в позицию в реальном мире. Например можно используйте привязку Пространственные, когда пользователь указывает точку, чтобы наибольший интерес. Не переместятся позиций привязки, но они могут быть изменены. По умолчанию при изменении привязки, например, тем, что повышает его положение в месте по кадрам, далее несколько после исправления. В зависимости от приложения в этом случае может потребоваться обрабатывать корректировки иным образом (например, дожидаясь, пока она выходит за пределы представления). <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> свойство и <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> события включить эти настройки.

## <a name="respond-to-locatability-changed-events"></a>Реагирование на события locatability изменен

Визуализации заблокирован world голограммы требуется устройства могли выполнять поиск самого в мире. Это не всегда возможно из-за условий эксплуатации, и если да, пользователь может ожидать визуальное отслеживание прерывания. Это визуальное должен визуализироваться с помощью опорных кадров, подключенным к устройству, а не бланк во всем мире.

Теперь приложение можно настроить уведомления об Если отслеживания прерывается по любой причине. Зарегистрируйте событие LocatabilityChanged обнаруживать устройства возможность обнаружения сам изменяется в мире. Из **AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Затем используйте это событие, чтобы определить, когда голограммы невозможно стационарные во всем мире.

## <a name="see-also"></a>См. также
* [Подготовка к просмотру в DirectX](rendering-in-directx.md)
* [Системы координат в DirectX](coordinate-systems-in-directx.md)
