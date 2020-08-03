---
title: Режим исследования HoloLens
description: С помощью режима исследований в HoloLens приложение может получать доступ к потокам датчиков устройств (глубина, отслеживание среды и IR-рефлективити).
author: hferrone
ms.author: v-haferr
ms.date: 07/31/2020
ms.topic: article
keywords: Режим исследований, ОПС, RS4, компьютерное зрение, исследование, HoloLens, HoloLens 2
ms.openlocfilehash: dd49186d1218b6a6a6c9a8d5943159daad3bcefb
ms.sourcegitcommit: 36316e2658d3dfa804d798b9f4fb2f9186052144
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507698"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="81479-104">Режим исследования HoloLens</span><span class="sxs-lookup"><span data-stu-id="81479-104">HoloLens Research Mode</span></span>

<span data-ttu-id="81479-105">Режим исследования появился в первом поколение HoloLens, чтобы предоставить доступ к датчикам ключей на устройстве, специально для исследования приложений, которые не предназначены для развертывания.</span><span class="sxs-lookup"><span data-stu-id="81479-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="81479-106">Режим исследования для HoloLens 2 обеспечивает возможности HoloLens 1, добавляя доступ к дополнительным потокам:</span><span class="sxs-lookup"><span data-stu-id="81479-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="81479-107">**Видимые камеры с отслеживанием светлых окружений** — серые камеры, используемые системой для отслеживания и создания карт.</span><span class="sxs-lookup"><span data-stu-id="81479-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="81479-108">**Камера с глубиной** — работает в двух режимах:</span><span class="sxs-lookup"><span data-stu-id="81479-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="81479-109">АХАТ, высокая частота (45 кадров/с). используется для отслеживания.</span><span class="sxs-lookup"><span data-stu-id="81479-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="81479-110">По-разному в режиме короткого создания, АХАТ предоставляет псевдо-depth с этапом, превышающим 1 счетчик.</span><span class="sxs-lookup"><span data-stu-id="81479-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="81479-111">Длительное исключение (1-5 кадров/с низкой частотой), используемое для [пространственного сопоставления](spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="81479-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>

* <span data-ttu-id="81479-112">**Две версии потока IR-рефлективити** , используемые HoloLens для расчета глубины.</span><span class="sxs-lookup"><span data-stu-id="81479-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="81479-113">Эти изображения загораются инфракрасной связью и не зависят от внешнего видимого светового индикатора.</span><span class="sxs-lookup"><span data-stu-id="81479-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="81479-114">Если вы используете HoloLens 2, вы также получите доступ к дополнительным входным данным ниже:</span><span class="sxs-lookup"><span data-stu-id="81479-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="81479-115">**Акселерометр** — используется системой для определения линейного ускорения по осям X, Y и Z, а также сила притяжения.</span><span class="sxs-lookup"><span data-stu-id="81479-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="81479-116">**Гиро** — используется системой для определения поворотов.</span><span class="sxs-lookup"><span data-stu-id="81479-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="81479-117">**Магнитометр** — используется системой для оценки абсолютной ориентации.</span><span class="sxs-lookup"><span data-stu-id="81479-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="81479-118">Режим исследования в настоящее время находится в общедоступной предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="81479-118">Research Mode is currently in Public Preview.</span></span> <span data-ttu-id="81479-119">Примеры, учебники и полная документация по API для HoloLens 2 будут доступны по адресу [еккв 2020](https://eccv2020.eu/
 ) в репозитории Git в режиме исследований.</span><span class="sxs-lookup"><span data-stu-id="81479-119">HoloLens 2 samples, tutorials, and full API documentation will be available at [ECCV 2020](https://eccv2020.eu/
 ) in the Research Mode Git repository.</span></span>

<span data-ttu-id="81479-120">![Снимок экрана приложения в режиме исследования](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="81479-120">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="81479-121">*Запись в смешанной реальности тестового приложения, отображающего восемь потоков датчиков, доступных в режиме исследования.*</span><span class="sxs-lookup"><span data-stu-id="81479-121">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="81479-122">Использование</span><span class="sxs-lookup"><span data-stu-id="81479-122">Usage</span></span>

<span data-ttu-id="81479-123">Режим исследования предназначен для академических и промышленных исследователей, посвященных новым идеям в полях Компьютерное зрение и Robotics.</span><span class="sxs-lookup"><span data-stu-id="81479-123">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="81479-124">Он не предназначен для приложений, развернутых в корпоративных средах или доступных через Microsoft Store или другие каналы распространения.</span><span class="sxs-lookup"><span data-stu-id="81479-124">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="81479-125">Кроме того, корпорация Майкрософт не предоставляет гарантии, что режим исследования или эквивалентные функции будут поддерживаться в будущих обновлениях оборудования или ОС.</span><span class="sxs-lookup"><span data-stu-id="81479-125">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="81479-126">Однако это не должно помешать вам использовать его для разработки и тестирования новых идей!</span><span class="sxs-lookup"><span data-stu-id="81479-126">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="81479-127">Безопасность и производительность</span><span class="sxs-lookup"><span data-stu-id="81479-127">Security and performance</span></span>

<span data-ttu-id="81479-128">Имейте в виду, что включение режима исследования использует больше энергии аккумулятора, чем использование HoloLens 2 в нормальных условиях.</span><span class="sxs-lookup"><span data-stu-id="81479-128">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="81479-129">Это справедливо, даже если приложение, использующее функции режима исследования, не работает.</span><span class="sxs-lookup"><span data-stu-id="81479-129">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="81479-130">Включение этого режима может также снизить общую безопасность устройства, так как приложения могут использовать данные датчика неверно.</span><span class="sxs-lookup"><span data-stu-id="81479-130">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="81479-131">Дополнительные сведения о безопасности устройств можно найти в [разделе вопросы и ответы о безопасности HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="81479-131">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="81479-132">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="81479-132">Device support</span></span>
<table><span data-ttu-id="81479-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="81479-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="81479-134"><strong>Компонент</strong></span><span class="sxs-lookup"><span data-stu-id="81479-134"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="81479-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1-го поколения</strong></a></span><span class="sxs-lookup"><span data-stu-id="81479-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="81479-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="81479-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81479-137">Камеры для отслеживания головного подразделения</span><span class="sxs-lookup"><span data-stu-id="81479-137">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="81479-138">✔️</span><span class="sxs-lookup"><span data-stu-id="81479-138">✔️</span></span></td>
        <td><span data-ttu-id="81479-139">✔️</span><span class="sxs-lookup"><span data-stu-id="81479-139">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="81479-140">Глубина & ИК-камере</span><span class="sxs-lookup"><span data-stu-id="81479-140">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="81479-141">✔️</span><span class="sxs-lookup"><span data-stu-id="81479-141">✔️</span></span></td>
        <td><span data-ttu-id="81479-142">✔️</span><span class="sxs-lookup"><span data-stu-id="81479-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="81479-143">Акселерометр</span><span class="sxs-lookup"><span data-stu-id="81479-143">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="81479-144">✔️</span><span class="sxs-lookup"><span data-stu-id="81479-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="81479-145">Гироскоп</span><span class="sxs-lookup"><span data-stu-id="81479-145">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="81479-146">✔️</span><span class="sxs-lookup"><span data-stu-id="81479-146">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="81479-147">Магнитометр</span><span class="sxs-lookup"><span data-stu-id="81479-147">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="81479-148">✔️</span><span class="sxs-lookup"><span data-stu-id="81479-148">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="81479-149">Включение режима исследований (HoloLens 1 Gen и HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="81479-149">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="81479-150">Режим исследования — это расширение режима разработчика.</span><span class="sxs-lookup"><span data-stu-id="81479-150">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="81479-151">Перед началом работы необходимо включить функции разработчика устройства для доступа к параметрам режима исследования:</span><span class="sxs-lookup"><span data-stu-id="81479-151">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="81479-152">Откройте **меню "Пуск" > "Параметры** " и выберите " **обновления**".</span><span class="sxs-lookup"><span data-stu-id="81479-152">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="81479-153">Выберите **для разработчиков** и включите **режим разработчика**.</span><span class="sxs-lookup"><span data-stu-id="81479-153">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="81479-154">Прокрутите вниз и включите **Портал устройств**.</span><span class="sxs-lookup"><span data-stu-id="81479-154">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="81479-155">После включения функций [для разработчиков подключитесь к порталу устройств](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) , чтобы включить функции режима исследования:</span><span class="sxs-lookup"><span data-stu-id="81479-155">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="81479-156">Перейдите в **режим "система > исследований** " на **портале устройств**.</span><span class="sxs-lookup"><span data-stu-id="81479-156">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="81479-157">Выберите **Разрешить доступ к потоку датчика**.</span><span class="sxs-lookup"><span data-stu-id="81479-157">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="81479-158">Перезапустите устройство из пункта меню " **Электропитание** " в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="81479-158">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="81479-159">После перезагрузки устройства приложения, загруженные с помощью **портала устройств** , могут получить доступ к потокам в режиме исследования.</span><span class="sxs-lookup"><span data-stu-id="81479-159">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="81479-160">![Вкладка "режим исследования" портала устройств HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="81479-160">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="81479-161">*Окно режима исследований на портале устройств HoloLens*</span><span class="sxs-lookup"><span data-stu-id="81479-161">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="81479-162">Режим исследования для HoloLens 2 доступен начиная с сборки 19041,1356.</span><span class="sxs-lookup"><span data-stu-id="81479-162">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="81479-163">Если вам нужен доступ в более ранней сборке, зарегистрируйтесь для получения [предварительной версии программы предварительной оценки](https://docs.microsoft.com/hololens/hololens-insider) .</span><span class="sxs-lookup"><span data-stu-id="81479-163">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="81479-164">Использование данных датчика в приложениях</span><span class="sxs-lookup"><span data-stu-id="81479-164">Using sensor data in your apps</span></span>

<span data-ttu-id="81479-165">Приложения могут получать доступ к данным потока датчика точно так же, как к видеокамере и видеокамерам обращаются через [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="81479-165">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="81479-166">Все API-интерфейсы, работающие для разработки HoloLens, также доступны в режиме исследований.</span><span class="sxs-lookup"><span data-stu-id="81479-166">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="81479-167">В частности, приложение точно знает, где HoloLens находится в 6DoF пространстве во время записи каждого кадра датчика.</span><span class="sxs-lookup"><span data-stu-id="81479-167">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="81479-168">Примеры приложений можно найти в, как получить доступ к различным потокам в режиме исследования, как использовать [встроенные функции и внешние компоненты](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), а также как записывать потоки в репозитории [репозитория GitHub хололенсфоркв](https://github.com/Microsoft/HoloLensForCV) .</span><span class="sxs-lookup"><span data-stu-id="81479-168">You can find sample applications on how to access the various Research Mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="81479-169">В настоящее время образец Хололенсфоркв не работает в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="81479-169">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="support"></a><span data-ttu-id="81479-170">Поддержка</span><span class="sxs-lookup"><span data-stu-id="81479-170">Support</span></span>

<span data-ttu-id="81479-171">Используйте [средство записи проблем](https://github.com/Microsoft/HololensForCV/issues) в репозитории хололенсфоркв для публикации отзывов и контроля известных проблем.</span><span class="sxs-lookup"><span data-stu-id="81479-171">Please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="81479-172">См. также статью</span><span class="sxs-lookup"><span data-stu-id="81479-172">See also</span></span>

* [<span data-ttu-id="81479-173">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="81479-173">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="81479-174">Репозиторий GitHub Хололенсфоркв</span><span class="sxs-lookup"><span data-stu-id="81479-174">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="81479-175">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="81479-175">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
