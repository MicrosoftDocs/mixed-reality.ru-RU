---
title: Заметки о выпуске — август 2016 г.
description: HoloLens заметки о выпуске для Windows 10 Anniversary выпуска (осенью 2016 г.)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, release notes, ОС, платформы, функции, пакет commercial suite
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603664"
---
# <a name="release-notes---august-2016"></a>Заметки о выпуске — август 2016 г.

Команда HoloLens относимся к отзывам, от разработчиков в программе предварительной оценки Windows для определения приоритета нашей работы. Переходите к [отзыв о нас](give-us-feedback.md) через Центр обратной связи, [форумы для разработчиков](https://forums.hololens.com) и [Twitter с помощью @HoloLens ](https://twitter.com/hololens). Как Windows 10 включает обновления Годовщина HoloLens team — рады доставлять улучшить в голографический интерфейс. В этом обновлении мы ознакомились с основной исправления, улучшения и вводные сведения о функциональных возможностей, запрашиваемых бизнесу и доступные в Microsoft HoloLens пакет Commercial Suite.

**Последний выпуск:** Обновление Windows Holographic август 2016 г. (**10.0.14393.0**, Юбилейного выпуска Windows 10)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Для [обновление до текущего выпуска](updating-hololens.md)откройте *параметры* приложение, перейдите к *обновление и безопасность*, а затем выберите *проверять наличие обновлений* кнопка.

## <a name="new-features"></a>Новые возможности

**Присоединение к отладке процесса** HoloLens теперь поддерживает присоединение к процессу отладки. Visual Studio 2015 с обновлением 3 можно использовать для подключения к выполняемому приложению на HoloLens и [начать его отладку](using-visual-studio.md#debugging-an-installed-or-running-app). Это работает без необходимости развертывать из проекта Visual Studio.

**Обновить эмулятор HoloLens** мы также выпустили обновленную версию эмулятора HoloLens.

**Поддержка игровой** теперь можно связать и использование Bluetooth игровые панели с HoloLens! Недавно выпущенный S контроллера Xbox беспроводной функции Bluetooth возможности и может использоваться для воспроизведения в свои любимые игры с поддержкой игровой и приложений. Объект [обновление контроллера](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) должны применяться перед подключением S контроллера Xbox беспроводной связи с HoloLens. Поддерживается S контроллера Xbox беспроводной [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) и [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API-интерфейсы. Дополнительные модели Bluetooth контроллеров может осуществляться через [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.

## <a name="improvements-and-fixes"></a>Улучшения и исправления

Мы синхронизированы с остальной частью Юбилейного обновления Windows 10, поэтому помимо определенные исправления Hololens, вы также получили описывает все преимущества из центра обновления Windows для повышения надежности платформы и производительности. Ваши отзывы очень с табличным значением и приоритеты для устранения проблемы в выпуске.

Мы улучшили следующие задачи:
* Войдите в возможности.
* Присоединение к рабочему месту.
* энергопотребление устройств power переходов между состояниями.
* стабильной работы захватывает смешанной реальности.
* надежность для подключения по Bluetooth
* голограмма сохраняемости в сценарии с несколькими приложения.

Исправлены следующие проблемы:
* средства профилирования Visual Studio и отладчик графики не удалось подключиться.
* фотографии и документы не отображаются в проводнике на портале устройства.
* Панели приложения можно flash, когда курсор находится над ним в режиме изменения.
* В режиме изменения глаз взглядом точки курсора изменится на курсор в виде стрелки 4 некоторое время медленнее.
* «Эй Cortana воспроизведение музыки» не запускается Groove.
* После предыдущего обновления о том, «Go Home» отображается на панели закрепления неправильно.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Общие сведения о наборе Microsoft HoloLens коммерческих

Microsoft HoloLens пакет Commercial Suite готов для корпоративного развертывания. Мы добавили несколько запрашиваемые [возможности профессиональной](commercial-features.md) из наших ранних деловых партнеров.

Обратитесь к местному менеджеру Майкрософт для приобретения Microsoft HoloLens пакет Commercial Suite.

### <a name="key-commercial-features"></a>Основные коммерческие возможности 

* **Режим киоска.** Режим киоска HoloLens позволяет ограничить приложения, которые следует выполнить для включения демонстрации или демонстрации взаимодействия.<br>
  ![В режиме киоска HoloLens запускается непосредственно в приложение по своему усмотрению.](images/201608-kioskmode-400px.png)
* **Управление мобильными устройствами (MDM) для HoloLens.** Ваш ИТ-отдел может управлять несколькими устройствами HoloLens, одновременно с помощью решений, таких как Microsoft Intune. Можно изменять параметры, выбирать приложения для установки и задавать настройки безопасности в соответствии с потребностями вашей организации.<br>
  ![Управление мобильными устройствами на HoloLens предоставляет корпоративное управление устройствами корпоративного уровня на нескольких устройствах.](images/201608-enterprisemanagement-400px.png)
* **Центр обновления Windows для бизнеса.** Контролировал обновления операционной системы на устройствах и поддержка ветвь долгосрочного обслуживания.
* **Безопасность данных.** Шифрование данных BitLocker с включенной HoloLens для предоставления тот же уровень защиты, как любые другие устройства Windows.
* **Рабочий доступ.** Все пользователи в организации можно удаленно подключаться к корпоративной сети через виртуальную частную сеть на HoloLens. HoloLens также имеют доступ к сетям Wi-Fi, которым требуются учетные данные.
* **Microsoft Store для бизнеса.** Ваш ИТ-отдел можно также настроить enterprise частного магазина, содержащий только приложений вашей компании для конкретного использования HoloLens. Безопасно распространять программное обеспечение предприятия для определенной группы пользователей предприятия.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition vs. Пакет Commercial Suite

<table>
<tr>
<th>Компоненты</th><th>Development Edition</th><th>Пакет Commercial Suite</th>
</tr><tr>
<td>Шифрование устройства (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Виртуальная частная сеть (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Полноэкранный режим</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Управление и развертывание</th>
</tr><tr>
<td>Управление мобильными устройствами (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Блокировать отмены регистрации</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Доступа к корпоративной сети Wi-Fi на основе сертификатов</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (потребитель)</td><td style="text-align: center;">Потребитель</td><td style="text-align: center;">Фильтрация с помощью MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Портал Store для бизнеса</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Безопасность и идентификация</th>
</tr><tr>
<td>Имя входа с Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Имя входа с учетной записью Майкрософт (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Разблокировать следующего поколения учетные данные с ПИН-код</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Безопасная загрузка</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Система обслуживания и поддержки</th>
</tr><tr>
<td>Автоматическая система обновляет при их поступлении</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Центр обновления Windows для бизнеса</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Ветвь обслуживания долгосрочной перспективе</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Заметки о выпуске для предыдущих
* [Заметки о выпуске — май 2016 г.](release-notes-may-2016.md)
* [Заметки о выпуске — март 2016 г.](release-notes-march-2016.md)

## <a name="see-also"></a>См. также
* [Известные проблемы HoloLens](hololens-known-issues.md)
* [Коммерческие функции](commercial-features.md)
* [Установка средств](install-the-tools.md)
* [Использование эмулятора HoloLens](using-the-hololens-emulator.md)
