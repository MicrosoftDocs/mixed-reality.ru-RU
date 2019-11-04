---
title: Заметки о выпуске — 2016 августа
description: Заметки о выпуске HoloLens для годовщины Windows 10 (попадают 2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, заметки о выпуске, ОС, платформа, функции, коммерческий набор
ms.openlocfilehash: dcac64524cd8d1b1f2b0a496c4dcd2ad2fc7b690
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438094"
---
# <a name="release-notes---august-2016"></a>Заметки о выпуске — 2016 августа

Команда HoloLens прослушивает Отзывы разработчиков в программе предварительной оценки Windows, чтобы задать приоритеты для нашей работы. Отправьте [нам отзыв](give-us-feedback.md) через центр обратной связи, [форумы для разработчиков](https://forums.hololens.com) и [Twitter с помощью @HoloLens](https://twitter.com/hololens). Так как в Windows 10 включено годовщина, Группа HoloLens с радостью попытается улучшить работу с Holographic. В этом обновлении мы посвящены основным исправлениям, улучшениям и внедрению функций, запрошенных компаниями и доступных в коммерческом наборе Microsoft HoloLens.

**Последний выпуск:** Обновление Windows holographic 2016 августа (**10.0.14393.0**, Юбилейная версия Windows 10)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Чтобы [обновить текущий выпуск](updating-hololens.md), откройте приложение " *Параметры* ", перейдите в раздел " *Обновление & безопасность*", а затем нажмите кнопку " *проверить обновления* ".

## <a name="new-features"></a>Новые возможности

**Присоединение к процессу отладки** HoloLens теперь поддерживает отладку присоединения к процессу. Вы можете использовать обновление 3 для Visual Studio 2015, чтобы подключиться к работающему приложению на HoloLens и [начать его отладку](using-visual-studio.md#debugging-an-installed-or-running-app). Это работает без необходимости развертывания из проекта Visual Studio.

**Обновленный эмулятор HoloLens** Мы также выпустили обновленную версию эмулятора HoloLens.

**Поддержка игровых** устройств Теперь вы можете связывать и использовать игровые устройства Bluetooth с HoloLens! Недавно выпущенный адаптер Xbox Wireless поддерживает функции Bluetooth и может использоваться для воспроизведения избранных игр и приложений, поддерживающих игровой планшет. Перед подключением контроллера беспроводной сети Xbox к серверу HoloLens необходимо применить [Обновление контроллера](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) . Контроллер беспроводной связи Xbox S поддерживается интерфейсами API [ксинпут](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) и [Windows. Gaming. input.](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) Доступ к дополнительным моделям контроллеров Bluetooth можно получить с помощью API [Windows. Gaming. Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) .

## <a name="improvements-and-fixes"></a>Улучшения и исправления

Мы работаем над обновлением годовщины Windows 10, поэтому в дополнение к исправлениям для HoloLens вы получаете также все самое самое от центра обновления Windows, чтобы повысить надежность и производительность платформы. Ваши отзывы очень значимы и имеют приоритет для исправлений в выпуске.

Мы улучшили следующие возможности:
* Вход в систему.
* присоединение к рабочей области.
* Энергосбережение для переходов в состояние электропитания устройства.
* стабильность с захватами смешанной реальности.
* надежность подключения Bluetooth
* сохраняемая голограмма в сценарии с несколькими приложениями.

Мы устранили следующие проблемы:
* не удается подключиться к профилировщику и отладчику графики Visual Studio.
* фотографии & документы не отображаются в проводнике на портале устройств.
* Панель приложений может мигать, когда курсор помещается над ним в режиме корректировки.
* В режиме корректировки курсор глаза будет меняться на указатель с 4 стрелками, что приведет к более медленной точке.
* "Привет, Кортана, воспроизведение музыки" не запускает Groove.
* После предыдущего обновления, говорящего на «Go Home», панель «контакты» не отображается правильно.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Знакомство с коммерческим набором Microsoft HoloLens

Коммерческий набор Microsoft HoloLens готов для корпоративного развертывания. Мы добавили несколько очень востребованных [коммерческих функций](commercial-features.md) от наших ранних бизнес-партнеров.

Обратитесь к локальному менеджеру учетная запись Майкрософт, чтобы приобрести коммерческий набор Microsoft HoloLens.

### <a name="key-commercial-features"></a>Основные коммерческие функции 

* **Режим киоска.** С помощью режима киоска HoloLens можно ограничить количество приложений, которые будут запускаться, чтобы включить демонстрационные или демонстрационные возможности.<br>
  ![в режиме киоска HoloLens запускается непосредственно в выбранном приложении.](images/201608-kioskmode-400px.png)
* **Управление мобильными устройствами (MDM) для HoloLens.** ИТ-отдел может управлять несколькими устройствами HoloLens одновременно, используя такие решения, как Microsoft Intune. Вы сможете изменять параметры, выбирать приложения для установки и задавать настройки безопасности в соответствии с потребностями вашей организации.<br>
  ![управления мобильными устройствами в HoloLens обеспечивает управление устройствами корпоративного класса на нескольких устройствах.](images/201608-enterprisemanagement-400px.png)
* **Центр обновления Windows для бизнеса.** Контролируемые обновления операционной системы на устройствах и поддержка долгосрочного обслуживания.
* **Безопасность данных.** Шифрование данных BitLocker включено в HoloLens для обеспечения того же уровня защиты безопасности, что и любое другое устройство Windows.
* **Рабочий доступ.** Любой пользователь в Организации может удаленно подключаться к корпоративной сети через виртуальную частную сеть на HoloLens. HoloLens также может получать доступ к сетям Wi-Fi, которым требуются учетные данные.
* **Microsoft Store для бизнеса.** ИТ-отдел также может настроить корпоративное личное хранилище, содержащее только приложения вашей компании для конкретного использования HoloLens. Безопасное распространение корпоративного программного обеспечения в выбранную группу корпоративных пользователей.

### <a name="development-edition-vs-commercial-suite"></a>Выпуск Development Edition и коммерческий набор

<table>
<tr>
<th>Возможности</th><th>Выпуск для разработки</th><th>Коммерческий набор</th>
</tr><tr>
<td>Шифрование устройства (BitLocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Виртуальная частная сеть (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Режим киоска</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Управление и развертывание</th>
</tr><tr>
<td>Управление мобильными устройствами (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Возможность блокировать отмену регистрации</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Доступ к корпоративному Wi-Fi на основе сертификата</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (потребитель)</td><td style="text-align: center;">Потребителей</td><td style="text-align: center;">Фильтрация с помощью MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Портал бизнес-магазина</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Безопасность и идентификация</th>
</tr><tr>
<td>Вход с Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Вход с использованием учетной записи Майкрософт (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Учетные данные следующего поколения с разблокированием ПИН-кода</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Безопасная загрузка</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Обслуживание и поддержка</th>
</tr><tr>
<td>Автоматические обновления системы по мере их поступления</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Центр обновления Windows для бизнеса</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Долгосрочная ветвь обслуживания</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Заметки о предыдущем выпуске
* [Заметки о выпуске — май 2016 г.](release-notes-may-2016.md)
* [Заметки о выпуске — март 2016 г.](release-notes-march-2016.md)

## <a name="see-also"></a>См. также
* [Известные проблемы с HoloLens](hololens-known-issues.md)
* [Коммерческие функции](commercial-features.md)
* [Установка средств](install-the-tools.md)
* [Использование эмулятора HoloLens](using-the-hololens-emulator.md)
