---
title: Установка инструментов
description: Ознакомьтесь с этой статьей, чтобы подготовиться к разработке решений смешанной реальности. В этой статье всегда должны быть указаны самые последние версии Unity, Visual Studio и других инструментов, рекомендованных для разработки приложений для иммерсивных гарнитур HoloLens и Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit
ms.openlocfilehash: 7dde2e90a3e1057a0b5ac33be1ddeed70bf79788
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597647"
---
# <a name="install-the-tools"></a>Установка инструментов

Получите инструменты, необходимые для создания приложений для иммерсивных гарнитур (гарнитур виртуальной реальности) Microsoft HoloLens и Windows Mixed Reality. Для разработки решений для Windows Mixed Reality не существует отдельного пакета SDK. Вы будете использовать Visual Studio с пакетом SDK для Windows 10.

У вас нет устройства смешанной реальности? Вы можете установить [эмулятор HoloLens](using-the-hololens-emulator.md), чтобы протестировать отдельные функции приложений смешанной реальности без HoloLens. Вы также можете использовать [симулятор Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md), чтобы протестировать приложения смешанной реальности для иммерсивных гарнитур.

Рекомендуем установить игровой модуль Unity — это самый простой способ приступить к созданию приложений смешанной реальности. Кроме того, вы можете воспользоваться DirectX, если захотите использовать собственный модуль.

>[!TIP]
>Добавьте эту страницу в закладки и регулярно просматривайте ее, чтобы быть в курсе самых последних версий каждого инструмента, рекомендованного для разработки приложений смешанной реальности.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Контрольный список установки


| Средство | Описание | Примечания |
|---------|---------|---------|
| ![Логотип Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (ссылка для установки вручную)</a> | Установите самую последнюю версию Windows 10, чтобы операционная система вашего компьютера соответствовала платформе, для которой вы создаете приложения смешанной реальности. | **Установка Windows 10** <br> <ul><li>Вы можете установить последнюю версию Windows 10 с помощью клиентского компонента Центра обновления Windows, к которому можно перейти в разделе параметров, или путем создания установочного носителя (открыв ссылку, указанную в левом столбце).<li>Сведения о новых функциях смешанной реальности, доступных в каждом выпуске Windows 10, см. в [заметках о текущем выпуске](release-notes-october-2018.md).</ul> **Включите режим разработчика на компьютере** в разделе "Параметры > Обновление и безопасность > Для разработчиков". <br><br> **Примечание, касающееся корпоративных компьютеров.** Если вашим компьютером управляет ИТ-отдел вашей организации, возможно, вам потребуется связаться с его сотрудниками для обновления. <br><br> **N-версии Windows.** Иммерсивные гарнитуры (виртуальная реальность) Windows Mixed Reality не поддерживаются в N-версиях Windows. |
| ![Логотип Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (версии 16.2 или более поздней)** (ссылка для установки)</a> | Полнофункциональная интегрированная среда разработки (IDE) для Windows и многое другое. Вы будете использовать Visual Studio для написания кода, отладки, тестирования и развертывания. | **Рабочие нагрузки, которые нужно установить:** <ul><li>"Разработка классических приложений на C++";</li><li>Разработка приложений универсальной платформы Windows (UWP)</li></ul>**Примечание касательно Unity.** Если вам не нужно устанавливать более новую (не с долгосрочной поддержкой (LTS)) версию Unity для конкретной цели, советуем *не* устанавливать рабочую нагрузку Unity в составе установки Visual Studio, а вместо этого установить версию Unity 2018.4 LTS, как отмечено ниже.<br> <br>**Примечание**. Сейчас в Visual Studio 2019 (версия 16.0) существует ряд известных проблем с отладкой приложений смешанной реальности.  Обновите Visual Studio 2019 до версии 16.2 или более поздней. |
| ![Логотип Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Пакет SDK для Windows 10 (10.0.18362.0)** (ссылка для установки вручную)</a> | Содержит новейшие заголовки, библиотеки, метаданные и средства для создания приложений для Windows 10 в HoloLens 2. | Для создания приложений HoloLens 2 потребуется установить пакет SDK для Windows сборки 18362 или новее.<br> <br> Если вы разрабатываете приложения только для настольных гарнитур Windows Mixed Reality или HoloLens (1-го поколения), можно использовать пакет SDK для Windows, установленный в Visual Studio 2017. |
| ![Логотип Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2112589" target="_blank">**Эмулятор HoloLens 2 (обновление за декабрь 2019 г.)** (ссылка для установки: 10.0.18362.1042)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Эмулятор HoloLens (1-го поколения)** (ссылка для установки: 10.0.17763.134)</a> | Эмулятор позволяет запускать приложения с помощью образа виртуальной машины HoloLens без физического устройства HoloLens.<br> <br> | Дополнительные сведения об использовании эмулятора HoloLens см. в [этой статье](using-the-hololens-emulator.md).<br> <br> Для успешной установки эмулятора **ваша система должна поддерживать Hyper-V**. Подробные сведения см. в разделе о системных требованиях. <br>|

## <a name="choose-your-engine"></a>Выберите подсистему

:::row:::
    :::column:::
       [![Unity](images/unity_logo.png)](https://unity3d.com/unity/qa/lts-releases?version=2018.4)<br>
        **[Unity](https://unity3d.com/unity/qa/lts-releases?version=2018.4)**<br>
        Обычно в качестве лучшей версии для запуска новых проектов мы рекомендуем Unity LTS (долгосрочная поддержка). Затем ее можно обновить до последней версии, чтобы получить новые стабильные исправления.<br> <br>Сейчас рекомендуем использовать **Unity 2018.4.x** — сборку LTS, необходимую для MRTK версии 2 (см. ниже).<br> <br>Некоторые разработчики по определенным причинам могут использовать другую версию Unity. В этих случаях Unity поддерживает параллельную установку различных версий.<br><br>[![MRTK](images/MRTKIcon.jpg)](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)<br>**[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)**<br>Mixed Reality Toolkit (MRTK) версии 2 для Unity — это кроссплатформенный пакет SDK с открытым кодом для приложений смешанной реальности.<br><br> MRTK версии 2 используется для ускорения разработки приложений, предназначенных для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR. Целью проекта является снижение барьеров для создания приложений смешанной реальности и внесение вклада в развитие сообщества по мере расширения личного опыта.
    :::column-end:::
    :::column:::
        [![Unreal](images/Unreal_logo.png)](https://docs.unrealengine.com//GettingStarted/Installation/index.html)<br>
        **[Unreal](https://docs.unrealengine.com//GettingStarted/Installation/index.html)**<br>
        Unreal Engine 4 — это мощная подсистема разработки с открытым кодом, обладающая полной поддержкой смешанной реальности в C++ и Blueprints.<br> <br>Поддержка HoloLens для Unreal Engine 4.23 в настоящее время находится на этапе бета-версии.
    :::column-end:::
    :::column:::
        [![Шаблоны приложений DirectX](images/DirectX_logo.png)](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)<br>
        **[DirectX](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)**<br>
        Шаблоны приложений Windows Mixed Reality содержат все необходимое, чтобы приступить к написанию приложения смешанной реальности с помощью DirectX и собственных API. Включают в себя цикл отрисовки (или "игровой цикл"), вспомогательный класс DeviceResources для управления устройством и контекстом Direct3D, а также простой пример отрисовщика голограмм. Доступны для Direct3D 11 и Direct3D 12.
    :::column-end:::
:::row-end:::

<br>

## <a name="mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK)

Набор средств для смешанной реальности предоставляет компоненты и функции, позволяющие ускорить разработку приложений, предназначенных для Microsoft HoloLens, гарнитур Windows Mixed Reality и платформы OpenVR. Целью проекта является снижение барьеров для создания приложений смешанной реальности и внесение вклада в развитие сообщества по мере расширения личного опыта.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit</a> — это набор сценариев и компонентов, предназначенных для ускорения разработки приложений смешанной реальности.
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit Unity</a> использует код из базового набора средств и упрощает его применение в Unity.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit</a> — фрагменты кода и компоненты, которые не могут работать непосредственно в HoloLens или иммерсивных гарнитурах (гарнитурах виртуальной реальности), но могут соединяться с ними для взаимодействия с Windows Mixed Reality.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Настройка компьютера для разработки приложений смешанной реальности

Этот пакет SDK для Windows 10 лучше всего использовать в операционной системе Windows 10. Он также поддерживается в следующих операционных системах: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Обратите внимание, что не все средства поддерживаются в операционных системах более ранних версий. 

### <a name="for-hololens-development"></a>Для разработки решений для HoloLens

При настройке компьютера для разработки решений для HoloLens убедитесь, что он соответствует системным требованиям для <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> и <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Если вы планируете использовать эмулятор HoloLens (1-го поколения), нужно чтобы ваш компьютер также отвечал системным требованиям [этого эмулятора](using-the-hololens-emulator.md#hololens-emulator-system-requirements).

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
<td> Процессор</td><td> <b>Ноутбук:</b> ЦП Intel Mobile Core i5 7-го поколения, двухъядерный процессор с технологией Hyper-Threading; <b>настольный компьютер:</b> ЦП Intel Desktop i5 6-го поколения, двухъядерный процессор с технологией Hyper-Threading <b>ИЛИ</b> эквивалент четырехъядерного процессора AMD FX4350 с частотой 4,2 ГГц</td><td> <b>Настольный компьютер:</b> Intel Desktop i7 6-го поколения (6 ядер) <b>ИЛИ</b> AMD Ryzen 5 1600 (6 ядер, 12 потоков)</td>
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
