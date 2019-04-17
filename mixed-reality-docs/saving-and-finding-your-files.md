---
title: Сохранение и поиск файлов
description: Как найти и сохранить общий доступ к файлам на HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: Практическое руководство, средства выбора файлов, файлы, фотографии, видео, изображения, OneDrive, хранилище, проводник файлов
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602686"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="e7335-104">Сохранение и поиск файлов</span><span class="sxs-lookup"><span data-stu-id="e7335-104">Saving and finding your files</span></span>

<span data-ttu-id="e7335-105">Файлы можно сохранить и управляемых так же, как к другим Windows 10 Desktop и мобильных устройств:</span><span class="sxs-lookup"><span data-stu-id="e7335-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="e7335-106">Использование приложение проводника для доступа к локальным папкам</span><span class="sxs-lookup"><span data-stu-id="e7335-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="e7335-107">В в хранилище приложения</span><span class="sxs-lookup"><span data-stu-id="e7335-107">Within an app's own storage</span></span>
* <span data-ttu-id="e7335-108">В специальной папке известных (например, в библиотеке видео и музыка)</span><span class="sxs-lookup"><span data-stu-id="e7335-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="e7335-109">С помощью службы хранилища, который включает в себя средство выбора приложения и файла (например, OneDrive)</span><span class="sxs-lookup"><span data-stu-id="e7335-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="e7335-110">На настольных ПК подключены к вашей HoloLens через USB, через службу поддержки MTP (протокола передачи мультимедиа)</span><span class="sxs-lookup"><span data-stu-id="e7335-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="e7335-111">Проводник</span><span class="sxs-lookup"><span data-stu-id="e7335-111">File Explorer</span></span>

<span data-ttu-id="e7335-112">Можно использовать проводник, чтобы перемещать и удалять файлы в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e7335-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="e7335-113">Если вы не видите все файлы в проводнике, фильтр «Последние» может быть активен (значок часов будет выделен на левой панели).</span><span class="sxs-lookup"><span data-stu-id="e7335-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="e7335-114">Чтобы устранить эту проблему, выберите **это устройство** документа значок в области слева (под значок часов), или откройте меню и выберите **это устройство**.</span><span class="sxs-lookup"><span data-stu-id="e7335-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="e7335-115">Файлы в приложении</span><span class="sxs-lookup"><span data-stu-id="e7335-115">Files within an app</span></span>

<span data-ttu-id="e7335-116">Если приложение сохраняет файлы на устройстве, можно использовать это приложение для доступа к ним.</span><span class="sxs-lookup"><span data-stu-id="e7335-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="e7335-117">Где находятся Мои фото и видео?</span><span class="sxs-lookup"><span data-stu-id="e7335-117">Where are my photos/videos?</span></span>

<span data-ttu-id="e7335-118">[Смешанный захвата реальности](mixed-reality-capture.md) фотографии и видео, сохраняется в папке камеры устройства.</span><span class="sxs-lookup"><span data-stu-id="e7335-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="e7335-119">Это может осуществляться через [приложение "фотографии"](see-your-photos.md#photos-app).</span><span class="sxs-lookup"><span data-stu-id="e7335-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="e7335-120">Можно использовать приложение "фотографии" синхронизировать свои фото и видео в OneDrive.</span><span class="sxs-lookup"><span data-stu-id="e7335-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="e7335-121">Также доступны свои фото и видео по странице смешанной реальности захвата [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span><span class="sxs-lookup"><span data-stu-id="e7335-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="e7335-122">Запрашивающий файлы из другого приложения</span><span class="sxs-lookup"><span data-stu-id="e7335-122">Requesting files from another app</span></span>

<span data-ttu-id="e7335-123">В приложении может потребоваться сохранить файл или открыть файл из другого приложения с помощью [файл выбора](app-model.md#file-pickers).</span><span class="sxs-lookup"><span data-stu-id="e7335-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="e7335-124">Известные папки</span><span class="sxs-lookup"><span data-stu-id="e7335-124">Known folders</span></span>

<span data-ttu-id="e7335-125">HoloLens поддерживает ряд [известные папки](app-model.md#known-folders) что приложения могут запрашивать разрешение на доступ.</span><span class="sxs-lookup"><span data-stu-id="e7335-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="e7335-126">Файлы в службе</span><span class="sxs-lookup"><span data-stu-id="e7335-126">Files in a service</span></span>

<span data-ttu-id="e7335-127">Сохраните файл (или получить доступ к файлам из) службы, приложения, связанного с ней должен быть установлен.</span><span class="sxs-lookup"><span data-stu-id="e7335-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="e7335-128">Чтобы сохранять файлы и получить доступ к файлам OneDrive, необходимо установить [приложение OneDrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span><span class="sxs-lookup"><span data-stu-id="e7335-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="e7335-129">MTP (протокола передачи мультимедиа)</span><span class="sxs-lookup"><span data-stu-id="e7335-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="e7335-130">Аналогично действиям на других мобильных устройствах, подключиться к настольному ПК HoloLens и откройте проводник на ПК для доступа к библиотекам HoloLens (фотографии, видео, документы) для переноса данных.</span><span class="sxs-lookup"><span data-stu-id="e7335-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="e7335-131">Точные сведения</span><span class="sxs-lookup"><span data-stu-id="e7335-131">Clarifications</span></span>

* <span data-ttu-id="e7335-132">HoloLens не поддерживает подключение к внешние жесткие диски или SD-карты.</span><span class="sxs-lookup"><span data-stu-id="e7335-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="e7335-133">Начиная с версии [Windows 10 апреля 2018 г. обновление (RS4) для HoloLens](release-notes-april-2018.md), HoloLens включает в себя проводник файлов для сохранения и управления ими файлы на устройстве.</span><span class="sxs-lookup"><span data-stu-id="e7335-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="e7335-134">Добавление проводник файлов также дает возможность выбирать вашего выбора файлов (например, сохранение файла на устройстве или в OneDrive).</span><span class="sxs-lookup"><span data-stu-id="e7335-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
