---
title: Потоковая передача в Unreal
description: Руководство по потоковой передаче в Unreal для HoloLens 2
author: suwu
ms.author: suwu
ms.date: 6/8/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, потоковая передача, компьютер, голографическое удаленное взаимодействие с приложением, проигрыватель для голографического удаленного взаимодействия, документация
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 78a019f5b74b254c1f32ec85dc639df47648555f
ms.sourcegitcommit: ff0e89b07d0b4a945967d64c5b8845a21dc5f476
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84888915"
---
# <a name="streaming-in-unreal"></a>Потоковая передача в Unreal

## <a name="overview"></a>Обзор
Потоковая передача с компьютера в HoloLens обеспечивает два основных преимущества: 
* Ваше приложение смешанной реальности может использовать вычислительные мощности компьютера. 
* Ускоренная итерация разработки. 

Чтобы приступить к работе, скачайте [Holographic Remoting Player](holographic-remoting-player.md) на устройство HoloLens. Этот инструмент позволит вашему приложению передавать данные в потоковом режиме непосредственно на проигрыватель удаленного взаимодействия на HoloLens из следующих источников:

* редактор Unreal Engine;
* упакованный исполняемый файл Windows. 

При потоковой передаче вы получаете доступ практически ко всем возможностям HoloLens, которые можно использовать при запуске приложения на устройстве. К ним относятся [отслеживание суставов рук](unreal-hand-tracking.md) (если вы используете HoloLens 2), [пространственное картирование](unreal-spatial-mapping.md) и [пространственные привязки](unreal-spatial-anchors.md). Но при этом недоступны функции из этого [списка ограничений](holographic-remoting-troubleshooting.md). 

> [!NOTE]
> Качество потоковой передачи в значительной степени зависит от уровня сигнала вашей беспроводной сети.

## <a name="device-support"></a>Поддержка устройств

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Источник</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1-го поколения</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>Иммерсивные гарнитуры</strong></td>
    </tr>
     <tr>
        <td>Unreal Editor</td>
        <td>✔</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Пакет Windows</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>Потоковая передача из Unreal Editor

Потоковая передача данных из Unreal Editor на устройство HoloLens обеспечивает разработчикам значительные преимущества при тестировании, а именно отсутствие необходимости ждать, пока приложение будет собрано и развернуто, для оценки обновлений.

Подробные инструкции по [потоковой передаче из Unreal Editor](unreal-uxt-ch6.md#device-only-streaming) можно найти в последнем разделе серии руководств по началу работы с Unreal.

## <a name="streaming-from-a-packaged-windows-executable"></a>Потоковая передача из упакованного исполняемого файла Windows

Начиная с версии Unreal 4.25.1, вы можете передавать данные вашего приложения на устройство HoloLens 2 в потоковом режиме из упакованного исполняемого файла Windows, выполнив следующие шаги: 

1. Выберите **File > Package Project > Windows** (Файл > Проект пакета > Windows) в меню редактора. 
    * Выберите расположение для сохранения пакета и нажмите **Select Folder** (Выбрать папку).

2. После завершения сборки пакета откройте инструмент **Holographic Remoting Player** на HoloLens 2 и запишите значение IP-адреса. 
3. Оставьте **Holographic Remoting Player** открытым и с помощью командной строки выполните следующие действия: 
    * С помощью команды cd перейдите в локальный каталог с сохраненным пакетом.
    * Введите следующую команду: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```

> [!NOTE]
> Имя приложения в параметрах проекта должно быть автоматически использовано для создания пакета Windows. Если по какой-либо причине имена отличаются, используйте имя исполняемого файла Windows в командной строке.

Нажмите клавишу ВВОД, и ваше приложение начнет потоковую передачу.

## <a name="see-also"></a>См. также статью
* [История версий голографического удаленного взаимодействия](holographic-remoting-version-history.md)
* [Создание пользовательского проигрывателя для голографического удаленного взаимодействия](holographic-remoting-create-player.md)
* [Установка безопасного подключения с использованием голографического удаленного взаимодействия](holographic-remoting-secure-connection.md)
