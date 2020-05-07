---
title: Взгляните на входные данные в нереальном режиме
description: Объясняется, как использовать ввод с помощью взгляда в нереальных
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, HoloLens, отслеживание глаз
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835631"
---
# <a name="gaze-input"></a><span data-ttu-id="9424e-104">Входные данные взгляда</span><span class="sxs-lookup"><span data-stu-id="9424e-104">Gaze Input</span></span>

<span data-ttu-id="9424e-105">Подключаемый модуль Windows Mixed Reality не предоставляет никаких специальных функций для ввода с помощью взгляда.</span><span class="sxs-lookup"><span data-stu-id="9424e-105">The Windows Mixed Reality plugin doesn’t provide any special functions for the gaze input.</span></span> <span data-ttu-id="9424e-106">Все работает, несмотря на стандартный нереалй API.</span><span class="sxs-lookup"><span data-stu-id="9424e-106">Everything works though the standard Unreal API.</span></span>

[<span data-ttu-id="9424e-107">API головного взгляда</span><span class="sxs-lookup"><span data-stu-id="9424e-107">Head gaze API</span></span>](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a><span data-ttu-id="9424e-108">Отслеживание взгляда</span><span class="sxs-lookup"><span data-stu-id="9424e-108">Eye tracking</span></span>

<span data-ttu-id="9424e-109">Чтобы использовать API отслеживания взгляда, разработчики должны включить возможность ввода с помощью взгляда в параметрах проекта HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9424e-109">To use the eye tracking API, developers should enable the “Gaze Input” capability in their HoloLens project settings.</span></span> <span data-ttu-id="9424e-110">При запуске приложения пользователь увидит следующее приглашение на согласие</span><span class="sxs-lookup"><span data-stu-id="9424e-110">When the application starts, user will see the following consent prompt</span></span>

![Разрешения на вход с глазами](images/unreal/eye-input-permissions.png)
 
<span data-ttu-id="9424e-112">Если пользователь предоставит свое разрешение, приложение получит доступ к входным данным.</span><span class="sxs-lookup"><span data-stu-id="9424e-112">If the user gives their permission, the application will get eye gaze input.</span></span> 

<span data-ttu-id="9424e-113">[Здесь](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html) приведена документация по API отслеживания взгляда на нереалию</span><span class="sxs-lookup"><span data-stu-id="9424e-113">Unreal’s eye tracking API is documented is [here](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span></span>

<span data-ttu-id="9424e-114">Технические сведения об отслеживании глаз [here](eye-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="9424e-114">The technical details of eye tracking are [here](eye-tracking.md)</span></span>

<span data-ttu-id="9424e-115">Обратите внимание, что в частности, для отслеживания взгляда HoloLens в обоих глаза есть один луч.</span><span class="sxs-lookup"><span data-stu-id="9424e-115">Note that specifically for Unreal, HoloLens eye tracking has a single gaze ray for both eyes.</span></span> <span data-ttu-id="9424e-116">HoloLens не обеспечивает отслеживание стереоскопикных глаз.</span><span class="sxs-lookup"><span data-stu-id="9424e-116">HoloLens doesn’t provide stereoscopic eye tracking.</span></span>
