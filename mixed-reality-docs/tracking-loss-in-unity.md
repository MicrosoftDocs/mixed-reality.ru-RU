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
# <a name="tracking-loss-in-unity"></a>Отслеживание потерь в Unity

Если устройство не может располагать себя в мире, в приложении происходит «отслеживание потерь». По умолчанию Unity приостанавливает цикл обновления и отображает для пользователя изображение заставки. Когда отслеживание восстанавливается, изображение-заставка исчезает, а цикл обновления продолжается.

В качестве альтернативы пользователь может вручную справиться с этим переходом, отменив параметр. При отслеживании потерь все содержимое становится заблокированным, если не выполняется никаких действий по его обработке.

## <a name="default-handling"></a>Обработка по умолчанию

По умолчанию цикл обновления приложения, а также все сообщения и события будут прекращаться на время отслеживания потери. В то же время для пользователя будет отображаться изображение. Вы можете настроить этот образ, перейдя в меню "Правка"-> "Параметры" — > "проигрыватель", щелкнув изображение заставки и задав образ потери отслеживания с помощью.

## <a name="manual-handling"></a>Ручная обработка

Чтобы вручную обрабатывалась отслеживание потерь, необходимо вернуться к разделу **изменение** >  > **параметров проекта параметры** > **проигрывателя** > **универсальная платформа Windows параметры** **изображение заставки**  >  **Windows holographic** и снять флажок "при отслеживании потерь приостановить и показывать изображение". После этого необходимо выполнить обработку изменений отслеживания с помощью API, указанных ниже.

**Имен** *UnityEngine. XR. WSA*<br>
**Тип** *ворлдманажер*

* Менеджер по всему миру предоставляет событие для обнаружения потерянных или полученных данных отслеживания (*ворлдманажер. онпоситионаллокаторстатечанжед*) и свойство для запроса текущего состояния (*ворлдманажер. State).*
* Если отслеживание состояния неактивно, Камера не будет переводиться в виртуальном мире даже при преобразовании пользователя. Это означает, что объекты больше не будут соответствовать ни одному физическому расположению, а все будут отображаться как заблокированные.

При обработке собственных изменений необходимо опросить свойство State для каждого кадра или обработать событие *онпоситионаллокаторстатечанжед* .

### <a name="polling"></a>Опроса

Наиболее важное состояние — *поситионаллокаторстате. Active* . Это означает, что отслеживание полностью работоспособно. Любое другое состояние приведет к появлению в основной камере только ротации. Пример:

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Обработка события Онпоситионаллокаторстатечанжед

Кроме того, можно также подписываться на *онпоситионаллокаторстатечанжед* для выполнения переходов:

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

## <a name="see-also"></a>См. также
* [Обработка потерь отслеживания в DirectX](coordinate-systems-in-directx.md#handling-tracking-loss)
