---
title: Взгляните на Unity
description: Взгляд — это основной способ, с помощью которого пользователи могут ориентироваться на голограммы, создаваемые приложением в смешанной реальности.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: взгляд, Unity, голограмма, Смешанная реальность
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453722"
---
# <a name="head-gaze-in-unity"></a>Головное взгляд в Unity

[Взгляд](gaze.md) — это основной способ, с помощью которого пользователи могут ориентироваться на [голограммы](hologram.md), создаваемые приложением в [смешанной реальности](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Реализация головного взгляда

По сути, [взгляд](gaze.md) реализуется путем проецирования луча из заголовка пользователя, где находится гарнитура, в прямом направлении и определяет, что луч конфликтует с. В Unity расположение и направление головного пользователя предоставляются с помощью основной [камеры](camera-in-unity.md)Unity, в частности [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [преобразование. Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) и [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Disposition](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Вызов функции [физик. райкаст](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) приводит к [райкассит](http://docs.unity3d.com/ScriptReference/RaycastHit.html) структуре, содержащей сведения о конфликте, включая трехмерную точку, в которой произошел конфликт, и другую GameObject, с которой был получен объект-Ray.

### <a name="example-implement-head-gaze"></a>Пример. Реализация головного взгляда

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

### <a name="best-practices"></a>Советы и рекомендации

Хотя в приведенном выше примере показано, как выполнить одно райкаст в цикле обновления, чтобы найти целевой объект взгляда, рекомендуется сделать это в одном объекте, управляющем взвзглядом, а не делать это в любом объекте, который потенциально заинтересован в объекте, газед в. Это позволяет приложению сохранять обработку, выполняя только один взгляд, райкаст каждый кадр.

## <a name="visualizing-gaze"></a>Визуализация взгляда

Как и на рабочем столе, где используется указатель мыши для назначения и взаимодействия с содержимым, следует реализовать [курсор](cursors.md) , который представляет взгляд пользователя. Это дает пользователю уверенность в том, с чем они взаимодействуют.

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>Взгляните на набор средств Mixed Reality версии 2
Доступ к элементу управления "взгляд" можно получить из [диспетчера ввода](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) в мртк v2.

## <a name="see-also"></a>См. также
* [Камера](camera-in-unity.md)
* [Входные данные взгляда](gaze.md)
* [Курсоры](cursors.md)
* [Нацеливание взглядом](gaze-targeting.md)
