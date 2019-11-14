---
title: Системный жест
description: Системный жест для вызова меню "Пуск".
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Смешанная реальность, жесты, взаимодействие, проектирование
ms.openlocfilehash: 417811fff9d98e459dc0047d46ea065acfced4ef
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064240"
---
# <a name="system-gesture"></a><span data-ttu-id="6d7b8-104">Системный жест</span><span class="sxs-lookup"><span data-stu-id="6d7b8-104">System gesture</span></span>

<span data-ttu-id="6d7b8-105">Системный жест — это жест руки, используемый для вызова меню "Пуск".</span><span class="sxs-lookup"><span data-stu-id="6d7b8-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="6d7b8-106">Это эквивалентно нажатию клавиши Windows на клавиатуре, кнопки Xbox на контроллере Xbox или кнопки Windows на контроллере движения головного телефона.</span><span class="sxs-lookup"><span data-stu-id="6d7b8-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="6d7b8-107">Важно понимать, какие жесты зарезервированы для системы на каждом устройстве смешанной реальности, чтобы предотвратить конфликты при проектировании взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="6d7b8-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="6d7b8-108">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="6d7b8-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6d7b8-109"><strong>Функциями</strong></span><span class="sxs-lookup"><span data-stu-id="6d7b8-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="6d7b8-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6d7b8-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6d7b8-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6d7b8-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6d7b8-112"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="6d7b8-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6d7b8-113">Раскрытия</span><span class="sxs-lookup"><span data-stu-id="6d7b8-113">Bloom</span></span></td>
        <td><span data-ttu-id="6d7b8-114">✔️</span><span class="sxs-lookup"><span data-stu-id="6d7b8-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="6d7b8-115">Кнопка "назначить"</span><span class="sxs-lookup"><span data-stu-id="6d7b8-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="6d7b8-116">✔️</span><span class="sxs-lookup"><span data-stu-id="6d7b8-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="6d7b8-117">Взгляд на глаза и ручное сжатие</span><span class="sxs-lookup"><span data-stu-id="6d7b8-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="6d7b8-118">✔️</span><span class="sxs-lookup"><span data-stu-id="6d7b8-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="6d7b8-119">Раскрытия</span><span class="sxs-lookup"><span data-stu-id="6d7b8-119">Bloom</span></span>
<span data-ttu-id="6d7b8-120">Чтобы открыть меню "Пуск" в HoloLens (1-й общий), мы разработали "раскрытия", который представляет собой символическое действие, копируя цветок цветок.</span><span class="sxs-lookup"><span data-stu-id="6d7b8-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="6d7b8-121">Это отличительная необходимость в взаимодействии с сурефутед, простоте выполнения и быстром отзыве.</span><span class="sxs-lookup"><span data-stu-id="6d7b8-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="6d7b8-122">Чтобы выполнить жест раскрытия на HoloLens (1-й общий), проведите руку с помощью карманного ПК, а затем откройте руку, добавив пальцы.</span><span class="sxs-lookup"><span data-stu-id="6d7b8-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="6d7b8-123">![раскрытия Close](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="6d7b8-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="6d7b8-124">**Шаг 1. поладонь с помощью совместного воссоздания**</span><span class="sxs-lookup"><span data-stu-id="6d7b8-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6d7b8-125">![раскрытия Open](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="6d7b8-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="6d7b8-126">**Шаг 2. Ручная разворота**</span><span class="sxs-lookup"><span data-stu-id="6d7b8-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a><span data-ttu-id="6d7b8-127">Кнопка "назначить"</span><span class="sxs-lookup"><span data-stu-id="6d7b8-127">Wrist button</span></span>
<span data-ttu-id="6d7b8-128">В HoloLens 2 мы заменили жест раскрытия на виртуальную кнопку, которая обеспечивает более инстинктуалные взаимодействия, не требующие дополнительной обучения.</span><span class="sxs-lookup"><span data-stu-id="6d7b8-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="6d7b8-129">Показывая пользователям кнопку на ручную, они могут быть понятными и нажимать их с другой стороны.</span><span class="sxs-lookup"><span data-stu-id="6d7b8-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="6d7b8-130">![готовой кнопки "на](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="6d7b8-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="6d7b8-131">**Шаг 1. Palm, чтобы отобразить кнопку "ручная"**</span><span class="sxs-lookup"><span data-stu-id="6d7b8-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6d7b8-132">Нажатие кнопки ![ого](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="6d7b8-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="6d7b8-133">**Шаг 2. Нажмите кнопку "нажимаю"**</span><span class="sxs-lookup"><span data-stu-id="6d7b8-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a><span data-ttu-id="6d7b8-134">Глаз-взгляд и ручное сжатие</span><span class="sxs-lookup"><span data-stu-id="6d7b8-134">Eye-gaze and palm up pinch</span></span>
<span data-ttu-id="6d7b8-135">Мы также разработали однонаправленное решение для простоты доступа в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6d7b8-135">We have also designed a one-handed solution for ease of access in HoloLens 2.</span></span> <span data-ttu-id="6d7b8-136">Этот жест требует от пользователя взглянуть на кнопку Palm, а затем используйте ту же руку для ручного сжатия с помощью бегунка и указателя пальца.</span><span class="sxs-lookup"><span data-stu-id="6d7b8-136">This gesture requires users to eye gaze at the wrist button, then use the same hand to perform a palm up pinch using their thumb and index finger.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="6d7b8-137">![готовой кнопки "на](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="6d7b8-137">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="6d7b8-138">**Шаг 1. Palm, чтобы отобразить кнопку "ручная"**</span><span class="sxs-lookup"><span data-stu-id="6d7b8-138">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6d7b8-139">![](images/wrist-button-pinch.png) сжатия кнопки</span><span class="sxs-lookup"><span data-stu-id="6d7b8-139">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="6d7b8-140">**Шаг 2. взгляд на кнопку, затем сжатие**</span><span class="sxs-lookup"><span data-stu-id="6d7b8-140">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="6d7b8-141">См. также</span><span class="sxs-lookup"><span data-stu-id="6d7b8-141">See also</span></span>

* [<span data-ttu-id="6d7b8-142">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="6d7b8-142">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="6d7b8-143">Направление взгляда</span><span class="sxs-lookup"><span data-stu-id="6d7b8-143">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="6d7b8-144">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="6d7b8-144">Voice input</span></span>](voice-input.md)
