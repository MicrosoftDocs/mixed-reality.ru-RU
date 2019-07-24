---
title: Сохраняемость в Unity
description: Сохраняемость позволяет вашим пользователям закреплять отдельные голограммы или рабочую область, где бы они ни находились, а затем находить их позже, когда они заходят на несколько используемых приложений.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, сохраняемость, Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524789"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="aa472-104">Сохраняемость в Unity</span><span class="sxs-lookup"><span data-stu-id="aa472-104">Persistence in Unity</span></span>

<span data-ttu-id="aa472-105">**Имен** *UnityEngine. XR. WSA. сохраняемость*</span><span class="sxs-lookup"><span data-stu-id="aa472-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="aa472-106">**См** *ворлданчорсторе*</span><span class="sxs-lookup"><span data-stu-id="aa472-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="aa472-107">Ворлданчорсторе — это ключ к созданию более реалистичных возможностей, в которых голограммы остаются в конкретных реальных местах для экземпляров приложения.</span><span class="sxs-lookup"><span data-stu-id="aa472-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="aa472-108">Это позволяет пользователям закреплять отдельные голограммы или рабочую область, где бы они ни находились, а затем находить их позже, когда они заходят на несколько используемых приложений.</span><span class="sxs-lookup"><span data-stu-id="aa472-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="aa472-109">Сохранение голограмм в сеансах</span><span class="sxs-lookup"><span data-stu-id="aa472-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="aa472-110">Ворлданчорсторе позволит сохранить расположение Ворлданчор в сеансах.</span><span class="sxs-lookup"><span data-stu-id="aa472-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="aa472-111">Чтобы фактически сохранить голограммы в сеансах, необходимо отдельно отследить объекты gameobject, использующие определенную привязку.</span><span class="sxs-lookup"><span data-stu-id="aa472-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="aa472-112">Часто имеет смысл создать корневой элемент GameObject с привязкой к международному сопоставлению и иметь в нем голограммы, прикрепленные с помощью смещения локальной позиции.</span><span class="sxs-lookup"><span data-stu-id="aa472-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="aa472-113">Чтобы загрузить голограммы из предыдущих сеансов, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="aa472-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="aa472-114">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="aa472-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="aa472-115">Загрузка данных приложения, связанных с универсальной привязкой, которая предоставляет идентификатор универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="aa472-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="aa472-116">Загрузка универсальной привязки из идентификатора</span><span class="sxs-lookup"><span data-stu-id="aa472-116">Load a world anchor from its id</span></span>

<span data-ttu-id="aa472-117">Чтобы сохранить голограммы для будущих сеансов:</span><span class="sxs-lookup"><span data-stu-id="aa472-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="aa472-118">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="aa472-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="aa472-119">Сохранение универсальной привязки с указанием идентификатора</span><span class="sxs-lookup"><span data-stu-id="aa472-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="aa472-120">Сохранение данных приложения, связанных с привязкой мира, вместе с идентификатором</span><span class="sxs-lookup"><span data-stu-id="aa472-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="aa472-121">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="aa472-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="aa472-122">Мы будем захотеть сослаться на Ворлданчорсторе, чтобы мы узнали, что мы готовы к работе, когда нам нужно выполнить операцию.</span><span class="sxs-lookup"><span data-stu-id="aa472-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="aa472-123">Так как это асинхронный вызов, потенциально как только запускается, мы хотим вызвать</span><span class="sxs-lookup"><span data-stu-id="aa472-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="aa472-124">Сторелоадед в этом случае — наш обработчик для момента завершения загрузки Ворлданчорсторе:</span><span class="sxs-lookup"><span data-stu-id="aa472-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="aa472-125">Теперь у нас есть ссылка на Ворлданчорсторе, которую мы будем использовать для сохранения и загрузки конкретных привязок мира.</span><span class="sxs-lookup"><span data-stu-id="aa472-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="aa472-126">Сохранение Ворлданчор</span><span class="sxs-lookup"><span data-stu-id="aa472-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="aa472-127">Чтобы сохранить, нужно просто присвоить имя сохраненному и передать его в Ворлданчор, прежде чем мы хотим сохранить.</span><span class="sxs-lookup"><span data-stu-id="aa472-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="aa472-128">Примечание. попытка сохранить две привязки в одной строке завершится ошибкой (хранилище. При сохранении будет возвращено значение false.</span><span class="sxs-lookup"><span data-stu-id="aa472-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="aa472-129">Перед сохранением нового необходимо удалить предыдущее сохранение:</span><span class="sxs-lookup"><span data-stu-id="aa472-129">You need to Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="aa472-130">Загрузка Ворлданчор</span><span class="sxs-lookup"><span data-stu-id="aa472-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="aa472-131">И для загрузки:</span><span class="sxs-lookup"><span data-stu-id="aa472-131">And to load:</span></span>

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

<span data-ttu-id="aa472-132">Кроме того, можно использовать Store. Удалите (), чтобы удалить привязку, сохраненную ранее, и сохранить ее. Clear () для удаления всех ранее сохраненных данных.</span><span class="sxs-lookup"><span data-stu-id="aa472-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="aa472-133">Перечисление существующих привязок</span><span class="sxs-lookup"><span data-stu-id="aa472-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="aa472-134">Чтобы обнаружить ранее сохраненные привязки, вызовите Жеталлидс.</span><span class="sxs-lookup"><span data-stu-id="aa472-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="aa472-135">Сохранение голограмм для нескольких устройств</span><span class="sxs-lookup"><span data-stu-id="aa472-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="aa472-136"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания надежной облачной привязки на основе локальной ворлданчор, которая может быть размещена на нескольких устройствах HoloLens, iOS и Android, даже если эти устройства не находятся одновременно.</span><span class="sxs-lookup"><span data-stu-id="aa472-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="aa472-137">Так как облачные привязки являются постоянными, несколько устройств с течением времени могут видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="aa472-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="aa472-138">Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.</span><span class="sxs-lookup"><span data-stu-id="aa472-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="aa472-139">После завершения работы с пространственными привязками Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="aa472-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa472-140">См. также</span><span class="sxs-lookup"><span data-stu-id="aa472-140">See Also</span></span>
* [<span data-ttu-id="aa472-141">Сохраняемость пространственной привязки</span><span class="sxs-lookup"><span data-stu-id="aa472-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="aa472-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a></span><span class="sxs-lookup"><span data-stu-id="aa472-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="aa472-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Пакет SDK для пространственных привязок Azure для Unity</a></span><span class="sxs-lookup"><span data-stu-id="aa472-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
