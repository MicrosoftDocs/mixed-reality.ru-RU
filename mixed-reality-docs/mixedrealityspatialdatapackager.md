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
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="a06fd-104">Документация по упаковщик смешанной реальности пространственных данных</span><span class="sxs-lookup"><span data-stu-id="a06fd-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="a06fd-105">Это средство и его операции предлагаются как-является.</span><span class="sxs-lookup"><span data-stu-id="a06fd-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="a06fd-106">Он может быть изменена без предварительного предупреждения и не могут быть совместимы с Windows в будущем или освобождает смешанной реальности HMD Windows.</span><span class="sxs-lookup"><span data-stu-id="a06fd-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="a06fd-107">Загрузить</span><span class="sxs-lookup"><span data-stu-id="a06fd-107">Download</span></span>
 <span data-ttu-id="a06fd-108">Скачайте [MixedRealitySpatialDataPackager здесь](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="a06fd-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="a06fd-109">Краткое руководство</span><span class="sxs-lookup"><span data-stu-id="a06fd-109">Quickstart</span></span>

<span data-ttu-id="a06fd-110">Средство пространственных смешанной реальности, упаковщик данных копирует Пространственные данные в целевое приложение с одного ПК в другую через два шага, экспорт и импорт процесса.</span><span class="sxs-lookup"><span data-stu-id="a06fd-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="a06fd-111">Это средство необходимо запускать с правами администратора и удаляет существующий пространственных данных при импорте.</span><span class="sxs-lookup"><span data-stu-id="a06fd-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="a06fd-112">Экспорта влияют на существующие Пространственные данные.</span><span class="sxs-lookup"><span data-stu-id="a06fd-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="a06fd-113">Основные требования и ограничения:</span><span class="sxs-lookup"><span data-stu-id="a06fd-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="a06fd-114">Средство необходимо запускать с правами администратора</span><span class="sxs-lookup"><span data-stu-id="a06fd-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="a06fd-115">Может потребоваться перезапуск компьютера в том случае, если смешанной реальности портал работает нестабильно после запуска программы</span><span class="sxs-lookup"><span data-stu-id="a06fd-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="a06fd-116">Средство не будет работать при обнаружении несоответствия версий пространственных данных или проблемы с совместимостью</span><span class="sxs-lookup"><span data-stu-id="a06fd-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="a06fd-117">Средство приведет к удалению существующих пространственных данных при импорте</span><span class="sxs-lookup"><span data-stu-id="a06fd-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="a06fd-118">Если процесс импорта завершится сбоем предыдущих данных нельзя будет восстановить без его резервного копирования путем экспорта ранее</span><span class="sxs-lookup"><span data-stu-id="a06fd-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="a06fd-119">Качество функции импорта, при условии, что режим «Только для чтения» для карты для пространственных данных</span><span class="sxs-lookup"><span data-stu-id="a06fd-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="a06fd-120">Сопоставление советы и рекомендации</span><span class="sxs-lookup"><span data-stu-id="a06fd-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="a06fd-121">Очистить существующие сопоставления с помощью панели управления (смешанной реальности на "->" Параметры "->" Среда "->" Очистить среды данных)</span><span class="sxs-lookup"><span data-stu-id="a06fd-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="a06fd-122">Убедитесь, достаточно освещения хороший отслеживания и если заблокированные карты режим работы пытаться Ведение же освещения</span><span class="sxs-lookup"><span data-stu-id="a06fd-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="a06fd-123">По возможности усложнять динамического диапазона освещения, избежав областей высокой освещения рядом с темно-теневой области</span><span class="sxs-lookup"><span data-stu-id="a06fd-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="a06fd-124">Свести к минимуму пустое, textureless поверхности например поместите широкий спектр различных плакаты на белый стенок</span><span class="sxs-lookup"><span data-stu-id="a06fd-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="a06fd-125">Сопоставление пространства без динамические объекты в сцене, такие как перемещение пользователей</span><span class="sxs-lookup"><span data-stu-id="a06fd-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="a06fd-126">Блокировать карту при импорте (доступно через Insider Preview)</span><span class="sxs-lookup"><span data-stu-id="a06fd-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="a06fd-127">Разблокировать карту и повторное сканирование находится среда, когда Отслеживание качества снижает и (или) имеются изменения в среде (освещения или изменения в макете объектов)</span><span class="sxs-lookup"><span data-stu-id="a06fd-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="a06fd-128">Выполнение упаковщике пространственных данных смешанной реальности со сценарием</span><span class="sxs-lookup"><span data-stu-id="a06fd-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="a06fd-129">Мы предоставили MRSpatialPackagerHelperScript.ps1, запускает средства, упаковщик карты.</span><span class="sxs-lookup"><span data-stu-id="a06fd-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="a06fd-130">Параметры сценария определены ниже.</span><span class="sxs-lookup"><span data-stu-id="a06fd-130">The script parameters are defined below:</span></span>

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

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="a06fd-131">Пример использования сценария PowerShell и выходных данных</span><span class="sxs-lookup"><span data-stu-id="a06fd-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="a06fd-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span><span class="sxs-lookup"><span data-stu-id="a06fd-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="a06fd-133">Как с помощью MixedRealityPackager.exe экспорта</span><span class="sxs-lookup"><span data-stu-id="a06fd-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="a06fd-134">Экспорт карты вне устройства создает два файла mapx, het.mapx и sa.mapx.</span><span class="sxs-lookup"><span data-stu-id="a06fd-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="a06fd-135">Во время экспорта все привязки пространственных удаляются за исключением указанного приложения и границ созданные пользователем (если он существует).</span><span class="sxs-lookup"><span data-stu-id="a06fd-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="a06fd-136">Имя семейства пакетов источника должно соответствовать существующей установленного приложения или EXE-файла произойдет сбой.</span><span class="sxs-lookup"><span data-stu-id="a06fd-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="a06fd-137">Для импорта с помощью MixedRealityPackager.exe</span><span class="sxs-lookup"><span data-stu-id="a06fd-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="a06fd-138">Импорт удаляет существующий пространственных данных и заменяет его с данными из указанного каталога.</span><span class="sxs-lookup"><span data-stu-id="a06fd-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="a06fd-139">Ввод имени приложения указывает целевого приложения, пространственных привязки, такие как имя пакета должно быть импортировано для с указанием целевого пользователя SID пользователя, который должен иметь доступ к импортированных пространственных привязки.</span><span class="sxs-lookup"><span data-stu-id="a06fd-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="a06fd-140">Имя семейства пакетов целевой и ИД безопасности пользователя, должно соответствовать существующие значения на ПК или EXE-файла произойдет сбой.</span><span class="sxs-lookup"><span data-stu-id="a06fd-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="a06fd-141">Сообщения об ошибке</span><span class="sxs-lookup"><span data-stu-id="a06fd-141">Error Messages</span></span>
<span data-ttu-id="a06fd-142">Помимо этого сообщения об ошибках ниже сбои также должен соответствовать с результатом HRESULT</span><span class="sxs-lookup"><span data-stu-id="a06fd-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="a06fd-143">Если произошла ошибка недопустимые аргументы</span><span class="sxs-lookup"><span data-stu-id="a06fd-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="a06fd-144">Если исполняемый файл не был запущен в режиме администратора</span><span class="sxs-lookup"><span data-stu-id="a06fd-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="a06fd-145">Если произошла ошибка, включение или отключение драйвера</span><span class="sxs-lookup"><span data-stu-id="a06fd-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="a06fd-146">Если произошла ошибка при проверке версии пространственных базы данных</span><span class="sxs-lookup"><span data-stu-id="a06fd-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="a06fd-147">Если произошла ошибка при проверке имени семейства пакетов, для импорта и экспорта целевого приложения</span><span class="sxs-lookup"><span data-stu-id="a06fd-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="a06fd-148">Если произошла ошибка при проверке ИД безопасности пользователя</span><span class="sxs-lookup"><span data-stu-id="a06fd-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="a06fd-149">В случае отсутствия ошибок, связанных с назначения или источника пространственных данных файлов</span><span class="sxs-lookup"><span data-stu-id="a06fd-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="a06fd-150">Если возникла ошибка, связанная с запуском и останавливающий спектра/SharedRealitySvc</span><span class="sxs-lookup"><span data-stu-id="a06fd-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
