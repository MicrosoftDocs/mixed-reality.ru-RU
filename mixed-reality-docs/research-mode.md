---
title: Режим исследования HoloLens
description: С помощью режима исследований в HoloLens приложение может получать доступ к потокам датчиков устройств (глубина, отслеживание среды и IR-рефлективити).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: режим исследования, КП, RS4, компьютерное зрение, исследование, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829930"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="faf0d-104">Режим исследования HoloLens</span><span class="sxs-lookup"><span data-stu-id="faf0d-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="faf0d-105">Эта функция была добавлена как часть [обновления Windows 10 от апреля 2018](release-notes-april-2018.md) для HoloLens и недоступна в более ранних выпусках.</span><span class="sxs-lookup"><span data-stu-id="faf0d-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="faf0d-106">Режим исследования — это новая возможность HoloLens, которая предоставляет приложению доступ к датчикам ключей на устройстве.</span><span class="sxs-lookup"><span data-stu-id="faf0d-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="faf0d-107">К ним можно отнести следующие.</span><span class="sxs-lookup"><span data-stu-id="faf0d-107">These include:</span></span>
- <span data-ttu-id="faf0d-108">Четыре камеры отслеживания среды, используемые системой для отслеживания построений и головных карт.</span><span class="sxs-lookup"><span data-stu-id="faf0d-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="faf0d-109">Две версии данных камеры с глубиной — один для высокоскоростного (30 КАДРОВого) подсчета, который обычно используется в отслеживании, а другой — для дальнего многофакторного определения (1/сек), которое в настоящее время используется для пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="faf0d-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="faf0d-110">Две версии потока рефлективити, используемые HoloLens для расчета глубины, но ценные в собственном виде, так как эти образы загораются из HoloLens и не зависят от внешнего освещения.</span><span class="sxs-lookup"><span data-stu-id="faf0d-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="faf0d-111">![Снимок экрана приложения в режиме исследования](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="faf0d-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="faf0d-112">*Запись в смешанной реальности тестового приложения, отображающего восемь потоков датчиков, доступных в режиме исследования.*</span><span class="sxs-lookup"><span data-stu-id="faf0d-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="faf0d-113">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="faf0d-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="faf0d-114"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="faf0d-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="faf0d-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="faf0d-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="faf0d-116"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="faf0d-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="faf0d-117">Режим исследования</span><span class="sxs-lookup"><span data-stu-id="faf0d-117">Research mode</span></span></td>
        <td><span data-ttu-id="faf0d-118">✔️</span><span class="sxs-lookup"><span data-stu-id="faf0d-118">✔️</span></span></td>
        <td><span data-ttu-id="faf0d-119">❌</span><span class="sxs-lookup"><span data-stu-id="faf0d-119">❌</span></span></td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="faf0d-120">Перед использованием режима исследования</span><span class="sxs-lookup"><span data-stu-id="faf0d-120">Before using Research mode</span></span>

<span data-ttu-id="faf0d-121">Режим исследования хорошо назван: он предназначен для академических и отраслевых исследователей, пытающихся получить новые идеи в полях Компьютерное зрение и Robotics.</span><span class="sxs-lookup"><span data-stu-id="faf0d-121">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="faf0d-122">Режим исследования не предназначен для приложений, которые будут развернуты на предприятии или доступны в Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="faf0d-122">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="faf0d-123">Это объясняется тем, что режим исследования снижает безопасность устройства и потребляет значительно больше энергии аккумулятора, чем нормальная работа.</span><span class="sxs-lookup"><span data-stu-id="faf0d-123">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="faf0d-124">Корпорация Майкрософт не фиксирует поддержку этого режима на всех будущих устройствах.</span><span class="sxs-lookup"><span data-stu-id="faf0d-124">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="faf0d-125">Поэтому рекомендуется использовать его для разработки и тестирования новых идей. Однако вы не сможете широко развертывать приложения, использующие режим исследования, или иметь возможность гарантировать, что она будет продолжать работать на будущем оборудовании.</span><span class="sxs-lookup"><span data-stu-id="faf0d-125">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="faf0d-126">Включение режима исследования</span><span class="sxs-lookup"><span data-stu-id="faf0d-126">Enabling Research mode</span></span>

<span data-ttu-id="faf0d-127">Режим исследования — это подраздел режима разработчика.</span><span class="sxs-lookup"><span data-stu-id="faf0d-127">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="faf0d-128">Сначала необходимо включить режим разработчика в приложении "Параметры" (**параметры > обновление & > безопасности для разработчиков**):</span><span class="sxs-lookup"><span data-stu-id="faf0d-128">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="faf0d-129">Установите для параметра "использовать функции разработчика" значение **вкл** .</span><span class="sxs-lookup"><span data-stu-id="faf0d-129">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="faf0d-130">Задайте для параметра "включить портал устройства" значение **вкл** .</span><span class="sxs-lookup"><span data-stu-id="faf0d-130">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="faf0d-131">Затем с помощью веб-браузера, подключенного к той же сети Wi-Fi, что и HoloLens, перейдите по IP-адресу HoloLens (с помощью **параметров > сеть & интернет > Wi-fi > свойства оборудования**).</span><span class="sxs-lookup"><span data-stu-id="faf0d-131">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="faf0d-132">Это [портал устройств](using-the-windows-device-portal.md), и в разделе "система" на портале вы увидите страницу "режим исследований":</span><span class="sxs-lookup"><span data-stu-id="faf0d-132">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="faf0d-133">![Вкладка "режим исследования" портала устройств HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="faf0d-133">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="faf0d-134">*Режим исследования на портале устройств HoloLens*</span><span class="sxs-lookup"><span data-stu-id="faf0d-134">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="faf0d-135">После выбора параметра **Разрешить доступ к потокам датчиков**необходимо перезагрузить HoloLens.</span><span class="sxs-lookup"><span data-stu-id="faf0d-135">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="faf0d-136">Это можно сделать на портале устройств в пункте меню "Power" в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="faf0d-136">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="faf0d-137">После перезагрузки устройства приложения, загруженные с помощью портала устройств, должны иметь доступ к потокам в режиме исследования.</span><span class="sxs-lookup"><span data-stu-id="faf0d-137">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="faf0d-138">Использование данных датчика в приложениях</span><span class="sxs-lookup"><span data-stu-id="faf0d-138">Using sensor data in your apps</span></span>

<span data-ttu-id="faf0d-139">Приложения могут получать доступ к данным потока датчиков, открывая [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) потоки точно так же, как они обращаются к видеокамере или видеофильму.</span><span class="sxs-lookup"><span data-stu-id="faf0d-139">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="faf0d-140">Все API-интерфейсы, работающие для разработки HoloLens, также доступны в режиме исследования.</span><span class="sxs-lookup"><span data-stu-id="faf0d-140">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="faf0d-141">В частности, приложение может точно понять, где HoloLens находится в 6DoF пространстве во время записи каждого кадра датчика.</span><span class="sxs-lookup"><span data-stu-id="faf0d-141">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="faf0d-142">Примеры приложений, демонстрирующие доступ к различным потокам в режиме исследования, использование встроенных функций и внешних компонентов, а также запись потоков в [репозитории GitHub хололенсфоркв](https://github.com/Microsoft/HoloLensForCV).</span><span class="sxs-lookup"><span data-stu-id="faf0d-142">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="faf0d-143">Известные проблемы</span><span class="sxs-lookup"><span data-stu-id="faf0d-143">Known issues</span></span>

<span data-ttu-id="faf0d-144">См. средство [записи проблем](https://github.com/Microsoft/HololensForCV/issues) в репозитории хололенсфоркв.</span><span class="sxs-lookup"><span data-stu-id="faf0d-144">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="faf0d-145">См. также</span><span class="sxs-lookup"><span data-stu-id="faf0d-145">See also</span></span>

* [<span data-ttu-id="faf0d-146">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="faf0d-146">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="faf0d-147">Репозиторий GitHub Хололенсфоркв</span><span class="sxs-lookup"><span data-stu-id="faf0d-147">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="faf0d-148">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="faf0d-148">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
