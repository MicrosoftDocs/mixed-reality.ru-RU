---
title: Смешанной реальности собственных объектов в Unity
description: Получите доступ к Holographic собственных объектов в Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, смешанный реальность, машинный код, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942100"
---
# <a name="mixed-reality-native-objects-in-unity"></a>Смешанной реальности собственных объектов в Unity

[Начало HolographicSpace](getting-a-holographicspace.md) — каждые смешанной реальности, приложение выполняет перед началом получения данных камеры и отрисовки кадров. В Unity ядро берет на себя эти действия для вас обработки Holographic объектов и обновляет внутренне, как часть его цикл прорисовки.

Однако в более сложных сценариях может потребоваться получить доступ к собственных объектов, таких как <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> и текущих <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> именно это и обеспечивает доступ к этим объектам собственного.

## <a name="xrdevice"></a>XRDevice 

**Пространство имен:** *UnityEngine.XR*<br>
**Тип:** *XRDevice*

*XRDevice* тип позволяет получить доступ к собственных объектов с помощью <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> метод. Возвращает GetNativePtr различается для разных платформ. В универсальной Windows платформы, при разработке для Windows SDK XR смешанной реальности XRDevice.GetNativePtr возвращается указатель (IntPtr) со следующей структурой: 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
Его можно преобразовать с помощью метода Marshal.PtrToStructure HolographicFrameNativeData:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** представляет собой массив IntPtr, маршалирован как UnmanagedType.ByValArray с длиной, равной MaxNumberOfCameras* 


### <a name="using-holographicframenativedata"></a>С помощью HolographicFrameNativeData

> [!NOTE]
> Изменение состояния для собственных объектов, полученных в ходе HolographicFrameNativeData может вызвать непредсказуемое поведение и артефакты отрисовки, особенно в том случае, если Unity также причинам об этом же состоянии.  Например, не следует вызывать HolographicFrame.UpdateCurrentPrediction, иначе поза прогноза, который Unity при отображении этого кадра будет синхронизирован с поза, ожидающей Windows, это позволит снизить [голограмма стабильность](hologram-stability.md).

Если необходим доступ для собственных интерфейсов для отрисовки или отладки в ваши собственные подключаемые модули можно использовать данные из HolographicFrameNativeData или C# кода. 

Ниже приведен пример того, как можно использовать для получения текущего кадра прогноз для времени photon HolographicFrameNativeData. 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a>См. также
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Отрисовка в DirectX](rendering-in-directx.md)
