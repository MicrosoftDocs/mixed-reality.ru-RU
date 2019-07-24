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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="2909f-104">Использование пространства имен Windows с приложениями Unity для HoloLens</span><span class="sxs-lookup"><span data-stu-id="2909f-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="2909f-105">На этой странице описывается, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2909f-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="2909f-106">Условно включить вызовы API WinRT</span><span class="sxs-lookup"><span data-stu-id="2909f-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="2909f-107">API-интерфейсы WinRT можно использовать для проектов Unity, созданных для универсальная платформа Windows и Xbox на одной платформе. любой код, написанный в скриптах Unity, предназначенных для API-интерфейсов WinRT, должен включаться в условия только для этих сборок.</span><span class="sxs-lookup"><span data-stu-id="2909f-107">WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="2909f-108">Это можно сделать с помощью двух шагов в Unity:</span><span class="sxs-lookup"><span data-stu-id="2909f-108">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="2909f-109">Уровень совместимости API должен иметь значение **.net 4,6** или **.NET Standard 2,0** в параметрах проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="2909f-109">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="2909f-110">**Изменение** > **параметров проекта параметры**    совместимости API конфигурациипроигрывателяс.NET4,6или.NETStandard2,0 >  >  > </span><span class="sxs-lookup"><span data-stu-id="2909f-110">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="2909f-111">Директива препроцессора **ENABLE_WINMD_SUPPORT** должна быть заключена в оболочку любого кода, использующего WinRT</span><span class="sxs-lookup"><span data-stu-id="2909f-111">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="2909f-112">Следующий фрагмент кода находится на странице ручного Unity для [универсальная платформа Windows: API WinRT в C# скриптах](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="2909f-112">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="2909f-113">В этом примере возвращается идентификатор объявления, но только для UWP и одной сборки Xbox:</span><span class="sxs-lookup"><span data-stu-id="2909f-113">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="2909f-114">Изменение скриптов в проекте Unity C#</span><span class="sxs-lookup"><span data-stu-id="2909f-114">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="2909f-115">При двойном щелчке скрипта в редакторе Unity он по умолчанию запускает скрипт в проекте редактора.</span><span class="sxs-lookup"><span data-stu-id="2909f-115">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="2909f-116">Интерфейсы API WinRT будут неизвестны, так как проект Visual Studio не ссылается на среда выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="2909f-116">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="2909f-117">Кроме того, Директива **ENALBE_WINMD_SUPPORT** будет неопределенной, а любой *#if* обернутый код будет игнорироваться до тех пор, пока вы не построите проект в решение Visual Studio UWP.</span><span class="sxs-lookup"><span data-stu-id="2909f-117">Further, the **ENALBE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="2909f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="2909f-118">See also</span></span>
* [<span data-ttu-id="2909f-119">Экспорт и разработка решения Visual Studio для Unity</span><span class="sxs-lookup"><span data-stu-id="2909f-119">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="2909f-120">среда выполнения Windows поддержки Unity</span><span class="sxs-lookup"><span data-stu-id="2909f-120">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)