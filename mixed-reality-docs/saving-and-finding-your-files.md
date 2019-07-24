---
title: Сохранение и поиск файлов
description: Сведения о поиске, сохранении и совместном использовании файлов в HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: инструкции по использованию средства выбора файлов, файлов, фотографий, видео, изображений, OneDrive, хранилища, проводника
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524602"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="e3359-104">Сохранение и поиск файлов</span><span class="sxs-lookup"><span data-stu-id="e3359-104">Saving and finding your files</span></span>

<span data-ttu-id="e3359-105">Файлы могут сохраняться и управляться аналогичным образом для других устройств Windows 10 Desktop и Mobile.</span><span class="sxs-lookup"><span data-stu-id="e3359-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="e3359-106">Использование приложения проводника для доступа к локальным папкам</span><span class="sxs-lookup"><span data-stu-id="e3359-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="e3359-107">В собственном хранилище приложения</span><span class="sxs-lookup"><span data-stu-id="e3359-107">Within an app's own storage</span></span>
* <span data-ttu-id="e3359-108">В особой известной папке (например, в библиотеке видео или музыкальной библиотеки);</span><span class="sxs-lookup"><span data-stu-id="e3359-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="e3359-109">Использование службы хранилища, включающей в себя приложение и средство выбора файлов (например, OneDrive);</span><span class="sxs-lookup"><span data-stu-id="e3359-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="e3359-110">Использование настольного ПК, подключенного к HoloLens через USB, с помощью поддержки протокола передачи мультимедиа (MTP)</span><span class="sxs-lookup"><span data-stu-id="e3359-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="e3359-111">Проводник</span><span class="sxs-lookup"><span data-stu-id="e3359-111">File Explorer</span></span>

<span data-ttu-id="e3359-112">Для перемещения и удаления файлов в HoloLens можно использовать приложение проводника.</span><span class="sxs-lookup"><span data-stu-id="e3359-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="e3359-113">Если в проводнике не отображаются файлы, то фильтр "последние" может быть активным (значок "Часы" выделяется в левой области).</span><span class="sxs-lookup"><span data-stu-id="e3359-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="e3359-114">Чтобы устранить эту проблему, щелкните значок документа **этого устройства** в левой области (под значком часов) или откройте меню и выберите **это устройство**.</span><span class="sxs-lookup"><span data-stu-id="e3359-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="e3359-115">Файлы в приложении</span><span class="sxs-lookup"><span data-stu-id="e3359-115">Files within an app</span></span>

<span data-ttu-id="e3359-116">Если приложение сохраняет файлы на устройстве, вы можете использовать это приложение для доступа к ним.</span><span class="sxs-lookup"><span data-stu-id="e3359-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="e3359-117">Где находятся мои фото и видео?</span><span class="sxs-lookup"><span data-stu-id="e3359-117">Where are my photos/videos?</span></span>

<span data-ttu-id="e3359-118">В [смешанной реальности](mixed-reality-capture.md) фотографии и видеозаписи сохраняются в папке рулона камеры устройства.</span><span class="sxs-lookup"><span data-stu-id="e3359-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="e3359-119">Доступ к ним можно получить с помощью [приложения "фотографии](see-your-photos.md#photos-app)".</span><span class="sxs-lookup"><span data-stu-id="e3359-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="e3359-120">Вы можете использовать приложение "фотографии" для синхронизации фотографий и видео в OneDrive.</span><span class="sxs-lookup"><span data-stu-id="e3359-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="e3359-121">Вы также можете получить доступ к фотографиям и видеороликам с помощью страницы "запись смешанной реальности" на [портале устройств Windows](using-the-windows-device-portal.md#mixed-reality-capture).</span><span class="sxs-lookup"><span data-stu-id="e3359-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="e3359-122">Запрос файлов из другого приложения</span><span class="sxs-lookup"><span data-stu-id="e3359-122">Requesting files from another app</span></span>

<span data-ttu-id="e3359-123">Приложение может запросить сохранение файла или открыть файл из другого приложения с помощью [выбора файлов](app-model.md#file-pickers).</span><span class="sxs-lookup"><span data-stu-id="e3359-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="e3359-124">Известные папки</span><span class="sxs-lookup"><span data-stu-id="e3359-124">Known folders</span></span>

<span data-ttu-id="e3359-125">HoloLens поддерживает ряд [известных папок](app-model.md#known-folders) , которые приложения могут запрашивать разрешение на доступ.</span><span class="sxs-lookup"><span data-stu-id="e3359-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="e3359-126">Файлы в службе</span><span class="sxs-lookup"><span data-stu-id="e3359-126">Files in a service</span></span>

<span data-ttu-id="e3359-127">Чтобы сохранить файл в службу (или получить доступ к файлам из), необходимо установить приложение, связанное с этой службой.</span><span class="sxs-lookup"><span data-stu-id="e3359-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="e3359-128">Чтобы сохранить файлы и получить доступ к файлам из OneDrive, вам потребуется установить [приложение onedrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span><span class="sxs-lookup"><span data-stu-id="e3359-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="e3359-129">MTP (протокол передачи мультимедиа)</span><span class="sxs-lookup"><span data-stu-id="e3359-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="e3359-130">Как и для других мобильных устройств, подключите HoloLens к настольному компьютеру и откройте проводник на компьютере, чтобы получить доступ к библиотекам HoloLens (фотографиям, видео, документам) для удобного переноса.</span><span class="sxs-lookup"><span data-stu-id="e3359-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="e3359-131">Уточнения</span><span class="sxs-lookup"><span data-stu-id="e3359-131">Clarifications</span></span>

* <span data-ttu-id="e3359-132">HoloLens не поддерживает подключение к внешним жестким дискам или SD-картам.</span><span class="sxs-lookup"><span data-stu-id="e3359-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="e3359-133">[Начиная с обновления Windows 10 от апреля 2018 (RS4) для hololens](release-notes-april-2018.md), hololens включает в себя проводник для сохранения файлов и управления ими на устройстве.</span><span class="sxs-lookup"><span data-stu-id="e3359-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="e3359-134">Кроме того, с помощью проводника можно выбрать средство выбора файлов (например, сохранить файл на устройстве или в OneDrive).</span><span class="sxs-lookup"><span data-stu-id="e3359-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
