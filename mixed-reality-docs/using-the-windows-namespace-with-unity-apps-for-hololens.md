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
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="fb008-104">API-интерфейсы WinRT с Unity для HoloLens</span><span class="sxs-lookup"><span data-stu-id="fb008-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="fb008-105">На этой странице описывается, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb008-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="fb008-106">Интерфейсы API смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="fb008-106">Mixed Reality APIs</span></span>

<span data-ttu-id="fb008-107">Подмножество Windows SDK, сосредоточенное на смешанной реальности, было доступно в проекции, совместимой с .NET Standard 2,0, которую можно использовать в проекте без директив препроцессора.</span><span class="sxs-lookup"><span data-stu-id="fb008-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="fb008-108">Сюда входят большинство API-интерфейсов в пространствах имен Windows. восприятие Windows. UI. input. пространственные и могут расширяться для включения дополнительных API в будущем.</span><span class="sxs-lookup"><span data-stu-id="fb008-108">This includes most APIs in the Windows.Perception and Windows.UI.Input.Spatial namespaces, and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="fb008-109">Планируемые API-интерфейсы можно использовать во время работы в редакторе, что позволяет использовать [режим воспроизведения](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span><span class="sxs-lookup"><span data-stu-id="fb008-109">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="fb008-110">Чтобы использовать эту проекцию, внесите в проект следующие изменения:</span><span class="sxs-lookup"><span data-stu-id="fb008-110">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="fb008-111">Добавьте ссылку на пакет NuGet [Microsoft. Windows. микседреалити. дотнетвинрт](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) с помощью [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="fb008-111">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="fb008-112">Префикс ссылается на пространство имен `Windows` с `Microsoft.`:</span><span class="sxs-lookup"><span data-stu-id="fb008-112">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="fb008-113">Замените приведение собственных указателей на `FromNativePtr`:</span><span class="sxs-lookup"><span data-stu-id="fb008-113">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="fb008-114">Условно включить вызовы API WinRT</span><span class="sxs-lookup"><span data-stu-id="fb008-114">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="fb008-115">Кроме того, можно использовать API-интерфейсы WinRT для проектов Unity, созданных для универсальная платформа Windows и платформы Xbox с помощью директив препроцессора; любой код, написанный в скриптах Unity, предназначенных для API-интерфейсов WinRT, должен включаться в условия только для этих сборок.</span><span class="sxs-lookup"><span data-stu-id="fb008-115">Alternatively, WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="fb008-116">Это можно сделать с помощью двух шагов в Unity:</span><span class="sxs-lookup"><span data-stu-id="fb008-116">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="fb008-117">Уровень совместимости API должен иметь значение **.net 4,6** или **.NET Standard 2,0** в параметрах проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="fb008-117">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="fb008-118">**Изменение** **параметров проекта** >  > **проигрывателя** > **конфигурация** > **уровень совместимости API** для **.NET 4,6** или **.NET Standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="fb008-118">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="fb008-119">Директива препроцессора **ENABLE_WINMD_SUPPORT** должна быть заключена в оболочку любого кода, использующего WinRT</span><span class="sxs-lookup"><span data-stu-id="fb008-119">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="fb008-120">Следующий фрагмент кода находится на странице ручного письма Unity для [универсальная платформа Windows: WINRT API в C# скриптах](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="fb008-120">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="fb008-121">В этом примере возвращается идентификатор объявления, но только для UWP и одной сборки Xbox:</span><span class="sxs-lookup"><span data-stu-id="fb008-121">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="fb008-122">Изменение скриптов в проекте Unity C#</span><span class="sxs-lookup"><span data-stu-id="fb008-122">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="fb008-123">При двойном щелчке скрипта в редакторе Unity он по умолчанию запускает скрипт в проекте редактора.</span><span class="sxs-lookup"><span data-stu-id="fb008-123">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="fb008-124">Интерфейсы API WinRT будут неизвестны, так как проект Visual Studio не ссылается на среда выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="fb008-124">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="fb008-125">Кроме того, Директива **ENABLE_WINMD_SUPPORT** будет неопределенной, а *#if* любой код, переданный в оболочке, будет игнорироваться до тех пор, пока вы не построите проект в решение Visual Studio UWP.</span><span class="sxs-lookup"><span data-stu-id="fb008-125">Further, the **ENABLE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb008-126">См. также:</span><span class="sxs-lookup"><span data-stu-id="fb008-126">See also</span></span>
* [<span data-ttu-id="fb008-127">Экспорт и разработка решения Visual Studio для Unity</span><span class="sxs-lookup"><span data-stu-id="fb008-127">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="fb008-128">среда выполнения Windows поддержки Unity</span><span class="sxs-lookup"><span data-stu-id="fb008-128">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
