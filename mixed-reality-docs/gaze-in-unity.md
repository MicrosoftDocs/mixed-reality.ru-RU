---
title: Помощи в Unity
description: Взглядом — это основной способ для пользователей для нацеливания голограммы, создаваемые приложения в смешанной реальности.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: взглядом, unity, голограмма, смешанной реальности
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604803"
---
# <a name="gaze-in-unity"></a><span data-ttu-id="976fb-104">Помощи в Unity</span><span class="sxs-lookup"><span data-stu-id="976fb-104">Gaze in Unity</span></span>

<span data-ttu-id="976fb-105">[Помощи](gaze.md) является основным способом для пользователей для нацеливания [голограммы](hologram.md) ваше приложение создает в [смешанной реальности](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="976fb-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [mixed reality](mixed-reality.md).</span></span>

## <a name="implementing-gaze"></a><span data-ttu-id="976fb-106">Реализация взглядом</span><span class="sxs-lookup"><span data-stu-id="976fb-106">Implementing Gaze</span></span>

<span data-ttu-id="976fb-107">По существу [помощи](gaze.md) реализуется путем проецирования лучом, проведенным из головы пользователя, где гарнитуры, в прямом направлении их с выходом и определение, Рэй конфликтует с.</span><span class="sxs-lookup"><span data-stu-id="976fb-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="976fb-108">В Unity пользователя головной положения и направления, предоставляются с помощью Unity Main [камеры](camera-in-unity.md), в частности [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) и [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="976fb-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="976fb-109">Вызов [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) приводит [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) структуры, который содержит сведения о конфликтов, включая трехмерной точки, где возник конфликт и других GameObject луч взглядом со стенами вдоль.</span><span class="sxs-lookup"><span data-stu-id="976fb-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-gaze"></a><span data-ttu-id="976fb-110">Пример. Реализуйте взглядом</span><span class="sxs-lookup"><span data-stu-id="976fb-110">Example: Implement Gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="976fb-111">Советы и рекомендации</span><span class="sxs-lookup"><span data-stu-id="976fb-111">Best Practices</span></span>

<span data-ttu-id="976fb-112">Хотя в приведенном выше примере показано, как сделать один raycast, чтобы найти целевой взглядом цикл обновления, рекомендуется для этого в управлении взглядом вместо этого в любой объект, который потенциально заинтересовано в объекте gazed в один объект.</span><span class="sxs-lookup"><span data-stu-id="976fb-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="976fb-113">Это позволяет сохранить обработки, выполнив только один raycast взглядом каждого кадра приложения.</span><span class="sxs-lookup"><span data-stu-id="976fb-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="976fb-114">Визуализация взглядом</span><span class="sxs-lookup"><span data-stu-id="976fb-114">Visualizing Gaze</span></span>

<span data-ttu-id="976fb-115">Так же, как на рабочем столе, где использовать указатель мыши выбирать и взаимодействовать с содержимым, следует реализовать [курсор](cursors.md) , представляющий взглядом пользователя.</span><span class="sxs-lookup"><span data-stu-id="976fb-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="976fb-116">Это дает уверенность пользователей в том, что они сейчас взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="976fb-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit"></a><span data-ttu-id="976fb-117">Помощи в наборе средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="976fb-117">Gaze in Mixed Reality Toolkit</span></span>
<span data-ttu-id="976fb-118">При импорте [Unity пакеты выпуска MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) или клонируйте проект со страницы [репозиторий GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), нужно найти новое меню «Смешанной реальности Toolkit» в Unity.</span><span class="sxs-lookup"><span data-stu-id="976fb-118">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="976fb-119">В меню «Настройка» вы увидите меню «Применить смешанной реальности сцены параметры».</span><span class="sxs-lookup"><span data-stu-id="976fb-119">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="976fb-120">Если щелкнуть его, он удаляет камеры по умолчанию и добавляет основных компонентов — [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), и [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span><span class="sxs-lookup"><span data-stu-id="976fb-120">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="976fb-121">![Меню MRTK для установки сцены](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="976fb-121">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="976fb-122">*Меню MRTK для установки сцены*</span><span class="sxs-lookup"><span data-stu-id="976fb-122">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="976fb-123">![Настройка автоматического сцены в MRTK](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="976fb-123">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="976fb-124">*Настройка автоматического сцены в MRTK*</span><span class="sxs-lookup"><span data-stu-id="976fb-124">*Automatic scene setup in MRTK*</span></span>

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a><span data-ttu-id="976fb-125">Помощи связанные скрипты в смешанной реальности Toolkit</span><span class="sxs-lookup"><span data-stu-id="976fb-125">Gaze related scripts in Mixed Reality Toolkit</span></span>
<span data-ttu-id="976fb-126">Смешанный реальности Toolkit включает InputManager prefab [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) и [помощи стабилизатор](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span><span class="sxs-lookup"><span data-stu-id="976fb-126">Mixed Reality Toolkit's InputManager prefab includes [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) and [Gaze Stabilizer](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span></span> <span data-ttu-id="976fb-127">В разделе [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), можно назначить пользовательский курсор.</span><span class="sxs-lookup"><span data-stu-id="976fb-127">Under [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), you can assign your custom Cursor.</span></span> <span data-ttu-id="976fb-128">По умолчанию, анимировано [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) назначается.</span><span class="sxs-lookup"><span data-stu-id="976fb-128">In default, animated [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) is assigned.</span></span>

<span data-ttu-id="976fb-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) и [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) показано, как визуализировать ваш взглядом, использование курсоров.</span><span class="sxs-lookup"><span data-stu-id="976fb-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) and [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) shows you how to visualize your Gaze using Cursors.</span></span>

## <a name="see-also"></a><span data-ttu-id="976fb-130">См. также</span><span class="sxs-lookup"><span data-stu-id="976fb-130">See also</span></span>
* [<span data-ttu-id="976fb-131">Камера</span><span class="sxs-lookup"><span data-stu-id="976fb-131">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="976fb-132">Взглядом</span><span class="sxs-lookup"><span data-stu-id="976fb-132">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="976fb-133">Курсоры</span><span class="sxs-lookup"><span data-stu-id="976fb-133">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="976fb-134">Нацеливание взглядом</span><span class="sxs-lookup"><span data-stu-id="976fb-134">Gaze targeting</span></span>](gaze-targeting.md)
