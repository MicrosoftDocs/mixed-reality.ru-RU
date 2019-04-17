---
title: Режим HoloLens Research
description: С помощью режима исследования на HoloLens, приложения могут обращаться к потока датчиков ключа устройства (глубина, отслеживание среды и отражательную IR).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: режим исследований, cv, rs4, компьютерного зрения, исследований, HoloLens
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597509"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="d8b56-104">Режим HoloLens Research</span><span class="sxs-lookup"><span data-stu-id="d8b56-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="d8b56-105">Эта функция была добавлена как часть [обновления Windows 10 апреля 2018 года](release-notes-april-2018.md) для HoloLens и не поддерживается в более ранних выпусках.</span><span class="sxs-lookup"><span data-stu-id="d8b56-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="d8b56-106">Режим Research является новой возможностью HoloLens, предоставляющий доступ приложения к датчикам, ключа на устройстве.</span><span class="sxs-lookup"><span data-stu-id="d8b56-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="d8b56-107">К ним можно отнести следующие.</span><span class="sxs-lookup"><span data-stu-id="d8b56-107">These include:</span></span>
- <span data-ttu-id="d8b56-108">Четыре среды отслеживания камеры, используемые системой для построения карты и головной отслеживания.</span><span class="sxs-lookup"><span data-stu-id="d8b56-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="d8b56-109">Две версии камеры глубины — один высокой частотой (30 кадров/с) рядом с глубиной датчика, обычно используется в стороны отслеживания, а другой частотой нижний (1 кадр/с) дальней глубины датчика, используется для сопоставления пространственных</span><span class="sxs-lookup"><span data-stu-id="d8b56-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="d8b56-110">Две версии в поток среды выполнения Интеграции отражательную, HoloLens, используемый для вычислений глубины, но ценность сама по себе, как эти образы являются оформленный из HoloLens и достаточно влияет на внешнее освещение.</span><span class="sxs-lookup"><span data-stu-id="d8b56-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="d8b56-111">![Снимок экрана приложения режим справочные материалы](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="d8b56-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="d8b56-112">*Запись смешанной реальности тестовое приложение, которое отображает потока восьми датчиков, доступные в режиме справочные материалы*</span><span class="sxs-lookup"><span data-stu-id="d8b56-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="d8b56-113">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="d8b56-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d8b56-114">Компонент</span><span class="sxs-lookup"><span data-stu-id="d8b56-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="d8b56-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d8b56-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d8b56-116"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d8b56-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d8b56-117">Режим справочные материалы</span><span class="sxs-lookup"><span data-stu-id="d8b56-117">Research mode</span></span></td><td style="text-align: center;"> <span data-ttu-id="d8b56-118">✔️</span><span class="sxs-lookup"><span data-stu-id="d8b56-118">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="d8b56-119">Прежде чем использовать режим справочные материалы</span><span class="sxs-lookup"><span data-stu-id="d8b56-119">Before using Research mode</span></span>

<span data-ttu-id="d8b56-120">Справочные материалы режим также называется: она предназначена для учебных заведений и промышленных исследователей, поработав с новыми идеями в полях компьютерного зрения и Robotics.</span><span class="sxs-lookup"><span data-stu-id="d8b56-120">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="d8b56-121">Режим Research не предназначен для приложений, которые будут развернуты на предприятии или становятся доступными в Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="d8b56-121">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="d8b56-122">Причина этого — что Research режим снижает безопасность устройства и использует значительно больше мощности батарей нормальной работы.</span><span class="sxs-lookup"><span data-stu-id="d8b56-122">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="d8b56-123">Microsoft не фиксируется для поддержки этого режима для любых последующих устройств.</span><span class="sxs-lookup"><span data-stu-id="d8b56-123">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="d8b56-124">Таким образом мы рекомендуем использовать его для разработки и тестирования новых идей; Тем не менее вы не сможете широко развертывание приложений, используйте режим Research или любой гарантию того, что она будет продолжать работать на будущих оборудовании.</span><span class="sxs-lookup"><span data-stu-id="d8b56-124">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="d8b56-125">Включение режима справочные материалы</span><span class="sxs-lookup"><span data-stu-id="d8b56-125">Enabling Research mode</span></span>

<span data-ttu-id="d8b56-126">Режим Research — вложенный режим режим разработчика.</span><span class="sxs-lookup"><span data-stu-id="d8b56-126">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="d8b56-127">Сначала необходимо включить режим разработчика в настройках приложения (**параметры > обновление и безопасность > для разработчиков**):</span><span class="sxs-lookup"><span data-stu-id="d8b56-127">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="d8b56-128">Значение «Использовать возможности для разработчиков» **на**</span><span class="sxs-lookup"><span data-stu-id="d8b56-128">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="d8b56-129">Значение «Включить портал устройств» **на**</span><span class="sxs-lookup"><span data-stu-id="d8b56-129">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="d8b56-130">Затем с помощью веб-браузер, подключенный к той же сети Wi-Fi, что ваш HoloLens, перейдите к IP-адрес вашего HoloLens (полученные с помощью **параметры > сеть и Интернет > Wi-Fi > Свойства оборудования**).</span><span class="sxs-lookup"><span data-stu-id="d8b56-130">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="d8b56-131">Это [портал устройств](using-the-windows-device-portal.md), и вы увидите страницу «Research режим» в разделе «Система» портала:</span><span class="sxs-lookup"><span data-stu-id="d8b56-131">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="d8b56-132">![Вкладка режим Research портала устройство HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="d8b56-132">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="d8b56-133">*Режим исследований на портале устройство HoloLens*</span><span class="sxs-lookup"><span data-stu-id="d8b56-133">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="d8b56-134">После выбора **разрешить доступ к потокам датчика**, вам придется перезагрузить HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d8b56-134">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="d8b56-135">Это можно сделать на портале устройства, пункт меню «Power» в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="d8b56-135">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="d8b56-136">После перезагрузки устройства, приложения, которые были загружены через портал устройств должно быть возможность доступа к Research режим потоков.</span><span class="sxs-lookup"><span data-stu-id="d8b56-136">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="d8b56-137">Использовать данные датчиков в приложениях</span><span class="sxs-lookup"><span data-stu-id="d8b56-137">Using sensor data in your apps</span></span>

<span data-ttu-id="d8b56-138">Приложения могут обращаться к потока данных датчиков, открыв [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) потоков в точно так же, они доступа к потоку камеры фото и видео.</span><span class="sxs-lookup"><span data-stu-id="d8b56-138">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="d8b56-139">Все API-интерфейсы, которые работают для разработки HoloLens, также доступны в режиме исследований.</span><span class="sxs-lookup"><span data-stu-id="d8b56-139">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="d8b56-140">В частности приложение можно знать точно HoloLens которого в пространстве 6DoF во время записи кадров каждого датчика.</span><span class="sxs-lookup"><span data-stu-id="d8b56-140">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="d8b56-141">Примеры приложений, показывающий, как получить доступ к различные потоки режим Research, как использовать встроенные функции и extrinsics и записи потоков доступны в [репозиторий HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV).</span><span class="sxs-lookup"><span data-stu-id="d8b56-141">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="d8b56-142">Известные проблемы</span><span class="sxs-lookup"><span data-stu-id="d8b56-142">Known issues</span></span>

<span data-ttu-id="d8b56-143">См. в разделе [программа issue tracker](https://github.com/Microsoft/HololensForCV/issues) HoloLensForCV репозитория.</span><span class="sxs-lookup"><span data-stu-id="d8b56-143">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8b56-144">См. также</span><span class="sxs-lookup"><span data-stu-id="d8b56-144">See also</span></span>

* [<span data-ttu-id="d8b56-145">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="d8b56-145">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="d8b56-146">Репозиторий HoloLensForCV GitHub</span><span class="sxs-lookup"><span data-stu-id="d8b56-146">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="d8b56-147">С помощью Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="d8b56-147">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
