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
# <a name="system-gesture"></a>Системный жест

Системный жест — это жест руки, используемый для вызова меню "Пуск". Это эквивалентно нажатию клавиши Windows на клавиатуре, кнопки Xbox на контроллере Xbox или кнопки Windows на контроллере движения головного телефона. Важно понимать, какие жесты зарезервированы для системы на каждом устройстве смешанной реальности, чтобы предотвратить конфликты при проектировании взаимодействий.

## <a name="device-support"></a>Поддержка устройств

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Функциями</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></td>
    </tr>
     <tr>
        <td>Раскрытия</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Кнопка "назначить"</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Взгляд на глаза и ручное сжатие</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Раскрытия
Чтобы открыть меню "Пуск" в HoloLens (1-й общий), мы разработали "раскрытия", который представляет собой символическое действие, копируя цветок цветок. Это отличительная необходимость в взаимодействии с сурефутед, простоте выполнения и быстром отзыве. Чтобы выполнить жест раскрытия на HoloLens (1-й общий), проведите руку с помощью карманного ПК, а затем откройте руку, добавив пальцы.

:::row:::
    :::column:::
        ![раскрытия Close](images/bloom-close.png)<br>
        **Шаг 1. поладонь с помощью совместного воссоздания**<br>
    :::column-end:::
    :::column:::
        ![раскрытия Open](images/bloom-open.png)<br>
        **Шаг 2. Ручная разворота**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a>Кнопка "назначить"
В HoloLens 2 мы заменили жест раскрытия на виртуальную кнопку, которая обеспечивает более инстинктуалные взаимодействия, не требующие дополнительной обучения. Показывая пользователям кнопку на ручную, они могут быть понятными и нажимать их с другой стороны.

:::row:::
    :::column:::
        ![готовой кнопки "на](images/wrist-button-ready.png)<br>
        **Шаг 1. Palm, чтобы отобразить кнопку "ручная"**<br>
    :::column-end:::
    :::column:::
        Нажатие кнопки ![ого](images/wrist-button-press.png)<br>
        **Шаг 2. Нажмите кнопку "нажимаю"**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a>Глаз-взгляд и ручное сжатие
Мы также разработали однонаправленное решение для простоты доступа в HoloLens 2. Этот жест требует от пользователя взглянуть на кнопку Palm, а затем используйте ту же руку для ручного сжатия с помощью бегунка и указателя пальца.<br>
:::row:::
    :::column:::
        ![готовой кнопки "на](images/wrist-button-ready.png)<br>
        **Шаг 1. Palm, чтобы отобразить кнопку "ручная"**<br>
    :::column-end:::
    :::column:::
        ![](images/wrist-button-pinch.png) сжатия кнопки<br>
        **Шаг 2. взгляд на кнопку, затем сжатие**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>См. также

* [Инстинктивное взаимодействие](interaction-fundamentals.md)
* [Направление взгляда](eye-tracking.md)
* [Голосовой ввод](voice-input.md)
