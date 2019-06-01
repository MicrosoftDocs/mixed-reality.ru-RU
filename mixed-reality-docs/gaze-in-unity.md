---
title: Помощи в Unity
description: Взглядом — это основной способ для пользователей для нацеливания голограммы, создаваемые приложения в смешанной реальности.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: взглядом, unity, голограмма, смешанной реальности
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453722"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="55211-104">Взглядом HEAD в Unity</span><span class="sxs-lookup"><span data-stu-id="55211-104">Head gaze in Unity</span></span>

<span data-ttu-id="55211-105">[Помощи](gaze.md) является основным способом для пользователей для нацеливания [голограммы](hologram.md) ваше приложение создает в [смешанной реальности](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="55211-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="55211-106">Реализации головной взглядом</span><span class="sxs-lookup"><span data-stu-id="55211-106">Implementing head gaze</span></span>

<span data-ttu-id="55211-107">По существу [помощи](gaze.md) реализуется путем проецирования лучом, проведенным из головы пользователя, где гарнитуры, в прямом направлении их с выходом и определение, Рэй конфликтует с.</span><span class="sxs-lookup"><span data-stu-id="55211-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="55211-108">В Unity пользователя головной положения и направления, предоставляются с помощью Unity Main [камеры](camera-in-unity.md), в частности [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) и [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="55211-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="55211-109">Вызов [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) приводит [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) структуры, который содержит сведения о конфликтов, включая трехмерной точки, где возник конфликт и других GameObject луч взглядом со стенами вдоль.</span><span class="sxs-lookup"><span data-stu-id="55211-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="55211-110">Пример. Реализуйте головной взглядом</span><span class="sxs-lookup"><span data-stu-id="55211-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="55211-111">Советы и рекомендации</span><span class="sxs-lookup"><span data-stu-id="55211-111">Best Practices</span></span>

<span data-ttu-id="55211-112">Хотя в приведенном выше примере показано, как сделать один raycast, чтобы найти целевой взглядом цикл обновления, рекомендуется для этого в управлении взглядом вместо этого в любой объект, который потенциально заинтересовано в объекте gazed в один объект.</span><span class="sxs-lookup"><span data-stu-id="55211-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="55211-113">Это позволяет сохранить обработки, выполнив только один raycast взглядом каждого кадра приложения.</span><span class="sxs-lookup"><span data-stu-id="55211-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="55211-114">Визуализация взглядом</span><span class="sxs-lookup"><span data-stu-id="55211-114">Visualizing Gaze</span></span>

<span data-ttu-id="55211-115">Так же, как на рабочем столе, где использовать указатель мыши выбирать и взаимодействовать с содержимым, следует реализовать [курсор](cursors.md) , представляющий взглядом пользователя.</span><span class="sxs-lookup"><span data-stu-id="55211-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="55211-116">Это дает уверенность пользователей в том, что они сейчас взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="55211-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="55211-117">Помощи в смешанной реальности Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="55211-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="55211-118">Вы можете получить доступ к взглядом из [ввода Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) в MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="55211-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="55211-119">См. также</span><span class="sxs-lookup"><span data-stu-id="55211-119">See also</span></span>
* [<span data-ttu-id="55211-120">Камера</span><span class="sxs-lookup"><span data-stu-id="55211-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="55211-121">Отслеживание взгляда</span><span class="sxs-lookup"><span data-stu-id="55211-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="55211-122">Курсоры</span><span class="sxs-lookup"><span data-stu-id="55211-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="55211-123">Нацеливание взглядом</span><span class="sxs-lookup"><span data-stu-id="55211-123">Gaze targeting</span></span>](gaze-targeting.md)
