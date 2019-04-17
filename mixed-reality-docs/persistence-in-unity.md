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
# <a name="persistence-in-unity"></a>Сохраняемость в Unity

**Пространство имен:** *UnityEngine.XR.WSA.Persistence*<br>
**Класс:** *WorldAnchorStore*

WorldAnchorStore является ключом к возможности holographic, где голограммы оставаться в конкретных реальных позиций между экземплярами приложения. Это позволяет пользователям закрепить отдельные голограммы или в рабочей области, везде, где они его, а затем найти его позже занимал через множество применений приложения.

## <a name="how-to-persist-holograms-across-sessions"></a>Как сохранить голограммы во всех сеансах

WorldAnchorStore позволит вам сохранить расположение элемента WorldAnchor между сеансами. Фактически сохранять голограммы между сеансами, необходимо будет отдельно хранить список ваши объекты Gameobject, используем привязку конкретного мира. Часто имеет смысл создать корневой объект GameObject с привязкой world и иметь дочерние элементы голограммы привязаны его со смещением локальное положение.

Загрузка голограммы из предыдущих сеансов.
1. Получить WorldAnchorStore
2. Загрузка данных приложения, относящиеся к world привязки, который дает идентификатор привязки world
3. Загрузка из его идентификатор привязки world

Чтобы сохранить голограммы для будущих сеансов:
1. Получить WorldAnchorStore
2. Сохранить world привязки, указав идентификатор
3. Хранить данные приложений, относящиеся к привязки world вместе с идентификатором

### <a name="getting-the-worldanchorstore"></a>Начало WorldAnchorStore

Будет необходимо хранить ссылку на WorldAnchorStore вокруг, поэтому мы знаем, что мы готовы перейти, если требуется выполнить операцию. Поскольку это асинхронный вызов, потенциально сразу, как начало, мы хотим вызвать

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

В этом случае StoreLoaded — наш обработчик для WorldAnchorStore после завершения загрузки:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Теперь у нас есть ссылка WorldAnchorStore, который будет использоваться для сохранения и загрузки определенных World привязки.

### <a name="saving-a-worldanchor"></a>Сохранение WorldAnchor

Чтобы сохранить, нам просто нужно назвать что мы сохраняются и передать его в WorldAnchor, мы получили перед, когда требуется сохранить. Примечание: при сохранении два якоря ту же строку завершится ошибкой (хранилище. Сохранение будет возвращать значение false). Вам потребуется удалить предыдущие сохранения перед сохранением в новую.

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

### <a name="loading-a-worldanchor"></a>Загрузка WorldAnchor

И для загрузки:

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

Кроме того, мы можем использовать хранилище. Delete() для удаления привязки, которые мы ранее сохранили и хранилище. Clear(), чтобы удалить все ранее сохраненные данные.

### <a name="enumerating-existing-anchors"></a>Перечисление существующих привязок

Чтобы найти ранее сохраненные привязки, вызовите GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Сохранение голограммы для нескольких устройств

Можно использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a> для создания привязки надежные облачные из локального WorldAnchor, что приложение можно найти в нескольких HoloLens, iOS и устройств Android, даже если эти устройства не существуют друг с другом, в то же самое время.  Так как привязки облака являются постоянными, несколько устройств со временем может каждый см. в разделе содержимое отображается относительно эту привязку, в том же физическом расположении.

Чтобы приступить к работе, создания общих возможностей в Unity, изучите 5-минутные <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">краткие руководства по Azure пространственных привязки Unity</a>.

После того, как приступить к работе с пространственными привязки Azure, вы можете затем <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создать и найдите привязки в Unity</a>.

## <a name="see-also"></a>См. также
* [Сохраняемость пространственных привязки](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure пространственных привязки</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure пространственных привязки пакета SDK для Unity</a>
