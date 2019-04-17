---
title: Перейдите в режим воспроизведения Unity
description: Используя режим воспроизведения в редакторе Unity для предварительного просмотра изменений на устройстве без развертывания приложения.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, удаленное взаимодействие, holographic удаленного взаимодействия, проигрыватель holographic удаленного взаимодействия
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597826"
---
# <a name="unity-play-mode"></a><span data-ttu-id="89ccb-104">Перейдите в режим воспроизведения Unity</span><span class="sxs-lookup"><span data-stu-id="89ccb-104">Unity Play Mode</span></span>

<span data-ttu-id="89ccb-105">Быстрый способ работы над проектом Unity находится в режиме «воспроизвести».</span><span class="sxs-lookup"><span data-stu-id="89ccb-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="89ccb-106">Выполняет приложение локально в редакторе Unity на ПК.</span><span class="sxs-lookup"><span data-stu-id="89ccb-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="89ccb-107">Unity использует Holographic удаленного взаимодействия предоставляет быстрый способ для предварительного просмотра содержимого на реальном устройстве HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89ccb-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="89ccb-108">Перейдите в режим воспроизведения Unity с помощью Holographic удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="89ccb-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="89ccb-109">Holographic взаимодействии приложения на HoloLens, могут возникнуть во время его выполнения в редакторе Unity на ПК.</span><span class="sxs-lookup"><span data-stu-id="89ccb-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="89ccb-110">Взглядом, жест, голоса и пространственное сопоставление входные данные поступают от вашего HoloLens на вашем ПК.</span><span class="sxs-lookup"><span data-stu-id="89ccb-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="89ccb-111">Отрисованные кадры, затем отправляются обратно к HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89ccb-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="89ccb-112">Это отличный способ быстро отладка приложения без построения и развертывания полного проекта.</span><span class="sxs-lookup"><span data-stu-id="89ccb-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="89ccb-113">На ваш HoloLens, перейдите в каталог **Microsoft Store** и установить **[Holographic проигрывателя удаленного взаимодействия](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** приложения.</span><span class="sxs-lookup"><span data-stu-id="89ccb-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="89ccb-114">Запустите на вашей HoloLens **Holographic проигрывателя удаленного взаимодействия** приложения.</span><span class="sxs-lookup"><span data-stu-id="89ccb-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="89ccb-115">В Unity, перейдите в раздел **окно** меню и выберите **Holographic эмуляции**.</span><span class="sxs-lookup"><span data-stu-id="89ccb-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="89ccb-116">Задайте **режима эмуляции** для **удаленного устройство**.</span><span class="sxs-lookup"><span data-stu-id="89ccb-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="89ccb-117">Для **удаленный компьютер**, введите IP-адрес вашего HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89ccb-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="89ccb-118">Нажмите кнопку **Подключить**.</span><span class="sxs-lookup"><span data-stu-id="89ccb-118">Click **Connect**.</span></span> <span data-ttu-id="89ccb-119">Вы должны увидеть **состояние подключения** измените **подключено** и просмотра перейдите в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89ccb-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="89ccb-120">Нажмите кнопку **воспроизведение** кнопку, чтобы перейти в режим воспроизведения и оценить приложение в вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89ccb-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="89ccb-121">Holographic удаленного взаимодействия требуется быстрое подключение Wi-Fi и ПК.</span><span class="sxs-lookup"><span data-stu-id="89ccb-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="89ccb-122">См. в разделе [Holographic проигрывателя удаленного взаимодействия](holographic-remoting-player.md) полные сведения.</span><span class="sxs-lookup"><span data-stu-id="89ccb-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="89ccb-123">Для получения наилучших результатов, убедитесь, что приложение правильно задает [сосредоточиться точки](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="89ccb-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="89ccb-124">Это помогает Holographic удаленного взаимодействия, наилучшим образом адаптировать сцены к задержке беспроводного подключения.</span><span class="sxs-lookup"><span data-stu-id="89ccb-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="89ccb-125">См. также</span><span class="sxs-lookup"><span data-stu-id="89ccb-125">See Also</span></span>
* [<span data-ttu-id="89ccb-126">Проигрыватель holographic удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="89ccb-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
