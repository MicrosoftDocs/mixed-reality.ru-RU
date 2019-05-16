---
title: Установка средств
description: Начните здесь, чтобы подготовиться к разработке смешанной реальности. В этой статье всегда должны отражать последние версии Unity, Visual Studio и другие средства, рекомендуется для разработки иммерсивных гарнитура HoloLens и смешанной реальностью Windows.
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: последнюю версию, средства, приступить к работе, основы, unity, visual studio, набор средств
ms.openlocfilehash: 03a310457bf5ef498a6369a158b697c7fa59d6d9
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730882"
---
# <a name="install-the-tools"></a>Установка средств

Получите средства, необходимые для создания приложений для Microsoft HoloLens и Windows Mixed Reality иммерсивную (VR). Имеется не отдельный пакет SDK для Windows Mixed Reality разработки; можно использовать Visual Studio с помощью пакета SDK для Windows 10.

У вас нет устройства смешанной реальности? Вы можете установить [HoloLens эмулятор](using-the-hololens-emulator.md) для тестирования некоторые функциональные возможности приложения смешанной реальности без HoloLens. Можно также использовать [симулятор Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) для тестирования приложений для иммерсивную смешанной реальности.

Мы рекомендуем установить игровое ядро Unity как самый простой способ приступить к созданию приложениях смешанной реальности, однако можно также создать с DirectX, если вы хотите использовать пользовательский модуль.

>[!TIP]
>Закладки и проверит его, регулярно, чтобы следить за новостями о самой последней версии каждого средства, рекомендуется для разработки приложений для смешанной реальности.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Контрольный список установки


| Инструмент | Описание | Примечания |
|---------|---------|---------|
| ![Логотип Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>(Ручной ссылка для установки)</a> | Установите последнюю версию Windows 10 так операционной системы, платформы, для которого вы создаете приложения смешанной реальности. | **Установка Windows 10** <br> <ul><li>Можно установить самую последнюю версию Windows 10 через Центр обновления Windows, в параметрах или путем создания установочного носителя (используя ссылку в столбце слева).<li>См. в разделе [заметки о текущем выпуске](release-notes-october-2018.md) сведения о новейших смешанный реальности функции, доступные с каждым выпуском Windows 10.</ul> **Включить режим разработчика на вашем Компьютере** в параметры > обновление и безопасность > для разработчиков. <br><br> **Примечание для предприятия и ПК организации под управлением:** Если компьютер находится под управлением организации ИТ-отдел, может потребоваться для обращения к администратору, чтобы обновить. <br><br> **"N" версии Windows:** Windows Mixed Reality иммерсивную (VR) не поддерживаются в версиях Windows "n". |
| ![Логотип Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>(Ссылка для установки)</a> | Полнофункциональная интегрированная среда разработки (IDE) для Windows и многое другое. Вы используете Visual Studio для написания кода, отладки, тестирования и развертывания. | **Рабочие нагрузки для установки:** <ul><li>Разработка классических приложений C++</li><li>Разработка приложений для универсальной платформы Windows</li></ul>**Примечание о Unity:** Если вы пытаетесь намеренно установить более новую версию (не LTS), из Unity для определенной цели, мы не рекомендуем *не* установка рабочей нагрузки Unity в процессе установки Visual Studio и вместо этого установка 2018.3 LTS поток Unity, как указано ниже.<br> <br>**Примечание.** Существуют некоторые известные проблемы с разработкой в Visual Studio 2019 на данный момент для смешанной реальности.  Сейчас мы рекомендуем продолжать использовать Visual Studio 2017. |
| ![Логотип Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)**<br>(Ручной ссылка для установки)</a> | Предоставляет последнюю заголовки, библиотеки, метаданных и средства для создания приложений Windows 10 на HoloLens 2. | Чтобы создавать приложения HoloLens 2, необходимо установить Windows SDK, сборки 18362 или более поздней версии.<br> <br> Если при разработке приложений для настольных систем Windows Mixed Reality гарнитуры или HoloLens только (1-го поколения), можно использовать пакет SDK для Windows, установленные Visual Studio 2017. |
| ![Логотип Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2087187" target="_blank">**Эмулятор HoloLens 2**<br>(Ссылка для установки: 10.0.18362.1005)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (1-го поколения) эмулятора**<br>(Ссылка для установки: 10.0.17763.253)</a> | Эмулятор позволяет запускать приложения на образ виртуальной машины HoloLens без физического HoloLens.<br> <br> Этот пакет также включает holographic шаблонов проектов DirectX для Visual Studio. | См. в разделе [с помощью эмулятора HoloLens](using-the-hololens-emulator.md) Дополнительные сведения о начале работы с эмулятором.<br> <br> **Компьютер должен поддерживать Hyper-V** для успешной установки эмулятора. См. в статье в разделе Требования к системе ниже сведения. При желании можно выбрать для установки только шаблоны без эмулятора.<br>|
| ![Значок Unity](images/unity_logo.png)<br><br><a href="https://unity3d.com/get-unity/download" target="_blank">**Unity 2018.3**<br>(Ссылка для установки)</a> | Игровое ядро Unity — это самый простой способ создать опыт смешанной реальности, со встроенной поддержкой для смешанной реальности Windows. | Обычно рекомендуется поток Unity LTS (Long Term Support) как лучшую версию для запуска новых проектов обновление его последнюю версию выбирает последнюю стабильную исправления.<br> <br> Рекомендуется использовать **Unity 2018.3.x**, который необходим для версии 2 MRTK ниже, и которой скоро станет Unity 2018 LTS построения. <br> <br> Некоторым разработчикам может потребоваться использовать разные версии Unity в особых случаях. В таких случаях Unity поддерживает side-by-side установка разных версий. |
| ![Логотип MRTK](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**Набор средств смешанной реальности (MRTK v2) для Unity**</a> | MRTK v2 для Unity — это пакету средств разработки кросс платформенных открытым исходным кодом для смешанной реальности приложений.<br><br> MRTK v2 предназначен для ускорения разработки приложений, предназначенных для Microsoft HoloLens, Windows Mixed Reality иммерсивную (VR) и платформой OpenVR. Проект является, предназначенные для снижения барьеры операции для создания приложений, смешанной реальности и участвующая с сообществом, как мы все роста. | Дополнительные сведения о MRTK v2, посетив проекта <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">вики-сайт GitHub</a>. |


## <a name="mixed-reality-toolkit"></a>Набор средств для смешанной реальности

Смешанной реальности Toolkit предоставляет компонентов и функций, которые предназначены для ускорения разработки приложений, предназначенных для Microsoft HoloLens, гарнитуры смешанной реальности Windows и OpenVR платформы. Проект является, предназначенные для снижения барьеры операции для создания приложения смешанной реальности и внести свой вклад сообщества по мере мы все роста.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit Unity</a> — использует код из базового набора средств и облегчает использование в Unity.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a> - code двоичные файлы и компоненты, которые не могут выполняться непосредственно для HoloLens или иммерсивную (VR), но вместо этого пары с ними для построения обнаруживает, предназначенных для смешанной реальности Windows.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Настройка компьютера для разработки смешанной реальности

Пакет SDK для Windows 10, лучше всего работает в операционной системе Windows 10. Этот пакет SDK также поддерживается в Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Обратите внимание, что не все средства, поддерживаются в старых операционных системах. 

### <a name="for-hololens-development"></a>Для разработки HoloLens

При настройке на Компьютере разработки для разработки HoloLens, убедитесь, что он соответствует системным требованиям для обоих <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> и <a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a>. Если вы планируете использовать HoloLens (1-го поколения) эмулятора, вы захотите убедитесь, что ваш компьютер удовлетворяет [системные требования для эмулятора HoloLens](using-the-hololens-emulator.md#hololens-emulator-system-requirements) также.

Чтобы начать работу с эмулятором HoloLens, см. в разделе [с помощью эмулятора HoloLens](using-the-hololens-emulator.md).

Если вы планируете разработку для HoloLens и Windows Mixed Reality иммерсивную (VR), используйте рекомендации системы и требования в разделе ниже.

### <a name="for-immersive-vr-headset-development"></a>Для разработки гарнитура иммерсивных (VR)

>[!NOTE]
>Следующие рекомендации являются текущего минимальные и рекомендуемые спецификации для вашего иммерсивных Гарнитура (VR) *Компьютере разработки*и будут обновляться регулярно.

>[!WARNING]
>Не следует путать с [минимальные рекомендации по совместимости оборудования ПК](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), где указаны *спецификации потребителя ПК* к которому следует выбирать иммерсивные приложения Гарнитура (VR) или игры.

Если на Компьютере разработки иммерсивных гарнитура нет полноразмерное порты HDMI и/или USB 3.0, нужно будет [адаптеров](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) для подключения вашего гарнитуры.

Сейчас [известные проблемы](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) с некоторых аппаратных конфигурациях, особенно при работе с записных книжек, которые имеют гибридной графики.

<table>
<tr>
<th></th><th> Минимальные требования</th><th> Рекомендуем</th>
</tr><tr>
<td> Процессор</td><td> <b>Записная книжка:</b> Mobile Intel Core i5 7 поколения ЦП, двумя ядрами с технологией Hyper Threading <b>рабочего стола:</b> Intel Desktop i5 6-го поколения ЦП, двумя ядрами с технологией Hyper Threading <b>или</b> AMD FX4350 эквивалент четырехъядерный процессор с тактовой частотой 4,2 ГГц</td><td> <b>Рабочий стол:</b> Рабочий стол Intel i7 6-го поколения (6 ядер) <b>или</b> Ryzen AMD 1600 5 (6 ядер, 12 потоков)</td>
</tr><tr>
<td> Графический процессор</td><td> <b>Записная книжка:</b> NVIDIA GTX 965M, AMD RX 460M (2 ГБ) эквивалентное или более поздней версии DX12 графическим Процессором с поддержкой <b>рабочего стола:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 ГБ) эквивалентное или более поздней версии DX12 графическим Процессором с поддержкой</td><td><b>Рабочий стол:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 ГБ) эквивалентное или более поздней версии DX12 графическим Процессором с поддержкой</td>
</tr><tr>
<td> Версия WDDM драйвера GPU</td><td colspan="2"> Драйвер WDDM 2.2</td>
</tr><tr>
<td> Расчетная мощность</td><td colspan="2"> 15W или более поздней версии</td>
</tr><tr>
<td> Графики отображает порты</td><td colspan="2"> порт для отображения 1 x доступны графики&#160;Гарнитура (HDMI 1.4 или DisplayPort 1.2 применяется 60 Гц, HDMI 2.0 или DisplayPort 1.2 применяется 90 Гц)</td>
</tr><tr>
<td> Разрешение экрана</td><td colspan="2"> Решение SVGA (800 x 600) или больше битовая глубина: 32 бита цвета на пиксель</td>
</tr><tr>
<td> Память</td><td> 8&#160;ГБ ОЗУ или больше</td><td> 16 ГБ ОЗУ или более поздней версии</td>
</tr><tr>
<td> Хранилище</td><td colspan="2"> &gt;10 ГБ дополнительного свободного пространства</td>
</tr><tr>
<td> USB-порты</td><td colspan="2"> порт 1 x доступных USB для Гарнитура (USB 3.0 Type-A) <b>Примечание: USB необходимо указать как минимум 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> 4.0 Bluetooth (для аксессуаров взаимодействия)</td>
</tr>
</table>

## <a name="see-also"></a>См. также

* [Общие сведения о разработке](development-overview.md)
* [Использование эмулятора HoloLens](using-the-hololens-emulator.md)
* [Использование симулятора Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Обзор разработки в Unity](unity-development-overview.md)
* [Обзор разработки в DirectX](directx-development-overview.md)
* [Архив эмулятора HoloLens](hololens-emulator-archive.md)
