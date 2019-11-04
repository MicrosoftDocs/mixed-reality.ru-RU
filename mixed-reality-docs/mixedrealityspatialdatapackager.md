---
title: Документация по диспетчеру пространственных данных в смешанной реальности
description: Документация по использованию упаковщика пространственных данных в смешанной реальности
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: лбе, Микседреалитиспатиалдатапаккажер. exe, Микседреалитиспатиалдатапаккажер
ms.openlocfilehash: 52556e4028407086f943c4b765a8bcfad2744eac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438474"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Документация по диспетчеру пространственных данных в смешанной реальности

>[!NOTE]
> Это средство и его операция предлагаются "как есть". Он может быть изменен без уведомления и не должен быть совместим с будущими выпусками Windows или Windows Mixed Reality ХМД.

## <a name="download"></a>"Скачать"
 Скачайте [микседреалитиспатиалдатапаккажер здесь](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

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
        <td>Упаковщик пространственных данных в смешанной реальности</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>QuickStart

Средство упаковщика пространственных данных Mixed Reality копирует пространственные данные целевого приложения с одного компьютера на другой через два этапа экспорта и импорта. Средство должно быть запущено с правами администратора и удаляет существующие пространственные данные при импорте. При экспорте существующие пространственные данные остаются неизменными.

Основные требования и ограничения:

1. Средство должно запускаться с правами администратора 
2. Если после запуска средства портал Mixed Reality нестабильн, может потребоваться перезапустить компьютер.
3. Средство не будет запускаться при обнаружении несоответствия версий пространственных данных или несовместимости
4. Средство удалит существующие пространственные данные при импорте
5. Если процесс импорта завершается неудачей, предыдущие данные не могут быть восстановлены, пока не будет выполнено их резервное копирование путем экспорта ранее
6. Качество функций импорта, зависящее от режима "только для чтения" для данных пространственных карт
***

## <a name="mapping-best-practices"></a>Рекомендации по сопоставлению

1. Удалить существующие карты из панели управления (параметры-> Смешанная реальность — > Среда — > Очистить данные среды)
2. Обеспечьте достаточное освещение для хорошего отслеживания и, если режим заблокированной схемы пытается сохранить одно освещение
3. Если возможно, не используйте динамический диапазон освещения, избегая областей высокого освещения рядом с темными, затененными областями.
4. Сократите пустое число поверхностей, например, поместите диапазон различных плакатов на белые стены.
5. Сопоставьте пространство без динамических объектов в сцене, например перемещение людей
6. Блокировать карту при импорте (доступно через предварительную версию Insider)
7. Разблокируйте карту и повторно просканируйте среды при отслеживании качества и/или изменении в среде (освещение или изменения в макете объекта).
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Запуск упаковщика пространственных данных Mixed Reality с сопутствующим скриптом

Мы предоставили Мрспатиалпаккажерхелперскрипт. ps1, который запускает средства диспетчера карт. 


Параметры сценария определены ниже:

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map
    This functionality requires an updated driver from Insider Preview Builds with the Map Locking feature

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Пример использования и выходные данные сценария PowerShell

.\MRSpatialPackagerHelperScript.ps1-AppName холошелл-UserName (административный режим), Export-Мапкспас Д:\темп\-Локкмап 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value succesfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>Экспорт с помощью Микседреалитипаккажер. exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

При экспорте карт из устройства создаются два файла мапкс: Хет. мапкс и SA. мапкс. Во время экспорта все пространственные привязки удаляются, за исключением указанного приложения и созданной пользователем границы (если она существует). Имя семейства пакетов исходного пакета должно совпадать с существующим установленным приложением, иначе exe завершится ошибкой.

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>Импорт с помощью Микседреалитипаккажер. exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
Импорт удаляет существующие пространственные данные и заменяет их данными из указанного каталога. Во входных данных имени приложения указывается имя пакета целевого приложения, которое, например, должны импортироваться пространственные привязки, а идентификатор безопасности целевого пользователя указывает пользователя, который должен иметь доступ к импортированным пространственным привязкам. Имя семейства целевого пакета и идентификаторы безопасности пользователя должны соответствовать существующим значениям на компьютере, иначе исполняемый файл будет невозможен.


***
## <a name="error-messages"></a>Сообщения об ошибке
Кроме того, сообщения об ошибках, приведенные ниже, также будут сопровождаться значением HRESULT.

### <a name="if-there-was-an-error-invalid-arguments"></a>Если произошла ошибка недопустимых аргументов
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Если исполняемый файл не был запущен в режиме администратора
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Если при включении или отключении драйвера произошла ошибка
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Если произошла ошибка при проверке версии пространственных баз данных
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Если произошла ошибка при проверке имени семейства пакетов, предоставленного для целевого приложения импорта и экспорта
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Если произошла ошибка при проверке SID пользователя
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Если произошла ошибка, связанная с файлами назначения или исходными пространственными данными
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a>Если произошла ошибка, связанная с запуском и остановкой спектра или Шаредреалитисвк
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
