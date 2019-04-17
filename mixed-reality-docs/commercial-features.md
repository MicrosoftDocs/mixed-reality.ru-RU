---
title: Коммерческие функции
description: Microsoft HoloLens пакет Commercial Suite включает в себя функции, которые упрощают процесс для бизнеса для управления устройствами HoloLens.
author: xerxesb85
ms.author: xerxesb
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, коммерческих и функции управления мобильными устройствами, управление мобильными устройствами, полноэкранный режим
ms.openlocfilehash: 5fd5c56983fb3e94376fac08c6e96510bccc0002
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604993"
---
# <a name="commercial-features"></a>Коммерческие функции

Microsoft HoloLens пакет Commercial Suite включает в себя функции, которые упрощают процесс для бизнеса для управления устройствами HoloLens. Коммерческие функции включены в операционной системе Windows, но они включены по лицензии. Почти всегда подразумевается лицензии обеспечивается управление устройствами Microsoft HoloLens, зарегистрированными в организации. Обратитесь к местному менеджеру Майкрософт для приобретения Microsoft HoloLens пакет Commercial Suite.

&nbsp;

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

## <a name="key-commercial-features"></a>Основные коммерческие возможности

* **Режим киоска.** Режим киоска HoloLens позволяет ограничить приложения, которые следует выполнить для включения демонстрации или демонстрации взаимодействия.

  ![В режиме киоска HoloLens запускается непосредственно в приложение по своему усмотрению.](images/201608-kioskmode-400px.png)

* **Управление мобильными устройствами (MDM) для HoloLens.** Ваш ИТ-отдел может управлять несколькими устройствами HoloLens, одновременно с помощью решений, таких как Microsoft Intune. Можно изменять параметры, выбирать приложения для установки и задавать настройки безопасности в соответствии с потребностями вашей организации.

  ![Управление мобильными устройствами на HoloLens предоставляет корпоративное управление устройствами корпоративного уровня на нескольких устройствах.](images/201608-enterprisemanagement-400px.png)
  
* **Центр обновления Windows для бизнеса.** Контролировал обновления операционной системы на устройствах и поддержка ветвь долгосрочного обслуживания.
* **Безопасность данных.** Шифрование данных BitLocker с включенной HoloLens для предоставления тот же уровень защиты, как любые другие устройства Windows.
* **Рабочий доступ.** Все пользователи в организации можно удаленно подключаться к корпоративной сети через виртуальную частную сеть на HoloLens. HoloLens также имеют доступ к сетям Wi-Fi, которым требуются учетные данные.
* **Microsoft Store для бизнеса.** Ваш ИТ-отдел можно также настроить enterprise частного магазина, содержащий только приложений вашей компании для конкретного использования HoloLens. Безопасно распространять программное обеспечение предприятия для определенной группы пользователей предприятия.

## <a name="development-edition-vs-commercial-suite"></a>Development Edition vs. Пакет Commercial Suite

<table>
<tr>
<th>Компоненты</th><th>HoloLens Development Edition</th><th>HoloLens Commercial Suite</th><th>HoloLens 2</th>
</tr><tr>
<td>Шифрование устройства (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Виртуальная частная сеть (VPN)</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Полноэкранный режим</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Управление и развертывание</th>
</tr><tr>
<td>Управление мобильными устройствами (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Блокировать отмены регистрации</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Доступа к корпоративной сети Wi-Fi на основе сертификатов</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (потребитель)</td><td style="text-align: center;">Потребитель</td><td style="text-align: center;">Фильтрация с помощью MDM</td><td style="text-align: center;">Фильтрация с помощью MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Портал Store для бизнеса</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Безопасность и идентификация</th>
</tr><tr>
<td>Имя входа с Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Имя входа с учетной записью Майкрософт (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Разблокировать следующего поколения учетные данные с ПИН-код</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Безопасная загрузка</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Система обслуживания и поддержки</th>
</tr><tr>
<td>Автоматическая система обновляет при их поступлении</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Центр обновления Windows для бизнеса</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Ветвь обслуживания долгосрочной перспективе</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>



## <a name="enabling-commercial-features"></a>Включение возможности профессиональной

Коммерческие функции, такие как Microsoft Store для бизнеса, полноэкранный режим и enterprise доступа Wi-Fi, программа установки по организации ИТ-администратору. [ИТ-центр Windows для HoloLens](https://technet.microsoft.com/itpro/hololens/index) содержит пошаговые инструкции по регистрации устройств и установка приложений из Microsoft Store для бизнеса.

## <a name="see-also"></a>См. также
* [IT Pro руководство для HoloLens](https://technet.microsoft.com/itpro/hololens/index)
* [Полноэкранный режим](using-the-windows-device-portal.md#kiosk-mode)
* [Поддерживаемые поставщики облачных служб в Windows Holographic Корпоративная](https://msdn.microsoft.com/library/windows/hardware/dn920025(v=vs.85).aspx#HoloLens)
* [Microsoft Store для бизнеса и бизнес-приложений](https://blogs.technet.microsoft.com/sbucci/2016/04/13/windows-store-for-business-and-line-of-business-applications/)
* [Работа с бизнес приложений](https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps)
