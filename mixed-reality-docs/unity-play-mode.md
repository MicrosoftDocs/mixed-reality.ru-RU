---
title: Режим воспроизведения Unity
description: Использование режима воспроизведения в редакторе Unity для предварительного просмотра изменений на устройстве без развертывания приложения.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, удаленное взаимодействие, holographic удаленное взаимодействие, удаленный плеер holographic
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548728"
---
# <a name="unity-play-mode"></a><span data-ttu-id="38b1b-104">Режим воспроизведения Unity</span><span class="sxs-lookup"><span data-stu-id="38b1b-104">Unity Play Mode</span></span>

<span data-ttu-id="38b1b-105">Быстрый способ работы с проектом Unity — использование режима воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="38b1b-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="38b1b-106">Это запускает приложение локально в редакторе Unity на компьютере.</span><span class="sxs-lookup"><span data-stu-id="38b1b-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="38b1b-107">Unity использует holographic удаленное взаимодействие, чтобы обеспечить быстрый способ предварительного просмотра содержимого на реальном устройстве HoloLens.</span><span class="sxs-lookup"><span data-stu-id="38b1b-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="38b1b-108">Режим воспроизведения Unity с holographic удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="38b1b-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="38b1b-109">С помощью удаленного взаимодействия с holographic вы можете столкнуться с приложением на HoloLens, пока оно выполняется в редакторе Unity на компьютере.</span><span class="sxs-lookup"><span data-stu-id="38b1b-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="38b1b-110">Входные данные с помощью взгляда, жеста, голоса и пространственного сопоставления отправляются из HoloLens на компьютер.</span><span class="sxs-lookup"><span data-stu-id="38b1b-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="38b1b-111">Затем отображаемые кадры отправляются обратно в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="38b1b-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="38b1b-112">Это отличный способ быстрой отладки приложения без создания и развертывания полного проекта.</span><span class="sxs-lookup"><span data-stu-id="38b1b-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="38b1b-113">На HoloLens перейдите к **Microsoft Store** и установите приложение с удаленным **[взаимодействием holographic](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .</span><span class="sxs-lookup"><span data-stu-id="38b1b-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="38b1b-114">На HoloLens запустите приложение **удаленного проигрывателя holographic** .</span><span class="sxs-lookup"><span data-stu-id="38b1b-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="38b1b-115">В Unity перейдите в меню **окно** и выберите " **holographic Emulator**".</span><span class="sxs-lookup"><span data-stu-id="38b1b-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="38b1b-116">Задайте для **режима эмуляции** значение **удаленно на устройство**.</span><span class="sxs-lookup"><span data-stu-id="38b1b-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="38b1b-117">Для параметра **Удаленный компьютер**введите IP-адрес HoloLens.</span><span class="sxs-lookup"><span data-stu-id="38b1b-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="38b1b-118">Нажмите кнопку **Подключить**.</span><span class="sxs-lookup"><span data-stu-id="38b1b-118">Click **Connect**.</span></span> <span data-ttu-id="38b1b-119">Вы должны увидеть, что **состояние подключения** изменится на **подключено** , и в HoloLens появится пустое окно.</span><span class="sxs-lookup"><span data-stu-id="38b1b-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="38b1b-120">Нажмите кнопку **Воспроизведение** , чтобы запустить режим воспроизведения и начать работу с приложением на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="38b1b-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="38b1b-121">Для удаленного взаимодействия с holographic требуется быстрый ПК и подключение Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="38b1b-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="38b1b-122">Подробные сведения см. в статье об [удаленном проигрывателе holographic](holographic-remoting-player.md) .</span><span class="sxs-lookup"><span data-stu-id="38b1b-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="38b1b-123">Для достижения лучших результатов убедитесь, что приложение правильно устанавливает [фокусную точку](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="38b1b-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="38b1b-124">Это помогает более удачному удаленному взаимодействию лучше адаптировать сцену к задержке беспроводного подключения.</span><span class="sxs-lookup"><span data-stu-id="38b1b-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="38b1b-125">См. также</span><span class="sxs-lookup"><span data-stu-id="38b1b-125">See Also</span></span>
* [<span data-ttu-id="38b1b-126">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="38b1b-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
