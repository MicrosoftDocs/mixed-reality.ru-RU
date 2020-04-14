---
title: API-интерфейсы WinRT с Unity для HoloLens
description: Объясняется, как использовать API-интерфейсы WinRT (пространство имен Windows) в проекте Unity для HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, пошаговое руководство
ms.openlocfilehash: 80f950d7571a936e93eb08490ad83dbb34a50b3a
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277992"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>API-интерфейсы WinRT с Unity для HoloLens

На этой странице описывается, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.

## <a name="mixed-reality-apis"></a>Интерфейсы API смешанной реальности

Подмножество Windows SDK, сосредоточенное на смешанной реальности, было доступно в проекции, совместимой с .NET Standard 2,0, которую можно использовать в проекте без директив препроцессора. Сюда входят большинство API-интерфейсов в пространствах имен Windows. восприятие Windows. UI. input. пространственные и могут расширяться для включения дополнительных API в будущем. Планируемые API-интерфейсы можно использовать во время работы в редакторе, что позволяет использовать [режим воспроизведения](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode). Чтобы использовать эту проекцию, внесите в проект следующие изменения:

1) Добавьте ссылку на пакет NuGet [Microsoft. Windows. микседреалити. дотнетвинрт](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) с помощью [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity).
2) Префикс ссылается на пространство имен `Windows` с `Microsoft.`:
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Замените приведение собственных указателей на `FromNativePtr`:
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Условно включить вызовы API WinRT

Кроме того, можно использовать API-интерфейсы WinRT для проектов Unity, созданных для универсальная платформа Windows и платформы Xbox с помощью директив препроцессора; любой код, написанный в скриптах Unity, предназначенных для API-интерфейсов WinRT, должен включаться в условия только для этих сборок. 

Это можно сделать с помощью двух шагов в Unity:
1) Уровень совместимости API должен иметь значение **.net 4,6** или **.NET Standard 2,0** в параметрах проигрывателя.
    - **Изменение** **параметров проекта** >  > **проигрывателя** > **конфигурация** > **уровень совместимости API** для **.NET 4,6** или **.NET Standard 2,0**
2) Директива препроцессора **ENABLE_WINMD_SUPPORT** должна быть заключена в оболочку любого кода, использующего WinRT

Следующий фрагмент кода находится на странице ручного письма Unity для [универсальная платформа Windows: WINRT API в C# скриптах](https://docs.unity3d.com/Manual/windowsstore-scripts.html). В этом примере возвращается идентификатор объявления, но только для UWP и одной сборки Xbox:

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

При двойном щелчке скрипта в редакторе Unity он по умолчанию запускает скрипт в проекте редактора. Интерфейсы API WinRT будут неизвестны, так как проект Visual Studio не ссылается на среда выполнения Windows. Кроме того, Директива **ENABLE_WINMD_SUPPORT** будет неопределенной, а *#if* любой код, переданный в оболочке, будет игнорироваться до тех пор, пока вы не построите проект в решение Visual Studio UWP.

## <a name="see-also"></a>См. также:
* [Экспорт и разработка решения Visual Studio для Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [среда выполнения Windows поддержки Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
