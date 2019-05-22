---
title: QR-код отслеживания
description: Узнайте, как включить отслеживание в Windows Mixed Reality иммерсивных (VR) гарнитура QR-кода и реализации функции в приложениях виртуальной Реальности.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR lbe, развлечения на основе расположения, vr arcade arcade эффект присутствия, qr, QR-кода
ms.openlocfilehash: e6588552c0cfa8bffa19ac2be5c247c5f73dc19c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974895"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="ff50c-104">QR-код отслеживания</span><span class="sxs-lookup"><span data-stu-id="ff50c-104">QR code tracking</span></span>

<span data-ttu-id="ff50c-105">QR-код отслеживания реализуется в драйвере Windows Mixed Reality для иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="ff50c-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="ff50c-106">Включив модуль отслеживания кода QR в драйвере гарнитуры, гарнитура проверяет наличие QR-коды, и они помечаются для заинтересованных приложений.</span><span class="sxs-lookup"><span data-stu-id="ff50c-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="ff50c-107">Эта функция доступна только начиная с версии [10 октября 2018 года Центр обновления Windows (также известный как RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="ff50c-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="ff50c-108">Фрагменты кода в этой статье, в настоящее время демонстрации применения C++/CX, а не C ++ 17-совместимым C++/WinRT в [ C++ шаблон проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="ff50c-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="ff50c-109">Основные понятия будут эквивалентны C++/WinRT проекта, то, что необходимо преобразовать код в код.</span><span class="sxs-lookup"><span data-stu-id="ff50c-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="ff50c-110">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="ff50c-110">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ff50c-111">Компонент</span><span class="sxs-lookup"><span data-stu-id="ff50c-111">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="ff50c-112"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff50c-112"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff50c-113"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="ff50c-113"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ff50c-114">QR-код отслеживания</span><span class="sxs-lookup"><span data-stu-id="ff50c-114">QR code tracking</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="ff50c-115">✔️</span><span class="sxs-lookup"><span data-stu-id="ff50c-115">✔️</span></span></td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="ff50c-116">Включение и отключение QR код отслеживания для вашей гарнитура</span><span class="sxs-lookup"><span data-stu-id="ff50c-116">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="ff50c-117">Примечание. В этом разделе допустимо только для [10 октября 2018 года Центр обновления Windows (также известный как RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="ff50c-117">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="ff50c-118">Из сборок 19h 1 и более поздних версий не имеется для этого.</span><span class="sxs-lookup"><span data-stu-id="ff50c-118">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="ff50c-119">Вы разрабатываете приложение смешанной реальности, которое будет использовать отслеживание QR-код, или вы являетесь клиентом одного из этих приложений, необходимо вручную включить отслеживания в драйвере вашей гарнитура QR-код.</span><span class="sxs-lookup"><span data-stu-id="ff50c-119">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="ff50c-120">Чтобы **включите QR-код отслеживания** для вашей иммерсивных Гарнитура (VR):</span><span class="sxs-lookup"><span data-stu-id="ff50c-120">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="ff50c-121">Закройте приложение смешанной реальности портала на вашем Компьютере.</span><span class="sxs-lookup"><span data-stu-id="ff50c-121">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="ff50c-122">Отключите гарнитура с вашего компьютера.</span><span class="sxs-lookup"><span data-stu-id="ff50c-122">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="ff50c-123">Выполните следующий скрипт в командной строке:</span><span class="sxs-lookup"><span data-stu-id="ff50c-123">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="ff50c-124">Повторное подключение вашего гарнитура на вашем ПК.</span><span class="sxs-lookup"><span data-stu-id="ff50c-124">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="ff50c-125">Чтобы **отключить QR-код отслеживания** для вашей иммерсивных Гарнитура (VR):</span><span class="sxs-lookup"><span data-stu-id="ff50c-125">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="ff50c-126">Закройте приложение смешанной реальности портала на вашем Компьютере.</span><span class="sxs-lookup"><span data-stu-id="ff50c-126">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="ff50c-127">Отключите гарнитура с вашего компьютера.</span><span class="sxs-lookup"><span data-stu-id="ff50c-127">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="ff50c-128">Выполните следующий скрипт в командной строке:</span><span class="sxs-lookup"><span data-stu-id="ff50c-128">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="ff50c-129">Повторное подключение вашего гарнитура на вашем ПК.</span><span class="sxs-lookup"><span data-stu-id="ff50c-129">Reconnect your headset to your PC.</span></span> <span data-ttu-id="ff50c-130">Это сделает все обнаруженные QR-коды «не-может быть найдена.»</span><span class="sxs-lookup"><span data-stu-id="ff50c-130">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="ff50c-131">Коды печати</span><span class="sxs-lookup"><span data-stu-id="ff50c-131">Printing codes</span></span>

<span data-ttu-id="ff50c-132">Прежде всего [спецификаций для QR-коды](https://www.qrcode.com/en/howto/code.html) говорит: «области символ QR-код требует поле или в «тихом зону» вокруг его можно использовать.</span><span class="sxs-lookup"><span data-stu-id="ff50c-132">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="ff50c-133">Поле-это очистить область вокруг символа, где ничего не выводится.</span><span class="sxs-lookup"><span data-stu-id="ff50c-133">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="ff50c-134">QR-код требует четыре модуля предсказанную во все стороны символа».</span><span class="sxs-lookup"><span data-stu-id="ff50c-134">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="ff50c-135">Это нужно имеют ширину, на каждой стороне, четыре раза больше объема модуль — единый черный квадрат в коде.</span><span class="sxs-lookup"><span data-stu-id="ff50c-135">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="ff50c-136">Спецификации страница содержит советы о том, как выполнить печать QR-коды и определить области, который требуется для того, определенные по размеру QR-кода.</span><span class="sxs-lookup"><span data-stu-id="ff50c-136">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="ff50c-137">В настоящее время качества обнаружения QR-кода делает возможной различными освещения и задника.</span><span class="sxs-lookup"><span data-stu-id="ff50c-137">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="ff50c-138">Для решения этой проблемы Обратите внимание на освещения и печать соответствующий код.</span><span class="sxs-lookup"><span data-stu-id="ff50c-138">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="ff50c-139">В сцене с особенно ярко-освещения напечатать, являющейся черной на сером фоне.</span><span class="sxs-lookup"><span data-stu-id="ff50c-139">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="ff50c-140">В условиях низкой освещенности сцены, черного на белый works.</span><span class="sxs-lookup"><span data-stu-id="ff50c-140">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="ff50c-141">Аналогичным образом Если особенно темно-backdrop к коду, попробуйте черного на серую кода в случае низкой скорости обнаружения.</span><span class="sxs-lookup"><span data-stu-id="ff50c-141">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="ff50c-142">В противном случае если подложки светлее, обычный код должна работать нормально.</span><span class="sxs-lookup"><span data-stu-id="ff50c-142">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="ff50c-143">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="ff50c-143">QRTracking API</span></span>

<span data-ttu-id="ff50c-144">Подключаемый модуль QRTracking предоставляет интерфейсы API для отслеживания QR-код.</span><span class="sxs-lookup"><span data-stu-id="ff50c-144">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="ff50c-145">Чтобы использовать подключаемый модуль, необходимо использовать следующие типы из *QRCodesTrackerPlugin* пространства имен.</span><span class="sxs-lookup"><span data-stu-id="ff50c-145">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="ff50c-146">Реализация отслеживания в Unity QR-кода</span><span class="sxs-lookup"><span data-stu-id="ff50c-146">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="ff50c-147">Пример Unity сцен в MRTK (смешанной реальности Toolkit)</span><span class="sxs-lookup"><span data-stu-id="ff50c-147">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="ff50c-148">Пример использования API отслеживания QR в смешанной реальности Toolkit можно найти [сайт GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span><span class="sxs-lookup"><span data-stu-id="ff50c-148">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="ff50c-149">MRTK реализовала необходимые скрипты для simpilify QR, отслеживание использования.</span><span class="sxs-lookup"><span data-stu-id="ff50c-149">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="ff50c-150">Все необходимые ресурсы для разработки QR отслеживания приложений находятся в папке «QRTracker».</span><span class="sxs-lookup"><span data-stu-id="ff50c-150">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="ff50c-151">Существуют двумя сценами: во-первых, пример, чтобы просто отобразить сведения о QR-коды, как их обнаружения, а второй показано, как использовать систему координат, подключенный к QR-код для отображения голограммы.</span><span class="sxs-lookup"><span data-stu-id="ff50c-151">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="ff50c-152">Нет prefab «QRScanner», добавлены все необходимые скрипты автоматически использовать QRCodes.</span><span class="sxs-lookup"><span data-stu-id="ff50c-152">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="ff50c-153">Сценарий QRCodeManager является singleton-класс, реализующий QRCode API.</span><span class="sxs-lookup"><span data-stu-id="ff50c-153">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="ff50c-154">Это должен быть добавлен в сцену.</span><span class="sxs-lookup"><span data-stu-id="ff50c-154">This needs to be added to your scene.</span></span> <span data-ttu-id="ff50c-155">Сценарий «AttachToQRCode» используется для присоединения голограммы для системы координат QR-код, этот сценарий можно добавить к любому из вашей голограммы.</span><span class="sxs-lookup"><span data-stu-id="ff50c-155">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="ff50c-156">«SpatialGraphCoordinateSystem» показано, как используется система координат QRCode.</span><span class="sxs-lookup"><span data-stu-id="ff50c-156">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="ff50c-157">Эти сценарии можно использовать в качестве-находится в проекте сцен. также можно написать собственный непосредственно с помощью подключаемого модуля как описано выше.</span><span class="sxs-lookup"><span data-stu-id="ff50c-157">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="ff50c-158">Реализация отслеживания в Unity без MRTK QR-кода</span><span class="sxs-lookup"><span data-stu-id="ff50c-158">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="ff50c-159">Можно также использовать API отслеживания QR в Unity не полагаться на MRTK.</span><span class="sxs-lookup"><span data-stu-id="ff50c-159">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="ff50c-160">Для использования API, необходимо подготовить проект со следующей инструкцией:</span><span class="sxs-lookup"><span data-stu-id="ff50c-160">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="ff50c-161">Создайте новую папку в папке assets проекта unity с именем: «Подключаемые модули».</span><span class="sxs-lookup"><span data-stu-id="ff50c-161">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="ff50c-162">Скопируйте все необходимые файлы из [эту папку](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) в локальной папке «Подключаемые модули», вы только что создали.</span><span class="sxs-lookup"><span data-stu-id="ff50c-162">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="ff50c-163">Можно использовать QR, отслеживания скрипты в [папке scripts MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) или написать собственный.</span><span class="sxs-lookup"><span data-stu-id="ff50c-163">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="ff50c-164">Примечание. Они предназначены только для [10 октября 2018 года Центр обновления Windows (также известный как RS5)](release-notes-october-2018.md) сборки.</span><span class="sxs-lookup"><span data-stu-id="ff50c-164">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="ff50c-165">Подключаемые модули будут обновляться в следующем выпуске windows.</span><span class="sxs-lookup"><span data-stu-id="ff50c-165">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="ff50c-166">Текущий подключаемые модули были экспериментальных и не будет работать для будущих версиях windows.</span><span class="sxs-lookup"><span data-stu-id="ff50c-166">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="ff50c-167">Будут опубликованы новые подключаемые модули, который может использоваться в следующем выпуске windows и они не будут обратной предварительными и не будет работать с RS5).</span><span class="sxs-lookup"><span data-stu-id="ff50c-167">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="ff50c-168">Реализация отслеживания в DirectX QR-кода</span><span class="sxs-lookup"><span data-stu-id="ff50c-168">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="ff50c-169">Чтобы использовать QRTrackingPlugin в Visual Studio, необходимо добавить ссылку на QRTrackingPlugin .winmd.</span><span class="sxs-lookup"><span data-stu-id="ff50c-169">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="ff50c-170">Можно найти [необходимые файлы для поддерживаемых платформ здесь](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span><span class="sxs-lookup"><span data-stu-id="ff50c-170">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="ff50c-171">Начало системы координат</span><span class="sxs-lookup"><span data-stu-id="ff50c-171">Getting a coordinate system</span></span>

<span data-ttu-id="ff50c-172">Мы определяем справа системы координат, выровнены с QR-код в верхнем левом углу квадрата быстрого обнаружения в верхнем левом углу.</span><span class="sxs-lookup"><span data-stu-id="ff50c-172">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="ff50c-173">Ниже приведен систему координат.</span><span class="sxs-lookup"><span data-stu-id="ff50c-173">The coordinate system is shown below.</span></span> <span data-ttu-id="ff50c-174">Указывает оси z в документе (не показан), но в Unity — ось z нет бумаги и для левши.</span><span class="sxs-lookup"><span data-stu-id="ff50c-174">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="ff50c-175">SpatialCoordinateSystem определяется, выравнивается, как показано.</span><span class="sxs-lookup"><span data-stu-id="ff50c-175">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="ff50c-176">Эту систему координат можно получить из платформы, с помощью API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span><span class="sxs-lookup"><span data-stu-id="ff50c-176">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![Система координат QR-кода](images/Qr-coordinatesystem.png) 

<span data-ttu-id="ff50c-178">Из QRCode ^ объекта кода, приведенный ниже показано, как создать прямоугольник и поместите его в системе координат QR:</span><span class="sxs-lookup"><span data-stu-id="ff50c-178">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

<span data-ttu-id="ff50c-179">Чтобы создать прямоугольник QR можно использовать физический размер:</span><span class="sxs-lookup"><span data-stu-id="ff50c-179">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="ff50c-180">Можно использовать систему координат для рисования QR-код или вложения голограммы расположение:</span><span class="sxs-lookup"><span data-stu-id="ff50c-180">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="ff50c-181">В общей сложности вашего *QRCodesTrackerPlugin::QRCodeAddedHandler* может выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ff50c-181">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="ff50c-182">Устранение неполадок и часто задаваемые вопросы</span><span class="sxs-lookup"><span data-stu-id="ff50c-182">Troubleshooting and FAQ</span></span>

<span data-ttu-id="ff50c-183">**Устранение общих неполадок**</span><span class="sxs-lookup"><span data-stu-id="ff50c-183">**General troubleshooting**</span></span>

* <span data-ttu-id="ff50c-184">— Это ваш ПК под управлением Windows 10 октября 2018 обновление?</span><span class="sxs-lookup"><span data-stu-id="ff50c-184">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="ff50c-185">Вы задали ключ реестра?</span><span class="sxs-lookup"><span data-stu-id="ff50c-185">Have you set the reg key?</span></span> <span data-ttu-id="ff50c-186">После перезапуска устройства?</span><span class="sxs-lookup"><span data-stu-id="ff50c-186">Restarted the device afterwards?</span></span>
* <span data-ttu-id="ff50c-187">Версия QR код поддерживаемой версии?</span><span class="sxs-lookup"><span data-stu-id="ff50c-187">Is the QR code version a supported version?</span></span> <span data-ttu-id="ff50c-188">Текущий API поддерживает до 20 версии QR код.</span><span class="sxs-lookup"><span data-stu-id="ff50c-188">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="ff50c-189">Мы рекомендуем использовать версии 5 для общего использования.</span><span class="sxs-lookup"><span data-stu-id="ff50c-189">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="ff50c-190">Они вам достаточно близко к QR-код?</span><span class="sxs-lookup"><span data-stu-id="ff50c-190">Are you close enough to the QR code?</span></span> <span data-ttu-id="ff50c-191">Чем ближе камеры на QR-код, тем выше QR код версии API может поддерживать.</span><span class="sxs-lookup"><span data-stu-id="ff50c-191">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="ff50c-192">**Насколько точно нужно быть QR-код для его обнаружения?**</span><span class="sxs-lookup"><span data-stu-id="ff50c-192">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="ff50c-193">Это будет зависеть от размера QR-код, а также версии это.</span><span class="sxs-lookup"><span data-stu-id="ff50c-193">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="ff50c-194">Для версии 1 QR-код, изменения из сторон 5 cm на 25 cm стороны обнаружение минимальное расстояние в диапазоне от 0,15 метров 0,5 м.</span><span class="sxs-lookup"><span data-stu-id="ff50c-194">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="ff50c-195">Выбирается самый дальний сейчас, они могут быть обнаружены из переходит от около 0,3 счетчики для целевых объектов меньшего размера QR код 1,4 счетчиков для больше.</span><span class="sxs-lookup"><span data-stu-id="ff50c-195">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="ff50c-196">Для QR-коды, больше, чем можно оценить; расстояние обнаружения для размера растет линейно.</span><span class="sxs-lookup"><span data-stu-id="ff50c-196">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="ff50c-197">Наши средства отслеживания не работает с QR-коды с сторон меньше, чем 5 см.</span><span class="sxs-lookup"><span data-stu-id="ff50c-197">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="ff50c-198">**Сделать QR-коды с работой логотипы?**</span><span class="sxs-lookup"><span data-stu-id="ff50c-198">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="ff50c-199">QR-коды с логотипами не были протестированы и сейчас не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="ff50c-199">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="ff50c-200">**Как очистить QR-коды из моего приложения, они не существуют?**</span><span class="sxs-lookup"><span data-stu-id="ff50c-200">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="ff50c-201">QR-коды сохраняются только в рамках сеанса загрузки.</span><span class="sxs-lookup"><span data-stu-id="ff50c-201">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="ff50c-202">После перезагрузки (или перезапустить драйвер), они будут покинут и определяются как новые объекты в следующий раз.</span><span class="sxs-lookup"><span data-stu-id="ff50c-202">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="ff50c-203">QR код журнал сохраняется на уровне системы в сеансе драйвер, но можно настроить приложения, чтобы игнорировать QR-коды, которые старше определенной метке времени, если требуется.</span><span class="sxs-lookup"><span data-stu-id="ff50c-203">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="ff50c-204">В настоящее время API-Интерфейс поддерживает журнал Очистка QR код, как несколько приложений могут быть заинтересованы в данных.</span><span class="sxs-lookup"><span data-stu-id="ff50c-204">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="ff50c-205">**Подключаемые модули для RS5 и будущих версий несовместимы** RS5 версии подключаемый модуль работает только для RS5 и не будет работать для будущих версий.</span><span class="sxs-lookup"><span data-stu-id="ff50c-205">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="ff50c-206">Подключаемый модуль expermental будут заменены на реальных подключаемого модуля и должен быть тем, что вы можете использовать в будущих версиях windows.</span><span class="sxs-lookup"><span data-stu-id="ff50c-206">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
