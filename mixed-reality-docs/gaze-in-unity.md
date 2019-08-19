---
title: Взгляните на Unity
description: Взгляд — это основной способ, с помощью которого пользователи могут ориентироваться на голограммы, создаваемые приложением в смешанной реальности.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: взгляд, Unity, голограмма, Смешанная реальность
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453722"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="1e3b0-104">Головное взгляд в Unity</span><span class="sxs-lookup"><span data-stu-id="1e3b0-104">Head gaze in Unity</span></span>

<span data-ttu-id="1e3b0-105">[Взгляд](gaze.md) — это основной способ, с помощью которого пользователи могут ориентироваться на [голограммы](hologram.md), создаваемые приложением в [смешанной реальности](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="1e3b0-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="1e3b0-106">Реализация головного взгляда</span><span class="sxs-lookup"><span data-stu-id="1e3b0-106">Implementing head gaze</span></span>

<span data-ttu-id="1e3b0-107">По сути, [взгляд](gaze.md) реализуется путем проецирования луча из заголовка пользователя, где находится гарнитура, в прямом направлении и определяет, что луч конфликтует с.</span><span class="sxs-lookup"><span data-stu-id="1e3b0-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="1e3b0-108">В Unity расположение и направление головного пользователя предоставляются с помощью основной [камеры](camera-in-unity.md)Unity, в частности [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [преобразование. Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) и [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Disposition](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="1e3b0-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="1e3b0-109">Вызов функции [физик. райкаст](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) приводит к [райкассит](http://docs.unity3d.com/ScriptReference/RaycastHit.html) структуре, содержащей сведения о конфликте, включая трехмерную точку, в которой произошел конфликт, и другую GameObject, с которой был получен объект-Ray.</span><span class="sxs-lookup"><span data-stu-id="1e3b0-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="1e3b0-110">Пример. Реализация головного взгляда</span><span class="sxs-lookup"><span data-stu-id="1e3b0-110">Example: Implement head gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="1e3b0-111">Советы и рекомендации</span><span class="sxs-lookup"><span data-stu-id="1e3b0-111">Best Practices</span></span>

<span data-ttu-id="1e3b0-112">Хотя в приведенном выше примере показано, как выполнить одно райкаст в цикле обновления, чтобы найти целевой объект взгляда, рекомендуется сделать это в одном объекте, управляющем взвзглядом, а не делать это в любом объекте, который потенциально заинтересован в объекте, газед в.</span><span class="sxs-lookup"><span data-stu-id="1e3b0-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="1e3b0-113">Это позволяет приложению сохранять обработку, выполняя только один взгляд, райкаст каждый кадр.</span><span class="sxs-lookup"><span data-stu-id="1e3b0-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="1e3b0-114">Визуализация взгляда</span><span class="sxs-lookup"><span data-stu-id="1e3b0-114">Visualizing Gaze</span></span>

<span data-ttu-id="1e3b0-115">Как и на рабочем столе, где используется указатель мыши для назначения и взаимодействия с содержимым, следует реализовать [курсор](cursors.md) , который представляет взгляд пользователя.</span><span class="sxs-lookup"><span data-stu-id="1e3b0-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="1e3b0-116">Это дает пользователю уверенность в том, с чем они взаимодействуют.</span><span class="sxs-lookup"><span data-stu-id="1e3b0-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="1e3b0-117">Взгляните на набор средств Mixed Reality версии 2</span><span class="sxs-lookup"><span data-stu-id="1e3b0-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="1e3b0-118">Доступ к элементу управления "взгляд" можно получить из [диспетчера ввода](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) в мртк v2.</span><span class="sxs-lookup"><span data-stu-id="1e3b0-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e3b0-119">См. также</span><span class="sxs-lookup"><span data-stu-id="1e3b0-119">See also</span></span>
* [<span data-ttu-id="1e3b0-120">Камера</span><span class="sxs-lookup"><span data-stu-id="1e3b0-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="1e3b0-121">Входные данные взгляда</span><span class="sxs-lookup"><span data-stu-id="1e3b0-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="1e3b0-122">Курсоры</span><span class="sxs-lookup"><span data-stu-id="1e3b0-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="1e3b0-123">Нацеливание взглядом</span><span class="sxs-lookup"><span data-stu-id="1e3b0-123">Gaze targeting</span></span>](gaze-targeting.md)
