---
title: Точку фокуса в Unity
description: Голограмма стабильность в Unity, установив точку фокуса, настраивать вручную
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, точку фокуса, фокус плоскости, стабилизации плоскости, стабилизации точка, reprojection, LSR, буфер глубины
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604883"
---
# <a name="focus-point-in-unity"></a>Точку фокуса в Unity

**Пространство имен:** *UnityEngine.XR.WSA*<br>
**Тип**: *HolographicSettings*

[Сосредоточиться точки](hologram-stability.md#stabilization-plane) может быть набор предоставить указание о том, как лучше всего выполнять стабилизации в настоящее время голограммы HoloLens отображение.

Если вы хотите установить точку фокуса в Unity, его необходимо задать каждого кадра с помощью *HolographicSettings.SetFocusPointForFrame()*. Если точку фокуса для кадра не установлен, будет использоваться плоскости стабилизации по умолчанию.

> [!NOTE]
> По умолчанию новые проекты Unity имеют параметр «Включить глубина буфера общий доступ».  В этом случае приложения Unity, выполняющихся на мощных настольных гарнитуры или HoloLens под управлением Windows 10 апреля 2018 г. обновление (RS4) или более поздней версии, передает в буфер глубины для Windows для оптимизации стабильности голограмма автоматически, без указания вашего приложения точку фокуса:
> * На мощных настольных гарнитуры это позволит reprojection основе глубины на пиксель.
> * На HoloLens под управлением Windows 10 апреля 2018 г. обновление или более поздней версии, это будет анализировать буфер глубины автоматически выбрать оптимальное стабилизации плоскости.
>
> Любой из этих подходов должен предоставить еще лучше качество изображения без явных действий для приложения, чтобы выбрать точку фокуса каждого кадра.  Учтите, что если вы вручную укажете точку фокуса, переопределит автоматическое поведение, описанное выше и обычно уменьшит голограмма стабильности.  Как правило, необходимо указать только точку вручную фокуса при запуске приложения на HoloLens, который еще не был обновлен до Windows 10 апреля 2018 г. обновление.

### <a name="example"></a>Пример

Существует много способов, чтобы задать точку фокуса по версии перегрузки, доступных на *SetFocusPointForFrame* статическая функция. Представленные ниже приведен простой пример присвоить плоскости фокус предоставленного объекта каждого кадра:

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

Обратите внимание, что приведенный выше код простой может оказаться уменьшение стабильность голограмма фокусом объекта заканчивается за пользователя.  Именно поэтому обычно задавайте «Разрешить общий глубины буфер» вместо вручную указания точку фокуса.

### <a name="see-also"></a>См. также
* [Плоскость стабилизации](hologram-stability.md#stabilization-plane)
