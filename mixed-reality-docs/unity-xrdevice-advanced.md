---
title: Собственные объекты смешанной реальности в Unity
description: Получить доступ к базовым объектам holographic в Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, Mixed Reality, Native, ксрдевице, спатиалкурдинатесистем, холографикфраме, холографиккамера, испатиалкурдинатесистем, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 975775f64a19fe5fff4bc395a3e954cbf529dfa9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437334"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="ec30e-104">Собственные объекты смешанной реальности в Unity</span><span class="sxs-lookup"><span data-stu-id="ec30e-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="ec30e-105">[Получение холографикспаце](getting-a-holographicspace.md) — это то, что делает каждое приложение смешанной реальности до того, как оно начнет получать данные камеры и кадры визуализации.</span><span class="sxs-lookup"><span data-stu-id="ec30e-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="ec30e-106">В Unity подсистема выполняет эти действия для вас, обрабатывая holographic и внутренне обновления в рамках цикла подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="ec30e-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="ec30e-107">Однако в сложных сценариях может потребоваться получить доступ к базовым собственным объектам, таким как <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">холографиккамера</a> и Current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a>.</span><span class="sxs-lookup"><span data-stu-id="ec30e-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="ec30e-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. ксрдевице</a> предоставляет доступ к этим собственным объектам.</span><span class="sxs-lookup"><span data-stu-id="ec30e-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="ec30e-109">ксрдевице</span><span class="sxs-lookup"><span data-stu-id="ec30e-109">XRDevice</span></span> 

<span data-ttu-id="ec30e-110">**Пространство имен:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="ec30e-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="ec30e-111">**Тип:** *ксрдевице*</span><span class="sxs-lookup"><span data-stu-id="ec30e-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="ec30e-112">Тип *ксрдевице* позволяет получить доступ к базовым машинным объектам с помощью метода <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">жетнативептр</a> .</span><span class="sxs-lookup"><span data-stu-id="ec30e-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="ec30e-113">Возвращаемые Жетнативептр различаются между различными платформами.</span><span class="sxs-lookup"><span data-stu-id="ec30e-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="ec30e-114">На универсальная платформа Windows при использовании пакета SDK XR для Windows Mixed Reality Ксрдевице. Жетнативептр возвращает указатель (IntPtr) в следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="ec30e-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="ec30e-115">Его можно преобразовать в Холографикфраменативедата с помощью метода Marshal. PtrToStructure нарушают:</span><span class="sxs-lookup"><span data-stu-id="ec30e-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="ec30e-116">***Ихолографиккамераптр** — это массив IntPtr, упакованный как UnmanagedType. ByValArray с длиной, равной макснумберофкамерас*</span><span class="sxs-lookup"><span data-stu-id="ec30e-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="ec30e-117">Распаковка собственных указателей</span><span class="sxs-lookup"><span data-stu-id="ec30e-117">Unmarshaling native pointers</span></span>

<span data-ttu-id="ec30e-118">При использовании [Microsoft. Windows. микседреалити. дотнетвинрт](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) можно создать управляемый объект из собственного указателя с помощью метода `FromNativePtr()`:</span><span class="sxs-lookup"><span data-stu-id="ec30e-118">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

<span data-ttu-id="ec30e-119">В противном случае используйте `Marshal.GetObjectForIUnknown()` и приведите к желаемому типу:</span><span class="sxs-lookup"><span data-stu-id="ec30e-119">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the desired type:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="ec30e-120">Преобразование между системами координат</span><span class="sxs-lookup"><span data-stu-id="ec30e-120">Converting between coordinate systems</span></span>

<span data-ttu-id="ec30e-121">Unity использует левую систему координат, а API-интерфейсы восприятия Windows — для использования правильных систем координат.</span><span class="sxs-lookup"><span data-stu-id="ec30e-121">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="ec30e-122">Для преобразования между этими двумя соглашениями можно использовать следующие вспомогательные методы:</span><span class="sxs-lookup"><span data-stu-id="ec30e-122">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(-q.X, -q.Y, q.Z, q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(-q.x, -q.y, q.z, q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="ec30e-123">Использование собственных данных Холографикфраме</span><span class="sxs-lookup"><span data-stu-id="ec30e-123">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="ec30e-124">Изменение состояния собственных объектов, полученных через Холографикфраменативедата, может привести к непредсказуемому поведению и артефактам визуализации, особенно если Unity также является причиной того же состояния.</span><span class="sxs-lookup"><span data-stu-id="ec30e-124">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="ec30e-125">Например, не следует вызывать Холографикфраме. Упдатекуррентпредиктион, или, в противном случае прогнозирование, которое Unity визуализирует с этим кадром, будет не синхронизировано с объектом, который ожидается Windows, что снизит [стабильность](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="ec30e-125">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="ec30e-126">Вы можете использовать данные из Холографикфраменативедата, когда доступ к собственным интерфейсам требуется для подготовки к просмотру или отладке, в C# собственных подключаемых модулях или коде.</span><span class="sxs-lookup"><span data-stu-id="ec30e-126">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="ec30e-127">Ниже приведен пример того, как можно использовать Холографикфраменативедата для получения прогноза текущего кадра для времени Photon.</span><span class="sxs-lookup"><span data-stu-id="ec30e-127">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="ec30e-128">См. также</span><span class="sxs-lookup"><span data-stu-id="ec30e-128">See Also</span></span>
* [<span data-ttu-id="ec30e-129">Использование пространства имен Windows с приложениями Unity для HoloLens</span><span class="sxs-lookup"><span data-stu-id="ec30e-129">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="ec30e-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">спатиалкурдинатесистем</a></span><span class="sxs-lookup"><span data-stu-id="ec30e-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="ec30e-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a></span><span class="sxs-lookup"><span data-stu-id="ec30e-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="ec30e-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="ec30e-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="ec30e-133">Отрисовка в DirectX</span><span class="sxs-lookup"><span data-stu-id="ec30e-133">Rendering in DirectX</span></span>](rendering-in-directx.md)
