---
title: Документация по диспетчеру пространственных данных в смешанной реальности
description: Документация по использованию упаковщика пространственных данных в смешанной реальности
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: лбе, Микседреалитиспатиалдатапаккажер. exe, Микседреалитиспатиалдатапаккажер
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942110"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="95e1d-104">Документация по диспетчеру пространственных данных в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="95e1d-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="95e1d-105">Это средство и его операция предлагаются "как есть".</span><span class="sxs-lookup"><span data-stu-id="95e1d-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="95e1d-106">Он может быть изменен без уведомления и не должен быть совместим с будущими выпусками Windows или Windows Mixed Reality ХМД.</span><span class="sxs-lookup"><span data-stu-id="95e1d-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="95e1d-107">Загрузить</span><span class="sxs-lookup"><span data-stu-id="95e1d-107">Download</span></span>
 <span data-ttu-id="95e1d-108">Скачайте [микседреалитиспатиалдатапаккажер здесь](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="95e1d-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="95e1d-109">QuickStart</span><span class="sxs-lookup"><span data-stu-id="95e1d-109">Quickstart</span></span>

<span data-ttu-id="95e1d-110">Средство упаковщика пространственных данных Mixed Reality копирует пространственные данные целевого приложения с одного компьютера на другой через два этапа экспорта и импорта.</span><span class="sxs-lookup"><span data-stu-id="95e1d-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="95e1d-111">Средство должно быть запущено с правами администратора и удаляет существующие пространственные данные при импорте.</span><span class="sxs-lookup"><span data-stu-id="95e1d-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="95e1d-112">При экспорте существующие пространственные данные остаются неизменными.</span><span class="sxs-lookup"><span data-stu-id="95e1d-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="95e1d-113">Основные требования и ограничения:</span><span class="sxs-lookup"><span data-stu-id="95e1d-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="95e1d-114">Средство должно запускаться с правами администратора</span><span class="sxs-lookup"><span data-stu-id="95e1d-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="95e1d-115">Если после запуска средства портал Mixed Reality нестабильн, может потребоваться перезапустить компьютер.</span><span class="sxs-lookup"><span data-stu-id="95e1d-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="95e1d-116">Средство не будет запускаться при обнаружении несоответствия версий пространственных данных или несовместимости</span><span class="sxs-lookup"><span data-stu-id="95e1d-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="95e1d-117">Средство удалит существующие пространственные данные при импорте</span><span class="sxs-lookup"><span data-stu-id="95e1d-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="95e1d-118">Если процесс импорта завершается неудачей, предыдущие данные не могут быть восстановлены, пока не будет выполнено их резервное копирование путем экспорта ранее</span><span class="sxs-lookup"><span data-stu-id="95e1d-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="95e1d-119">Качество функций импорта, зависящее от режима "только для чтения" для данных пространственных карт</span><span class="sxs-lookup"><span data-stu-id="95e1d-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="95e1d-120">Рекомендации по сопоставлению</span><span class="sxs-lookup"><span data-stu-id="95e1d-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="95e1d-121">Удалить существующие карты из панели управления (параметры-> Смешанная реальность — > Среда — > Очистить данные среды)</span><span class="sxs-lookup"><span data-stu-id="95e1d-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="95e1d-122">Обеспечьте достаточное освещение для хорошего отслеживания и, если режим заблокированной схемы пытается сохранить одно освещение</span><span class="sxs-lookup"><span data-stu-id="95e1d-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="95e1d-123">Если возможно, не используйте динамический диапазон освещения, избегая областей высокого освещения рядом с темными, затененными областями.</span><span class="sxs-lookup"><span data-stu-id="95e1d-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="95e1d-124">Сократите пустое число поверхностей, например, поместите диапазон различных плакатов на белые стены.</span><span class="sxs-lookup"><span data-stu-id="95e1d-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="95e1d-125">Сопоставьте пространство без динамических объектов в сцене, например перемещение людей</span><span class="sxs-lookup"><span data-stu-id="95e1d-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="95e1d-126">Блокировать карту при импорте (доступно через предварительную версию Insider)</span><span class="sxs-lookup"><span data-stu-id="95e1d-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="95e1d-127">Разблокируйте карту и повторно просканируйте среды при отслеживании качества и/или изменении в среде (освещение или изменения в макете объекта).</span><span class="sxs-lookup"><span data-stu-id="95e1d-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="95e1d-128">Запуск упаковщика пространственных данных Mixed Reality с сопутствующим скриптом</span><span class="sxs-lookup"><span data-stu-id="95e1d-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="95e1d-129">Мы предоставили Мрспатиалпаккажерхелперскрипт. ps1, который запускает средства диспетчера карт.</span><span class="sxs-lookup"><span data-stu-id="95e1d-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="95e1d-130">Параметры сценария определены ниже:</span><span class="sxs-lookup"><span data-stu-id="95e1d-130">The script parameters are defined below:</span></span>

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

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="95e1d-131">Пример использования и выходные данные сценария PowerShell</span><span class="sxs-lookup"><span data-stu-id="95e1d-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="95e1d-132">.\MRSpatialPackagerHelperScript.ps1-AppName холошелл-UserName (административный режим), Export-Мапкспас Д:\темп\-Локкмап 0</span><span class="sxs-lookup"><span data-stu-id="95e1d-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="95e1d-133">Экспорт с помощью Микседреалитипаккажер. exe</span><span class="sxs-lookup"><span data-stu-id="95e1d-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="95e1d-134">При экспорте карт из устройства создаются два файла мапкс: Хет. мапкс и SA. мапкс.</span><span class="sxs-lookup"><span data-stu-id="95e1d-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="95e1d-135">Во время экспорта все пространственные привязки удаляются, за исключением указанного приложения и созданной пользователем границы (если она существует).</span><span class="sxs-lookup"><span data-stu-id="95e1d-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="95e1d-136">Имя семейства пакетов исходного пакета должно совпадать с существующим установленным приложением, иначе exe завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="95e1d-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="95e1d-137">Импорт с помощью Микседреалитипаккажер. exe</span><span class="sxs-lookup"><span data-stu-id="95e1d-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="95e1d-138">Импорт удаляет существующие пространственные данные и заменяет их данными из указанного каталога.</span><span class="sxs-lookup"><span data-stu-id="95e1d-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="95e1d-139">Во входных данных имени приложения указывается имя пакета целевого приложения, которое, например, должны импортироваться пространственные привязки, а идентификатор безопасности целевого пользователя указывает пользователя, который должен иметь доступ к импортированным пространственным привязкам.</span><span class="sxs-lookup"><span data-stu-id="95e1d-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="95e1d-140">Имя семейства целевого пакета и идентификаторы безопасности пользователя должны соответствовать существующим значениям на компьютере, иначе исполняемый файл будет невозможен.</span><span class="sxs-lookup"><span data-stu-id="95e1d-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="95e1d-141">Сообщения об ошибке</span><span class="sxs-lookup"><span data-stu-id="95e1d-141">Error Messages</span></span>
<span data-ttu-id="95e1d-142">Кроме того, сообщения об ошибках, приведенные ниже, также будут сопровождаться значением HRESULT.</span><span class="sxs-lookup"><span data-stu-id="95e1d-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="95e1d-143">Если произошла ошибка недопустимых аргументов</span><span class="sxs-lookup"><span data-stu-id="95e1d-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="95e1d-144">Если исполняемый файл не был запущен в режиме администратора</span><span class="sxs-lookup"><span data-stu-id="95e1d-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="95e1d-145">Если при включении или отключении драйвера произошла ошибка</span><span class="sxs-lookup"><span data-stu-id="95e1d-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="95e1d-146">Если произошла ошибка при проверке версии пространственных баз данных</span><span class="sxs-lookup"><span data-stu-id="95e1d-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="95e1d-147">Если произошла ошибка при проверке имени семейства пакетов, предоставленного для целевого приложения импорта и экспорта</span><span class="sxs-lookup"><span data-stu-id="95e1d-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="95e1d-148">Если произошла ошибка при проверке SID пользователя</span><span class="sxs-lookup"><span data-stu-id="95e1d-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="95e1d-149">Если произошла ошибка, связанная с файлами назначения или исходными пространственными данными</span><span class="sxs-lookup"><span data-stu-id="95e1d-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="95e1d-150">Если произошла ошибка, связанная с запуском и остановкой спектра или Шаредреалитисвк</span><span class="sxs-lookup"><span data-stu-id="95e1d-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
