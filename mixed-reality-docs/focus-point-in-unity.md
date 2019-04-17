---
title: Точку фокуса в Unity
description: Голограмма стабильность в Unity, установив точку фокуса, настраивать вручную
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, точку фокуса, фокус плоскости, стабилизации плоскости, стабилизации точка, reprojection, LSR, буфер глубины
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604883"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="e8d9e-104">Точку фокуса в Unity</span><span class="sxs-lookup"><span data-stu-id="e8d9e-104">Focus point in Unity</span></span>

<span data-ttu-id="e8d9e-105">**Пространство имен:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="e8d9e-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="e8d9e-106">**Тип**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="e8d9e-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="e8d9e-107">[Сосредоточиться точки](hologram-stability.md#stabilization-plane) может быть набор предоставить указание о том, как лучше всего выполнять стабилизации в настоящее время голограммы HoloLens отображение.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-107">The [focus point](hologram-stability.md#stabilization-plane) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="e8d9e-108">Если вы хотите установить точку фокуса в Unity, его необходимо задать каждого кадра с помощью *HolographicSettings.SetFocusPointForFrame()*.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="e8d9e-109">Если точку фокуса для кадра не установлен, будет использоваться плоскости стабилизации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="e8d9e-110">По умолчанию новые проекты Unity имеют параметр «Включить глубина буфера общий доступ».</span><span class="sxs-lookup"><span data-stu-id="e8d9e-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="e8d9e-111">В этом случае приложения Unity, выполняющихся на мощных настольных гарнитуры или HoloLens под управлением Windows 10 апреля 2018 г. обновление (RS4) или более поздней версии, передает в буфер глубины для Windows для оптимизации стабильности голограмма автоматически, без указания вашего приложения точку фокуса:</span><span class="sxs-lookup"><span data-stu-id="e8d9e-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="e8d9e-112">На мощных настольных гарнитуры это позволит reprojection основе глубины на пиксель.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="e8d9e-113">На HoloLens под управлением Windows 10 апреля 2018 г. обновление или более поздней версии, это будет анализировать буфер глубины автоматически выбрать оптимальное стабилизации плоскости.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="e8d9e-114">Любой из этих подходов должен предоставить еще лучше качество изображения без явных действий для приложения, чтобы выбрать точку фокуса каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="e8d9e-115">Учтите, что если вы вручную укажете точку фокуса, переопределит автоматическое поведение, описанное выше и обычно уменьшит голограмма стабильности.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="e8d9e-116">Как правило, необходимо указать только точку вручную фокуса при запуске приложения на HoloLens, который еще не был обновлен до Windows 10 апреля 2018 г. обновление.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="e8d9e-117">Пример</span><span class="sxs-lookup"><span data-stu-id="e8d9e-117">Example</span></span>

<span data-ttu-id="e8d9e-118">Существует много способов, чтобы задать точку фокуса по версии перегрузки, доступных на *SetFocusPointForFrame* статическая функция.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="e8d9e-119">Представленные ниже приведен простой пример присвоить плоскости фокус предоставленного объекта каждого кадра:</span><span class="sxs-lookup"><span data-stu-id="e8d9e-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

<span data-ttu-id="e8d9e-120">Обратите внимание, что приведенный выше код простой может оказаться уменьшение стабильность голограмма фокусом объекта заканчивается за пользователя.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="e8d9e-121">Именно поэтому обычно задавайте «Разрешить общий глубины буфер» вместо вручную указания точку фокуса.</span><span class="sxs-lookup"><span data-stu-id="e8d9e-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="e8d9e-122">См. также</span><span class="sxs-lookup"><span data-stu-id="e8d9e-122">See also</span></span>
* [<span data-ttu-id="e8d9e-123">Плоскость стабилизации</span><span class="sxs-lookup"><span data-stu-id="e8d9e-123">Stabilization plane</span></span>](hologram-stability.md#stabilization-plane)
