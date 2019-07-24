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
# <a name="locatable-camera-in-directx"></a>Камера размещаемые в DirectX

В этом разделе описывается настройка конвейера [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) для доступа к [камере](locatable-camera.md) в приложении DirectX, включая метаданные кадра, позволяющие искать изображения, созданные в реальном мире.

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Разработка Windows Media Capture и Media Foundation: имфаттрибутес

Каждый кадр изображения [включает систему координат](locatable-camera.md#images-with-coordinate-systems) , а также два важных преобразования. Преобразование «Просмотр» сопоставляет из предоставленной системы координат с камерой, а «проекция» — от камеры к пикселям изображения. Система координат и 2 преобразования внедряются в виде метаданных в каждый кадр изображения через [имфаттрибутес](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)Media Foundation.

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>Пример использования чтения атрибутов с помощью пользовательского приемника MF и проекции

В пользовательском потоке приемника MF ([имфстреамсинк](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)) вы получите [имфсампле](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) с примерами атрибутов:

Для кода на основе WinRT необходимо определить следующие Медиаекстенсионс:

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

Доступ к этим атрибутам из API-интерфейсов WinRT невозможен, но требуется реализация расширения мультимедиа [имфтрансформ](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (для effect) или [имфмедиасинк](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) и [имфстреамсинк](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (для пользовательского приемника). При обработке образца в этом расширении в [имфтрансформ::P роцессинпут ()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[имфтрансформ::P роцессаутпут ()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) или [имфстреамсинк::P роцесссампле ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)можно запрашивать атрибуты, подобные этому примеру.

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

Для доступа к текстуре из камеры требуется устройство D3D, которое создает текстуру кадров камеры. Это устройство D3D находится в [имфдксгидевицеманажер](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) конвейере захвата. Чтобы получить диспетчер устройств DXGI из записи мультимедиа, можно использовать интерфейсы [иадванцедмедиакаптуре](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) и [иадванцедмедиакаптуресеттингс](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) .

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

Можно также включить ввод с помощью мыши и клавиатуры в качестве необязательных методов ввода для приложения Windows Mixed Reality. Это также может быть отличной функцией отладки для устройств, таких как HoloLens, и может быть предпочтительным для ввода данных пользователя в приложениях смешанной реальности, работающих в впечатляющих гарнитурах, подключенных к ПК.
