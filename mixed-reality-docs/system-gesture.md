---
title: Системный жест
description: Системный жест для вызова меню "Пуск".
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Смешанная реальность, жесты, взаимодействие, проектирование
ms.openlocfilehash: b46f642babb18387da2e76d5bdbb7631577c85de
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439825"
---
# <a name="system-gesture"></a><span data-ttu-id="f0ee3-104">Системный жест</span><span class="sxs-lookup"><span data-stu-id="f0ee3-104">System gesture</span></span>

<span data-ttu-id="f0ee3-105">Системный жест — это жест руки, используемый для вызова меню "Пуск".</span><span class="sxs-lookup"><span data-stu-id="f0ee3-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="f0ee3-106">Это эквивалентно нажатию клавиши Windows на клавиатуре, кнопки Xbox на контроллере Xbox или кнопки Windows на контроллере движения головного телефона.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="f0ee3-107">Важно понимать, какие жесты зарезервированы для системы на каждом устройстве смешанной реальности, чтобы предотвратить конфликты при проектировании взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="f0ee3-108">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="f0ee3-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f0ee3-109"><strong>Функциями</strong></span><span class="sxs-lookup"><span data-stu-id="f0ee3-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f0ee3-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="f0ee3-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f0ee3-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f0ee3-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f0ee3-112"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="f0ee3-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f0ee3-113">Раскрытия</span><span class="sxs-lookup"><span data-stu-id="f0ee3-113">Bloom</span></span></td>
        <td><span data-ttu-id="f0ee3-114">✔️</span><span class="sxs-lookup"><span data-stu-id="f0ee3-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="f0ee3-115">Кнопка "назначить"</span><span class="sxs-lookup"><span data-stu-id="f0ee3-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="f0ee3-116">✔️</span><span class="sxs-lookup"><span data-stu-id="f0ee3-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="f0ee3-117">Взгляд на глаза и ручное сжатие</span><span class="sxs-lookup"><span data-stu-id="f0ee3-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="f0ee3-118">✔️</span><span class="sxs-lookup"><span data-stu-id="f0ee3-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="f0ee3-119">Раскрытия</span><span class="sxs-lookup"><span data-stu-id="f0ee3-119">Bloom</span></span>
<span data-ttu-id="f0ee3-120">Чтобы открыть меню "Пуск" в HoloLens (1-й общий), мы разработали "раскрытия", который представляет собой символическое действие, копируя цветок цветок.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="f0ee3-121">Это отличительная необходимость в взаимодействии с сурефутед, простоте выполнения и быстром отзыве.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="f0ee3-122">Чтобы выполнить жест раскрытия на HoloLens (1-й общий), проведите руку с помощью карманного ПК, а затем откройте руку, добавив пальцы.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f0ee3-123">![раскрытия Close](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="f0ee3-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="f0ee3-124">**Шаг 1. поладонь с помощью совместного воссоздания**</span><span class="sxs-lookup"><span data-stu-id="f0ee3-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f0ee3-125">![раскрытия Open](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="f0ee3-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="f0ee3-126">**Шаг 2. воссоздание карманного ПК с помощью прочтения**</span><span class="sxs-lookup"><span data-stu-id="f0ee3-126">**Step 2: Palm up with fingertips spreaded**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a><span data-ttu-id="f0ee3-127">Кнопка "назначить"</span><span class="sxs-lookup"><span data-stu-id="f0ee3-127">Wrist button</span></span>
<span data-ttu-id="f0ee3-128">В HoloLens 2 мы заменили жест раскрытия на виртуальную кнопку, которая обеспечивает более инстинктуалные взаимодействия, не требующие дополнительной обучения.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="f0ee3-129">Показывая пользователям кнопку на ручную, они могут быть понятными и нажимать их с другой стороны.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f0ee3-130">![готовой кнопки "на](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="f0ee3-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="f0ee3-131">**Шаг 1. Palm, чтобы отобразить кнопку "ручная"**</span><span class="sxs-lookup"><span data-stu-id="f0ee3-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f0ee3-132">Нажатие кнопки ![ого](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="f0ee3-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="f0ee3-133">**Шаг 2. Нажмите кнопку "нажимаю"**</span><span class="sxs-lookup"><span data-stu-id="f0ee3-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a><span data-ttu-id="f0ee3-134">Глаз-взгляд и ручное сжатие</span><span class="sxs-lookup"><span data-stu-id="f0ee3-134">Eye-gaze and palm up pinch</span></span>
<span data-ttu-id="f0ee3-135">Мы также разработали однонаправленное решение для простоты доступа в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-135">We have also designed a one-handed solution for ease of access in HoloLens 2.</span></span> <span data-ttu-id="f0ee3-136">Этот жест требует от пользователя взглянуть на кнопку Palm, а затем используйте ту же руку для ручного сжатия с помощью бегунка и указателя пальца.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-136">This gesture requires users to eye gaze at the wrist button, then use the same hand to perform a palm up pinch using their thumb and index finger.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="f0ee3-137">![готовой кнопки "на](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="f0ee3-137">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="f0ee3-138">**Шаг 1. Palm, чтобы отобразить кнопку "ручная"**</span><span class="sxs-lookup"><span data-stu-id="f0ee3-138">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f0ee3-139">![](images/wrist-button-pinch.png) сжатия кнопки</span><span class="sxs-lookup"><span data-stu-id="f0ee3-139">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="f0ee3-140">**Шаг: Просмотр глаз на кнопке, затем сжатие**</span><span class="sxs-lookup"><span data-stu-id="f0ee3-140">**Step: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="f0ee3-141">См. также</span><span class="sxs-lookup"><span data-stu-id="f0ee3-141">See also</span></span>

* [<span data-ttu-id="f0ee3-142">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="f0ee3-142">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="f0ee3-143">Направление взгляда</span><span class="sxs-lookup"><span data-stu-id="f0ee3-143">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="f0ee3-144">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="f0ee3-144">Voice input</span></span>](voice-input.md)
