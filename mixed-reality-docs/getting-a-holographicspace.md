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
# <a name="getting-a-holographicspace"></a>Получение Холографикспаце

Класс <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a> является порталом в holographic мире. Он контролирует иммерсивное визуализацию, предоставляет данные камеры и предоставляет доступ к API-интерфейсам пространственной причины. Вы создадите его для <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> приложения UWP или HWND приложения Win32.

## <a name="set-up-the-holographic-space"></a>Настройка holographic-дискового пространства

Создание объекта holographic — это первый шаг в создании приложения Windows Mixed Reality. Традиционные приложения Windows подготавливаются к цепочке переключения Direct3D, созданной для основного окна представления приложения. Эта цепочка подкачки отображается на планшете с помощью интерфейса пользователя Holographic. Чтобы сделать представление приложения более holographic, а не 2D-планшетом, создайте для его основного окна, а не цепочки буферов. Представление holographic-кадров, созданных с помощью этого holographic-места, помещает приложение в полноэкранный режим отрисовки.

Для **приложения UWP** , [начиная с *шаблона приложения holographic DirectX 11 (Universal Windows)* ](creating-a-holographic-directx-project.md), найдите этот код в методе **сетвиндов** в аппвиев. cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Для **приложения Win32** , [начиная с примера Win32 *басичолограм* ](creating-a-holographic-directx-project.md#creating-a-win32-project), рассмотрим **Приложение:: креатевиндовандхолографикспаце** , в котором приведен пример того, как создать HWND и преобразовать его в иммерсивное окно HWND, создав связанный <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">элемент Холографикспаце</a>:
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

Теперь, когда вы получили Холографикспаце для CoreWindowов UWP или Win32 HWND, вы будете использовать этот Холографикспаце для обработки holographic-камер, создания систем координат и работы с Holographic. Текущий holographic-диск используется в нескольких местах шаблона DirectX:
* Класс **DeviceResources** должен получить некоторую информацию из объекта холографикспаце, чтобы создать устройство Direct3D. Это идентификатор адаптера DXGI, связанный с holographic-дисплеем. Класс <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a> использует устройство Direct3D 11 приложения для создания ресурсов на основе устройств и управления ими, например задними буферами для каждой из holographic камер. Если вы заинтересованы в том, какую функцию выполняет эта функция, вы найдете ее в DeviceResources. cpp.
* Функция **DeviceResources:: инитиализеусингхолографикспаце** показывает, как получить адаптер путем поиска LUID — и как выбрать адаптер по умолчанию, если предпочтительный адаптер не указан.
* В основном классе приложения для обновлений и отрисовки используется пространство с **аппвиев:: сетвиндов** или **app:: креатевиндовандхолографикспаце** .

>[!NOTE]
>В разделах ниже упоминаются имена функций из шаблона, например **аппвиев:: сетвиндов** , которые предполагают, что вы начали из шаблона приложения с шаблоном UWP, отображаемые фрагменты кода будут применяться одинаково в приложениях UWP и Win32.

Далее мы рассмотрим процесс установки, который **сесолографикспаце** отвечает за в классе аппмаин.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Подпишитесь на события камеры, создавайте и удаляйте ресурсы камеры

Содержимое вашего приложения живет в жизнь и просматривается с помощью одной или нескольких holographic камер, которые представляют различные перспективы сцены. Теперь, когда у вас есть место, вы можете получить данные для более holographic камер.

Приложение должно реагировать на события **камерааддед** , создавая все ресурсы, относящиеся к этой камере, такие как представление целевого объекта отрисовки заднего буфера. Этот код можно увидеть в функции **DeviceResources:: сесолографикспаце** , вызываемой **Аппвиев:: сетвиндов** до того, как приложение создаст все holographic кадров:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

Приложение также должно отвечать на события **камераремовед** , освобождая ресурсы, созданные для этой камеры.

Из **DeviceResources:: сесолографикспаце**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Обработчики событий должны выполнить некоторую работу, чтобы обеспечить плавное перетекание с помощью, чтобы приложение могло работать вообще. Ознакомьтесь с кодом и комментариями для получения сведений: вы можете найти **онкамерааддед** и **онкамераремовед** в основном классе, чтобы понять, как в **DeviceResources**обрабатывается схема **m_cameraResources** .

Сейчас мы сосредоточены на Аппмаин и настройке, которые он делает для того, чтобы ваше приложение знало о holographic фотокамер. Учитывая это, важно отметить следующие два требования:

1. Для обработчика событий **камерааддед** приложение может работать асинхронно, чтобы завершить создание ресурсов и загрузку ресурсов для новой камеры Holographic. Приложения, которые используют более одного кадра для выполнения этой работы, должны запрашивать РБП и завершать РБП после асинхронной загрузки; [задачу PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) можно использовать для асинхронной работы. Приложение должно убедиться, что оно готово к отображению на этой камере сразу после выхода из обработчика событий или после завершения периода отсрочки. Выход из обработчика событий или завершение периода отсрочки сообщает системе, что ваше приложение готово к получению holographic с помощью включенной камеры.

2. Когда приложение получает событие **камераремовед** , оно должно освободить все ссылки на задний буфер и сразу же выйти из функции. Сюда входят представления целевого объекта прорисовки и любой другой ресурс, который может содержать ссылку на [идксгиресаурце](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). Приложение также должно гарантировать, что задний буфер не присоединен в качестве целевого объекта отрисовки, как показано в **камераресаурцес:: релеасересаурцесфорбаккбуффер**. Чтобы ускорить работу, приложение может освободить задний буфер, а затем запустить задачу для асинхронного завершения любой другой работы, необходимой для удаления этой камеры. Шаблон holographic App содержит задачу PPL, которую можно использовать для этой цели.

>[!NOTE]
>Если вы хотите определить, когда в рамке отображается добавленная или удаленная камера, используйте свойства **холографикфраме** [аддедкамерас](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) и [ремоведкамерас](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Создание рамки ссылки для вашего holographic-содержимого

Содержимое вашего приложения должно быть размещено в пространственной [системе координат](coordinate-systems-in-directx.md) для подготовки к просмотру в холографикспаце. Система предоставляет два основных кадра ссылок, которые можно использовать для создания системы координат для голограмм.

В Windows holographic есть два вида опорных кадра: справочные фреймы, присоединенные к устройству, и ссылки на кадры, которые остаются стационарными при перемещении устройства через среду пользователя. Шаблон holographic App по умолчанию использует стационарный ссылочный фрейм. Это один из самых простых способов визуализации голограмм с блокировкой мира.

Стационарные опорные кадры предназначены для стабилизации положений в текущем расположении устройства. Это означает, что более подробное смещение от устройства может немного отменяться в отношении среды пользователя, так как устройство узнает больше о пространстве вокруг него. Существует два способа создания стационарной рамки ссылки: получение системы координат с [пространственного этапа](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)или использование <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">спатиаллокатор</a>по умолчанию. Если вы создаете приложение Windows Mixed Reality для впечатляющих головных телефонов, рекомендуемой отправной точкой является [пространственный этап](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), который также предоставляет сведения о возможностях надеты гарнитуры, которые проигрыватель. Здесь мы покажем, как использовать <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">спатиаллокатор</a>по умолчанию.

Пространственный локатор представляет устройство Windows Mixed Reality и отслеживает движение устройства и предоставляет системы координат, которые могут быть понятны по отношению к его расположению.

Из **аппмаин:: онхолографикдисплайисаваилаблечанжед**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Создайте стационарный фрейм ссылки один раз при запуске приложения. Это аналогично определению мировой системы координат, когда источник помещается в положение устройства при запуске приложения. Этот ссылочный кадр не перемещается вместе с устройством.

Из **аппмаин:: сесолографикспаце**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Все ссылочные фреймы имеют согласованный объект, что означает, что ось y указывает на "вверх" в отношении среды пользователя. Так как в Windows используются "правильные" системы координат, направление оси – z совпадает с направлением "вперед", когда создается ссылочный фрейм.

>[!NOTE]
>Если для приложения требуется точное размещение отдельных голограмм, используйте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">спатиаланчор</a> , чтобы привязать отдельную голограмму к положению в реальном мире. Например, используйте пространственное привязку, когда пользователь указывает на точку, которая является специальным интересом. Позиции привязки не отменяют смещение, но их можно скорректировать. По умолчанию, когда привязка корректируется, она упрощает свою позицию в следующих нескольких кадрах после исправления. В зависимости от приложения, когда это происходит, может потребоваться выполнить корректировку другим способом (например, отложив его до тех пор, пока не появится голограмма). Свойства <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">равкурдинатесистем</a> и <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">равкурдинатесистемаджустед</a> позволяют выполнять эти настройки.

## <a name="respond-to-locatability-changed-events"></a>Реагирование на события изменения локатабилити

Для отрисовки голограмм, заблокированных в мире, устройство должно иметь возможность размещать себя в мире. Это может быть не всегда возможно из-за условий окружающей среды. Если да, то пользователь может столкнуться с визуальным индикатором прерывания отслеживания. Этот визуальный индикатор должен быть визуализирован с помощью ссылочных фреймов, присоединенных к устройству, а не по всему миру.

Приложение может запросить уведомления, если отслеживание прервано по какой-либо причине. Зарегистрируйтесь на событие Локатабилитичанжед, чтобы определить, когда устройство может найти себя в мире изменений. Из **аппмаин:: сесолографикспаце:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Затем используйте это событие, чтобы определить, когда голограммы не могут быть отображены в нестационарном мире.

## <a name="see-also"></a>См. также
* [Отрисовка в DirectX](rendering-in-directx.md)
* [Системы координат в DirectX](coordinate-systems-in-directx.md)
