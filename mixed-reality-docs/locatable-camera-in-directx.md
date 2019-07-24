---
title: Камера размещаемые в DirectX
description: Объясняется, как использовать камеру точки зрения (вид) в приложении HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, размещаемые камера, точка зрения, вид, унпорожект, Media Foundation, MF, пользовательский приемник, пошаговое руководство, пример кода
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516864"
---
# <a name="locatable-camera-in-directx"></a><span data-ttu-id="3b035-104">Камера размещаемые в DirectX</span><span class="sxs-lookup"><span data-stu-id="3b035-104">Locatable camera in DirectX</span></span>

<span data-ttu-id="3b035-105">В этом разделе описывается настройка конвейера [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) для доступа к [камере](locatable-camera.md) в приложении DirectX, включая метаданные кадра, позволяющие искать изображения, созданные в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="3b035-105">This topic describes how to set up a [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline to access the [camera](locatable-camera.md) in a DirectX app, including the frame metadata that will allow you to locate the images produced in the real world.</span></span>

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a><span data-ttu-id="3b035-106">Разработка Windows Media Capture и Media Foundation: имфаттрибутес</span><span class="sxs-lookup"><span data-stu-id="3b035-106">Windows Media Capture and Media Foundation Development: IMFAttributes</span></span>

<span data-ttu-id="3b035-107">Каждый кадр изображения [включает систему координат](locatable-camera.md#images-with-coordinate-systems) , а также два важных преобразования.</span><span class="sxs-lookup"><span data-stu-id="3b035-107">Each image frame [includes a coordinate system](locatable-camera.md#images-with-coordinate-systems) , as well as two important transforms.</span></span> <span data-ttu-id="3b035-108">Преобразование «Просмотр» сопоставляет из предоставленной системы координат с камерой, а «проекция» — от камеры к пикселям изображения.</span><span class="sxs-lookup"><span data-stu-id="3b035-108">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="3b035-109">Система координат и 2 преобразования внедряются в виде метаданных в каждый кадр изображения через [имфаттрибутес](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)Media Foundation.</span><span class="sxs-lookup"><span data-stu-id="3b035-109">The coordinate system and the 2 transforms are embedded as metadata in every image frame via Media Foundation's [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span></span>

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a><span data-ttu-id="3b035-110">Пример использования чтения атрибутов с помощью пользовательского приемника MF и проекции</span><span class="sxs-lookup"><span data-stu-id="3b035-110">Sample usage of reading attributes with MF custom sink and doing projection</span></span>

<span data-ttu-id="3b035-111">В пользовательском потоке приемника MF ([имфстреамсинк](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)) вы получите [имфсампле](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) с примерами атрибутов:</span><span class="sxs-lookup"><span data-stu-id="3b035-111">In your custom MF Sink stream ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), you will get [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) with sample attributes:</span></span>

<span data-ttu-id="3b035-112">Для кода на основе WinRT необходимо определить следующие Медиаекстенсионс:</span><span class="sxs-lookup"><span data-stu-id="3b035-112">The following MediaExtensions must be defined for WinRT based code:</span></span>

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

<span data-ttu-id="3b035-113">Доступ к этим атрибутам из API-интерфейсов WinRT невозможен, но требуется реализация расширения мультимедиа [имфтрансформ](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (для effect) или [имфмедиасинк](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) и [имфстреамсинк](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (для пользовательского приемника).</span><span class="sxs-lookup"><span data-stu-id="3b035-113">You can't access these attributes from WinRT APIs, but requires Media Extension implementation of [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (for Effect) or [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) and [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (for Custom Sink).</span></span> <span data-ttu-id="3b035-114">При обработке образца в этом расширении в [имфтрансформ::P роцессинпут ()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[имфтрансформ::P роцессаутпут ()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) или [имфстреамсинк::P роцесссампле ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)можно запрашивать атрибуты, подобные этому примеру.</span><span class="sxs-lookup"><span data-stu-id="3b035-114">When you process the sample in this extension either in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) or [IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), you can query attributes like this sample.</span></span>

```
ComPtr<IUnknown> spUnknown;
ComPtr<Windows::Perception::Spatial::ISpatialCoordinateSystem> spSpatialCoordinateSystem;
ComPtr<Windows::Foundation::IReference<Windows::Foundation::Numerics::Matrix4x4>> spTransformRef;
Windows::Foundation::Numerics::Matrix4x4 worldToCameraMatrix;
Windows::Foundation::Numerics::Matrix4x4 viewMatrix;
Windows::Foundation::Numerics::Matrix4x4 projectionMatrix;
UINT32 cbBlobSize = 0;
hr = pSample->GetUnknown(MFSampleExtension_Spatial_CameraCoordinateSystem, IID_PPV_ARGS(&spUnknown));
if (SUCCEEDED(hr))
{
    hr = spUnknown.As(&spSpatialCoordinateSystem);
    if (FAILED(hr))
    {
        return hr;
    }
    hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraViewTransform,
                          (UINT8*)(&viewMatrix),
                          sizeof(viewMatrix),
                          &cbBlobSize);
    if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
    {
        hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraProjectionTransform,
                              (UINT8*)(&projectionMatrix),
                              sizeof(projectionMatrix),
                              &cbBlobSize);
        if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
        {
            // Assume m_spCurrentCoordinateSystem is representing
            // world coordinate system application is using
            hr = m_spCurrentCoordinateSystem->TryGetTransformTo(spSpatialCoordinateSystem.Get(),
                                                                &spTransformRef);
            if (FAILED(hr))
            {
                return hr;
            }
            hr = spTransformRef->get_Value(&worldToCameraMatrix);
            if (FAILED(hr))
            {
                return hr;
            }
        }
    }
}
```

<span data-ttu-id="3b035-115">Для доступа к текстуре из камеры требуется устройство D3D, которое создает текстуру кадров камеры.</span><span class="sxs-lookup"><span data-stu-id="3b035-115">To access the texture from the camera, you need same D3D device which creates camera frame texture.</span></span> <span data-ttu-id="3b035-116">Это устройство D3D находится в [имфдксгидевицеманажер](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) конвейере захвата.</span><span class="sxs-lookup"><span data-stu-id="3b035-116">This D3D device is in [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in the capture pipeline.</span></span> <span data-ttu-id="3b035-117">Чтобы получить диспетчер устройств DXGI из записи мультимедиа, можно использовать интерфейсы [иадванцедмедиакаптуре](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) и [иадванцедмедиакаптуресеттингс](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) .</span><span class="sxs-lookup"><span data-stu-id="3b035-117">To get the DXGI Device manager from Media Capture you can use [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) and [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfaces.</span></span>

```
Microsoft::WRL::ComPtr<IAdvancedMediaCapture> spAdvancedMediaCapture;
Microsoft::WRL::ComPtr<IAdvancedMediaCaptureSettings> spAdvancedMediaCaptureSettings;
Microsoft::WRL::ComPtr<IMFDXGIDeviceManager> spDXGIDeviceManager;
// Assume mediaCapture is Windows::Media::Capture::MediaCapture and initialized
if (SUCCEEDED(((IUnknown *)(mediaCapture))->QueryInterface(IID_PPV_ARGS(&spAdvancedMediaCapture))))
{
    if (SUCCEEDED(spAdvancedMediaCapture->GetAdvancedMediaCaptureSettings(&spAdvancedMediaCaptureSettings)))
    {
        spAdvancedMediaCaptureSettings->GetDirectxDeviceManager(&spDXGIDeviceManager);
    }
}
```

<span data-ttu-id="3b035-118">Можно также включить ввод с помощью мыши и клавиатуры в качестве необязательных методов ввода для приложения Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3b035-118">You can also enable mouse and keyboard input as optional input methods for your Windows Mixed Reality app.</span></span> <span data-ttu-id="3b035-119">Это также может быть отличной функцией отладки для устройств, таких как HoloLens, и может быть предпочтительным для ввода данных пользователя в приложениях смешанной реальности, работающих в впечатляющих гарнитурах, подключенных к ПК.</span><span class="sxs-lookup"><span data-stu-id="3b035-119">This can also be a great debugging feature for devices such as HoloLens, and may be desirable for user input in mixed reality apps running in immersive headsets attached to PCs.</span></span>
