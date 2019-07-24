---
title: Использование пространства имен Windows с приложениями Unity для HoloLens
description: Объясняется, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, пошаговое руководство
ms.openlocfilehash: fd25548de8eeb3c8157a3f9de283dc5004ed1180
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548733"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>Использование пространства имен Windows с приложениями Unity для HoloLens

На этой странице описывается, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.

## <a name="conditionally-include-winrt-api-calls"></a>Условно включить вызовы API WinRT

API-интерфейсы WinRT можно использовать для проектов Unity, созданных для универсальная платформа Windows и Xbox на одной платформе. любой код, написанный в скриптах Unity, предназначенных для API-интерфейсов WinRT, должен включаться в условия только для этих сборок. 

Это можно сделать с помощью двух шагов в Unity:
1) Уровень совместимости API должен иметь значение **.net 4,6** или **.NET Standard 2,0** в параметрах проигрывателя.
    - **Изменение** > **параметров проекта параметры**    совместимости API конфигурациипроигрывателяс.NET4,6или.NETStandard2,0 >  >  > 
2) Директива препроцессора **ENABLE_WINMD_SUPPORT** должна быть заключена в оболочку любого кода, использующего WinRT

Следующий фрагмент кода находится на странице ручного Unity для [универсальная платформа Windows: API WinRT в C# скриптах](http://docs.unity3d.com/Manual/windowsstore-scripts.html). В этом примере возвращается идентификатор объявления, но только для UWP и одной сборки Xbox:

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Изменение скриптов в проекте Unity C#

При двойном щелчке скрипта в редакторе Unity он по умолчанию запускает скрипт в проекте редактора. Интерфейсы API WinRT будут неизвестны, так как проект Visual Studio не ссылается на среда выполнения Windows. Кроме того, Директива **ENALBE_WINMD_SUPPORT** будет неопределенной, а любой *#if* обернутый код будет игнорироваться до тех пор, пока вы не построите проект в решение Visual Studio UWP.

## <a name="see-also"></a>См. также
* [Экспорт и разработка решения Visual Studio для Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [среда выполнения Windows поддержки Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)