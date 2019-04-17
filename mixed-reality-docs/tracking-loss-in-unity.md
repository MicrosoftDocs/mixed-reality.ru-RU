---
title: Отслеживание потери в Unity
description: Обработка отслеживание потери в приложении Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, отслеживание потери, отслеживание потери образа
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602769"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="55682-104">Отслеживание потери в Unity</span><span class="sxs-lookup"><span data-stu-id="55682-104">Tracking loss in Unity</span></span>

<span data-ttu-id="55682-105">Если устройство не может найти сам в мире, приложение интерфейсы «отслеживания потери».</span><span class="sxs-lookup"><span data-stu-id="55682-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="55682-106">По умолчанию Unity Приостановка цикла обновления и отображаемое изображение заставки для пользователя.</span><span class="sxs-lookup"><span data-stu-id="55682-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="55682-107">Когда отслеживания, освобождается, изображение заставки исчезает и продолжает цикла обновления.</span><span class="sxs-lookup"><span data-stu-id="55682-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="55682-108">Кроме того пользователь может вручную обрабатывать этот переход, отказавшись от параметра.</span><span class="sxs-lookup"><span data-stu-id="55682-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="55682-109">Все содержимое будет казаться, что в качестве текста во время отслеживания потери в случае, если ничего не происходит его обработать.</span><span class="sxs-lookup"><span data-stu-id="55682-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="55682-110">Обработка по умолчанию</span><span class="sxs-lookup"><span data-stu-id="55682-110">Default Handling</span></span>

<span data-ttu-id="55682-111">По умолчанию в течение отслеживание потери перестанет цикла обновления приложения, а также все сообщения и события.</span><span class="sxs-lookup"><span data-stu-id="55682-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="55682-112">Одновременно изображение будет отображаться для пользователя.</span><span class="sxs-lookup"><span data-stu-id="55682-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="55682-113">Этот образ можно настроить, открыв для редактирования "->" Параметры "->" Player, нужно щелкнуть изображение заставки и задание Holographic отслеживание потери изображения.</span><span class="sxs-lookup"><span data-stu-id="55682-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="55682-114">Обработка вручную</span><span class="sxs-lookup"><span data-stu-id="55682-114">Manual Handling</span></span>

<span data-ttu-id="55682-115">Чтобы вручную обрабатывать потерю отслеживания, необходимо перейти к **изменить** > **параметры проекта** > **проигрывателя**  >   **Вкладка параметров универсальной платформы Windows** > **изображение заставки** > **Windows Holographic** и снимите флажок «на отслеживание потери Pause и Показать изображение ".</span><span class="sxs-lookup"><span data-stu-id="55682-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="55682-116">После этого вам нужно обрабатывать отслеживание изменений с помощью интерфейсов API, указанных ниже.</span><span class="sxs-lookup"><span data-stu-id="55682-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="55682-117">**Пространство имен:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="55682-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="55682-118">**Тип:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="55682-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="55682-119">Мир Manager предоставляет событие для обнаружения, отслеживания потери/положены (*WorldManager.OnPositionalLocatorStateChanged*) и свойство, чтобы запрашивать текущее состояние (*WorldManager.state*)</span><span class="sxs-lookup"><span data-stu-id="55682-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="55682-120">Когда состояние отслеживания не активен, для преобразования в виртуальный мир, даже если пользователь переводит не появится камеры.</span><span class="sxs-lookup"><span data-stu-id="55682-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="55682-121">Это означает, что объекты больше не будет соответствовать любое физическое расположение и все будет отображаться текст заблокирован.</span><span class="sxs-lookup"><span data-stu-id="55682-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="55682-122">При обработке отслеживание изменений на собственные вы либо требуется проводить опрос свойстве state каждый кадр или дескриптор *OnPositionalLocatorStateChanged* событий.</span><span class="sxs-lookup"><span data-stu-id="55682-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="55682-123">опрос</span><span class="sxs-lookup"><span data-stu-id="55682-123">Polling</span></span>

<span data-ttu-id="55682-124">Наиболее важным состояние *PositionalLocatorState.Active* означающее отслеживания будут обладать полной функциональностью.</span><span class="sxs-lookup"><span data-stu-id="55682-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="55682-125">Любое другое состояние произойдет только вращения «дельты» на главной камеры.</span><span class="sxs-lookup"><span data-stu-id="55682-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="55682-126">Пример:</span><span class="sxs-lookup"><span data-stu-id="55682-126">For example:</span></span>

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="55682-127">Обработка события OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="55682-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="55682-128">Можно также и более удобным, вы также можете подписаться на *OnPositionalLocatorStateChanged* для обработки переходов:</span><span class="sxs-lookup"><span data-stu-id="55682-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="55682-129">См. также</span><span class="sxs-lookup"><span data-stu-id="55682-129">See also</span></span>
* [<span data-ttu-id="55682-130">Обработка отслеживание потери в DirectX</span><span class="sxs-lookup"><span data-stu-id="55682-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
