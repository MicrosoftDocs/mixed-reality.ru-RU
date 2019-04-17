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
# <a name="tracking-loss-in-unity"></a>Отслеживание потери в Unity

Если устройство не может найти сам в мире, приложение интерфейсы «отслеживания потери». По умолчанию Unity Приостановка цикла обновления и отображаемое изображение заставки для пользователя. Когда отслеживания, освобождается, изображение заставки исчезает и продолжает цикла обновления.

Кроме того пользователь может вручную обрабатывать этот переход, отказавшись от параметра. Все содержимое будет казаться, что в качестве текста во время отслеживания потери в случае, если ничего не происходит его обработать.

## <a name="default-handling"></a>Обработка по умолчанию

По умолчанию в течение отслеживание потери перестанет цикла обновления приложения, а также все сообщения и события. Одновременно изображение будет отображаться для пользователя. Этот образ можно настроить, открыв для редактирования "->" Параметры "->" Player, нужно щелкнуть изображение заставки и задание Holographic отслеживание потери изображения.

## <a name="manual-handling"></a>Обработка вручную

Чтобы вручную обрабатывать потерю отслеживания, необходимо перейти к **изменить** > **параметры проекта** > **проигрывателя**  >   **Вкладка параметров универсальной платформы Windows** > **изображение заставки** > **Windows Holographic** и снимите флажок «на отслеживание потери Pause и Показать изображение ". После этого вам нужно обрабатывать отслеживание изменений с помощью интерфейсов API, указанных ниже.

**Пространство имен:** *UnityEngine.XR.WSA*<br>
**Тип:** *WorldManager*

* Мир Manager предоставляет событие для обнаружения, отслеживания потери/положены (*WorldManager.OnPositionalLocatorStateChanged*) и свойство, чтобы запрашивать текущее состояние (*WorldManager.state*)
* Когда состояние отслеживания не активен, для преобразования в виртуальный мир, даже если пользователь переводит не появится камеры. Это означает, что объекты больше не будет соответствовать любое физическое расположение и все будет отображаться текст заблокирован.

При обработке отслеживание изменений на собственные вы либо требуется проводить опрос свойстве state каждый кадр или дескриптор *OnPositionalLocatorStateChanged* событий.

### <a name="polling"></a>опрос

Наиболее важным состояние *PositionalLocatorState.Active* означающее отслеживания будут обладать полной функциональностью. Любое другое состояние произойдет только вращения «дельты» на главной камеры. Пример:

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Обработка события OnPositionalLocatorStateChanged

Можно также и более удобным, вы также можете подписаться на *OnPositionalLocatorStateChanged* для обработки переходов:

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
* [Обработка отслеживание потери в DirectX](coordinate-systems-in-directx.md#handling-tracking-loss)
