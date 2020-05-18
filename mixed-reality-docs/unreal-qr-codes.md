---
title: QR-коды в Unreal
description: Введение в использование QR-кодов в Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, QR-коды
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342662"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="be960-104">QR-коды в Unreal</span><span class="sxs-lookup"><span data-stu-id="be960-104">QR codes in Unreal</span></span>

<span data-ttu-id="be960-105">HoloLens умеет находить QR-коды в абсолютном пространстве и отображать голограммы на известных позициях в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="be960-105">HoloLens can locate QR codes in world space to render holograms at known positions in the real world.</span></span>  <span data-ttu-id="be960-106">Это позволяет, помимо прочего, визуализировать голограммы на нескольких устройствах в одном и том же расположении, чтобы создать единое взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="be960-106">This can also be used to render holograms on multiple devices in the same location to create a shared experience.</span></span> 

<span data-ttu-id="be960-107">Чтобы включить обнаружение QR-кодов в HoloLens, установите флажок Webcam (Веб-камера) в разделе Project Settings (Параметры проекта) > Platform (Платформа) > HoloLens > Capabilities (Возможности) редактора Unreal.</span><span class="sxs-lookup"><span data-stu-id="be960-107">To enable QR detection on HoloLens, ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="be960-108">Включите отслеживание QR-кодов в Unreal, запустив сеанс ARSession с функцией StartARSession.</span><span class="sxs-lookup"><span data-stu-id="be960-108">Opt into using QR code tracking in Unreal by starting an ARSession with the StartARSession function.</span></span> 

<span data-ttu-id="be960-109">QR-коды выводятся в виде отслеживаемого изображения через отслеживаемую геометрическую систему дополненной реальности Unreal.</span><span class="sxs-lookup"><span data-stu-id="be960-109">QR Codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span>  <span data-ttu-id="be960-110">Чтобы использовать эту возможность, добавьте к субъекту Blueprint (Схема) компонент AR Trackable Notify.</span><span class="sxs-lookup"><span data-stu-id="be960-110">To use this, add an AR Trackable Notify component to a Blueprint actor:</span></span> 

![AR Trackable Notify для QR-кодов](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="be960-112">Затем перейдите к сведениям об этом компоненте и зелеными кнопками "+" выберите события для отслеживания.</span><span class="sxs-lookup"><span data-stu-id="be960-112">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span>  

![События QR-кодов](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="be960-114">В нашем примере мы подписались на событие OnUpdateTrackedImage, чтобы отображать точку в центре QR-кода и выводить закодированные в QR-коде данные.</span><span class="sxs-lookup"><span data-stu-id="be960-114">Here, we have subscribed to OnUpdateTrackedImage to render a point in the center of a QR Code and print the QR code’s encoded data.</span></span> 

![Пример отрисовки QR-кода](images/unreal-qr-render.PNG)

<span data-ttu-id="be960-116">Сначала приведите отслеживаемое изображение к типу ARTrackedQRCode и убедитесь, что текущее обновленное изображение содержит QR-код.</span><span class="sxs-lookup"><span data-stu-id="be960-116">First cast the tracked image to an ARTrackedQRCode to verify that the current updated image is a QR code.</span></span>  <span data-ttu-id="be960-117">Затем вы сможете получить закодированные данные через переменную QRCode.</span><span class="sxs-lookup"><span data-stu-id="be960-117">Then the encoded data can be retrieved with the QRCode variable.</span></span>  <span data-ttu-id="be960-118">Левый верхний край QR-кода можно получить по расположению GetLocalToWorldTransform.</span><span class="sxs-lookup"><span data-stu-id="be960-118">The top-left of the QR code can be retrieved from the location of GetLocalToWorldTransform.</span></span>  <span data-ttu-id="be960-119">Размеры кода можно получить из свойства GetEstimateSize.</span><span class="sxs-lookup"><span data-stu-id="be960-119">The dimensions can be retrieved with GetEstimateSize.</span></span> 

<span data-ttu-id="be960-120">Каждый QR-код также имеет уникальный код GUID:</span><span class="sxs-lookup"><span data-stu-id="be960-120">Every QR code also has a unique guid ID:</span></span> 

![GUID для QR-кода](images/unreal-qr-guid.PNG)

## <a name="see-also"></a><span data-ttu-id="be960-122">См. также статью</span><span class="sxs-lookup"><span data-stu-id="be960-122">See also</span></span>
* [<span data-ttu-id="be960-123">Отслеживание QR-кода</span><span class="sxs-lookup"><span data-stu-id="be960-123">QR code tracking</span></span>](qr-code-tracking.md)
