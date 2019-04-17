---
title: Использование пространства имен Windows с приложениями Unity для HoloLens
description: Объясняется, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Пошаговое руководство для смешанной реальности, API, windows Unity, WinRT,
ms.openlocfilehash: ed65b5995d74c54057a49b878c1206d0f06394ca
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599869"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>Использование пространства имен Windows с приложениями Unity для HoloLens

Этой странице описывается, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.

## <a name="conditionally-include-winrt-api-calls"></a>Условно включают вызовы WinRT API

API-интерфейсы WinRT будет использоваться только в сборках проекта Unity, предназначенных для Windows 8, Windows 8.1 или универсальной платформы Windows; любой код, созданный в сценарии Unity, предназначенный API-интерфейсы WinRT должен быть условно включен для только для этих сборок. Это делается с помощью NETFX_CORE или WINDOWS_UWP определений препроцессора. Это правило применяется к с помощью инструкций, а также другой код.

Следующий фрагмент кода взят из Unity вручную страницы для [универсальной платформы Windows: API WinRT в C# сценарии](http://docs.unity3d.com/Manual/windowsstore-scripts.html). В этом примере идентификатор получателя рекламы возвращается, но только в Windows 8.0 или более поздней версии целевой сборки:

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if NETFX_CORE
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Изменение скриптов в Unity C# проекта

При двойном щелчке скрипт в редакторе Unity, он будет по умолчанию запуска скрипта в проекте редактора. API-интерфейсы WinRT будут отображаться как неизвестный по двум причинам: NETFX_CORE не определен в этой среде, и проект не ссылается на среду выполнения Windows. Если вы используете [рекомендуется экспорта и встроенные параметры](exporting-and-building-a-unity-visual-studio-solution.md)и изменение скриптов в этом проекте вместо этого, он будет определять NETFX_CORE и также включает ссылку на среду выполнения Windows; с этой конфигурацией на месте, API-интерфейсы WinRT будет доступны для IntelliSense.

Обратите внимание, что в Unity C# проекта также позволяют выполнять отладку с помощью сценариев с помощью клавиши F5, удаленная отладка в Visual Studio. Если вы не видите IntelliSense, работа при первом открытии Unity C# проекта, закройте проект и откройте его снова. Технология IntelliSense должна начать работу.

## <a name="see-also"></a>См. также
* [Экспорт и создание решения Visual Studio для Unity](exporting-and-building-a-unity-visual-studio-solution.md)
