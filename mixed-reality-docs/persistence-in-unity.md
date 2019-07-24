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
# <a name="persistence-in-unity"></a>Сохраняемость в Unity

**Имен** *UnityEngine. XR. WSA. сохраняемость*<br>
**См** *ворлданчорсторе*

Ворлданчорсторе — это ключ к созданию более реалистичных возможностей, в которых голограммы остаются в конкретных реальных местах для экземпляров приложения. Это позволяет пользователям закреплять отдельные голограммы или рабочую область, где бы они ни находились, а затем находить их позже, когда они заходят на несколько используемых приложений.

## <a name="how-to-persist-holograms-across-sessions"></a>Сохранение голограмм в сеансах

Ворлданчорсторе позволит сохранить расположение Ворлданчор в сеансах. Чтобы фактически сохранить голограммы в сеансах, необходимо отдельно отследить объекты gameobject, использующие определенную привязку. Часто имеет смысл создать корневой элемент GameObject с привязкой к международному сопоставлению и иметь в нем голограммы, прикрепленные с помощью смещения локальной позиции.

Чтобы загрузить голограммы из предыдущих сеансов, выполните следующие действия.
1. Получение Ворлданчорсторе
2. Загрузка данных приложения, связанных с универсальной привязкой, которая предоставляет идентификатор универсальной привязки
3. Загрузка универсальной привязки из идентификатора

Чтобы сохранить голограммы для будущих сеансов:
1. Получение Ворлданчорсторе
2. Сохранение универсальной привязки с указанием идентификатора
3. Сохранение данных приложения, связанных с привязкой мира, вместе с идентификатором

### <a name="getting-the-worldanchorstore"></a>Получение Ворлданчорсторе

Мы будем захотеть сослаться на Ворлданчорсторе, чтобы мы узнали, что мы готовы к работе, когда нам нужно выполнить операцию. Так как это асинхронный вызов, потенциально как только запускается, мы хотим вызвать

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

Сторелоадед в этом случае — наш обработчик для момента завершения загрузки Ворлданчорсторе:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Теперь у нас есть ссылка на Ворлданчорсторе, которую мы будем использовать для сохранения и загрузки конкретных привязок мира.

### <a name="saving-a-worldanchor"></a>Сохранение Ворлданчор

Чтобы сохранить, нужно просто присвоить имя сохраненному и передать его в Ворлданчор, прежде чем мы хотим сохранить. Примечание. попытка сохранить две привязки в одной строке завершится ошибкой (хранилище. При сохранении будет возвращено значение false. Перед сохранением нового необходимо удалить предыдущее сохранение:

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

### <a name="loading-a-worldanchor"></a>Загрузка Ворлданчор

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

Кроме того, можно использовать Store. Удалите (), чтобы удалить привязку, сохраненную ранее, и сохранить ее. Clear () для удаления всех ранее сохраненных данных.

### <a name="enumerating-existing-anchors"></a>Перечисление существующих привязок

Чтобы обнаружить ранее сохраненные привязки, вызовите Жеталлидс.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Сохранение голограмм для нескольких устройств

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания надежной облачной привязки на основе локальной ворлданчор, которая может быть размещена на нескольких устройствах HoloLens, iOS и Android, даже если эти устройства не находятся одновременно.  Так как облачные привязки являются постоянными, несколько устройств с течением времени могут видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.

Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.

После завершения работы с пространственными привязками Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.

## <a name="see-also"></a>См. также
* [Сохраняемость пространственной привязки](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Пакет SDK для пространственных привязок Azure для Unity</a>
