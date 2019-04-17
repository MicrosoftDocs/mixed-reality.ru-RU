---
title: Проигрыватель holographic удаленного взаимодействия
description: Holographic проигрыватель удаленного взаимодействия является сопутствующее приложение, которое подключается к ПК приложений и игр, которые поддерживают удаленное взаимодействие Holographic. Holographic удаленного взаимодействия потоковую передачу holographic из ПК вашей Microsoft HoloLens в режиме реального времени, с помощью подключения Wi-Fi.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, Holographic удаленного взаимодействия
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605003"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="d51f5-105">Проигрыватель holographic удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d51f5-105">Holographic Remoting Player</span></span>

<span data-ttu-id="d51f5-106">Holographic проигрыватель удаленного взаимодействия является сопутствующее приложение, которое подключается к ПК приложений и игр, которые поддерживают удаленное взаимодействие Holographic.</span><span class="sxs-lookup"><span data-stu-id="d51f5-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="d51f5-107">Holographic удаленного взаимодействия потоковую передачу holographic из ПК вашей Microsoft HoloLens в режиме реального времени, с помощью подключения Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="d51f5-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="d51f5-108">Holographic проигрыватель удаленного взаимодействия может использоваться только с помощью приложений, которые специально предназначены для поддержки Holographic удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d51f5-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

> [!NOTE]
> <span data-ttu-id="d51f5-109">Дополнительные рекомендации, относящиеся к HoloLens 2 [ожидается в ближайшее время](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="d51f5-109">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="d51f5-110">Подключение к исполнителю Holographic удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d51f5-110">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="d51f5-111">Следуйте инструкциям вашего приложения, чтобы подключиться к Holographic проигрыватель удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d51f5-111">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="d51f5-112">Будет необходимо ввести IP-адрес устройства HoloLens, который можно увидеть на главном экране игрока удаленного взаимодействия, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d51f5-112">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![Проигрыватель holographic удаленного взаимодействия](images/holographicremotingplayer.png)

<span data-ttu-id="d51f5-114">Каждый раз, когда вы видите в главном окне, вы будете знать, что у вас нет подключения приложения.</span><span class="sxs-lookup"><span data-stu-id="d51f5-114">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="d51f5-115">Обратите внимание, что соединение удаленного взаимодействия holographic **не зашифрован**.</span><span class="sxs-lookup"><span data-stu-id="d51f5-115">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="d51f5-116">Следует всегда использовать Holographic удаленного взаимодействия через безопасное подключение Wi-Fi, вы доверяете.</span><span class="sxs-lookup"><span data-stu-id="d51f5-116">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="d51f5-117">Качество и производительность</span><span class="sxs-lookup"><span data-stu-id="d51f5-117">Quality and Performance</span></span>

<span data-ttu-id="d51f5-118">Качество и производительность работы зависит от трех факторов:</span><span class="sxs-lookup"><span data-stu-id="d51f5-118">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="d51f5-119">**Голографический интерфейс, вы используете** -приложений, которые отображают содержимое с высоким разрешением или очень подробные может потребоваться быстрее ПК или быстрее беспроводного подключения.</span><span class="sxs-lookup"><span data-stu-id="d51f5-119">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="d51f5-120">**Оборудование компьютера** -свой компьютер должен иметь возможность запуска и кодирования в голографический интерфейс в 60 кадров в секунду.</span><span class="sxs-lookup"><span data-stu-id="d51f5-120">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="d51f5-121">Для видеокарты обычно рекомендуется GeForce GTX 970 или AMD Radeon R9 290 или выше.</span><span class="sxs-lookup"><span data-stu-id="d51f5-121">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="d51f5-122">Опять же к конкретным вариантом может потребоваться более поздней версии или нижней части карточки.</span><span class="sxs-lookup"><span data-stu-id="d51f5-122">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="d51f5-123">**Подключение к Wi-Fi** -вашей голографический интерфейс передаются через Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="d51f5-123">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="d51f5-124">Используйте быстрой сети с низкой перегрузки для повышения качества.</span><span class="sxs-lookup"><span data-stu-id="d51f5-124">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="d51f5-125">С помощью компьютера, подключенного через кабель Ethernet, вместо того чтобы Wi-Fi, может также повысить качество.</span><span class="sxs-lookup"><span data-stu-id="d51f5-125">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="d51f5-126">Диагностика</span><span class="sxs-lookup"><span data-stu-id="d51f5-126">Diagnostics</span></span>

<span data-ttu-id="d51f5-127">Чтобы измерить качество подключения, скажем **«включить диагностику»** while на главном экране Holographic проигрывателя удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d51f5-127">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="d51f5-128">Когда включены диагностические сообщения, приложение будет отображать вы:</span><span class="sxs-lookup"><span data-stu-id="d51f5-128">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="d51f5-129">**FPS** — среднее число отрисованные кадры проигрыватель удаленного взаимодействия получение и Подготовка к просмотру в секунду.</span><span class="sxs-lookup"><span data-stu-id="d51f5-129">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="d51f5-130">Идеальный вариант — 60 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="d51f5-130">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="d51f5-131">**Задержка** -среднее количество времени, необходимое для кадра для перехода с ПК, HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d51f5-131">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="d51f5-132">Чем меньше, тем лучше.</span><span class="sxs-lookup"><span data-stu-id="d51f5-132">The lower the better.</span></span> <span data-ttu-id="d51f5-133">Это во многом зависит от вашей сети Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="d51f5-133">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="d51f5-134">В главном окне, можно сказать **«отключить диагностику»** Чтобы отключить диагностику.</span><span class="sxs-lookup"><span data-stu-id="d51f5-134">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="d51f5-135">Требования к системе ПК</span><span class="sxs-lookup"><span data-stu-id="d51f5-135">PC System Requirements</span></span>
* <span data-ttu-id="d51f5-136">Компьютер **необходимо** работать под управлением Windows 10 Anniversary Update.</span><span class="sxs-lookup"><span data-stu-id="d51f5-136">Your PC **must** be running the Windows 10 Anniversary Update.</span></span>
* <span data-ttu-id="d51f5-137">Мы рекомендуем GeForce GTX 970 или AMD Radeon R9 290 или лучше видеокарте.</span><span class="sxs-lookup"><span data-stu-id="d51f5-137">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="d51f5-138">Мы рекомендуем подключении компьютера к сети через ethernet, чтобы уменьшить количество прыжков беспроводной связи.</span><span class="sxs-lookup"><span data-stu-id="d51f5-138">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="d51f5-139">См. также</span><span class="sxs-lookup"><span data-stu-id="d51f5-139">See Also</span></span>
* [<span data-ttu-id="d51f5-140">Условия лицензионного соглашения на использование программного обеспечения holographic удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d51f5-140">Holographic remoting software license terms</span></span>](microsoft-holographic-remoting-software-license-terms.md)
* [<span data-ttu-id="d51f5-141">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="d51f5-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
