---
title: Системы координат в Unity
description: Сведения о создании за кресло репутацию комнаты и масштабирования смешении и мир и масштабирования интерфейсов реальности в Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: системы координат, пространственные системы координат, только для ориентации, установки и масштабирования, положение и масштабирования, места и масштабирования, всему миру и масштабирования, сидели 360 градусов, положение, номере, всему миру, масштаб, позиции, ориентации, Unity, привязки, пространственных привязки, привязки к всему миру, заблокированы в мире, Блокировка в мире, заблокирован для текста, текст блокировки, отслеживания потери, locatability, границы, центровку
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605053"
---
# <a name="coordinate-systems-in-unity"></a>Системы координат в Unity

Смешанная реальность Windows поддерживает приложения для широкого диапазона из [возникнуть шкал](coordinate-systems.md), из приложений только для ориентации и сидели масштабирования вверх через комнаты масштабируемых приложений. На HoloLens можно пойти дальше и создавать world масштабируемых приложений, позволяющих пользователям пройти за 5 м изучение всей этаж здания и за ее пределами.

Является первым шагом в создании более возможности смешанной реальности в Unity, чтобы определить, какие [возможности масштабирования](coordinate-systems.md) будет работать ваше приложение.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Построение интерфейс только для ориентации или установки и масштабирования

**Пространство имен:** *UnityEngine.XR*<br>
**Тип:** *XRDevice*

Для создания **только для ориентации** или **сидели высококлассные возможности**, необходимо задать Unity бланк отслеживания тип пространства. Этот параметр задает Unity мировая система координат для отслеживания [стационарной системой отсчета координат](coordinate-systems.md#spatial-coordinate-systems). В режиме отслеживания неподвижным, содержимое помещено в редакторе перед камерой расположение по умолчанию (вперед -Z) будет отображаться перед пользователем, при запуске приложения.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Пространство имен:** *UnityEngine.XR*<br>
**Тип:** *InputTracking*

Для чистого **только для ориентации интерфейс** например характеристиках видео средства просмотра, (где позиционные обновления головного бы разрушить иллюзию), затем можно задать [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) значение true:

```cs
InputTracking.disablePositionalTracking = true;
```

Для **сидели высококлассные возможности**, чтобы пользователи могли позже центровку за кресло источника, можно вызвать [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) метод:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Фиксированный масштаб или масштаб комнаты качества построения

**Пространство имен:** *UnityEngine.XR*<br>
**Тип:** *XRDevice*

Для **положение шкалы** или **комнаты высококлассные возможности**, вам потребуется разместить содержимое относительно ближайшее снизу целое. Обсуждения пользователя floor с помощью  **[пространственных этап](coordinate-systems.md#spatial-coordinate-systems)**, который представляет пользователя определенные полу источника и границ необязательно комнаты, заданный во время первого запуска.

Чтобы убедиться, что Unity работает с мировая система координат на уровне floor, можно присвоить Unity RoomScale, отслеживание типа пространство и убедитесь, что набор выполняется успешно:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* Если SetTrackingSpaceType возвращает значение true, мировая система координат для отслеживания успешно переключился Unity [этап подразумевает](coordinate-systems.md#spatial-coordinate-systems).
* Если SetTrackingSpaceType возвращает false, Unity не удалось переключиться на этапе отсчета, скорее всего, поскольку пользователь не установил даже этаж в своей среде. Это не часто, но также может произойти, если в рабочей области были настроены в другой комнате и устройства был перемещен в текущего места без пользователь, настраивающий новый этап.

После приложения успешно задает RoomScale, отслеживания тип пространства, содержимого уделено y = 0, плоскость появятся в ближайшее снизу целое. Исходный объект на (0, 0, 0) будет определенное место в процессе установки, где пользователь стояли во время установки комнате с -Z, представляющая вперед, которые они были с выходом во время установки.

**Пространство имен:** *UnityEngine.Experimental.XR*<br>
**Тип:** *Границ*

В коде скрипта можно вызов метода TryGetGeometry на вы будете типа UnityEngine.Experimental.XR.Boundary многоугольника границ, задание типа TrackedArea границ. Если определяемый пользователем границе (можно вернуть список вершин), вы знаете, безопасно доставлять **комнаты высококлассные возможности** для пользователя, где они могут помочь вокруг сцены создать.

Обратите внимание на то, система автоматически будет отображать границу пользователя приближается к его. Приложения не нужно использовать для подготовки к просмотру самой границе этого многоугольника. Тем не менее вы можете разместить объекты сцены с помощью этого многоугольника границ, чтобы убедиться, что пользователь физически имеет доступ к этим объектам без teleporting:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Создание более world высококлассные возможности

**Пространство имен:** *UnityEngine.XR.WSA*<br>
**Тип:** *WorldAnchor*

Для значения верно **world высококлассные возможности** на HoloLens, с помощью которых пользователи перемещаются за пределы 5 м, вам потребуется новые методики, помимо тех, которые используются для работы в комнате и масштабирования. Один ключевой метод, вы будете использовать, — для создания [пространственных привязки](coordinate-systems.md#spatial-anchors) заблокировать кластера голограммы точно на месте в физическом мире, независимо от того, насколько далеко перемещаемого пользователя, а затем [найти эти голограммы попытку в более поздней версии сеансы](coordinate-systems.md#spatial-anchor-persistence).

В Unity, вы создадите пространственных привязки, добавив **WorldAnchor** компонент Unity в объект GameObject.

### <a name="adding-a-world-anchor"></a>Добавление привязки к всему миру

Чтобы добавить привязку мира, вызовите AddComponent<WorldAnchor>() в объекте игры с преобразованием, нужно закрепить в реальном мире.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Вот и все! Теперь этот объект игр будет привязана к текущего места в физическом мире — немного изменить со временем, чтобы обеспечить выравнивание физических мировых координатах его Unity система может появиться. Используйте [сохраняемости](persistence-in-unity.md) найти этот прикрепленных расположение еще раз в сеансе приложению в дальнейшем.

### <a name="removing-a-world-anchor"></a>Удаление привязки World

Если вы больше не нужны GameObject будут находиться в физическом мире расположение и не планируете его перемещения этого кадра, затем можно просто вызвать Destroy World привязки компонента.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Если вы хотите переместить объект GameObject данного кадра, необходимо вместо этого вызвать DestroyImmediate.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Перемещение мир привязанный объект GameObject

Невозможно переместить объект GameObject во время привязки к всему миру на нем. Если вам нужно переместить объект GameObject данного кадра, необходимо:
1. DestroyImmediate World привязки компонента
2. Переместить GameObject
3. Добавьте новый компонент привязки World GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Обработка изменений Locatability

WorldAnchor может оказаться может быть найдена в физическом мире общую точку во времени. Если это происходит, Unity не обновлять преобразование привязанного объекта. Это также можно изменить во время работы приложения. Ошибка для обработки изменений в locatability вызовет элемент, который отображается в в нужное место в мире.

Чтобы получать уведомления об изменениях locatability:
1. Подписаться на событие OnTrackingChanged
2. Обработка события

**OnTrackingChanged** событие будет вызываться при каждом изменении базовых пространственных привязки между состоянием, может быть найдена, и не может быть найдена.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Затем можно обработать событие:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Иногда привязки, расположены немедленно. В этом случае это свойство isLocated привязки будет присвоено значение true, если AddComponent<WorldAnchor>() возвращает. В результате OnTrackingChanged событие не будет применяться. Очистить шаблон будет вызывать обработчик OnTrackingChanged с начальное состояние IsLocated после присоединения привязки.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Совместное использование привязки на устройствах

Можно использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a> для создания привязки надежные облачные из локального WorldAnchor, который приложения можно найти в нескольких HoloLens, iOS и устройств Android.  Совместное использование общих пространственных привязки на нескольких устройствах, каждый пользователь может видеть содержимое отображается относительно эту привязку, в том же физическом расположении.  Это позволяет выполнять публикацию в режиме реального времени.

Чтобы приступить к работе, создания общих возможностей в Unity, изучите 5-минутные <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">краткие руководства по Azure пространственных привязки Unity</a>.

После того, как приступить к работе с пространственными привязки Azure, вы можете затем <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создать и найдите привязки в Unity</a>.

## <a name="see-also"></a>См. также
* [Возможности масштабирования](coordinate-systems.md#mixed-reality-experience-scales)
* [Пространственные рабочей области](coordinate-systems.md#stage-frame-of-reference)
* [Отслеживание потери в Unity](tracking-loss-in-unity.md)
* [Пространственные привязки](spatial-anchors.md)
* [Сохраняемость в Unity](persistence-in-unity.md)
* [Публикацию в Unity](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure пространственных привязки</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure пространственных привязки пакета SDK для Unity</a>