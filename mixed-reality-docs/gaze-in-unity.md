---
title: Взгляните на Unity
description: Взгляд — это основной способ, с помощью которого пользователи могут ориентироваться на голограммы, создаваемые приложением в смешанной реальности.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: глаз — взгляд, голова, Unity, голограмма, Смешанная реальность
ms.openlocfilehash: 8222a5199cc1ea35429f21e7490e1eff49fcd1bc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435292"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="e1208-104">Головной взгляд в Unity</span><span class="sxs-lookup"><span data-stu-id="e1208-104">Head-gaze in Unity</span></span>

<span data-ttu-id="e1208-105">[Взгляд](gaze-and-commit.md) — это основной способ, с помощью которого пользователи могут ориентироваться на [голограммы](hologram.md) , создаваемые приложением в [смешанной реальности](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="e1208-105">[Gaze](gaze-and-commit.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="e1208-106">Реализация головного взгляда</span><span class="sxs-lookup"><span data-stu-id="e1208-106">Implementing head-gaze</span></span>

<span data-ttu-id="e1208-107">По сути, [элемент "Head-взгляд](gaze-and-commit.md) " реализуется путем проецирования луча из заголовка пользователя, где находится гарнитура, в прямом направлении и определяет, что луч конфликтует с.</span><span class="sxs-lookup"><span data-stu-id="e1208-107">Conceptually, [head-gaze](gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="e1208-108">В Unity расположение и направление головного пользователя предоставляются с помощью основной [камеры](camera-in-unity.md)Unity, в частности [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [преобразование. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) и [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Disposition](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="e1208-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="e1208-109">Вызов функции [физик. райкаст](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) приводит к [райкассит](https://docs.unity3d.com/ScriptReference/RaycastHit.html) структуре, содержащей сведения о конфликте, включая трехмерную точку, в которой произошел конфликт, а другая GameObjectа, с которой был получен элемент head-взгляда.</span><span class="sxs-lookup"><span data-stu-id="e1208-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="e1208-110">Пример: реализация Heading-взгляда</span><span class="sxs-lookup"><span data-stu-id="e1208-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="e1208-111">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="e1208-111">Best practices</span></span>

<span data-ttu-id="e1208-112">Хотя в приведенном выше примере показано, как выполнить одно райкаст в цикле обновления, чтобы найти целевые баллы пользователя, рекомендуется сделать это в одном объекте, управляющем Head-взглядом, а не делать это в любом объекте, который потенциально заинтересован в объекта t газед в.</span><span class="sxs-lookup"><span data-stu-id="e1208-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="e1208-113">Это позволяет приложению сохранять обработку, выполняя только один заголовок-взгляд, райкаст каждый кадр.</span><span class="sxs-lookup"><span data-stu-id="e1208-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="e1208-114">Визуализация головного взгляда</span><span class="sxs-lookup"><span data-stu-id="e1208-114">Visualizing head-gaze</span></span>

<span data-ttu-id="e1208-115">Точно так же, как и на рабочем столе, где используется указатель мыши для назначения и взаимодействия с содержимым, следует реализовать [курсор](cursors.md) , представляющий голову пользователя.</span><span class="sxs-lookup"><span data-stu-id="e1208-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="e1208-116">Это дает пользователю уверенность в том, с чем они взаимодействуют.</span><span class="sxs-lookup"><span data-stu-id="e1208-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="e1208-117">Руководитель-взгляд в наборе средств Mixed Reality версии 2</span><span class="sxs-lookup"><span data-stu-id="e1208-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="e1208-118">Вы можете получить доступ к Head с помощью [диспетчера ввода](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) в мртк v2.</span><span class="sxs-lookup"><span data-stu-id="e1208-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1208-119">См. также</span><span class="sxs-lookup"><span data-stu-id="e1208-119">See also</span></span>
* [<span data-ttu-id="e1208-120">Камера</span><span class="sxs-lookup"><span data-stu-id="e1208-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="e1208-121">Курсоры</span><span class="sxs-lookup"><span data-stu-id="e1208-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e1208-122">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="e1208-122">Head-gaze and commit</span></span>](gaze-and-commit.md)
