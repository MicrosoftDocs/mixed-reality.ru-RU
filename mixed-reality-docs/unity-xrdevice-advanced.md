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
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="f4aba-104">Смешанной реальности собственных объектов в Unity</span><span class="sxs-lookup"><span data-stu-id="f4aba-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="f4aba-105">[Начало HolographicSpace](getting-a-holographicspace.md) — каждые смешанной реальности, приложение выполняет перед началом получения данных камеры и отрисовки кадров.</span><span class="sxs-lookup"><span data-stu-id="f4aba-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="f4aba-106">В Unity ядро берет на себя эти действия для вас обработки Holographic объектов и обновляет внутренне, как часть его цикл прорисовки.</span><span class="sxs-lookup"><span data-stu-id="f4aba-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="f4aba-107">Однако в более сложных сценариях может потребоваться получить доступ к собственных объектов, таких как <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> и текущих <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span><span class="sxs-lookup"><span data-stu-id="f4aba-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="f4aba-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> именно это и обеспечивает доступ к этим объектам собственного.</span><span class="sxs-lookup"><span data-stu-id="f4aba-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="f4aba-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="f4aba-109">XRDevice</span></span> 

<span data-ttu-id="f4aba-110">**Пространство имен:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="f4aba-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="f4aba-111">**Тип:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="f4aba-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="f4aba-112">*XRDevice* тип позволяет получить доступ к собственных объектов с помощью <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> метод.</span><span class="sxs-lookup"><span data-stu-id="f4aba-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="f4aba-113">Возвращает GetNativePtr различается для разных платформ.</span><span class="sxs-lookup"><span data-stu-id="f4aba-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="f4aba-114">В универсальной Windows платформы, при разработке для Windows SDK XR смешанной реальности XRDevice.GetNativePtr возвращается указатель (IntPtr) со следующей структурой:</span><span class="sxs-lookup"><span data-stu-id="f4aba-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="f4aba-115">Его можно преобразовать с помощью метода Marshal.PtrToStructure HolographicFrameNativeData:</span><span class="sxs-lookup"><span data-stu-id="f4aba-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="f4aba-116">***IHolographicCameraPtr** представляет собой массив IntPtr, маршалирован как UnmanagedType.ByValArray с длиной, равной MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="f4aba-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="f4aba-117">С помощью HolographicFrameNativeData</span><span class="sxs-lookup"><span data-stu-id="f4aba-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="f4aba-118">Изменение состояния для собственных объектов, полученных в ходе HolographicFrameNativeData может вызвать непредсказуемое поведение и артефакты отрисовки, особенно в том случае, если Unity также причинам об этом же состоянии.</span><span class="sxs-lookup"><span data-stu-id="f4aba-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="f4aba-119">Например, не следует вызывать HolographicFrame.UpdateCurrentPrediction, иначе поза прогноза, который Unity при отображении этого кадра будет синхронизирован с поза, ожидающей Windows, это позволит снизить [голограмма стабильность](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="f4aba-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="f4aba-120">Если необходим доступ для собственных интерфейсов для отрисовки или отладки в ваши собственные подключаемые модули можно использовать данные из HolographicFrameNativeData или C# кода.</span><span class="sxs-lookup"><span data-stu-id="f4aba-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="f4aba-121">Ниже приведен пример того, как можно использовать для получения текущего кадра прогноз для времени photon HolographicFrameNativeData.</span><span class="sxs-lookup"><span data-stu-id="f4aba-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="f4aba-122">См. также</span><span class="sxs-lookup"><span data-stu-id="f4aba-122">See Also</span></span>
* <span data-ttu-id="f4aba-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="f4aba-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="f4aba-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="f4aba-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="f4aba-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="f4aba-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="f4aba-126">Отрисовка в DirectX</span><span class="sxs-lookup"><span data-stu-id="f4aba-126">Rendering in DirectX</span></span>](rendering-in-directx.md)
