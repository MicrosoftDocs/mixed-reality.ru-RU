---
title: Отслеживание QR-кода
description: Узнайте, как обнаруживать QR-коды в HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, лбе, развлечения на основе расположения, VR Аркадные, Аркадные, иммерсивное, QR, QR-код, hololens2
ms.openlocfilehash: 6d3dc442c28e498cc00e14325398de2026261a17
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476766"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="dc0fd-104">Отслеживание QR-кода</span><span class="sxs-lookup"><span data-stu-id="dc0fd-104">QR code tracking</span></span>

<span data-ttu-id="dc0fd-105">HoloLens 2 может обнаруживать QR-коды в окружении, окружающем гарнитуру, устанавливая систему координат в реальном расположении всего кода.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="dc0fd-106">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="dc0fd-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="dc0fd-107">Функция</span><span class="sxs-lookup"><span data-stu-id="dc0fd-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="dc0fd-108"><a href="hololens-hardware-details.md">HoloLens (1-го поколения)</a></span><span class="sxs-lookup"><span data-stu-id="dc0fd-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="dc0fd-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dc0fd-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="dc0fd-110"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="dc0fd-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="dc0fd-111">Обнаружение QR-кода</span><span class="sxs-lookup"><span data-stu-id="dc0fd-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="dc0fd-112">️</span><span class="sxs-lookup"><span data-stu-id="dc0fd-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="dc0fd-113">✔️</span><span class="sxs-lookup"><span data-stu-id="dc0fd-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="dc0fd-114">✔️</span><span class="sxs-lookup"><span data-stu-id="dc0fd-114">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="dc0fd-115">Отслеживание QR-кодов с помощью впечатляющих головных телефонов Windows Mixed Reality на настольных компьютерах поддерживается в Windows 10 версии 2004 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-115">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="dc0fd-116">Используйте API Microsoft. Микседреалити. Кркодеватчер. support (), чтобы определить, поддерживается ли эта функция на текущем устройстве.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-116">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="dc0fd-117">Получение QR-пакета</span><span class="sxs-lookup"><span data-stu-id="dc0fd-117">Getting the QR package</span></span>
<span data-ttu-id="dc0fd-118">Пакет NuGet для обнаружения QR-кода можно скачать [здесь](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span><span class="sxs-lookup"><span data-stu-id="dc0fd-118">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="dc0fd-119">Обнаружение QR-кодов</span><span class="sxs-lookup"><span data-stu-id="dc0fd-119">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="dc0fd-120">Добавление возможности веб-камеры</span><span class="sxs-lookup"><span data-stu-id="dc0fd-120">Adding the webcam capability</span></span>
<span data-ttu-id="dc0fd-121">Для обнаружения QR-кодов необходимо добавить в `webcam` Манифест возможность.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-121">You will need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="dc0fd-122">Эта возможность необходима, так как данные в обнаруженных кодах в пользовательской среде могут содержать конфиденциальные сведения.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-122">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="dc0fd-123">Разрешение можно запросить, вызвав `QRCodeWatcher.RequestAccessAsync()` :</span><span class="sxs-lookup"><span data-stu-id="dc0fd-123">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="dc0fd-124">_См_</span><span class="sxs-lookup"><span data-stu-id="dc0fd-124">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="dc0fd-125">_C++_</span><span class="sxs-lookup"><span data-stu-id="dc0fd-125">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="dc0fd-126">Разрешение должно быть запрошено до создания объекта Кркодеватчер.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-126">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="dc0fd-127">Хотя для обнаружения QR-кодов требуется `webcam` возможность, обнаружение осуществляется с помощью камер отслеживания устройства.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-127">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="dc0fd-128">Это обеспечивает более широкое ФОВное обнаружение и повышает время работы аккумулятора по сравнению с обнаружением с помощью камеры устройства и видео (ПС).</span><span class="sxs-lookup"><span data-stu-id="dc0fd-128">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="dc0fd-129">Обнаружение QR-кодов в Unity</span><span class="sxs-lookup"><span data-stu-id="dc0fd-129">Detecting QR codes in Unity</span></span>

<span data-ttu-id="dc0fd-130">Вы можете использовать API обнаружения QR-кода в Unity, не принимая зависимость от МРТК.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-130">You can use the QR code detection API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="dc0fd-131">Для этого необходимо установить пакет NuGet с помощью [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="dc0fd-131">To do so, you must install the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>

<span data-ttu-id="dc0fd-132">Существует пример приложения Unity, которое отображает holographic-квадрат над QR-кодами вместе со связанными данными, такими как GUID, физический размер, метка времени и декодированные данные.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-132">There is a sample Unity app that displays a holographic square over QR codes, along with the associated data such as GUID, physical size, timestamp, and decoded data.</span></span> <span data-ttu-id="dc0fd-133">Это приложение можно найти по адресу https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes .</span><span class="sxs-lookup"><span data-stu-id="dc0fd-133">This app can be located at https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="dc0fd-134">Обнаружение QR-кодов в C++</span><span class="sxs-lookup"><span data-stu-id="dc0fd-134">Detecting QR codes in C++</span></span>

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="dc0fd-135">Получение системы координат для QR-кода</span><span class="sxs-lookup"><span data-stu-id="dc0fd-135">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="dc0fd-136">Каждый обнаруженный QR-код предоставляет [систему пространственных координат](coordinate-systems.md) , выравниваемая по левому краю в верхнем левом углу квадрата быстрого обнаружения, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-136">Each detected QR code exposes a [spatial coordinate system](coordinate-systems.md) aligned with the QR code at the top left corner of the fast detection square in the top left as seen below.</span></span>  <span data-ttu-id="dc0fd-137">При непосредственном использовании QR-пакета SDK ось Z указывает на бумагу (не показано) — при преобразовании в координаты Unity точки оси Z находятся за пределами бумаги и остаются в левой части.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-137">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="dc0fd-138">Спатиалкурдинатесистем QR-кода выстраивается так, как показано.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-138">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="dc0fd-139">Эта система координат может быть получена из платформы путем вызова <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">спатиалграфинтероппревиев:: креатекурдинатесистемфорноде</a> и передачи спатиалграфнодеид кода.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-139">This coordinate system can be obtained from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

![Система координат QR-кода](images/Qr-coordinatesystem.png) 

<span data-ttu-id="dc0fd-141">Для объекта Кркоде в следующем коде C++ показано, как создать прямоугольник и разместить его с помощью системы координат QR-кода:</span><span class="sxs-lookup"><span data-stu-id="dc0fd-141">For a QRCode object, the following C++ code shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="dc0fd-142">Для создания QR-прямоугольника можно использовать физический размер:</span><span class="sxs-lookup"><span data-stu-id="dc0fd-142">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="dc0fd-143">Систему координат можно использовать для рисования QR-кода или прикрепления голограмм к расположению:</span><span class="sxs-lookup"><span data-stu-id="dc0fd-143">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="dc0fd-144">В целом, ваш *кркодеаддедхандлер* может выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="dc0fd-144">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="dc0fd-145">Рекомендации по обнаружению QR-кода</span><span class="sxs-lookup"><span data-stu-id="dc0fd-145">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="dc0fd-146">Зоны без кавычек вокруг QR-кодов</span><span class="sxs-lookup"><span data-stu-id="dc0fd-146">Quiet zones around QR Codes</span></span>

<span data-ttu-id="dc0fd-147">Для правильного чтения QR-коды занимают поля вокруг всех сторон кода.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-147">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="dc0fd-148">Это поле не должно содержать ни одного печатного содержимого и должно состоять из четырех модулей (один черный квадрат в коде).</span><span class="sxs-lookup"><span data-stu-id="dc0fd-148">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="dc0fd-149">[QR-спецификация](https://www.qrcode.com/en/howto/code.html) содержит дополнительные сведения о зонах «тихий».</span><span class="sxs-lookup"><span data-stu-id="dc0fd-149">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="dc0fd-150">Освещение и фон</span><span class="sxs-lookup"><span data-stu-id="dc0fd-150">Lighting and backdrop</span></span>
<span data-ttu-id="dc0fd-151">Качество обнаружения QR-кодов является уязвимым для различных освещения и подложки.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-151">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="dc0fd-152">В сцене с особенно ярким освещением распечатайте черный цвет на сером фоне.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-152">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="dc0fd-153">В противном случае распечатайте черный QR-код на белом фоне.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-153">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="dc0fd-154">Если фон кода является особенно темным, попробуйте использовать черный цвет в сером коде, если частота обнаружения мала.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-154">If the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="dc0fd-155">Если подложка относительно легкая, то обычный код должен работать нормально.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-155">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="dc0fd-156">Размер QR-кодов</span><span class="sxs-lookup"><span data-stu-id="dc0fd-156">Size of QR codes</span></span>
<span data-ttu-id="dc0fd-157">Устройства Windows Mixed Reality не работают с QR-кодами с сторонами, меньшими 5 cm.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-157">Windows Mixed Reality devices do not work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="dc0fd-158">Для QR-кодов, которые находятся в диапазоне от 5 до 10 cm, вы должны быть достаточно близки для обнаружения кода.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-158">For QR codes between 5 and 10 cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="dc0fd-159">Для обнаружения кодов с таким размером также потребуется больше времени.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-159">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="dc0fd-160">Точное время на обнаружение кодов зависит не только от размера QR-кодов, но от того, на каком расстоянии у вас нет кода.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-160">The exact time to detect codes depends not only on the size of the QR codes, but how far you are away from the code.</span></span> <span data-ttu-id="dc0fd-161">Переход ближе к коду поможет в смещении проблем с размером.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-161">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="dc0fd-162">Расстояние и угловое расположение из QR-кода</span><span class="sxs-lookup"><span data-stu-id="dc0fd-162">Distance and angular position from the QR code</span></span>
<span data-ttu-id="dc0fd-163">Отслеживающие камеры могут обнаруживать только определенный уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-163">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="dc0fd-164">Для действительно небольших кодов — < 10cm вдоль сторон, вы должны быть достаточно близки.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-164">For really small codes - < 10cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="dc0fd-165">Для QR-кода версии 1, наличного от 10 до 25 сантиметров, минимальное расстояние обнаружения составляет от 0,15 метров до 0,5 метров.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-165">For a version 1 QR code varying from 10 to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="dc0fd-166">Расстояние обнаружения для размера увеличивается линейно.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-166">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="dc0fd-167">Обнаружение QR работает с диапазоном углов + = 45deg.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-167">QR detection works with a range of angles += 45deg.</span></span> <span data-ttu-id="dc0fd-168">Это необходимо для того, чтобы убедиться, что у нас есть правильное разрешение для обнаружения кода.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-168">This is to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="dc0fd-169">QR-коды с логотипами</span><span class="sxs-lookup"><span data-stu-id="dc0fd-169">QR codes with logos</span></span>
<span data-ttu-id="dc0fd-170">QR-коды с логотипами не тестировались и в настоящее время не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-170">QR codes with logos have not been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="dc0fd-171">Управление данными QR-кода</span><span class="sxs-lookup"><span data-stu-id="dc0fd-171">Managing QR code data</span></span>
<span data-ttu-id="dc0fd-172">Устройства Windows Mixed Reality обнаруживают QR-коды на уровне системы в драйвере.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-172">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="dc0fd-173">При перезагрузке устройства обнаруженные QR-коды исчезают и будут повторно обнаружены как новые объекты в следующий раз.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-173">When the device is rebooted, the detected QR codes are gone and will be re-detected as new objects next time.</span></span>

<span data-ttu-id="dc0fd-174">Рекомендуется настроить приложение так, чтобы оно игнорировало QR-коды старше определенной метки времени.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-174">It is recommended to configure your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="dc0fd-175">В настоящее время API не поддерживает очистку журнала QR-кода.</span><span class="sxs-lookup"><span data-stu-id="dc0fd-175">Currently, the API does not support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="dc0fd-176">Размещение QR-кода в пространстве</span><span class="sxs-lookup"><span data-stu-id="dc0fd-176">QR code placement in a space</span></span>
<span data-ttu-id="dc0fd-177">Рекомендации по расположению и способу размещения QR-кодов см. в статье [рекомендации по окружению для HoloLens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="dc0fd-177">For recommendations on where and how to place QR codes, please refer to [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="dc0fd-178">Справочник по QR-API</span><span class="sxs-lookup"><span data-stu-id="dc0fd-178">QR API reference</span></span>

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a><span data-ttu-id="dc0fd-179">См. также</span><span class="sxs-lookup"><span data-stu-id="dc0fd-179">See also</span></span>
* [<span data-ttu-id="dc0fd-180">Системы координат</span><span class="sxs-lookup"><span data-stu-id="dc0fd-180">Coordinate systems</span></span>](coordinate-systems.md)
* <span data-ttu-id="dc0fd-181"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a></span><span class="sxs-lookup"><span data-stu-id="dc0fd-181"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>
