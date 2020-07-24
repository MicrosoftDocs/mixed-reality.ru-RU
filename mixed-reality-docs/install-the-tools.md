---
title: Установка инструментов
description: Ознакомьтесь с этой статьей, чтобы подготовиться к разработке решений смешанной реальности. В этой статье всегда должны быть указаны самые последние версии Unity, Visual Studio и других инструментов, рекомендованных для разработки приложений для иммерсивных гарнитур HoloLens и Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 3/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit
ms.openlocfilehash: ac3e4967ce687f7cb3009de64748841f88562a92
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86447946"
---
# <a name="install-the-tools"></a>Установка инструментов

Получите инструменты, необходимые для создания приложений для иммерсивных гарнитур (гарнитур виртуальной реальности) Microsoft HoloLens и Windows Mixed Reality. Для разработки решений для Windows Mixed Reality не существует отдельного пакета SDK. Вы будете использовать Visual Studio с пакетом SDK для Windows 10.

У вас нет устройства смешанной реальности? Вы можете установить [эмулятор HoloLens](using-the-hololens-emulator.md), чтобы протестировать отдельные функции приложений смешанной реальности без HoloLens. Вы также можете использовать [симулятор Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md), чтобы протестировать приложения смешанной реальности для иммерсивных гарнитур. Если вы работаете с Unity, вы можете использовать имитацию ввода, предлагаемую [набором средств для смешанной реальности (МРТК)](https://github.com/Microsoft/MixedRealityToolkit-Unity), чтобы протестировать разные типы взаимодействий ввода, например с помощью отслеживания взгляда или движений рук.

Рекомендуем установить игровой модуль Unity — это самый простой способ приступить к созданию приложений смешанной реальности. Кроме того, вы можете воспользоваться DirectX, если захотите использовать собственный модуль.

>[!TIP]
>Добавьте эту страницу в закладки и регулярно просматривайте ее, чтобы быть в курсе самых последних версий каждого инструмента, рекомендованного для разработки приложений смешанной реальности.

<br>

## <a name="installation-checklist"></a>Контрольный список установки


| Средство | Примечания |
|---------|---------|
| ![Логотип Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (ссылка для установки вручную)</a><br><br>Установите самую последнюю версию Windows 10, чтобы операционная система вашего компьютера соответствовала платформе, для которой вы создаете приложения смешанной реальности.  | **Установка Windows 10** <br> Вы можете установить последнюю версию Windows 10 с помощью клиентского компонента Центра обновления Windows, к которому можно перейти в разделе параметров, или путем создания установочного носителя (открыв ссылку, указанную в левом столбце). <br><br>Сведения о новых функциях смешанной реальности, доступных в каждом выпуске Windows 10, см. в [заметках о текущем выпуске](release-notes-october-2018.md). **Включите режим разработчика на компьютере** в разделе "Параметры > Обновление и безопасность > Для разработчиков". <br><br> **Примечание, касающееся корпоративных компьютеров**<br>Если вашим компьютером управляет ИТ-отдел вашей организации, возможно, вам потребуется связаться с его сотрудниками для обновления. <br><br> **N-версии Windows**<br> Иммерсивные гарнитуры (виртуальная реальность) Windows Mixed Reality не поддерживаются в N-версиях Windows. |
| ![Логотип Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (версии 16.2 или более поздней)** (ссылка для установки)</a> <br><br>Полнофункциональная интегрированная среда разработки (IDE) для Windows и многое другое. Вы будете использовать Visual Studio для написания кода, отладки, тестирования и развертывания. | Установите следующие рабочие нагрузки: <br><br>**● Разработка классических приложений на C++**<br>**● Разработка приложений универсальной платформы Windows (UWP)**<br><br>В рабочей нагрузке UWP обязательно проверьте следующий дополнительный компонент, если вы выполняете разработку для HoloLens:<br><br>**● Подключение USB-устройств**<br><br>**Примечание, касающееся Unity**<br>Если вам не нужно устанавливать более новую (не LTS) версию Unity для своих задач, мы рекомендуем *не* устанавливать рабочую нагрузку Unity в составе установки Visual Studio, а вместо этого установить версию **Unity 2019 LTS**, как показано ниже.<br><br>**Примечание**<br>Сейчас в Visual Studio 2019 (версия 16.0) существует ряд известных проблем с отладкой приложений смешанной реальности.  Обновите **Visual Studio 2019 до версии не ниже 16.2**. |
| ![Логотип Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Пакет SDK для Windows 10 (10.0.18362.0)** (ссылка для установки вручную)</a> <br><br>Содержит новейшие заголовки, библиотеки, метаданные и средства для создания приложений для Windows 10 в HoloLens 2. | **Для создания приложений HoloLens 2 потребуется установить пакет Windows SDK сборки 18362 или более поздней.**<br> <br> Если вы разрабатываете приложения только для настольных гарнитур Windows Mixed Reality или HoloLens (1-го поколения), можно использовать пакет SDK для Windows, установленный в Visual Studio 2017. |
| ![Логотип Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2132415" target="_blank">**Эмулятор HoloLens 2 (Windows Holographic, версия 2004 с обновлением за июнь 2020 г.)** (ссылка для установки: 10.0.19041.1106)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Эмулятор HoloLens (1-го поколения)** (ссылка для установки: 10.0.17763.134)</a> <br><br>Эмулятор позволяет запускать приложения с помощью образа виртуальной машины HoloLens без физического устройства HoloLens.<br> <br> | Дополнительные сведения об использовании эмулятора HoloLens см. в [этой статье](using-the-hololens-emulator.md).<br> <br> Для успешной установки эмулятора **ваша система должна поддерживать Hyper-V**. Подробные сведения см. в разделе о системных требованиях. <br>|

## <a name="choose-your-engine"></a>Выберите подсистему

:::row:::
    :::column:::
        <a href="https://unity3d.com/unity/qa/lts-releases" target="_blank">![Unity](images/unity_logo.png)<br>**Unity**</a><br>
        Обычно в качестве лучшей версии для запуска новых проектов мы рекомендуем Unity LTS (долгосрочная поддержка). Затем ее можно обновить до последней версии, чтобы получить новые стабильные исправления.<br>
        <br>
        Сейчас рекомендуем использовать **Unity 2019** — сборку LTS, необходимую для MRTK версии 2 (см. ниже).<br>
        <br>
        Некоторые разработчики по определенным причинам могут использовать другую версию Unity. В этих случаях Unity поддерживает параллельную установку различных версий.<br>
        <br>
        См. сведения о [разработке приложений Unity для иммерсивных гарнитур Windows Mixed Reality или HoloLens 2](unity-development-overview.md).<br>
        <br>
    :::column-end:::
    :::column:::
        <a href="https://docs.unrealengine.com//GettingStarted/Installation/index.html" target="_blank">![Unreal](images/Unreal_logo.png)<br>**Unreal**</a><br>
        Unreal Engine 4 — это мощная подсистема разработки с открытым кодом, обладающая полной поддержкой смешанной реальности в C++ и Blueprints.<br>
        <br>
        Начиная с версии Unreal Engine 4.25, поддержка HoloLens считается полной и пригодной для рабочей среды.<br>
        <br>
        См. сведения о [разработке Unreal для HoloLens 2](unreal-development-overview.md).
    :::column-end:::
    :::column:::
        ![Разработка собственных приложений](images/visualstudio-small_logo.png)<br>
        [**Собственные решения (OpenXR)** ](openxr-getting-started.md)<br>
        OpenXR — это открытый бесплатный стандарт API из Khronos, который предоставляет возможности собственного доступа к широкому спектру устройств от многих поставщиков решений смешанной реальности.  Проект <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> демонстрирует простой пример OpenXR с двумя файлами проекта Visual Studio — один для классического приложения Win32, а другой для приложения UWP HoloLens 2.<br>
        <br>
        <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">**Собственные решения (WinRT)** </a><br>
        <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">Шаблоны приложений Windows Mixed Reality</a> содержат все необходимое, чтобы приступить к созданию приложений смешанной реальности с помощью DirectX и собственных API. Включают в себя цикл отрисовки (или "игровой цикл"), вспомогательный класс DeviceResources для управления устройством и контекстом Direct3D, а также простой пример отрисовщика голограмм. Доступны для Direct3D 11 и Direct3D 12.<br>
        <br>
        См. сведения о [собственной разработке](directx-development-overview.md), чтобы приступить к разработке собственных приложений с помощью WinRT или OpenXR для иммерсивных гарнитур Windows Mixed Reality или HoloLens 2.
    :::column-end:::
:::row-end:::

<br>

## <a name="mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK)
![MRTK](images/UX/MRTK_UX_Hero.png)

Набор средств для смешанной реальности (MRTK) — это кроссплатформенный пакет SDK с открытым кодом для приложений смешанной реальности. MRTK предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий. Набор используется для ускорения разработки приложений, предназначенных для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](images/MRTK_Badge_Unity.png)<br>**Набор средств для смешанной реальности — Unity (GitHub)** </a><br>
    :::column-end:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](images/MRTK_Badge_Unreal.png)<br>**Набор средств для смешанной реальности — Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

### <a name="other-tools"></a>Другие средства
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Вспомогательный набор средств для смешанной реальности (GitHub)</a> — фрагменты кода и компоненты, которые не могут работать непосредственно в HoloLens или иммерсивных гарнитурах (гарнитурах виртуальной реальности), но могут объединяться с ними для взаимодействия в Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Набор средств для смешанной реальности — общий (GitHub)</a>. Это коллекция общих скриптов и компонентов.


## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Настройка компьютера для разработки приложений смешанной реальности

Этот пакет SDK для Windows 10 лучше всего использовать в операционной системе Windows 10. Он также поддерживается в следующих операционных системах: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Обратите внимание, что не все средства поддерживаются в операционных системах более ранних версий. 

### <a name="for-hololens-development"></a>Для разработки решений для HoloLens

При настройке компьютера для разработки решений для HoloLens убедитесь, что он соответствует системным требованиям для <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> и <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Если вы планируете использовать эмулятор HoloLens, ваш компьютер должен отвечать системным требованиям [этого эмулятора](using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Сведения о начале работы с эмулятором HoloLens см. в [этой статье](using-the-hololens-emulator.md).

Если вы планируете разработку приложений для иммерсивных гарнитур (гарнитур виртуальной реальности) HoloLens и Windows Mixed Reality, ознакомьтесь с системными рекомендациями и требованиями в приведенном ниже разделе.

### <a name="for-immersive-vr-headset-development"></a>Для разработки приложений для иммерсивных гарнитур (виртуальная реальность)

>[!NOTE]
>Приведенные ниже рекомендации являются действующими минимальными и рекомендуемыми характеристиками для *компьютера, где будут разрабатываться приложения* для иммерсивных гарнитур (гарнитур виртуальной реальности). Эти рекомендации регулярно обновляются.

>[!WARNING]
>Не путайте их с [минимальными рекомендациями по совместимости аппаратного обеспечения компьютера](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), в которых изложены *спецификации компьютера потребителя*, на которые следует ориентироваться при работе с приложением или игрой, используемых с иммерсивной гарнитурой (виртуальная реальность).

Если на компьютере для разработки решений для иммерсивных гарнитур отсутствуют полноразмерные порты HDMI и (или) USB 3.0, для подключения гарнитуры вам потребуются [адаптеры](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).

Сейчас есть [известные проблемы](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) с некоторыми аппаратными конфигурациями, особенно на ноутбуках с гибридной графикой.

<table>
<tr>
<th></th><th> Минимальные требования</th><th> Рекомендуется</th>
</tr><tr>
<td> Процессор</td><td> <b>Ноутбук:</b> двухъядерный ЦП Intel Core i5 для мобильных систем 7-го поколения с технологией Hyper-Threading. <b>Настольный компьютер:</b> двухъядерный ЦП Intel i5 для настольных систем 6-го поколения с технологией Hyper-Threading <b>или</b> эквивалентный четырехъядерный процессор AMD FX4350 с частотой 4,2 ГГц.</td><td> <b>Настольный компьютер:</b> Intel i7 для настольных систем 6-го поколения (6 ядер) <b>или</b> AMD Ryzen 5 1600 (6 ядер, 12 потоков).</td>
</tr><tr>
<td> Графический процессор</td><td> <b>Ноутбук:</b> графический процессор, эквивалентный NVIDIA GTX 965M, AMD RX 460M (2 ГБ) или более мощным процессорам с поддержкой DX12; <b>настольный компьютер:</b> графический процессор, эквивалентный NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 ГБ) или более мощным процессорам с поддержкой DX12</td><td><b>Настольный компьютер:</b> графический процессор, эквивалентный NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 ГБ) или более мощным процессорам с поддержкой DX12</td>
</tr><tr>
<td> Версия WDDM драйвера графического процессора</td><td colspan="2"> Драйвер WDDM 2.2</td>
</tr><tr>
<td> Тепловая мощность</td><td colspan="2"> 15 Вт или выше</td>
</tr><tr>
<td> Порты для графического отображения</td><td colspan="2"> 1 доступный порт графического отображения для гарнитуры (HDMI 1.4 или DisplayPort 1.2 для гарнитур с частотой 60 Гц, HDMI 2.0 или DisplayPort 1.2 для гарнитур с частотой 90 Гц)</td>
</tr><tr>
<td> Разрешение дисплея</td><td colspan="2"> Разрешение: SVGA (800 x 600) или большая глубина цвета: 32 бита цвета на пиксель</td>
</tr><tr>
<td> Память</td><td> 8 ГБ ОЗУ или более</td><td> 16 ГБ ОЗУ или более</td>
</tr><tr>
<td> Хранение</td><td colspan="2"> &gt;10 ГБ дополнительного пространства</td>
</tr><tr>
<td> USB-порты</td><td colspan="2"> 1 доступный USB-порт для гарнитуры (USB 3.0 Type-A)<b>Примечание. Сила тока USB должна составлять минимум 900 мА</b>.</td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (для подключения периферийных устройств)</td>
</tr>
</table>

## <a name="see-also"></a>См. также статью

* [Общие сведения о разработке](development.md)
* [Использование эмулятора HoloLens](using-the-hololens-emulator.md)
* [Использование симулятора Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Обзор разработки в Unity](unity-development-overview.md)
* [Обзор разработки для Unreal](unreal-development-overview.md)
* [Обзор разработки в DirectX](directx-development-overview.md)
* [Архив эмулятора HoloLens](hololens-emulator-archive.md)
