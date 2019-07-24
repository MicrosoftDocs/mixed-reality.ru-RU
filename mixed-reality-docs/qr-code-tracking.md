---
title: Отслеживание QR-кода
description: Узнайте, как включить отслеживание QR-кода для головной гарнитуры Windows Mixed Reality (VR) и реализовать эту функцию в приложениях VR.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR, лбе, развлечения на основе расположения, VR Аркадные, Аркадные, иммерсивное, QR, QR-код
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829985"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="71252-104">Отслеживание QR-кода</span><span class="sxs-lookup"><span data-stu-id="71252-104">QR code tracking</span></span>

<span data-ttu-id="71252-105">Отслеживание QR-кода реализуется в драйвере Windows Mixed Reality для головных телефонов (VR).</span><span class="sxs-lookup"><span data-stu-id="71252-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="71252-106">Включив средство трассировки QR-кода в драйвере гарнитуры, гарнитура сканирует QR-коды и сообщает заинтересованным приложениям о них.</span><span class="sxs-lookup"><span data-stu-id="71252-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="71252-107">Эта функция доступна только в [Windows 10 октября с обновлением 2018 (также известное как RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="71252-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="71252-108">Фрагменты кода в этой статье в настоящее время демонстрируют использование C++языка/CX вместо C + +17, соответствующего C++/WinRT, как используется в [ C++ шаблоне проекта holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="71252-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="71252-109">Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="71252-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="71252-110">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="71252-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="71252-111"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="71252-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="71252-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="71252-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="71252-113"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="71252-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="71252-114">Отслеживание QR-кода</span><span class="sxs-lookup"><span data-stu-id="71252-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="71252-115">❌</span><span class="sxs-lookup"><span data-stu-id="71252-115">❌</span></span></td>
        <td><span data-ttu-id="71252-116">✔️</span><span class="sxs-lookup"><span data-stu-id="71252-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="71252-117">Включение и отключение отслеживания QR-кода для гарнитуры</span><span class="sxs-lookup"><span data-stu-id="71252-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="71252-118">Примечание. Этот раздел действителен только для [Windows 10 октября 2018 с обновлением (также известное как RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="71252-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="71252-119">Из сборок 19h1, начиная с версии, это не потребуется делать.</span><span class="sxs-lookup"><span data-stu-id="71252-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="71252-120">Независимо от того, разрабатывается ли приложение для смешанной реальности, которое будет использовать отслеживание QR-кода, или вы являетесь клиентом одного из этих приложений, вам потребуется вручную включить отслеживание QR-кода в драйвере гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="71252-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="71252-121">Чтобы **включить отслеживание QR-кода** для головной гарнитуры (VR), сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="71252-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="71252-122">Закройте приложение портала Mixed Reality на компьютере.</span><span class="sxs-lookup"><span data-stu-id="71252-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="71252-123">Отсоедините гарнитуру от компьютера.</span><span class="sxs-lookup"><span data-stu-id="71252-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="71252-124">В командной строке выполните следующий скрипт:</span><span class="sxs-lookup"><span data-stu-id="71252-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="71252-125">Повторно подключите гарнитуру к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="71252-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="71252-126">Чтобы **отключить отслеживание QR-кода** для головной гарнитуры (VR), выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="71252-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="71252-127">Закройте приложение портала Mixed Reality на компьютере.</span><span class="sxs-lookup"><span data-stu-id="71252-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="71252-128">Отсоедините гарнитуру от компьютера.</span><span class="sxs-lookup"><span data-stu-id="71252-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="71252-129">В командной строке выполните следующий скрипт:</span><span class="sxs-lookup"><span data-stu-id="71252-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="71252-130">Повторно подключите гарнитуру к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="71252-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="71252-131">Это сделает все обнаруженные QR-коды "не размещаемые".</span><span class="sxs-lookup"><span data-stu-id="71252-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="71252-132">Печать кодов</span><span class="sxs-lookup"><span data-stu-id="71252-132">Printing codes</span></span>

<span data-ttu-id="71252-133">В первой и самой самой [спецификации QR-кодов](https://www.qrcode.com/en/howto/code.html) указано "область символов QR-кода требует наличия поля или" скрытой зоны ", которую он будет использовать.</span><span class="sxs-lookup"><span data-stu-id="71252-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="71252-134">Поле является четкой областью вокруг символа, где ничего не печатается.</span><span class="sxs-lookup"><span data-stu-id="71252-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="71252-135">QR-коду требуется четыре модуля на всех сторонах символа. "</span><span class="sxs-lookup"><span data-stu-id="71252-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="71252-136">Она должна иметь ширину на каждой стороне в четыре раза больше размера модуля — единичного Черного квадрата в коде.</span><span class="sxs-lookup"><span data-stu-id="71252-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="71252-137">На странице спецификации содержатся советы по печати QR-кодов и определению области, необходимой для создания QR-кода определенного размера.</span><span class="sxs-lookup"><span data-stu-id="71252-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="71252-138">В настоящее время качество обнаружения QR-кодов является уязвимым для различных освещения и подложки.</span><span class="sxs-lookup"><span data-stu-id="71252-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="71252-139">Чтобы бороться с этим, обратите внимание на освещения и распечатайте соответствующий код.</span><span class="sxs-lookup"><span data-stu-id="71252-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="71252-140">В сцене с особенно ярким освещением распечатайте черный цвет на сером фоне.</span><span class="sxs-lookup"><span data-stu-id="71252-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="71252-141">При низких сценах черный цвет на белом фоне работает.</span><span class="sxs-lookup"><span data-stu-id="71252-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="71252-142">Аналогично, если фон для кода является особенно темным, попробуйте использовать черный цвет в сером коде, если частота обнаружения мала.</span><span class="sxs-lookup"><span data-stu-id="71252-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="71252-143">В противном случае, если заднися светлее, обычный код должен работать нормально.</span><span class="sxs-lookup"><span data-stu-id="71252-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="71252-144">API Кртраккинг</span><span class="sxs-lookup"><span data-stu-id="71252-144">QRTracking API</span></span>

<span data-ttu-id="71252-145">Подключаемый модуль Кртраккинг предоставляет интерфейсы API для отслеживания QR-кода.</span><span class="sxs-lookup"><span data-stu-id="71252-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="71252-146">Чтобы использовать подключаемый модуль, необходимо использовать следующие типы из пространства имен *кркодестраккерплугин* .</span><span class="sxs-lookup"><span data-stu-id="71252-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

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

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="71252-147">Реализация отслеживания QR-кода в Unity</span><span class="sxs-lookup"><span data-stu-id="71252-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="71252-148">Пример сцен Unity в МРТК (набор средств для смешанной реальности)</span><span class="sxs-lookup"><span data-stu-id="71252-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="71252-149">Пример использования API отслеживания QR-кодов можно найти на [сайте GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)для набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="71252-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="71252-150">МРТК реализовала необходимые сценарии для симпилифи использования отслеживания QR-кодов.</span><span class="sxs-lookup"><span data-stu-id="71252-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="71252-151">Все необходимые активы для разработки приложений для отслеживания QR-файлов находятся в папке "Кртраккер".</span><span class="sxs-lookup"><span data-stu-id="71252-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="71252-152">Существует два монтажных фрагмента: первый — пример для простого отображения сведений о QR-кодах при их обнаружении, а во втором демонстрируется использование системы координат, прикрепленной к QR-коду, для отображения голограмм.</span><span class="sxs-lookup"><span data-stu-id="71252-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="71252-153">Существует prefab "Крсканнер", который добавил все необходимые сценарии в сцен для использования Кркодес.</span><span class="sxs-lookup"><span data-stu-id="71252-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="71252-154">Кркодеманажер сценария — это одноэлементный класс, реализующий API Кркоде.</span><span class="sxs-lookup"><span data-stu-id="71252-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="71252-155">Его необходимо добавить в сцену.</span><span class="sxs-lookup"><span data-stu-id="71252-155">This needs to be added to your scene.</span></span> <span data-ttu-id="71252-156">Сценарий «Аттачтокркоде» используется для прикрепления голограмм к системам координат QR-кода. Этот сценарий можно добавить к любой из ваших голограмм.</span><span class="sxs-lookup"><span data-stu-id="71252-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="71252-157">В "Спатиалграфкурдинатесистем" показано, как использовать систему координат Кркоде.</span><span class="sxs-lookup"><span data-stu-id="71252-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="71252-158">Эти скрипты можно использовать как есть в сценах проекта, или вы можете написать собственный объект непосредственно с помощью подключаемого модуля, как описано выше.</span><span class="sxs-lookup"><span data-stu-id="71252-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="71252-159">Реализация отслеживания QR-кода в Unity без МРТК</span><span class="sxs-lookup"><span data-stu-id="71252-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="71252-160">Вы также можете использовать API отслеживания QR в Unity, не принимая во внимание зависимость от МРТК.</span><span class="sxs-lookup"><span data-stu-id="71252-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="71252-161">Чтобы использовать API, необходимо подготовить проект с помощью следующей инструкции:</span><span class="sxs-lookup"><span data-stu-id="71252-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="71252-162">Создайте новую папку в папке Assets проекта Unity с именем: "Подключаемые модули".</span><span class="sxs-lookup"><span data-stu-id="71252-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="71252-163">Скопируйте все необходимые файлы из [этой папки](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) в локальную папку "Plugins", которая была только что создана.</span><span class="sxs-lookup"><span data-stu-id="71252-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="71252-164">Вы можете использовать скрипты отслеживания QR в [папке сценариев мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) или написать собственный.</span><span class="sxs-lookup"><span data-stu-id="71252-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="71252-165">Примечание. Эти подключаемые модули предназначены только для сборок [Windows 10 октябрь 2018 с обновлением (также известных как RS5)](release-notes-october-2018.md) .</span><span class="sxs-lookup"><span data-stu-id="71252-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="71252-166">Подключаемые модули будут обновлены в следующем выпуске Windows.</span><span class="sxs-lookup"><span data-stu-id="71252-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="71252-167">Текущие подключаемые модули были экспериментальными и не будут работать в будущих версиях Windows.</span><span class="sxs-lookup"><span data-stu-id="71252-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="71252-168">Будут опубликованы новые подключаемые модули, которые можно использовать в следующем выпуске Windows, и они не будут поддерживать обратную совместимость и не будут работать с RS5).</span><span class="sxs-lookup"><span data-stu-id="71252-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="71252-169">Реализация отслеживания QR-кода в DirectX</span><span class="sxs-lookup"><span data-stu-id="71252-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="71252-170">Чтобы использовать Кртраккингплугин в Visual Studio, необходимо добавить ссылку на Кртраккингплугин в WINMD-файла.</span><span class="sxs-lookup"><span data-stu-id="71252-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="71252-171">[Необходимые файлы для поддерживаемых платформ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)можно найти здесь.</span><span class="sxs-lookup"><span data-stu-id="71252-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

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

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="71252-172">Получение системы координат</span><span class="sxs-lookup"><span data-stu-id="71252-172">Getting a coordinate system</span></span>

<span data-ttu-id="71252-173">Мы определим правую систему координат, согласованную с QR-кодом в левом верхнем углу квадрата быстрого обнаружения в левом верху.</span><span class="sxs-lookup"><span data-stu-id="71252-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="71252-174">Ниже показана система координат.</span><span class="sxs-lookup"><span data-stu-id="71252-174">The coordinate system is shown below.</span></span> <span data-ttu-id="71252-175">Ось Z указывает на бумагу (не показано), но в Unity ось z находится за пределами бумаги и левши.</span><span class="sxs-lookup"><span data-stu-id="71252-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="71252-176">Определяется Спатиалкурдинатесистем, который выводится по отображаемому рассогласованию.</span><span class="sxs-lookup"><span data-stu-id="71252-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="71252-177">Эта система координат может быть получена с платформы с помощью окон API *::P ерцептион:: spatial::P проверка:: спатиалграфинтероппревиев:: креатекурдинатесистемфорноде*.</span><span class="sxs-lookup"><span data-stu-id="71252-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![Система координат QR-кода](images/Qr-coordinatesystem.png) 

<span data-ttu-id="71252-179">В следующем коде из объекта Кркоде ^ Code показано, как создать прямоугольник и разместить его в системе координат QR:</span><span class="sxs-lookup"><span data-stu-id="71252-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

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

<span data-ttu-id="71252-180">Для создания QR-прямоугольника можно использовать физический размер:</span><span class="sxs-lookup"><span data-stu-id="71252-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="71252-181">Систему координат можно использовать для рисования QR-кода или прикрепления голограмм к расположению:</span><span class="sxs-lookup"><span data-stu-id="71252-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="71252-182">В целом, *кркодестраккерплугин:: кркодеаддедхандлер* может выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="71252-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="71252-183">Устранение неполадок и часто задаваемые вопросы</span><span class="sxs-lookup"><span data-stu-id="71252-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="71252-184">**Общие сведения об устранении неполадок**</span><span class="sxs-lookup"><span data-stu-id="71252-184">**General troubleshooting**</span></span>

* <span data-ttu-id="71252-185">Ваш ПК работает под управлением Windows 10 октября с обновлением 2018?</span><span class="sxs-lookup"><span data-stu-id="71252-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="71252-186">Вы установили ключ reg?</span><span class="sxs-lookup"><span data-stu-id="71252-186">Have you set the reg key?</span></span> <span data-ttu-id="71252-187">После этого устройство перезагружено?</span><span class="sxs-lookup"><span data-stu-id="71252-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="71252-188">Поддерживается ли версия QR-кода поддерживаемой версией?</span><span class="sxs-lookup"><span data-stu-id="71252-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="71252-189">Текущий API поддерживает до версии 20 с кодом QR.</span><span class="sxs-lookup"><span data-stu-id="71252-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="71252-190">Мы рекомендуем использовать версию 5 для общего использования.</span><span class="sxs-lookup"><span data-stu-id="71252-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="71252-191">Достаточно близко к QR-коду?</span><span class="sxs-lookup"><span data-stu-id="71252-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="71252-192">Чем ближе камера к QR-коду, тем выше эта версия может поддерживаться API.</span><span class="sxs-lookup"><span data-stu-id="71252-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="71252-193">**Как это должно быть в QR-коде для его обнаружения?**</span><span class="sxs-lookup"><span data-stu-id="71252-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="71252-194">Это будет зависеть от размера QR-кода, а также от его версии.</span><span class="sxs-lookup"><span data-stu-id="71252-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="71252-195">Для QR-кода версии 1, наличного от 5 сторон cm до 25 Сторон cm, минимальное расстояние обнаружения составляет от 0,15 метров до 0,5 метров.</span><span class="sxs-lookup"><span data-stu-id="71252-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="71252-196">Самое далекое из них можно обнаружить, отказаться от приблизительно 0,3 метров для меньших объемов QR-кода до 1,4 метров.</span><span class="sxs-lookup"><span data-stu-id="71252-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="71252-197">Для больших QR-кодов, которые больше этого размера, можно оценить. Расстояние обнаружения для размера увеличивается линейно.</span><span class="sxs-lookup"><span data-stu-id="71252-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="71252-198">Наш датчик не работает с QR-кодами с сторонами, размер которых меньше 5 см.</span><span class="sxs-lookup"><span data-stu-id="71252-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="71252-199">**Работают ли QR-коды с логотипами?**</span><span class="sxs-lookup"><span data-stu-id="71252-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="71252-200">QR-коды с логотипами не тестировались и в настоящее время не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="71252-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="71252-201">**Разделы справки удалить QR-коды из моего приложения, чтобы они не сохранялись?**</span><span class="sxs-lookup"><span data-stu-id="71252-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="71252-202">QR-коды сохраняются только в сеансе загрузки.</span><span class="sxs-lookup"><span data-stu-id="71252-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="71252-203">После перезагрузки (или перезапуска драйвера) они будут пропала и обнаружены как новые объекты в следующий раз.</span><span class="sxs-lookup"><span data-stu-id="71252-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="71252-204">Журнал QR-кодов сохраняется на уровне системы в сеансе драйвера, но вы можете настроить приложение таким же, чтобы при необходимости игнорировать QR-коды старше определенной метки времени.</span><span class="sxs-lookup"><span data-stu-id="71252-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="71252-205">В настоящее время API поддерживает очистку журнала QR-кода, так как данные могут заинтересовать несколько приложений.</span><span class="sxs-lookup"><span data-stu-id="71252-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="71252-206">**Подключаемые модули для RS5 и будущих версий не поддерживают совместимость** RS5 версия подключаемого модуля работает только для RS5 и не будет работать в будущих версиях.</span><span class="sxs-lookup"><span data-stu-id="71252-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="71252-207">Подключаемый модуль експерментал будет заменен реальным подключаемым модулем и должен быть тем, который можно использовать в будущих версиях Windows.</span><span class="sxs-lookup"><span data-stu-id="71252-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
