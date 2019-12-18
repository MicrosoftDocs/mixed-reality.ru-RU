---
title: Системный жест
description: Системный жест для вызова меню "Пуск".
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Смешанная реальность, жесты, взаимодействие, проектирование
ms.openlocfilehash: 9cfee1104cb9b8135dae51bea73850062fadd25c
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182004"
---
# <a name="system-gesture"></a><span data-ttu-id="3c12e-104">Системный жест</span><span class="sxs-lookup"><span data-stu-id="3c12e-104">System gesture</span></span>

<span data-ttu-id="3c12e-105">Системный жест — это жест руки, используемый для вызова меню "Пуск".</span><span class="sxs-lookup"><span data-stu-id="3c12e-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="3c12e-106">Это эквивалентно нажатию клавиши Windows на клавиатуре, кнопки Xbox на контроллере Xbox или кнопки Windows на контроллере движения головного телефона.</span><span class="sxs-lookup"><span data-stu-id="3c12e-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="3c12e-107">Важно понимать, какие жесты зарезервированы для системы на каждом устройстве смешанной реальности, чтобы предотвратить конфликты при проектировании взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="3c12e-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="3c12e-108">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="3c12e-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3c12e-109"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="3c12e-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3c12e-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3c12e-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3c12e-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3c12e-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="3c12e-112"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="3c12e-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3c12e-113">Цветение</span><span class="sxs-lookup"><span data-stu-id="3c12e-113">Bloom</span></span></td>
        <td><span data-ttu-id="3c12e-114">✔️</span><span class="sxs-lookup"><span data-stu-id="3c12e-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="3c12e-115">Кнопка "назначить"</span><span class="sxs-lookup"><span data-stu-id="3c12e-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3c12e-116">✔️</span><span class="sxs-lookup"><span data-stu-id="3c12e-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="3c12e-117">Взгляд на глаза и ручное сжатие</span><span class="sxs-lookup"><span data-stu-id="3c12e-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3c12e-118">✔️</span><span class="sxs-lookup"><span data-stu-id="3c12e-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="3c12e-119">Цветение</span><span class="sxs-lookup"><span data-stu-id="3c12e-119">Bloom</span></span>
<span data-ttu-id="3c12e-120">Чтобы открыть меню "Пуск" в HoloLens (1-й общий), мы разработали "раскрытия", который представляет собой символическое действие, копируя цветок цветок.</span><span class="sxs-lookup"><span data-stu-id="3c12e-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="3c12e-121">Это отличительная необходимость в взаимодействии с сурефутед, простоте выполнения и быстром отзыве.</span><span class="sxs-lookup"><span data-stu-id="3c12e-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="3c12e-122">Чтобы выполнить жест раскрытия на HoloLens (1-й общий), проведите руку с помощью карманного ПК, а затем откройте руку, добавив пальцы.</span><span class="sxs-lookup"><span data-stu-id="3c12e-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3c12e-123">![раскрытия Close](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="3c12e-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="3c12e-124">**Шаг 1. поладонь с помощью совместного воссоздания**</span><span class="sxs-lookup"><span data-stu-id="3c12e-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3c12e-125">![раскрытия Open](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="3c12e-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="3c12e-126">**Шаг 2. Ручная разворота**</span><span class="sxs-lookup"><span data-stu-id="3c12e-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="3c12e-127">Жест запуска</span><span class="sxs-lookup"><span data-stu-id="3c12e-127">Start gesture</span></span>
<span data-ttu-id="3c12e-128">В HoloLens 2 мы заменили жест раскрытия на виртуальную кнопку, которая обеспечивает более инстинктуалные взаимодействия, не требующие дополнительной обучения.</span><span class="sxs-lookup"><span data-stu-id="3c12e-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="3c12e-129">Показывая пользователям кнопку на ручную, они могут быть понятными и нажимать их с другой стороны.</span><span class="sxs-lookup"><span data-stu-id="3c12e-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3c12e-130">![готовой кнопки "на](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="3c12e-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="3c12e-131">**Шаг 1. Palm, чтобы отобразить кнопку "ручная"**</span><span class="sxs-lookup"><span data-stu-id="3c12e-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3c12e-132">Нажатие кнопки ![ого](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="3c12e-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="3c12e-133">**Шаг 2. Нажмите кнопку "нажимаю"**</span><span class="sxs-lookup"><span data-stu-id="3c12e-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a><span data-ttu-id="3c12e-134">Жест запуска с одной рукой</span><span class="sxs-lookup"><span data-stu-id="3c12e-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3c12e-135">Для работы с однократным жестом запуска:</span><span class="sxs-lookup"><span data-stu-id="3c12e-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="3c12e-136">Необходимо обновить до обновления за ноябрь 2019 (сборка 18363,1039) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="3c12e-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="3c12e-137">Ваши глаза должны быть откалиброваны на устройстве, чтобы отслеживание взгляда было правильно работать.</span><span class="sxs-lookup"><span data-stu-id="3c12e-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="3c12e-138">Если вы не видите точки вокруг значка «начало», то при просмотре на устройстве ваши глаза не будут откалиброваны.</span><span class="sxs-lookup"><span data-stu-id="3c12e-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="3c12e-139">Вы также можете выполнить жест запуска только с одной рукой.</span><span class="sxs-lookup"><span data-stu-id="3c12e-139">You can also perform the Start gesture with only one hand.</span></span> <span data-ttu-id="3c12e-140">Чтобы сделать это, проделайте свое руки и взгляните на **значок "начало** " на своем внутреннем кармане.</span><span class="sxs-lookup"><span data-stu-id="3c12e-140">To do this, hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="3c12e-141">**В то же время следите за значком**, сохранив палец и проиндексировать пальца вместе.</span><span class="sxs-lookup"><span data-stu-id="3c12e-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="3c12e-142">![готовой кнопки "на](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="3c12e-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="3c12e-143">**Шаг 1. Palm, чтобы отобразить кнопку "ручная"**</span><span class="sxs-lookup"><span data-stu-id="3c12e-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3c12e-144">![](images/wrist-button-pinch.png) сжатия кнопки</span><span class="sxs-lookup"><span data-stu-id="3c12e-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="3c12e-145">**Шаг 2. взгляд на кнопку, затем сжатие**</span><span class="sxs-lookup"><span data-stu-id="3c12e-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="3c12e-146">См. также</span><span class="sxs-lookup"><span data-stu-id="3c12e-146">See also</span></span>

* [<span data-ttu-id="3c12e-147">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="3c12e-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="3c12e-148">Направление взгляда</span><span class="sxs-lookup"><span data-stu-id="3c12e-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="3c12e-149">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="3c12e-149">Voice input</span></span>](voice-input.md)
