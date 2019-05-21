---
title: Документация по упаковщик смешанной реальности пространственных данных
description: Документацию по использованию пространственных смешанной реальности, упаковщик данных
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942110"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Документация по упаковщик смешанной реальности пространственных данных

>[!NOTE]
> Это средство и его операции предлагаются как-является. Он может быть изменена без предварительного предупреждения и не могут быть совместимы с Windows в будущем или освобождает смешанной реальности HMD Windows.

## <a name="download"></a>Загрузить
 Скачайте [MixedRealitySpatialDataPackager здесь](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="quickstart"></a>Краткое руководство

Средство пространственных смешанной реальности, упаковщик данных копирует Пространственные данные в целевое приложение с одного ПК в другую через два шага, экспорт и импорт процесса. Это средство необходимо запускать с правами администратора и удаляет существующий пространственных данных при импорте. Экспорта влияют на существующие Пространственные данные.

Основные требования и ограничения:

1. Средство необходимо запускать с правами администратора 
2. Может потребоваться перезапуск компьютера в том случае, если смешанной реальности портал работает нестабильно после запуска программы
3. Средство не будет работать при обнаружении несоответствия версий пространственных данных или проблемы с совместимостью
4. Средство приведет к удалению существующих пространственных данных при импорте
5. Если процесс импорта завершится сбоем предыдущих данных нельзя будет восстановить без его резервного копирования путем экспорта ранее
6. Качество функции импорта, при условии, что режим «Только для чтения» для карты для пространственных данных
***

## <a name="mapping-best-practices"></a>Сопоставление советы и рекомендации

1. Очистить существующие сопоставления с помощью панели управления (смешанной реальности на "->" Параметры "->" Среда "->" Очистить среды данных)
2. Убедитесь, достаточно освещения хороший отслеживания и если заблокированные карты режим работы пытаться Ведение же освещения
3. По возможности усложнять динамического диапазона освещения, избежав областей высокой освещения рядом с темно-теневой области
4. Свести к минимуму пустое, textureless поверхности например поместите широкий спектр различных плакаты на белый стенок
5. Сопоставление пространства без динамические объекты в сцене, такие как перемещение пользователей
6. Блокировать карту при импорте (доступно через Insider Preview)
7. Разблокировать карту и повторное сканирование находится среда, когда Отслеживание качества снижает и (или) имеются изменения в среде (освещения или изменения в макете объектов)
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Выполнение упаковщике пространственных данных смешанной реальности со сценарием

Мы предоставили MRSpatialPackagerHelperScript.ps1, запускает средства, упаковщик карты. 


Параметры сценария определены ниже.

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

### <a name="powershell-script-example-usage-and-output"></a>Пример использования сценария PowerShell и выходных данных

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>Как с помощью MixedRealityPackager.exe экспорта
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

Экспорт карты вне устройства создает два файла mapx, het.mapx и sa.mapx. Во время экспорта все привязки пространственных удаляются за исключением указанного приложения и границ созданные пользователем (если он существует). Имя семейства пакетов источника должно соответствовать существующей установленного приложения или EXE-файла произойдет сбой.

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>Для импорта с помощью MixedRealityPackager.exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
Импорт удаляет существующий пространственных данных и заменяет его с данными из указанного каталога. Ввод имени приложения указывает целевого приложения, пространственных привязки, такие как имя пакета должно быть импортировано для с указанием целевого пользователя SID пользователя, который должен иметь доступ к импортированных пространственных привязки. Имя семейства пакетов целевой и ИД безопасности пользователя, должно соответствовать существующие значения на ПК или EXE-файла произойдет сбой.


***
## <a name="error-messages"></a>Сообщения об ошибке
Помимо этого сообщения об ошибках ниже сбои также должен соответствовать с результатом HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>Если произошла ошибка недопустимые аргументы
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Если исполняемый файл не был запущен в режиме администратора
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Если произошла ошибка, включение или отключение драйвера
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Если произошла ошибка при проверке версии пространственных базы данных
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Если произошла ошибка при проверке имени семейства пакетов, для импорта и экспорта целевого приложения
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Если произошла ошибка при проверке ИД безопасности пользователя
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>В случае отсутствия ошибок, связанных с назначения или источника пространственных данных файлов
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a>Если возникла ошибка, связанная с запуском и останавливающий спектра/SharedRealitySvc
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
