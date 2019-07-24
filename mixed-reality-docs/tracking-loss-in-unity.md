---
title: Отслеживание потерь в Unity
description: Обработка потерь отслеживания в приложении Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, отслеживание потерь, отслеживание потерь изображения
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548742"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="9736d-104">Отслеживание потерь в Unity</span><span class="sxs-lookup"><span data-stu-id="9736d-104">Tracking loss in Unity</span></span>

<span data-ttu-id="9736d-105">Если устройство не может располагать себя в мире, в приложении происходит «отслеживание потерь».</span><span class="sxs-lookup"><span data-stu-id="9736d-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="9736d-106">По умолчанию Unity приостанавливает цикл обновления и отображает для пользователя изображение заставки.</span><span class="sxs-lookup"><span data-stu-id="9736d-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="9736d-107">Когда отслеживание восстанавливается, изображение-заставка исчезает, а цикл обновления продолжается.</span><span class="sxs-lookup"><span data-stu-id="9736d-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="9736d-108">В качестве альтернативы пользователь может вручную справиться с этим переходом, отменив параметр.</span><span class="sxs-lookup"><span data-stu-id="9736d-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="9736d-109">При отслеживании потерь все содержимое становится заблокированным, если не выполняется никаких действий по его обработке.</span><span class="sxs-lookup"><span data-stu-id="9736d-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="9736d-110">Обработка по умолчанию</span><span class="sxs-lookup"><span data-stu-id="9736d-110">Default Handling</span></span>

<span data-ttu-id="9736d-111">По умолчанию цикл обновления приложения, а также все сообщения и события будут прекращаться на время отслеживания потери.</span><span class="sxs-lookup"><span data-stu-id="9736d-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="9736d-112">В то же время для пользователя будет отображаться изображение.</span><span class="sxs-lookup"><span data-stu-id="9736d-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="9736d-113">Вы можете настроить этот образ, перейдя в меню "Правка"-> "Параметры" — > "проигрыватель", щелкнув изображение заставки и задав образ потери отслеживания с помощью.</span><span class="sxs-lookup"><span data-stu-id="9736d-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="9736d-114">Ручная обработка</span><span class="sxs-lookup"><span data-stu-id="9736d-114">Manual Handling</span></span>

<span data-ttu-id="9736d-115">Чтобы вручную обрабатывалась отслеживание потерь, необходимо вернуться к разделу **изменение** >  > **параметров проекта параметры** > **проигрывателя** > **универсальная платформа Windows параметры** **изображение заставки**  >  **Windows holographic** и снять флажок "при отслеживании потерь приостановить и показывать изображение".</span><span class="sxs-lookup"><span data-stu-id="9736d-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="9736d-116">После этого необходимо выполнить обработку изменений отслеживания с помощью API, указанных ниже.</span><span class="sxs-lookup"><span data-stu-id="9736d-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="9736d-117">**Имен** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="9736d-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="9736d-118">**Тип** *ворлдманажер*</span><span class="sxs-lookup"><span data-stu-id="9736d-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="9736d-119">Менеджер по всему миру предоставляет событие для обнаружения потерянных или полученных данных отслеживания (*ворлдманажер. онпоситионаллокаторстатечанжед*) и свойство для запроса текущего состояния (*ворлдманажер. State).*</span><span class="sxs-lookup"><span data-stu-id="9736d-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="9736d-120">Если отслеживание состояния неактивно, Камера не будет переводиться в виртуальном мире даже при преобразовании пользователя.</span><span class="sxs-lookup"><span data-stu-id="9736d-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="9736d-121">Это означает, что объекты больше не будут соответствовать ни одному физическому расположению, а все будут отображаться как заблокированные.</span><span class="sxs-lookup"><span data-stu-id="9736d-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="9736d-122">При обработке собственных изменений необходимо опросить свойство State для каждого кадра или обработать событие *онпоситионаллокаторстатечанжед* .</span><span class="sxs-lookup"><span data-stu-id="9736d-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="9736d-123">Опроса</span><span class="sxs-lookup"><span data-stu-id="9736d-123">Polling</span></span>

<span data-ttu-id="9736d-124">Наиболее важное состояние — *поситионаллокаторстате. Active* . Это означает, что отслеживание полностью работоспособно.</span><span class="sxs-lookup"><span data-stu-id="9736d-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="9736d-125">Любое другое состояние приведет к появлению в основной камере только ротации.</span><span class="sxs-lookup"><span data-stu-id="9736d-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="9736d-126">Пример:</span><span class="sxs-lookup"><span data-stu-id="9736d-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="9736d-127">Обработка события Онпоситионаллокаторстатечанжед</span><span class="sxs-lookup"><span data-stu-id="9736d-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="9736d-128">Кроме того, можно также подписываться на *онпоситионаллокаторстатечанжед* для выполнения переходов:</span><span class="sxs-lookup"><span data-stu-id="9736d-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="9736d-129">См. также</span><span class="sxs-lookup"><span data-stu-id="9736d-129">See also</span></span>
* [<span data-ttu-id="9736d-130">Обработка потерь отслеживания в DirectX</span><span class="sxs-lookup"><span data-stu-id="9736d-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
