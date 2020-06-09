---
title: Режим исследования HoloLens
description: С помощью режима исследований в HoloLens приложение может получать доступ к потокам датчиков устройств (глубина, отслеживание среды и IR-рефлективити).
author: hferrone
ms.author: v-haferr
ms.date: 05/03/2018
ms.topic: article
keywords: режим исследований, ОПС, RS4, компьютерное зрение, исследование, HoloLens, HoloLens 2
ms.openlocfilehash: ec6f7b73a1f25932f10c10a7f0daaf78e536c0c4
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533106"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="f255b-104">Режим исследования в HoloLens</span><span class="sxs-lookup"><span data-stu-id="f255b-104">HoloLens Research mode</span></span>

## <a name="overview"></a><span data-ttu-id="f255b-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="f255b-105">Overview</span></span>

<span data-ttu-id="f255b-106">Режим исследования появился в первом поколение HoloLens, чтобы предоставить доступ к датчикам ключей на устройстве, специально для исследования приложений, которые не предназначены для развертывания.</span><span class="sxs-lookup"><span data-stu-id="f255b-106">Research mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="f255b-107">Теперь вы можете собирать данные из следующих входных данных:</span><span class="sxs-lookup"><span data-stu-id="f255b-107">You can now gather data from the following inputs:</span></span>

* <span data-ttu-id="f255b-108">**Видимые камеры для отслеживания окружения** — используются системой для отслеживания и создания карт.</span><span class="sxs-lookup"><span data-stu-id="f255b-108">**Visible Light Environment Tracking Cameras** - Used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="f255b-109">**Камера с глубиной** — работает в двух режимах:</span><span class="sxs-lookup"><span data-stu-id="f255b-109">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="f255b-110">Краткосрочное, с высокой частотой (30 кадров/с), которое используется для [отслеживания вручную](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="f255b-110">Short-throw, high-frequency (30 FPS) near-depth sensing used for [Hand Tracking](interaction-fundamentals.md)</span></span>
    + <span data-ttu-id="f255b-111">Длительное исключение (1-5 кадров/с низкой частотой), используемое для [пространственного сопоставления](spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="f255b-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>
* <span data-ttu-id="f255b-112">**Две версии потока IR-рефлективити** , используемые HoloLens для расчета глубины.</span><span class="sxs-lookup"><span data-stu-id="f255b-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="f255b-113">Эти изображения загораются инфракрасной связью и не зависят от внешнего видимого светового индикатора.</span><span class="sxs-lookup"><span data-stu-id="f255b-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="f255b-114">Если вы используете HoloLens 2, вы также сможете получить доступ к следующим входным данным:</span><span class="sxs-lookup"><span data-stu-id="f255b-114">If you're using a HoloLens 2 you will also be able to access the following inputs:</span></span>

* <span data-ttu-id="f255b-115">**Акселерометр** — используется системой для определения линейного ускорения по осям X, Y и Z, а также сила притяжения.</span><span class="sxs-lookup"><span data-stu-id="f255b-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="f255b-116">**Гиро** — используется системой для определения поворотов.</span><span class="sxs-lookup"><span data-stu-id="f255b-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="f255b-117">**Магнитометр** — используется системой для оценки абсолютной ориентации.</span><span class="sxs-lookup"><span data-stu-id="f255b-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

<span data-ttu-id="f255b-118">![Снимок экрана приложения в режиме исследования](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="f255b-118">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="f255b-119">*Запись в смешанной реальности тестового приложения, отображающего восемь потоков датчиков, доступных в режиме исследования.*</span><span class="sxs-lookup"><span data-stu-id="f255b-119">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

> [!NOTE]
> <span data-ttu-id="f255b-120">Функция режима исследования была добавлена как часть [обновления Windows 10 от апреля 2018](release-notes-april-2018.md) для HoloLens и недоступна в более ранних выпусках.</span><span class="sxs-lookup"><span data-stu-id="f255b-120">The Research Mode feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

## <a name="usage"></a><span data-ttu-id="f255b-121">Использование</span><span class="sxs-lookup"><span data-stu-id="f255b-121">Usage</span></span>

<span data-ttu-id="f255b-122">Режим исследования предназначен для академических и промышленных исследователей, посвященных новым идеям в полях Компьютерное зрение и Robotics.</span><span class="sxs-lookup"><span data-stu-id="f255b-122">Research mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="f255b-123">Он не предназначен для приложений, развернутых в корпоративных средах или доступных через Microsoft Store или другие каналы распространения.</span><span class="sxs-lookup"><span data-stu-id="f255b-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="f255b-124">Кроме того, корпорация Майкрософт не предоставляет гарантии, что режим исследования или эквивалентные функции будут поддерживаться в будущих обновлениях оборудования или ОС.</span><span class="sxs-lookup"><span data-stu-id="f255b-124">Additionally, Microsoft doesn't provide assurances that research mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="f255b-125">Однако это не должно помешать вам использовать его для разработки и тестирования новых идей!</span><span class="sxs-lookup"><span data-stu-id="f255b-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="f255b-126">Безопасность и производительность</span><span class="sxs-lookup"><span data-stu-id="f255b-126">Security and performance</span></span>

<span data-ttu-id="f255b-127">Имейте в виду, что включение режима исследования использует больше энергии аккумулятора, чем использование HoloLens 2 в нормальных условиях.</span><span class="sxs-lookup"><span data-stu-id="f255b-127">Be aware that enabling research mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="f255b-128">Это справедливо, даже если приложение, использующее функции режима исследования, не работает.</span><span class="sxs-lookup"><span data-stu-id="f255b-128">This is true even if the application using the research mode features is not running.</span></span>  <span data-ttu-id="f255b-129">Включение этого режима может также снизить общую безопасность устройства, так как приложения могут использовать данные датчика неверно.</span><span class="sxs-lookup"><span data-stu-id="f255b-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="f255b-130">Дополнительные сведения о безопасности устройств можно найти в [разделе вопросы и ответы о безопасности HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="f255b-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  


## <a name="device-support"></a><span data-ttu-id="f255b-131">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="f255b-131">Device support</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><span data-ttu-id="f255b-132"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="f255b-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f255b-133"><a href="hololens-hardware-details.md"><strong>Первое поколение HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f255b-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td><span data-ttu-id="f255b-134">Камеры для отслеживания головного подразделения</span><span class="sxs-lookup"><span data-stu-id="f255b-134">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="f255b-135">✔️</span><span class="sxs-lookup"><span data-stu-id="f255b-135">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="f255b-136">Глубина & ИК-камере</span><span class="sxs-lookup"><span data-stu-id="f255b-136">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="f255b-137">✔️</span><span class="sxs-lookup"><span data-stu-id="f255b-137">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="f255b-138">Акселерометр</span><span class="sxs-lookup"><span data-stu-id="f255b-138">Accelerometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="f255b-139">Гироскоп</span><span class="sxs-lookup"><span data-stu-id="f255b-139">Gyroscope</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="f255b-140">Магнитометр</span><span class="sxs-lookup"><span data-stu-id="f255b-140">Magnetometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="f255b-141">Поддержка режима исследования для HoloLens 2 должна быть доступна в общедоступной предварительной версии в июле 2020 и будет включать все перечисленные выше компоненты.</span><span class="sxs-lookup"><span data-stu-id="f255b-141">Research Mode support for HoloLens 2 is expected to be available in public preview in July 2020 and will include all the features listed above.</span></span> <span data-ttu-id="f255b-142">Дополнительные сведения см. в этой обратной записи.</span><span class="sxs-lookup"><span data-stu-id="f255b-142">Please check back for more information.</span></span> 

## <a name="enabling-research-mode"></a><span data-ttu-id="f255b-143">Включение режима исследования</span><span class="sxs-lookup"><span data-stu-id="f255b-143">Enabling Research mode</span></span>

<span data-ttu-id="f255b-144">Режим исследования — это расширение режима разработчика.</span><span class="sxs-lookup"><span data-stu-id="f255b-144">Research mode is an extension of Developer Mode.</span></span> <span data-ttu-id="f255b-145">Перед началом работы необходимо включить функции разработчика устройства для доступа к параметрам режима исследования:</span><span class="sxs-lookup"><span data-stu-id="f255b-145">Before starting, the developer features of the device need to be enabled to access the research mode settings:</span></span> 

* <span data-ttu-id="f255b-146">Откройте **меню "Пуск" > "Параметры** " и выберите " **обновления**".</span><span class="sxs-lookup"><span data-stu-id="f255b-146">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="f255b-147">Выберите **для разработчиков** и включите **режим разработчика**.</span><span class="sxs-lookup"><span data-stu-id="f255b-147">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="f255b-148">Прокрутите вниз и включите **портал устройств**.</span><span class="sxs-lookup"><span data-stu-id="f255b-148">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="f255b-149">После включения функций [для разработчиков подключитесь к порталу устройств](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) , чтобы включить функции режима исследования.</span><span class="sxs-lookup"><span data-stu-id="f255b-149">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the research mode features.</span></span>

<span data-ttu-id="f255b-150">В *HoloLens 1-го поколения*:</span><span class="sxs-lookup"><span data-stu-id="f255b-150">On *HoloLens 1st Gen*:</span></span>

* <span data-ttu-id="f255b-151">Перейдите в **режим "система > исследований** " на **портале устройств**.</span><span class="sxs-lookup"><span data-stu-id="f255b-151">Go to **System > Research mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="f255b-152">Выберите **Разрешить доступ к потоку датчика**.</span><span class="sxs-lookup"><span data-stu-id="f255b-152">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="f255b-153">Перезапустите устройство из пункта меню " **Электропитание** " в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="f255b-153">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="f255b-154">После перезагрузки устройства приложения, загруженные с помощью **портала устройств** , могут получить доступ к потокам в режиме исследования.</span><span class="sxs-lookup"><span data-stu-id="f255b-154">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research mode streams.</span></span>

<span data-ttu-id="f255b-155">![Вкладка "режим исследования" портала устройств HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="f255b-155">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="f255b-156">*Окно режима исследований на портале устройств HoloLens*</span><span class="sxs-lookup"><span data-stu-id="f255b-156">*Research mode window in the HoloLens Device Portal*</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="f255b-157">Использование данных датчика в приложениях</span><span class="sxs-lookup"><span data-stu-id="f255b-157">Using sensor data in your apps</span></span>

<span data-ttu-id="f255b-158">*Первое поколение HoloLens*</span><span class="sxs-lookup"><span data-stu-id="f255b-158">*HoloLens 1st Gen*</span></span>

<span data-ttu-id="f255b-159">Приложения могут получать доступ к данным потока датчика точно так же, как к видеокамере и видеокамерам обращаются через [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="f255b-159">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="f255b-160">Все API-интерфейсы, работающие для разработки HoloLens, также доступны в режиме исследований.</span><span class="sxs-lookup"><span data-stu-id="f255b-160">All APIs that work for HoloLens development are also available in Research mode.</span></span> <span data-ttu-id="f255b-161">В частности, приложение точно знает, где HoloLens находится в 6DoF пространстве во время записи каждого кадра датчика.</span><span class="sxs-lookup"><span data-stu-id="f255b-161">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="f255b-162">Примеры приложений можно найти в, как получить доступ к различным потокам в режиме исследования, как использовать [встроенные функции и внешние компоненты](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), а также как записывать потоки в репозитории [репозитория GitHub хололенсфоркв](https://github.com/Microsoft/HoloLensForCV) .</span><span class="sxs-lookup"><span data-stu-id="f255b-162">You can find sample applications on how to access the various Research mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="f255b-163">В настоящее время образец Хололенсфоркв не работает в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f255b-163">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="known-issues"></a><span data-ttu-id="f255b-164">Известные проблемы</span><span class="sxs-lookup"><span data-stu-id="f255b-164">Known issues</span></span>

<span data-ttu-id="f255b-165">Вы можете использовать [средство отслеживания проблем](https://github.com/Microsoft/HololensForCV/issues) в репозитории хололенсфоркв, чтобы отслеживать известные проблемы.</span><span class="sxs-lookup"><span data-stu-id="f255b-165">You can use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to follow known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="f255b-166">См. также</span><span class="sxs-lookup"><span data-stu-id="f255b-166">See also</span></span>

* [<span data-ttu-id="f255b-167">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="f255b-167">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="f255b-168">Репозиторий GitHub Хололенсфоркв</span><span class="sxs-lookup"><span data-stu-id="f255b-168">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="f255b-169">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="f255b-169">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
