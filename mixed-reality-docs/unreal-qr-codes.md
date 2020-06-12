---
title: QR-коды в Unreal
description: Введение в использование QR-кодов в Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, QR-коды
ms.openlocfilehash: 90a51227ae455389168fb3262e83f34b64a7bfb5
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428751"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="beafa-104">QR-коды в Unreal</span><span class="sxs-lookup"><span data-stu-id="beafa-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="beafa-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="beafa-105">Overview</span></span>

<span data-ttu-id="beafa-106">Устройство HoloLens 2 способно видеть QR-коды в мировом пространстве с помощью веб-камеры, отрисовывая их в виде голограмм с использованием системы координат в месте расположения каждого QR-кода в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="beafa-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="beafa-107">Помимо одиночных QR-кодов, HoloLens 2 может также отрисовывать голограммы в одном и том же месте на нескольких устройствах для общего взаимодействия с несколькими пользователями.</span><span class="sxs-lookup"><span data-stu-id="beafa-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="beafa-108">Соблюдайте рекомендации по добавлению QR-кодов в приложения:</span><span class="sxs-lookup"><span data-stu-id="beafa-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="beafa-109">Тихие зоны</span><span class="sxs-lookup"><span data-stu-id="beafa-109">Quiet zones</span></span>
- <span data-ttu-id="beafa-110">Освещение и фон</span><span class="sxs-lookup"><span data-stu-id="beafa-110">Lighting and backdrop</span></span>
- <span data-ttu-id="beafa-111">Размер, расстояние и угловое положение</span><span class="sxs-lookup"><span data-stu-id="beafa-111">Size, distance, and angular position</span></span>

<span data-ttu-id="beafa-112">Размещая QR-коды в приложении, следует уделять особое внимание [особенностям пространственной среды](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="beafa-112">Pay special attention to the [environment considerations](environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="beafa-113">Более подробные сведения по каждой из этих тем, а также инструкции по скачиванию соответствующего пакета NuGet см. в главном документе "[Отслеживание QR-кодов](qr-code-tracking.md)".</span><span class="sxs-lookup"><span data-stu-id="beafa-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](qr-code-tracking.md) document.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="beafa-114">Включение обнаружения QR-кодов</span><span class="sxs-lookup"><span data-stu-id="beafa-114">Enabling QR detection</span></span>
<span data-ttu-id="beafa-115">Поскольку для обнаружения QR-кодов устройству HoloLens 2 нужно задействовать веб-камеру, необходимо включить эту функцию в параметрах проекта:</span><span class="sxs-lookup"><span data-stu-id="beafa-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="beafa-116">Выберите **Edit > Project Settings** (Правка > Параметры проекта), прокрутите вниз до раздела **Platforms** (Платформы) и выберите **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="beafa-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="beafa-117">Разверните раздел **Capabilities** (Возможности) и установите флажок **Webcam** (Веб-камера).</span><span class="sxs-lookup"><span data-stu-id="beafa-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="beafa-118">Необходимо также включить отслеживание QR-кодов, [добавив ресурс ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset) (по умолчанию оно выключено).</span><span class="sxs-lookup"><span data-stu-id="beafa-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="beafa-119">Настройка отслеживаемого изображения</span><span class="sxs-lookup"><span data-stu-id="beafa-119">Setting up a tracked image</span></span>

<span data-ttu-id="beafa-120">QR-коды выводятся в виде отслеживаемого изображения через систему отслеживания геометрии в дополненной реальности Unreal.</span><span class="sxs-lookup"><span data-stu-id="beafa-120">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="beafa-121">Чтобы обеспечить работу этого механизма:</span><span class="sxs-lookup"><span data-stu-id="beafa-121">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="beafa-122">Создайте схему Blueprint и добавьте в нее компонент **ARTrackableNotify**.</span><span class="sxs-lookup"><span data-stu-id="beafa-122">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![AR Trackable Notify для QR-кодов](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="beafa-124">Выберите компонент **ARTrackableNotify** и в панели **Details** (Сведения) разверните раздел **Events** (События).</span><span class="sxs-lookup"><span data-stu-id="beafa-124">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span> 

![События QR-кодов](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="beafa-126">Нажмите кнопку **+** напротив события **On Add Tracked Geometry** (При добавлении отслеживаемой геометрии), чтобы добавить соответствующий узел в граф событий.</span><span class="sxs-lookup"><span data-stu-id="beafa-126">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="beafa-127">Полный список событий можно найти в API объекта [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="beafa-127">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

![Пример отрисовки QR-кода](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="beafa-129">Использование отслеживаемого изображения</span><span class="sxs-lookup"><span data-stu-id="beafa-129">Using a tracked image</span></span>
<span data-ttu-id="beafa-130">В графе событий, показанном на следующей иллюстрации, событие **OnUpdateTrackedImage** используется для отрисовки точки в центре QR-кода и печати его данных.</span><span class="sxs-lookup"><span data-stu-id="beafa-130">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span> 

![Пример отрисовки QR-кода](images/unreal-qr-render.PNG)

<span data-ttu-id="beafa-132">Вот что здесь происходит:</span><span class="sxs-lookup"><span data-stu-id="beafa-132">Here's waht's going on:</span></span>
1. <span data-ttu-id="beafa-133">Сначала отслеживаемое изображение приводится к типу **ARTrackedQRCode** и проверяется, что текущее обновленное изображение содержит QR-код.</span><span class="sxs-lookup"><span data-stu-id="beafa-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="beafa-134">Закодированные данные извлекаются из переменной **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="beafa-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="beafa-135">Координаты левого верхнего угла QR-кода можно получить из расположения, возвращаемого функцией **GetLocalToWorldTransform**, а размеры кода — с помощью функции **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="beafa-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span> 

<span data-ttu-id="beafa-136">Можно также [получить систему координат для QR-кода](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) в программном коде.</span><span class="sxs-lookup"><span data-stu-id="beafa-136">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="beafa-137">Поиск уникального идентификатора</span><span class="sxs-lookup"><span data-stu-id="beafa-137">Finding the unique ID</span></span>
<span data-ttu-id="beafa-138">Каждый QR-код имеет уникальный идентификатор (GUID), найти который можно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="beafa-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="beafa-139">Перетащите закрепление **As ARTracked QRCode** (Как отслеживаемый QR-код дополненной реальности) и найдите узел **Get Unique ID** (Получить уникальный идентификатор).</span><span class="sxs-lookup"><span data-stu-id="beafa-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID для QR-кода](images/unreal-qr-guid.PNG)

<span data-ttu-id="beafa-141">При работе с QR-кодами многое происходит за кадром, поэтому приведенные здесь сведения не исчерпывающие.</span><span class="sxs-lookup"><span data-stu-id="beafa-141">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="beafa-142">Ознакомьтесь с материалами по приведенным ниже ссылкам, чтобы узнать подробнее, как все организовано на более низком уровне.</span><span class="sxs-lookup"><span data-stu-id="beafa-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="see-also"></a><span data-ttu-id="beafa-143">См. также статью</span><span class="sxs-lookup"><span data-stu-id="beafa-143">See also</span></span>
* [<span data-ttu-id="beafa-144">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="beafa-144">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="beafa-145">Голограммы</span><span class="sxs-lookup"><span data-stu-id="beafa-145">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="beafa-146">Системы координат</span><span class="sxs-lookup"><span data-stu-id="beafa-146">Coordinate systems</span></span>](coordinate-systems.md)