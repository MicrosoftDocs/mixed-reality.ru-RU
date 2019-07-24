---
title: Собственные объекты смешанной реальности в Unity
description: Получить доступ к базовым объектам holographic в Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, Mixed Reality, Native, ксрдевице, спатиалкурдинатесистем, холографикфраме, холографиккамера, испатиалкурдинатесистем, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942100"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="bddd1-104">Собственные объекты смешанной реальности в Unity</span><span class="sxs-lookup"><span data-stu-id="bddd1-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="bddd1-105">[Получение холографикспаце](getting-a-holographicspace.md) — это то, что делает каждое приложение смешанной реальности до того, как оно начнет получать данные камеры и кадры визуализации.</span><span class="sxs-lookup"><span data-stu-id="bddd1-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="bddd1-106">В Unity подсистема выполняет эти действия для вас, обрабатывая holographic и внутренне обновления в рамках цикла подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="bddd1-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="bddd1-107">Однако в сложных сценариях может потребоваться получить доступ к базовым собственным объектам, таким как <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">холографиккамера</a> и Current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a>.</span><span class="sxs-lookup"><span data-stu-id="bddd1-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="bddd1-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. ксрдевице</a> предоставляет доступ к этим собственным объектам.</span><span class="sxs-lookup"><span data-stu-id="bddd1-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="bddd1-109">ксрдевице</span><span class="sxs-lookup"><span data-stu-id="bddd1-109">XRDevice</span></span> 

<span data-ttu-id="bddd1-110">**Имен** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="bddd1-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="bddd1-111">**Тип** *ксрдевице*</span><span class="sxs-lookup"><span data-stu-id="bddd1-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="bddd1-112">Тип *ксрдевице* позволяет получить доступ к базовым машинным объектам с помощью метода <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">жетнативептр</a> .</span><span class="sxs-lookup"><span data-stu-id="bddd1-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="bddd1-113">Возвращаемые Жетнативептр различаются между различными платформами.</span><span class="sxs-lookup"><span data-stu-id="bddd1-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="bddd1-114">На универсальная платформа Windows при использовании пакета SDK XR для Windows Mixed Reality Ксрдевице. Жетнативептр возвращает указатель (IntPtr) в следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="bddd1-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="bddd1-115">Его можно преобразовать в Холографикфраменативедата с помощью метода Marshal. PtrToStructure нарушают:</span><span class="sxs-lookup"><span data-stu-id="bddd1-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="bddd1-116">***Ихолографиккамераптр** — это массив IntPtr, упакованный как UnmanagedType. ByValArray с длиной, равной макснумберофкамерас*</span><span class="sxs-lookup"><span data-stu-id="bddd1-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="bddd1-117">Использование Холографикфраменативедата</span><span class="sxs-lookup"><span data-stu-id="bddd1-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="bddd1-118">Изменение состояния собственных объектов, полученных через Холографикфраменативедата, может привести к непредсказуемому поведению и артефактам визуализации, особенно если Unity также является причиной того же состояния.</span><span class="sxs-lookup"><span data-stu-id="bddd1-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="bddd1-119">Например, не следует вызывать Холографикфраме. Упдатекуррентпредиктион, или, в противном случае прогнозирование, которое Unity визуализирует с этим кадром, будет не синхронизировано с объектом, который ожидается Windows, что снизит [стабильность](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="bddd1-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="bddd1-120">Вы можете использовать данные из Холографикфраменативедата, когда доступ к собственным интерфейсам требуется для подготовки к просмотру или отладке, в C# собственных подключаемых модулях или коде.</span><span class="sxs-lookup"><span data-stu-id="bddd1-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="bddd1-121">Ниже приведен пример того, как можно использовать Холографикфраменативедата для получения прогноза текущего кадра для времени Photon.</span><span class="sxs-lookup"><span data-stu-id="bddd1-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="bddd1-122">См. также</span><span class="sxs-lookup"><span data-stu-id="bddd1-122">See Also</span></span>
* <span data-ttu-id="bddd1-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">спатиалкурдинатесистем</a></span><span class="sxs-lookup"><span data-stu-id="bddd1-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="bddd1-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a></span><span class="sxs-lookup"><span data-stu-id="bddd1-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="bddd1-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="bddd1-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="bddd1-126">Отрисовка в DirectX</span><span class="sxs-lookup"><span data-stu-id="bddd1-126">Rendering in DirectX</span></span>](rendering-in-directx.md)
