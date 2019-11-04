---
title: Управляемая отладка с помощью Unity IL2CPP
description: В этой статье описывается, как запустить управляемый отладчик в проекте UWP для Unity IL2CPP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, отладка, il2cpp
ms.openlocfilehash: fd09c3ca1bd410c56e46eb8e8815742f87482d08
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439635"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="1e267-104">Управляемая отладка с помощью Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="1e267-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="1e267-105">Выполните следующие действия, чтобы подключить управляемый отладчик к сборке UWP в Unity IL2CPP.</span><span class="sxs-lookup"><span data-stu-id="1e267-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="1e267-106">Это руководством изначально было разработано для HoloLens и HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1e267-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="1e267-107">Необходимо находиться в сети, поддерживающей [многоадресную рассылку](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="1e267-107">You will need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
1. <span data-ttu-id="1e267-108">Убедитесь, что **интернетклиентсервер** и **приватенетворкклиентсервер** проверяются в Unity в соответствии с возможностями параметров публикации UWP.</span><span class="sxs-lookup"><span data-stu-id="1e267-108">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![Возможности параметров публикации UWP](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="1e267-110">Настройте параметры сборки UWP для Unity:</span><span class="sxs-lookup"><span data-stu-id="1e267-110">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="1e267-111">Сборка разработки</span><span class="sxs-lookup"><span data-stu-id="1e267-111">Development Build</span></span>
    - <span data-ttu-id="1e267-112">Отладка сценария</span><span class="sxs-lookup"><span data-stu-id="1e267-112">Script Debugging</span></span>
    - <span data-ttu-id="1e267-113">Ожидание управляемого отладчика (необязательно)</span><span class="sxs-lookup"><span data-stu-id="1e267-113">Wait for Managed Debugger (optional)</span></span>

    ![Параметры сборки UWP](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="1e267-115">Сборка в Unity.</span><span class="sxs-lookup"><span data-stu-id="1e267-115">Build in Unity.</span></span>
1. <span data-ttu-id="1e267-116">Выполните сборку и развертывание из решения Visual Studio на устройстве.</span><span class="sxs-lookup"><span data-stu-id="1e267-116">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="1e267-117">Необходимо выполнить сборку с конфигурациями **отладки** или **выпуска** .</span><span class="sxs-lookup"><span data-stu-id="1e267-117">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="1e267-118">**Основная** конфигурация отключает профилировщик Unity и может предотвратить оптимальную отладку.</span><span class="sxs-lookup"><span data-stu-id="1e267-118">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="1e267-119">При необходимости проверьте **Интернет (клиент & сервер)** и **частные сети (клиент & сервер)** в списке возможностей в Package. appxmanifest в решении.</span><span class="sxs-lookup"><span data-stu-id="1e267-119">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="1e267-120">Запустите приложение на устройстве.</span><span class="sxs-lookup"><span data-stu-id="1e267-120">Start the app on your device.</span></span> <span data-ttu-id="1e267-121">Убедитесь, что устройство подключено к той же сети, что и ваш компьютер.</span><span class="sxs-lookup"><span data-stu-id="1e267-121">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="1e267-122">Убедитесь, что устройство **не** подключено к компьютеру через USB.</span><span class="sxs-lookup"><span data-stu-id="1e267-122">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="1e267-123">Перейдите в решение Visual Studio, которое создается при двойном щелчке сценария в Unity, где можно просматривать и редактировать C# скрипты.</span><span class="sxs-lookup"><span data-stu-id="1e267-123">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="1e267-124">Отладка — > присоединить отладчик Unity.</span><span class="sxs-lookup"><span data-stu-id="1e267-124">Debug -> Attach Unity Debugger.</span></span>

    ![Присоединить отладчик Unity](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="1e267-126">Выберите устройство в списке и нажмите кнопку "ОК", чтобы присоединиться.</span><span class="sxs-lookup"><span data-stu-id="1e267-126">Select your device in the list and click "OK" to attach.</span></span>

    ![Список устройств](images/il2cpp-debugging-machines.png)
