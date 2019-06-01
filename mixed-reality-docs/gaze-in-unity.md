---
title: Помощи в Unity
description: Взглядом — это основной способ для пользователей для нацеливания голограммы, создаваемые приложения в смешанной реальности.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: взглядом, unity, голограмма, смешанной реальности
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453722"
---
# <a name="head-gaze-in-unity"></a>Взглядом HEAD в Unity

[Помощи](gaze.md) является основным способом для пользователей для нацеливания [голограммы](hologram.md) ваше приложение создает в [смешанной реальности](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Реализации головной взглядом

По существу [помощи](gaze.md) реализуется путем проецирования лучом, проведенным из головы пользователя, где гарнитуры, в прямом направлении их с выходом и определение, Рэй конфликтует с. В Unity пользователя головной положения и направления, предоставляются с помощью Unity Main [камеры](camera-in-unity.md), в частности [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) и [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Вызов [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) приводит [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) структуры, который содержит сведения о конфликтов, включая трехмерной точки, где возник конфликт и других GameObject луч взглядом со стенами вдоль.

### <a name="example-implement-head-gaze"></a>Пример. Реализуйте головной взглядом

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

Хотя в приведенном выше примере показано, как сделать один raycast, чтобы найти целевой взглядом цикл обновления, рекомендуется для этого в управлении взглядом вместо этого в любой объект, который потенциально заинтересовано в объекте gazed в один объект. Это позволяет сохранить обработки, выполнив только один raycast взглядом каждого кадра приложения.

## <a name="visualizing-gaze"></a>Визуализация взглядом

Так же, как на рабочем столе, где использовать указатель мыши выбирать и взаимодействовать с содержимым, следует реализовать [курсор](cursors.md) , представляющий взглядом пользователя. Это дает уверенность пользователей в том, что они сейчас взаимодействовать.

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>Помощи в смешанной реальности Toolkit v2
Вы можете получить доступ к взглядом из [ввода Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) в MRTK v2.

## <a name="see-also"></a>См. также
* [Камера](camera-in-unity.md)
* [Отслеживание взгляда](gaze.md)
* [Курсоры](cursors.md)
* [Нацеливание взглядом](gaze-targeting.md)
