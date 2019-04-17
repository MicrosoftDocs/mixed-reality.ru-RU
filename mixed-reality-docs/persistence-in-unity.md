---
title: Сохраняемость в Unity
description: Сохранение позволяет пользователям закрепить отдельные голограммы или в рабочей области, везде, где они хотят, а затем найдите, где они ожидают через многие применяется приложения.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, сохранение, Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605076"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="f2310-104">Сохраняемость в Unity</span><span class="sxs-lookup"><span data-stu-id="f2310-104">Persistence in Unity</span></span>

<span data-ttu-id="f2310-105">**Пространство имен:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="f2310-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="f2310-106">**Класс:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="f2310-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="f2310-107">WorldAnchorStore является ключом к возможности holographic, где голограммы оставаться в конкретных реальных позиций между экземплярами приложения.</span><span class="sxs-lookup"><span data-stu-id="f2310-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="f2310-108">Это позволяет пользователям закрепить отдельные голограммы или в рабочей области, везде, где они его, а затем найти его позже занимал через множество применений приложения.</span><span class="sxs-lookup"><span data-stu-id="f2310-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="f2310-109">Как сохранить голограммы во всех сеансах</span><span class="sxs-lookup"><span data-stu-id="f2310-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="f2310-110">WorldAnchorStore позволит вам сохранить расположение элемента WorldAnchor между сеансами.</span><span class="sxs-lookup"><span data-stu-id="f2310-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="f2310-111">Фактически сохранять голограммы между сеансами, необходимо будет отдельно хранить список ваши объекты Gameobject, используем привязку конкретного мира.</span><span class="sxs-lookup"><span data-stu-id="f2310-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="f2310-112">Часто имеет смысл создать корневой объект GameObject с привязкой world и иметь дочерние элементы голограммы привязаны его со смещением локальное положение.</span><span class="sxs-lookup"><span data-stu-id="f2310-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="f2310-113">Загрузка голограммы из предыдущих сеансов.</span><span class="sxs-lookup"><span data-stu-id="f2310-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="f2310-114">Получить WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f2310-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="f2310-115">Загрузка данных приложения, относящиеся к world привязки, который дает идентификатор привязки world</span><span class="sxs-lookup"><span data-stu-id="f2310-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="f2310-116">Загрузка из его идентификатор привязки world</span><span class="sxs-lookup"><span data-stu-id="f2310-116">Load a world anchor from its id</span></span>

<span data-ttu-id="f2310-117">Чтобы сохранить голограммы для будущих сеансов:</span><span class="sxs-lookup"><span data-stu-id="f2310-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="f2310-118">Получить WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f2310-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="f2310-119">Сохранить world привязки, указав идентификатор</span><span class="sxs-lookup"><span data-stu-id="f2310-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="f2310-120">Хранить данные приложений, относящиеся к привязки world вместе с идентификатором</span><span class="sxs-lookup"><span data-stu-id="f2310-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="f2310-121">Начало WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f2310-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="f2310-122">Будет необходимо хранить ссылку на WorldAnchorStore вокруг, поэтому мы знаем, что мы готовы перейти, если требуется выполнить операцию.</span><span class="sxs-lookup"><span data-stu-id="f2310-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="f2310-123">Поскольку это асинхронный вызов, потенциально сразу, как начало, мы хотим вызвать</span><span class="sxs-lookup"><span data-stu-id="f2310-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="f2310-124">В этом случае StoreLoaded — наш обработчик для WorldAnchorStore после завершения загрузки:</span><span class="sxs-lookup"><span data-stu-id="f2310-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="f2310-125">Теперь у нас есть ссылка WorldAnchorStore, который будет использоваться для сохранения и загрузки определенных World привязки.</span><span class="sxs-lookup"><span data-stu-id="f2310-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="f2310-126">Сохранение WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="f2310-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="f2310-127">Чтобы сохранить, нам просто нужно назвать что мы сохраняются и передать его в WorldAnchor, мы получили перед, когда требуется сохранить.</span><span class="sxs-lookup"><span data-stu-id="f2310-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="f2310-128">Примечание: при сохранении два якоря ту же строку завершится ошибкой (хранилище. Сохранение будет возвращать значение false).</span><span class="sxs-lookup"><span data-stu-id="f2310-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="f2310-129">Вам потребуется удалить предыдущие сохранения перед сохранением в новую.</span><span class="sxs-lookup"><span data-stu-id="f2310-129">You need to Delete the previous save before saving the new one:</span></span>

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="f2310-130">Загрузка WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="f2310-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="f2310-131">И для загрузки:</span><span class="sxs-lookup"><span data-stu-id="f2310-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="f2310-132">Кроме того, мы можем использовать хранилище. Delete() для удаления привязки, которые мы ранее сохранили и хранилище. Clear(), чтобы удалить все ранее сохраненные данные.</span><span class="sxs-lookup"><span data-stu-id="f2310-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="f2310-133">Перечисление существующих привязок</span><span class="sxs-lookup"><span data-stu-id="f2310-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="f2310-134">Чтобы найти ранее сохраненные привязки, вызовите GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="f2310-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="f2310-135">Сохранение голограммы для нескольких устройств</span><span class="sxs-lookup"><span data-stu-id="f2310-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="f2310-136">Можно использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a> для создания привязки надежные облачные из локального WorldAnchor, что приложение можно найти в нескольких HoloLens, iOS и устройств Android, даже если эти устройства не существуют друг с другом, в то же самое время.</span><span class="sxs-lookup"><span data-stu-id="f2310-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="f2310-137">Так как привязки облака являются постоянными, несколько устройств со временем может каждый см. в разделе содержимое отображается относительно эту привязку, в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="f2310-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="f2310-138">Чтобы приступить к работе, создания общих возможностей в Unity, изучите 5-минутные <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">краткие руководства по Azure пространственных привязки Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="f2310-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="f2310-139">После того, как приступить к работе с пространственными привязки Azure, вы можете затем <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создать и найдите привязки в Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="f2310-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2310-140">См. также</span><span class="sxs-lookup"><span data-stu-id="f2310-140">See Also</span></span>
* [<span data-ttu-id="f2310-141">Сохраняемость пространственных привязки</span><span class="sxs-lookup"><span data-stu-id="f2310-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="f2310-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure пространственных привязки</a></span><span class="sxs-lookup"><span data-stu-id="f2310-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="f2310-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure пространственных привязки пакета SDK для Unity</a></span><span class="sxs-lookup"><span data-stu-id="f2310-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
