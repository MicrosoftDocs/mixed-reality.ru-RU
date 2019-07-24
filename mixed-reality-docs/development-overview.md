---
title: Общие сведения о разработке
description: В этой статье описываются основные строительные блоки разработки приложения Windows Mixed Reality.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: Начало работы, основы, HoloLens, HoloLens 2, иммерсивное головной телефон, Unity, Visual Studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873969"
---
# <a name="development-overview"></a>Общие сведения о разработке

Приложения смешанной реальности можно разрабатывать с помощью различных технологий разработки.  HoloLens запускает приложения, созданные с помощью [универсальная платформа Windows](https://dev.windows.com/getstarted).  Впечатляющие головные телефоны запускаются универсальная платформа Windows приложениями, а также приложениями Win32.
Изучив средства по промежуточного слоя, такие как Unity, вы можете приступить к созданию смешанных возможностей в прямом мире.  Используйте [набор средств смешанной реальности](install-the-tools.md) с открытым исходным кодом, чтобы быстро приступить к работе.
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Службы смешанной реальности</a>, такие как <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>, имеют пакеты SDK, которые могут интегрироваться с различными технологиями разработки на разных платформах.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Основы разработки приложений смешанной реальности

Возможности [смешанной реальности](mixed-reality.md) доступны благодаря новым функциям Windows, предназначенным для отображения особенностей окружающей среды. Они позволяют разработчикам размещать [голограмму](hologram.md) в реальном мире, а пользователям — перемещаться по цифровым мирам. 

Ниже приведены основные стандартные блоки развития смешанной реальности:

<table>
<tr>
<th>Ввод</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1-го поколения)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> <a href="gaze.md">Отслеживание направления головы</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">Отслеживание глаз</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> Руки и <a href="gestures.md">жесты</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Голосовые команды</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Игровой планшет</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">Контроллеры движения</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> Восприятие и пространственные функции</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1-го поколения)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">Координаты мира</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">Пространственный звук</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">Пространственное сопоставление</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



Основной моделью взаимодействия для [HoloLens](hololens-hardware-details.md) является [взгляд](gaze.md), [жест](gestures.md) и [голос](voice-input.md) (иногда называется *GGV*). [Иммерсивные гарнитуры Windows Mixed Reality](immersive-headset-hardware-details.md) также используют взгляд и голос, но заменяют [контроллеры движения](motion-controllers.md) на жесты.


Все устройства смешанной реальности под управлением Windows получают преимущества от экосистемы ввода, доступной для Windows, включая мышь, клавиатуру, игровой планшет и т. д. При использовании HoloLens [аппаратные аксессуары](hardware-accessories.md) подключаются через Bluetooth. При использовании иммерсивных гарнитур аксессуары подключаются к главному компьютеру через Bluetooth, USB и другие поддерживаемые протоколы.

Функции обнаружения особенностей окружающей среды, такие как [координаты](coordinate-systems.md), [пространственный звук](spatial-sound.md) и [пространственное сопоставление](spatial-mapping.md), предоставляют необходимые возможности для смешивания реальности. Пространственное сопоставление уникально для HoloLens. Оно позволяет голограммам взаимодействовать как с пользователем, так и с окружающим его физическим миром. Системы координат позволяют движению пользователя влиять на движение в цифровом мире.

[Голограммы](hologram.md) состоят из светлого и звукового эффекта, основанного на более удачной [отрисовке](rendering.md). Ознакомление с основными сведениями о возможностях размещения и сохраняемости, описанных [в этой статье о среде Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) (иногда называемой оболочкой), — отличный способ освоить взаимодействие с пользователем.

## <a name="tools-for-developing-for-mixed-reality"></a>Инструменты для разработки приложений смешанной реальности

Используемые инструменты будут зависеть от [стиля создаваемого приложения](app-views.md).
* [Приложения с двухмерным представлением](building-2d-apps.md) используют инструменты для создания приложений универсальной платформы Windows, подходящих для таких сред, как Windows Phone, ПК и планшеты. Эти приложения являются двухмерными проекциями, размещенными в среде Windows Mixed Reality. Они могут работать на разных типах устройств (включая телефон и компьютер).
* Иммерсивным и голографическим приложениям нужны инструменты, предназначенные для использования API-интерфейсов Windows Mixed Reality. [Рекомендуем использовать Unity](unity-development-overview.md) для создания приложений смешанной реальности. Разработчики, заинтересованные в создании собственного модуля, могут [использовать DirectX и другие API Windows](directx-development-overview.md).

Независимо от типа создаваемого приложения, приведенные ниже инструменты смогут пригодиться вам в разработке:
* [Visual Studio и пакет SDK для Windows](using-visual-studio.md);
* [Портал устройств Windows](using-the-windows-device-portal.md)
* [Эмулятор HoloLens](using-the-hololens-emulator.md) (Ожидается эмулятор HoloLens 2 в ближайшее время)
* [симулятор Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md);
* [Критерии качества приложения](app-quality-criteria.md)

## <a name="see-also"></a>См. также
* [Установка средств](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Службы смешанной реальности</a>
* [Учебники по смешанной реальности](tutorials.md)
* [Проекты с открытым исходным кодом](open-source-projects.md)
* [100. Основы смешанной реальности: начало работы с Unity](holograms-100.md)
* [Минимальные рекомендации по совместимости Windows Mixed Reality с оборудованием ПК](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Отправка приложения в магазин Windows](submitting-an-app-to-the-microsoft-store.md)
