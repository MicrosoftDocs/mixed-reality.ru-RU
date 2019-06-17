---
title: Управляемая отладка с помощью Unity IL2CPP
description: В этой статье описывается, как для запуска управляемого отладчика в проекте Unity IL2CPP UWP.
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: Unity, visual studio, отладка, il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148859"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="1a95f-104">Управляемая отладка с помощью Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="1a95f-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="1a95f-105">Выполните следующие действия, чтобы подключать управляемый отладчик Unity IL2CPP UWP сборку.</span><span class="sxs-lookup"><span data-stu-id="1a95f-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="1a95f-106">В этом руководстве была изначально разработана для HoloLens и HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1a95f-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="1a95f-107">Убедитесь, что **InternetClientServer** и **PrivateNetworkClientServer** проверяются в Unity в разделе параметров возможности публикации универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="1a95f-107">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![Публикация параметров возможностей универсальной платформы Windows](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="1a95f-109">Настройка параметров сборки Unity универсальной платформы Windows:</span><span class="sxs-lookup"><span data-stu-id="1a95f-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="1a95f-110">Сборка для разработки</span><span class="sxs-lookup"><span data-stu-id="1a95f-110">Development Build</span></span>
    - <span data-ttu-id="1a95f-111">Отладка сценария</span><span class="sxs-lookup"><span data-stu-id="1a95f-111">Script Debugging</span></span>
    - <span data-ttu-id="1a95f-112">Дождитесь управляемого отладчика (необязательно)</span><span class="sxs-lookup"><span data-stu-id="1a95f-112">Wait for Managed Debugger (optional)</span></span>

    ![Параметры сборки UWP](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="1a95f-114">Сборки в Unity.</span><span class="sxs-lookup"><span data-stu-id="1a95f-114">Build in Unity.</span></span>
1. <span data-ttu-id="1a95f-115">Создавайте и развертывайте из решения Visual Studio к устройству.</span><span class="sxs-lookup"><span data-stu-id="1a95f-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="1a95f-116">Следует создать с помощью **Отладка** или **выпуска** конфигураций.</span><span class="sxs-lookup"><span data-stu-id="1a95f-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="1a95f-117">**Master** конфигурации отключает профилировщик Unity и помешать оптимальной отладки.</span><span class="sxs-lookup"><span data-stu-id="1a95f-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="1a95f-118">При необходимости проверьте **Интернет (клиент и сервер)** и **частные сети (клиент и сервер)** в списке возможностей в файл Package.appxmanifest в решении.</span><span class="sxs-lookup"><span data-stu-id="1a95f-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="1a95f-119">Запустите приложение на устройстве.</span><span class="sxs-lookup"><span data-stu-id="1a95f-119">Start the app on your device.</span></span> <span data-ttu-id="1a95f-120">Убедитесь, что ваше устройство подключено к той же сети, что ПК.</span><span class="sxs-lookup"><span data-stu-id="1a95f-120">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="1a95f-121">Убедитесь, что устройство **не** подключен к Компьютеру через USB.</span><span class="sxs-lookup"><span data-stu-id="1a95f-121">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="1a95f-122">Перейдите в решение Visual Studio, который создается при двойном щелчке на скрипт в Unity, где можно просматривать и изменять ваш C# сценариев.</span><span class="sxs-lookup"><span data-stu-id="1a95f-122">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="1a95f-123">Отладка -> подключить отладчик Unity.</span><span class="sxs-lookup"><span data-stu-id="1a95f-123">Debug -> Attach Unity Debugger.</span></span>

    ![Присоединить отладчик Unity](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="1a95f-125">Выберите устройство в списке и нажмите кнопку «ОК» для присоединения.</span><span class="sxs-lookup"><span data-stu-id="1a95f-125">Select your device in the list and click "OK" to attach.</span></span>

    ![Список устройств](images/il2cpp-debugging-machines.png)
