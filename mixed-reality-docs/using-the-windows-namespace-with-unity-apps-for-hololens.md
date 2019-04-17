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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="cdf0e-104">Использование пространства имен Windows с приложениями Unity для HoloLens</span><span class="sxs-lookup"><span data-stu-id="cdf0e-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="cdf0e-105">Этой странице описывается, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cdf0e-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="cdf0e-106">Условно включают вызовы WinRT API</span><span class="sxs-lookup"><span data-stu-id="cdf0e-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="cdf0e-107">API-интерфейсы WinRT будет использоваться только в сборках проекта Unity, предназначенных для Windows 8, Windows 8.1 или универсальной платформы Windows; любой код, созданный в сценарии Unity, предназначенный API-интерфейсы WinRT должен быть условно включен для только для этих сборок.</span><span class="sxs-lookup"><span data-stu-id="cdf0e-107">WinRT APIs will only be used in Unity project builds that target Windows 8, Windows 8.1, or the Universal Windows Platform; any code that you write in Unity scripts that targets WinRT APIs must be conditionally included for only those builds.</span></span> <span data-ttu-id="cdf0e-108">Это делается с помощью NETFX_CORE или WINDOWS_UWP определений препроцессора.</span><span class="sxs-lookup"><span data-stu-id="cdf0e-108">This is done using the NETFX_CORE or WINDOWS_UWP preprocessor definitions.</span></span> <span data-ttu-id="cdf0e-109">Это правило применяется к с помощью инструкций, а также другой код.</span><span class="sxs-lookup"><span data-stu-id="cdf0e-109">This rule applies to using statements, as well as other code.</span></span>

<span data-ttu-id="cdf0e-110">Следующий фрагмент кода взят из Unity вручную страницы для [универсальной платформы Windows: API WinRT в C# сценарии](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="cdf0e-110">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="cdf0e-111">В этом примере идентификатор получателя рекламы возвращается, но только в Windows 8.0 или более поздней версии целевой сборки:</span><span class="sxs-lookup"><span data-stu-id="cdf0e-111">In this example, an advertising ID is returned, but only on Windows 8.0 or higher target builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="cdf0e-112">Изменение скриптов в Unity C# проекта</span><span class="sxs-lookup"><span data-stu-id="cdf0e-112">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="cdf0e-113">При двойном щелчке скрипт в редакторе Unity, он будет по умолчанию запуска скрипта в проекте редактора.</span><span class="sxs-lookup"><span data-stu-id="cdf0e-113">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="cdf0e-114">API-интерфейсы WinRT будут отображаться как неизвестный по двум причинам: NETFX_CORE не определен в этой среде, и проект не ссылается на среду выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="cdf0e-114">The WinRT APIs will appear to be unknown for two reasons: NETFX_CORE is not defined in this environment, and the project does not reference the Windows Runtime.</span></span> <span data-ttu-id="cdf0e-115">Если вы используете [рекомендуется экспорта и встроенные параметры](exporting-and-building-a-unity-visual-studio-solution.md)и изменение скриптов в этом проекте вместо этого, он будет определять NETFX_CORE и также включает ссылку на среду выполнения Windows; с этой конфигурацией на месте, API-интерфейсы WinRT будет доступны для IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="cdf0e-115">If you use the [recommended export and built settings](exporting-and-building-a-unity-visual-studio-solution.md), and edit the scripts in that project instead, it will define NETFX_CORE and also include a reference to the Windows Runtime; with this configuration in place, WinRT APIs will be available for IntelliSense.</span></span>

<span data-ttu-id="cdf0e-116">Обратите внимание, что в Unity C# проекта также позволяют выполнять отладку с помощью сценариев с помощью клавиши F5, удаленная отладка в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cdf0e-116">Note that your Unity C# project can also be used to debug through your scripts using F5 remote debugging in Visual Studio.</span></span> <span data-ttu-id="cdf0e-117">Если вы не видите IntelliSense, работа при первом открытии Unity C# проекта, закройте проект и откройте его снова.</span><span class="sxs-lookup"><span data-stu-id="cdf0e-117">If you do not see IntelliSense working the first time that you open your Unity C# project, close the project and re-open it.</span></span> <span data-ttu-id="cdf0e-118">Технология IntelliSense должна начать работу.</span><span class="sxs-lookup"><span data-stu-id="cdf0e-118">IntelliSense should start working.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdf0e-119">См. также</span><span class="sxs-lookup"><span data-stu-id="cdf0e-119">See also</span></span>
* [<span data-ttu-id="cdf0e-120">Экспорт и создание решения Visual Studio для Unity</span><span class="sxs-lookup"><span data-stu-id="cdf0e-120">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
