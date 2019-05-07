---
title: Общие сведения о разработке
description: В этой статье описывается разработка приложения Windows Mixed Reality основные стандартные блоки.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: Начало работы, основы, HoloLens, HoloLens 2, иммерсивных гарнитура, unity, visual studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873969"
---
# <a name="development-overview"></a>Общие сведения о разработке

Смешанная реальность приложения можно разрабатывать с использованием широкого спектра технологий.  HoloLens запускает приложения, построенные с помощью [универсальной платформы Windows](https://dev.windows.com/getstarted).  Иммерсивную запуска приложений универсальной платформы Windows, а также приложений Win32.
С первого знакомства с инструментами по промежуточного слоя, например Unity, можно приступить к созданию смешанной реальности возникает сегодня.  Использовать открытым [смешанной реальности Toolkit](install-the-tools.md) быстро приступить к работе.
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Смешанный службы реальностью</a>, такие как <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">пространственных привязки Azure</a>, пакеты SDK, которые можно интегрировать в различные технологии кросс платформенной разработки также имеют.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Основы разработки смешанной реальности

[Смешанной реальности](mixed-reality.md) возможности включены по новые функции Windows разобраться в окружающую среду. Они позволяют разработчикам поместить [голограмма](hologram.md) в реальном мире, и позволить пользователям переходить по цифровой миров разбором буквально о. 

Ниже приведены основные строительные блоки для разработки смешанной реальности.

<table>
<tr>
<th>Ввод</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1-го поколения)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> <a href="gaze.md">HEAD взглядом</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">Взглядом глаз</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> Руки / <a href="gestures.md">жесты</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Голоса</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">Контроллеры движения</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> Восприятие и функции обработки пространственных данных</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1-го поколения)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">Мировые координаты</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">Пространственный звук</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">Пространственное сопоставление</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



Базовая модель взаимодействия для [HoloLens](hololens-hardware-details.md) — [помощи](gaze.md), [жест](gestures.md), и [голоса](voice-input.md), которые иногда называются *GGV* . [Windows Mixed Reality иммерсивную](immersive-headset-hardware-details.md) также используйте взглядом и голоса, но замены [движения контроллеров](motion-controllers.md) для жестов.


Все устройства на базе Windows смешанной реальности преимуществ экосистемы ввода доступны для Windows, включая мышь, клавиатура, игровые панели и многое другое. С HoloLens [стандартные оборудования](hardware-accessories.md) подключены через Bluetooth. Стандартные иммерсивную, подключаться к главным Компьютером через Bluetooth, USB и других поддерживаемых протоколов.

Среды основные сведения о функции, такие как [координаты](coordinate-systems.md), [пространственных звук](spatial-sound.md), и [пространственное сопоставление](spatial-mapping.md) предоставить необходимые возможности для смешивания реальность. Пространственное сопоставление является уникальным для HoloLens и позволяет голограммы для взаимодействия с пользователем и физического мира их. Системы координат Разрешить перемещение пользователя на перемещение в эпоху цифровых технологий.

[Голограммы](hologram.md) вносятся света и звука, которые используют [holographic отрисовки](rendering.md). Основные сведения о возможности размещения и сохраняемости, как показано в [Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md) (иногда называется «оболочка») это отличный способ Обеспечьте собственное заземление во взаимодействие с пользователем.

## <a name="tools-for-developing-for-mixed-reality"></a>Средства разработки для смешанной реальности

Будет зависеть от средства, [стиль приложения](app-views.md) требуется выполнить сборку.
* [Приложений с помощью двухмерное](building-2d-apps.md) использовать инструменты для создания приложений универсальной платформы Windows подходит для сред, например Windows Phone, ПК и планшеты. Эти приложения есть опыт работы как двумерный проекции, помещаются в Windows Mixed Reality домашней и может работать в разных разных типов устройств (включая phone и ПК).
* Holographic и иммерсивных приложений требуются инструменты, преимущества смешанной реальности API-интерфейсов Windows. Мы [рекомендуем использовать Unity](unity-development-overview.md) для создания приложений для смешанной реальности. Разработчики, заинтересованных в создании собственных ядра могут [использования DirectX и другие API-интерфейсы Windows](directx-development-overview.md).

Независимо от типа приложения, которые вы создаете эти средства будут упрощают процесс разработки приложения:
* [Visual Studio и Windows SDK](using-visual-studio.md)
* [Портал устройств Windows](using-the-windows-device-portal.md)
* [Эмулятор HoloLens](using-the-hololens-emulator.md) (эмулятор HoloLens 2 ожидается в ближайшее время)
* [Симулятор Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Критерии качества приложения](app-quality-criteria.md)

## <a name="see-also"></a>См. также
* [Установка средств](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Смешанная реальность служб</a>
* [Учебники смешанной реальности](tutorials.md)
* [Проекты с открытым кодом](open-source-projects.md)
* [100. Основы смешанной реальности: начало работы с Unity](holograms-100.md)
* [Windows Mixed Reality минимальное ПК совместимости рекомендаций по оборудованию](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Отправка приложения в Windows Store](submitting-an-app-to-the-microsoft-store.md)
