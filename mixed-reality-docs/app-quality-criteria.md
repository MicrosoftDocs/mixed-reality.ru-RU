---
title: Критерии качества приложения
description: В этом документе описываются лучшие факторы, влияющие на качество приложений смешанной реальности.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: критерии качества приложения, Смешанная реальность, приложение смешанной реальности
ms.openlocfilehash: d167e141b536f9247d22e40afefa718ecc399f5a
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926591"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="4b416-104">Критерии качества приложения</span><span class="sxs-lookup"><span data-stu-id="4b416-104">App quality criteria</span></span>

<span data-ttu-id="4b416-105">В этом документе описываются лучшие факторы, влияющие на качество приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="4b416-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="4b416-106">Для каждого фактора предоставляются следующие сведения.</span><span class="sxs-lookup"><span data-stu-id="4b416-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="4b416-107">Обзор — краткое описание фактора качества и его важность.</span><span class="sxs-lookup"><span data-stu-id="4b416-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="4b416-108">Влияние на устройства: тип устройства Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4b416-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="4b416-109">Критерии качества — оценка коэффициента качества.</span><span class="sxs-lookup"><span data-stu-id="4b416-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="4b416-110">Способ измерения — методы для измерения (или взаимодействия) проблемы.</span><span class="sxs-lookup"><span data-stu-id="4b416-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="4b416-111">Рекомендации — общие сведения о подходах, обеспечивающих лучшую работу пользователей.</span><span class="sxs-lookup"><span data-stu-id="4b416-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="4b416-112">Ресурсы — соответствующие ресурсы для разработчиков и проектирования, которые полезны для создания лучших возможностей приложений.</span><span class="sxs-lookup"><span data-stu-id="4b416-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="4b416-113">Частота кадров</span><span class="sxs-lookup"><span data-stu-id="4b416-113">Frame rate</span></span>

<span data-ttu-id="4b416-114">Частота кадров — первый основополагающий уровень стабильности и комфорт пользователя.</span><span class="sxs-lookup"><span data-stu-id="4b416-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="4b416-115">Частота кадров ниже рекомендуемых целевых объектов может привести к неблагоприятному снижению голограмм, негативно сказывается на белиевабилити опыта и потенциально выносливости глаз.</span><span class="sxs-lookup"><span data-stu-id="4b416-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="4b416-116">В зависимости от того, какие компьютеры, совместимые с Windows Mixed Reality, вы хотите поддерживать, частота целевого кадра на впечатляющих наушниках Windows Mixed Reality будет либо 60 Гц, либо 90Hz.</span><span class="sxs-lookup"><span data-stu-id="4b416-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="4b416-117">Для HoloLens частота целевого кадра составляет 60 Гц.</span><span class="sxs-lookup"><span data-stu-id="4b416-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-118">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-120"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-121">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-121">✔️</span></span></td>
        <td><span data-ttu-id="4b416-122">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-123">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-123">Quality criteria</span></span>

|  <span data-ttu-id="4b416-124">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-124">Best</span></span>  |  <span data-ttu-id="4b416-125">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-125">Meets</span></span> |  <span data-ttu-id="4b416-126">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="4b416-127">Приложение согласованно соответствует цели кадров в секунду (/сек) для целевого устройства: 60fps в HoloLens; 90fps на Ultra PCs; и 60fps на самых распространенных ПК.</span><span class="sxs-lookup"><span data-stu-id="4b416-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="4b416-128">Приложение имеет периодические падения кадров, не мешая основным интерфейсам. или кадр/сек постоянно меньше требуемой цели, но не помешать работе приложения.</span><span class="sxs-lookup"><span data-stu-id="4b416-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="4b416-129">В этом приложении частота кадров в среднем составляет каждые десять секунд или меньше.</span><span class="sxs-lookup"><span data-stu-id="4b416-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4b416-130">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-130">How to measure</span></span>

* <span data-ttu-id="4b416-131">Диаграмма частоты кадров в реальном времени предоставляется на [портале устройств Windows](using-the-windows-device-portal.md#system-performance) в разделе "производительность системы".</span><span class="sxs-lookup"><span data-stu-id="4b416-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="4b416-132">Для отладки разработки добавьте в приложение счетчик диагностики частоты кадров.</span><span class="sxs-lookup"><span data-stu-id="4b416-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="4b416-133">Пример счетчика см. в разделе ресурсы.</span><span class="sxs-lookup"><span data-stu-id="4b416-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="4b416-134">При этом на устройстве могут возникать частоты кадров, пока приложение работает, перемещая головную часть в сторону.</span><span class="sxs-lookup"><span data-stu-id="4b416-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="4b416-135">Если в голограмме отображается непредвиденное движение с нарушением колебаний, то, скорее всего, причиной является низкая частота кадров или уровень стабильности.</span><span class="sxs-lookup"><span data-stu-id="4b416-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-136">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-136">Recommendations</span></span>

* <span data-ttu-id="4b416-137">Добавьте счетчик частоты кадров в начале работы по разработке.</span><span class="sxs-lookup"><span data-stu-id="4b416-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="4b416-138">Изменения, которые требуют сброса в частоте кадров, должны оцениваться и надлежащим образом разрешаться как ошибки производительности.</span><span class="sxs-lookup"><span data-stu-id="4b416-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-139">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4b416-140">Документы</span><span class="sxs-lookup"><span data-stu-id="4b416-140">Documentation</span></span>

* [<span data-ttu-id="4b416-141">Основные сведения о производительности смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="4b416-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="4b416-142">Голограмма, стабильность и частота кадров</span><span class="sxs-lookup"><span data-stu-id="4b416-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="4b416-143">Бюджет производительности активов</span><span class="sxs-lookup"><span data-stu-id="4b416-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="4b416-144">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4b416-145">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="4b416-145">Tools and tutorials</span></span>

* [<span data-ttu-id="4b416-146">Мртулкит, отображение счетчика кадров/с</span><span class="sxs-lookup"><span data-stu-id="4b416-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="4b416-147">Мртулкит, шейдеры</span><span class="sxs-lookup"><span data-stu-id="4b416-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="4b416-148">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="4b416-148">External references</span></span>

* [<span data-ttu-id="4b416-149">Unity, оптимизация мобильных приложений</span><span class="sxs-lookup"><span data-stu-id="4b416-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="4b416-150">Голограмма, стабильность</span><span class="sxs-lookup"><span data-stu-id="4b416-150">Hologram stability</span></span>

<span data-ttu-id="4b416-151">Стабильные голограммы повышают удобство использования и белиевабилити приложения и создают более удобное для пользователя удобство просмотра.</span><span class="sxs-lookup"><span data-stu-id="4b416-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="4b416-152">Качество стабильной работы является результатом хорошей разработки приложений и способности устройства понять (отслеживанию) его среды.</span><span class="sxs-lookup"><span data-stu-id="4b416-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="4b416-153">Хотя Частота кадров — первый основополагающий уровень стабильности, другие факторы могут повлиять на стабильность, включая:</span><span class="sxs-lookup"><span data-stu-id="4b416-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="4b416-154">Использование плоскости стабилизации</span><span class="sxs-lookup"><span data-stu-id="4b416-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="4b416-155">Расстояние до пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="4b416-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="4b416-156">Отслеживающ</span><span class="sxs-lookup"><span data-stu-id="4b416-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-157">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-159"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-160">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-161">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-161">Quality criteria</span></span>

|  <span data-ttu-id="4b416-162">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-162">Best</span></span>  |  <span data-ttu-id="4b416-163">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-163">Meets</span></span> |  <span data-ttu-id="4b416-164">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4b416-165">Голограммы согласованно выглядят стабильно.</span><span class="sxs-lookup"><span data-stu-id="4b416-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="4b416-166">Во вторичном содержимом возникает непредвиденное перемещение; или непредвиденное перемещение не помешать общей работе приложения.</span><span class="sxs-lookup"><span data-stu-id="4b416-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="4b416-167">Основное содержимое в кадре приводит к непредвиденному перемещению.</span><span class="sxs-lookup"><span data-stu-id="4b416-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4b416-168">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-168">How to measure</span></span>

<span data-ttu-id="4b416-169">Людьми устройство и просматривая его работу:</span><span class="sxs-lookup"><span data-stu-id="4b416-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="4b416-170">Переместите заголовок с боковой стороны на сторону. Если на голограммах отображается непредвиденное перемещение, то вероятная причина может быть вызвана низкой частотой кадров или неправильным выравниванием области стабильности с фокусом плоскости.</span><span class="sxs-lookup"><span data-stu-id="4b416-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="4b416-171">Перемещайтесь по голограммам и окружениям, ищите такие варианты поведения, как дорожки и «переход».</span><span class="sxs-lookup"><span data-stu-id="4b416-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="4b416-172">Этот тип движения, скорее всего, вызван тем, что устройство не отслеживает среду или расстояние до пространственной привязки.</span><span class="sxs-lookup"><span data-stu-id="4b416-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="4b416-173">Если в кадре находятся большие или несколько голограмм, обратите внимание на поведение голограммы с различной глубиной при перемещении головной позиции с стороны в сторону, если шакинесс, вероятно, это вызвано плоскостью стабилизации.</span><span class="sxs-lookup"><span data-stu-id="4b416-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-174">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-174">Recommendations</span></span>

* <span data-ttu-id="4b416-175">Добавьте счетчик частоты кадров в начале работы по разработке.</span><span class="sxs-lookup"><span data-stu-id="4b416-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="4b416-176">Используйте плоскость стабилизации.</span><span class="sxs-lookup"><span data-stu-id="4b416-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="4b416-177">Всегда Визуализируйте закрепленные голограммы в пределах 3 метров их привязки.</span><span class="sxs-lookup"><span data-stu-id="4b416-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="4b416-178">Убедитесь, что в вашей среде настроено правильное отслеживание.</span><span class="sxs-lookup"><span data-stu-id="4b416-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="4b416-179">Создайте свой опыт, чтобы избежать голограмм с различными уровнями фокусной глубины внутри рамки.</span><span class="sxs-lookup"><span data-stu-id="4b416-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-180">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4b416-181">Документы</span><span class="sxs-lookup"><span data-stu-id="4b416-181">Documentation</span></span>

* [<span data-ttu-id="4b416-182">Голограмма, стабильность и частота кадров</span><span class="sxs-lookup"><span data-stu-id="4b416-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="4b416-183">Пример использования с плоскостью стабилизации</span><span class="sxs-lookup"><span data-stu-id="4b416-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="4b416-184">Основные сведения о производительности смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="4b416-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="4b416-185">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="4b416-186">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="4b416-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="4b416-187">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="4b416-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="4b416-188">Стационарная рамка ссылки</span><span class="sxs-lookup"><span data-stu-id="4b416-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4b416-189">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="4b416-189">Tools and tutorials</span></span>

* [<span data-ttu-id="4b416-190">Пакет, сопровождающий MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="4b416-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="4b416-191">Расположение голограмм на реальных поверхностях</span><span class="sxs-lookup"><span data-stu-id="4b416-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="4b416-192">Неверное выравнивание голограмм с физическими объектами (если предполагается, что они помещаются в связи друг с другом) является четкой признаком того, что не является объединением голограмм и реального мира.</span><span class="sxs-lookup"><span data-stu-id="4b416-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="4b416-193">Точность размещения должна относиться к потребностям сценария. Например, при размещении в общей области можно использовать пространственное соответствие, но более точное размещение потребует использования маркеров и калибровки.</span><span class="sxs-lookup"><span data-stu-id="4b416-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-194">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-196"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-196"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-197">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-198">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-198">Quality criteria</span></span>

|  <span data-ttu-id="4b416-199">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-199">Best</span></span>  |  <span data-ttu-id="4b416-200">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-200">Meets</span></span> |  <span data-ttu-id="4b416-201">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="4b416-202">Голограммы выводятся на поверхность, как правило, в диапазоне от сантиметров до сантиметров.</span><span class="sxs-lookup"><span data-stu-id="4b416-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="4b416-203">Если требуется более высокая точность, приложение должно предоставить эффективные средства для совместной работы в пределах требуемой спецификации приложения.</span><span class="sxs-lookup"><span data-stu-id="4b416-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="4b416-204">Н/Д</span><span class="sxs-lookup"><span data-stu-id="4b416-204">NA</span></span> | <span data-ttu-id="4b416-205">Голограммы выводятся без согласования с физическим целевым объектом путем его разрыва или появления в плавающей области.</span><span class="sxs-lookup"><span data-stu-id="4b416-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="4b416-206">Если требуется точность, голограммы должны соответствовать спецификации близости в сценарии.</span><span class="sxs-lookup"><span data-stu-id="4b416-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4b416-207">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-207">How to measure</span></span>

* <span data-ttu-id="4b416-208">Голограммы, размещенные на пространственной карте, не должны иметь заметного числа с плавающей запятой выше или ниже поверхности.</span><span class="sxs-lookup"><span data-stu-id="4b416-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="4b416-209">Голограммы, для которых требуется точное размещение, должны иметь некоторую форму системы маркеров и калибровки, точную для требования сценария.</span><span class="sxs-lookup"><span data-stu-id="4b416-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-210">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-210">Recommendations</span></span>

* <span data-ttu-id="4b416-211">Пространственное соответствие удобно использовать для размещения объектов на поверхностях, когда точность не требуется.</span><span class="sxs-lookup"><span data-stu-id="4b416-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="4b416-212">Для наилучшей точности используйте маркеры или афиши, чтобы задать голограммы и контроллер Xbox (или какой-либо механизм выравнивания вручную) для окончательной калибровки.</span><span class="sxs-lookup"><span data-stu-id="4b416-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="4b416-213">Рассмотрите возможность разбиения очень больших голограмм на логические части и согласования каждой части с поверхностью.</span><span class="sxs-lookup"><span data-stu-id="4b416-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="4b416-214">Неправильное задание расстояния интерпупиллари (IPD) также может влиять на выравнивание голограмм.</span><span class="sxs-lookup"><span data-stu-id="4b416-214">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="4b416-215">Всегда настраивайте HoloLens для пользователя IPD.</span><span class="sxs-lookup"><span data-stu-id="4b416-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-216">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4b416-217">Документы</span><span class="sxs-lookup"><span data-stu-id="4b416-217">Documentation</span></span>

* [<span data-ttu-id="4b416-218">Размещение пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="4b416-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="4b416-219">Процесс сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="4b416-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="4b416-220">Рекомендации по пространственной привязке</span><span class="sxs-lookup"><span data-stu-id="4b416-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="4b416-221">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="4b416-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="4b416-222">Пространственное сопоставление в Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="4b416-223">Общие сведения о разработке вуфориа</span><span class="sxs-lookup"><span data-stu-id="4b416-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4b416-224">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="4b416-224">Tools and tutorials</span></span>

* [<span data-ttu-id="4b416-225">Индекс MR 230: пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="4b416-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="4b416-226">MR Toolkit, библиотеки пространственных сопоставлений</span><span class="sxs-lookup"><span data-stu-id="4b416-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="4b416-227">Комплект поставки пакета MR, пример калибровки афиши</span><span class="sxs-lookup"><span data-stu-id="4b416-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="4b416-228">Пакет, сопровождающий MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="4b416-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="4b416-229">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="4b416-229">External references</span></span>

* [<span data-ttu-id="4b416-230">Ловес пример, выравнивание точности</span><span class="sxs-lookup"><span data-stu-id="4b416-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="4b416-231">Просмотр зоны отдыха</span><span class="sxs-lookup"><span data-stu-id="4b416-231">Viewing zone of comfort</span></span>

<span data-ttu-id="4b416-232">Разработчики приложений контролируют, где соходят глаза пользователей, размещая содержимое и голограммы с различной глубиной.</span><span class="sxs-lookup"><span data-stu-id="4b416-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="4b416-233">Пользователи людьми HoloLens всегда будут работать с 2.0 m, чтобы обеспечить четкий образ, так как отображение HoloLens фиксировано на оптическом расстоянии примерно 2,0 млн от пользователя.</span><span class="sxs-lookup"><span data-stu-id="4b416-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="4b416-234">Неправильная глубина содержимого может привести к появлению Visual дискомфорт или выносливости.</span><span class="sxs-lookup"><span data-stu-id="4b416-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-235">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-237"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-237"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-238">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-239">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="4b416-240">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="4b416-241">Разместите содержимое в 2 MБ.</span><span class="sxs-lookup"><span data-stu-id="4b416-241">Place content at 2m.</span></span></li><li><span data-ttu-id="4b416-242">Если не удается поместить голограммы в 2 МБ, а конфликты между конвергенцией и проживанием не могут быть устранены, оптимальная зона для размещения с голограммами находится между 1,25 м и 5 мин.</span><span class="sxs-lookup"><span data-stu-id="4b416-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="4b416-243">В каждом случае разработчики должны структурировать содержимое, чтобы рекомендовать пользователям взаимодействовать с 1 + m (например, настроить размер содержимого и параметры размещения по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="4b416-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="4b416-244">Если не требуется специально для сценария, следует реализовать плоскость отсечения с эффектом затухания, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="4b416-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="4b416-245">В случаях, когда требуется более близкое наблюдение за голограммой мотионлесс, содержимое не должно быть ближе к 50cm.</span><span class="sxs-lookup"><span data-stu-id="4b416-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="4b416-246">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-246">Meets</span></span></td><td> <span data-ttu-id="4b416-247">Содержимое находится в рамках руководства по просмотру и перемещению, но неверно использует или не использует плоскость обрезки.</span><span class="sxs-lookup"><span data-stu-id="4b416-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="4b416-248">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-248">Fail</span></span> </td><td> <span data-ttu-id="4b416-249">Содержимое представлено слишком близко (обычно &lt;1,25 m или &lt;50cm для стационарных голограмм, для которых необходимо более внимательное наблюдение).</span><span class="sxs-lookup"><span data-stu-id="4b416-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="4b416-250">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-250">How to measure</span></span>

* <span data-ttu-id="4b416-251">Как правило, содержимое должно находиться на расстоянии до 2 МБ, но не ближе к 1,25 или более чем 5 мин.</span><span class="sxs-lookup"><span data-stu-id="4b416-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="4b416-252">За некоторыми исключениями расстояние отсечения HoloLens должно быть равно. 85CM с появлением содержимого, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="4b416-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="4b416-253">Допишитесь на содержимое и обратите внимание на эффекты обтравочной плоскости.</span><span class="sxs-lookup"><span data-stu-id="4b416-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="4b416-254">Стационарное содержимое не должно быть ближе к 50cm.</span><span class="sxs-lookup"><span data-stu-id="4b416-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-255">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-255">Recommendations</span></span>

* <span data-ttu-id="4b416-256">Создайте содержимое для оптимального расстояния до 2 МБ.</span><span class="sxs-lookup"><span data-stu-id="4b416-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="4b416-257">Установите значение расстояния отрисовки обрезки равным 85cm с появлением содержимого, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="4b416-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="4b416-258">Для стационарных голограмм, для которых требуется более близкое к просмотру, плоскость обрезки не должна быть ближе к 30cm, а эффект затухания должен начинаться по крайней мере 10cm от плоскости обрезки.</span><span class="sxs-lookup"><span data-stu-id="4b416-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-259">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-259">Resources</span></span>

* [<span data-ttu-id="4b416-260">Расстояние визуализации</span><span class="sxs-lookup"><span data-stu-id="4b416-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="4b416-261">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="4b416-262">Эксперименты с масштабом</span><span class="sxs-lookup"><span data-stu-id="4b416-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="4b416-263">Текст, рекомендуемый размер шрифта</span><span class="sxs-lookup"><span data-stu-id="4b416-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="4b416-264">Переключение глубины</span><span class="sxs-lookup"><span data-stu-id="4b416-264">Depth switching</span></span>

<span data-ttu-id="4b416-265">Независимо от способа просмотра зоны проблем, требования пользователя к частому или быстрому переключению между ближайшими и далекими объектами (включая голограммы и реальное содержимое) могут привести к окуломотор выносливости и общему дискомфорт.</span><span class="sxs-lookup"><span data-stu-id="4b416-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-266">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-268"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-268"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-269">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-269">✔️</span></span></td>
        <td><span data-ttu-id="4b416-270">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-271">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-271">Quality criteria</span></span>

|  <span data-ttu-id="4b416-272">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-272">Best</span></span>  |  <span data-ttu-id="4b416-273">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-273">Meets</span></span> |  <span data-ttu-id="4b416-274">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4b416-275">Ограниченное или естественное изменение глубины, которое не приводит к неестественному переключению пользователя.</span><span class="sxs-lookup"><span data-stu-id="4b416-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="4b416-276">Параметр с внезапной глубиной является базовым и разрабатывается в процессе работы приложения или с внезапной глубиной, вызванной непредвиденным реальным содержимым.</span><span class="sxs-lookup"><span data-stu-id="4b416-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="4b416-277">Постоянный переключатель глубины или внезапное переключение глубины, которое не требуется или является ядром для работы приложения.</span><span class="sxs-lookup"><span data-stu-id="4b416-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4b416-278">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-278">How to measure</span></span>

* <span data-ttu-id="4b416-279">Если приложение требует, чтобы пользователь постоянно или резко изменил фокус глубины, существует проблема переключения глубины.</span><span class="sxs-lookup"><span data-stu-id="4b416-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-280">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-280">Recommendations</span></span>

* <span data-ttu-id="4b416-281">Сделайте основной контент на согласованной плоскости, убедитесь, что плоскость стабилизации соответствует фокальной плоскости.</span><span class="sxs-lookup"><span data-stu-id="4b416-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="4b416-282">Это позволит сократить окуломотор выносливости и неожиданное перемещение голограмм.</span><span class="sxs-lookup"><span data-stu-id="4b416-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-283">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-283">Resources</span></span>

* [<span data-ttu-id="4b416-284">Расстояние визуализации</span><span class="sxs-lookup"><span data-stu-id="4b416-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="4b416-285">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="4b416-286">Использование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="4b416-286">Use of spatial sound</span></span>

<span data-ttu-id="4b416-287">В Windows Mixed Reality подсистема аудио предоставляет компонент Аурал в режиме смешанной реальности, имитируя трехмерный звук с помощью направления, расстояния и моделирования окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="4b416-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="4b416-288">Использование пространственного звука в приложении позволяет разработчикам убедительно размещать звуки в трехмерном пространстве (Sphere) вокруг пользователя.</span><span class="sxs-lookup"><span data-stu-id="4b416-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="4b416-289">Эти звуки будут выглядеть так, как будто они поступают от реальных физических объектов или голограмм в смешанной реальности в окружающей среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="4b416-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="4b416-290">Пространственный звук — это мощный инструмент для погружения, специальных возможностей и разработки UX в приложениях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="4b416-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-291">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-293"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-293"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-294">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-294">✔️</span></span></td>
        <td><span data-ttu-id="4b416-295">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-296">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-296">Quality criteria</span></span>

|  <span data-ttu-id="4b416-297">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-297">Best</span></span>  |  <span data-ttu-id="4b416-298">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-298">Meets</span></span> |  <span data-ttu-id="4b416-299">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4b416-300">Звук логически пространственно, а UX соответствующим образом использует звук, чтобы помочь в обнаружении объектов и отзыве пользователей.</span><span class="sxs-lookup"><span data-stu-id="4b416-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="4b416-301">Звук является естественным и относится к объектам и нормализуется в рамках сценария.</span><span class="sxs-lookup"><span data-stu-id="4b416-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="4b416-302">Пространственный звук используется соответствующим образом для белиевабилити, но отсутствует как средство для получения отзывов пользователей и возможности обнаружения.</span><span class="sxs-lookup"><span data-stu-id="4b416-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="4b416-303">Звук не пространственно, как ожидалось, и (или) недостаток звука, чтобы помочь пользователю в его интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="4b416-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="4b416-304">Или пространственный звук не рассматривался или не используется в проектировании сценария.</span><span class="sxs-lookup"><span data-stu-id="4b416-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4b416-305">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-305">How to measure</span></span>

* <span data-ttu-id="4b416-306">Как правило, соответствующие звуки должны выдаваться из голограмм (например, лайного звука, поступающего от Holographic.)</span><span class="sxs-lookup"><span data-stu-id="4b416-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="4b416-307">Звуковые подсказки следует использовать по всему внешнему интерфейсу, чтобы помочь пользователю в отзыве или осведомлении о действиях, выходящих за рамки Holographic.</span><span class="sxs-lookup"><span data-stu-id="4b416-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-308">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-308">Recommendations</span></span>

* <span data-ttu-id="4b416-309">Используйте Пространственный звук для помощи с обнаружением объектов и пользовательскими интерфейсами.</span><span class="sxs-lookup"><span data-stu-id="4b416-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="4b416-310">Реальные звуки работают лучше, чем синтезированный или неестественный звук.</span><span class="sxs-lookup"><span data-stu-id="4b416-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="4b416-311">Большинство звуков должно быть пространственно.</span><span class="sxs-lookup"><span data-stu-id="4b416-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="4b416-312">Избегайте невидимых передатчиков.</span><span class="sxs-lookup"><span data-stu-id="4b416-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="4b416-313">Избегайте использования пространственных масок.</span><span class="sxs-lookup"><span data-stu-id="4b416-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="4b416-314">Нормализовать все звуки.</span><span class="sxs-lookup"><span data-stu-id="4b416-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-315">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4b416-316">Документы</span><span class="sxs-lookup"><span data-stu-id="4b416-316">Documentation</span></span>

* [<span data-ttu-id="4b416-317">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="4b416-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="4b416-318">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="4b416-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="4b416-319">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="4b416-320">Пример использования: Пространственный звук для Холотаур</span><span class="sxs-lookup"><span data-stu-id="4b416-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="4b416-321">Пример использования пространственного звука в Робораид</span><span class="sxs-lookup"><span data-stu-id="4b416-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4b416-322">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="4b416-322">Tools and tutorials</span></span>

* [<span data-ttu-id="4b416-323">MR 220: Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="4b416-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="4b416-324">Мртулкит, Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="4b416-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="4b416-325">Фокус на границах в holographic кадрах (фов)</span><span class="sxs-lookup"><span data-stu-id="4b416-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="4b416-326">Хорошо спроектированное взаимодействие с пользователем может создать и поддерживать полезный контекст виртуальной среды, который будет расширяться вокруг пользователей.</span><span class="sxs-lookup"><span data-stu-id="4b416-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="4b416-327">Устранение последствий границ фов заключается в продуманном проектировании масштабирования и контекста содержимого, использовании пространственных аудио, руководств и расположения пользователей.</span><span class="sxs-lookup"><span data-stu-id="4b416-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="4b416-328">Если вы сделали это правильно, то у пользователя будет меньше ограничений, чем границы фов, и удобство работы с приложением.</span><span class="sxs-lookup"><span data-stu-id="4b416-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-329">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-329">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-331"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-331"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-332">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-332">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-333">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-333">Quality criteria</span></span>

|  <span data-ttu-id="4b416-334">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-334">Best</span></span>  |  <span data-ttu-id="4b416-335">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-335">Meets</span></span> |  <span data-ttu-id="4b416-336">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4b416-337">Пользователь никогда не теряет контекст и не может его просматривать.</span><span class="sxs-lookup"><span data-stu-id="4b416-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="4b416-338">Для больших объектов предоставляется помощь по контексту.</span><span class="sxs-lookup"><span data-stu-id="4b416-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="4b416-339">Для объектов за пределами фрейма предоставляется возможность обнаружения и просмотра.</span><span class="sxs-lookup"><span data-stu-id="4b416-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="4b416-340">Как правило, проектирование движения и масштабирование голограмм подходят для удобства просмотра.</span><span class="sxs-lookup"><span data-stu-id="4b416-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="4b416-341">Пользователь никогда не теряет контекст, но в ограниченных ситуациях может потребоваться дополнительный перенос горловины.</span><span class="sxs-lookup"><span data-stu-id="4b416-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="4b416-342">В ограниченных ситуациях масштаб приводит к тому, что голограммы нарушают вертикальную или горизонтальную рамку, что вызывает некоторое движение горловины для просмотра голограмм.</span><span class="sxs-lookup"><span data-stu-id="4b416-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="4b416-343">Пользователь, вероятно, потеряет контекст и (или) одинаковое движение горловины необходимо для просмотра голограмм.</span><span class="sxs-lookup"><span data-stu-id="4b416-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="4b416-344">Нет руководства по контексту для больших holographic объектов, перемещение объектов, которые легко потерять за пределами рамки без рекомендаций по обнаружению или высоких голограмм, требует регулярного движения горловины для просмотра.</span><span class="sxs-lookup"><span data-stu-id="4b416-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4b416-345">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-345">How to measure</span></span>

* <span data-ttu-id="4b416-346">Контекст для (большой) голограммы потерян или не распознан из-за усечения в границах.</span><span class="sxs-lookup"><span data-stu-id="4b416-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="4b416-347">Расположение голограмм трудно найти в связи с отсутствием менеджеров по обучению или содержимым, которое быстро перемещается в holographic кадр и из него.</span><span class="sxs-lookup"><span data-stu-id="4b416-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="4b416-348">В сценарии требуется регулярное и повторяющееся движение головного движения, чтобы полностью увидеть голограмму, полученную в результате выносливости горловины.</span><span class="sxs-lookup"><span data-stu-id="4b416-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-349">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-349">Recommendations</span></span>

* <span data-ttu-id="4b416-350">Начните работу с небольшими объектами, которые соответствуют фов, а затем переходите с визуальными подсказками в более крупные версии.</span><span class="sxs-lookup"><span data-stu-id="4b416-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="4b416-351">Воспользуйтесь пространственными советами и директорами внимания, чтобы помочь пользователям найти содержимое, находящееся за пределами фов.</span><span class="sxs-lookup"><span data-stu-id="4b416-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="4b416-352">По возможности старайтесь не использовать голограммы, которые обфовся по вертикали.</span><span class="sxs-lookup"><span data-stu-id="4b416-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="4b416-353">Предоставьте пользователю рекомендации в приложении для наилучшего расположения для просмотра.</span><span class="sxs-lookup"><span data-stu-id="4b416-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-354">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4b416-355">Документы</span><span class="sxs-lookup"><span data-stu-id="4b416-355">Documentation</span></span>

* [<span data-ttu-id="4b416-356">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="4b416-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="4b416-357">Пример внедрения, Холостудио пользовательского интерфейса и разработки взаимодействия</span><span class="sxs-lookup"><span data-stu-id="4b416-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="4b416-358">Масштабирование объектов и сред</span><span class="sxs-lookup"><span data-stu-id="4b416-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="4b416-359">Курсоры, визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="4b416-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="4b416-360">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="4b416-360">External references</span></span>

* [<span data-ttu-id="4b416-361">Множество ADO о фов</span><span class="sxs-lookup"><span data-stu-id="4b416-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="4b416-362">Содержимое реагирует на расположение пользователя</span><span class="sxs-lookup"><span data-stu-id="4b416-362">Content reacts to user position</span></span>

<span data-ttu-id="4b416-363">Голограммы должны реагировать на пользовательскую точку примерно так же, как и «реальные» объекты.</span><span class="sxs-lookup"><span data-stu-id="4b416-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="4b416-364">Важным аспектом разработки являются элементы пользовательского интерфейса, которые не обязательно предполагают, что положение пользователя является стационарным и адаптируется к перемещению пользователя.</span><span class="sxs-lookup"><span data-stu-id="4b416-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="4b416-365">Проектирование приложения, которое правильно адаптируется к положению пользователей, приведет к более белиевабленому интерфейсу и упрощению его использования.</span><span class="sxs-lookup"><span data-stu-id="4b416-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-366">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-366">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-368"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-368"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-369">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-369">✔️</span></span></td>
        <td><span data-ttu-id="4b416-370">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-370">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-371">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="4b416-372">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-372">Best</span></span> </td><td> <span data-ttu-id="4b416-373">Содержимое и пользовательский интерфейс адаптируются к позициям пользователей, что позволяет пользователю естественным образом взаимодействовать с содержимым в области ожидаемого перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="4b416-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="4b416-374">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-374">Meets</span></span> </td><td> <span data-ttu-id="4b416-375">Пользовательский интерфейс адаптируется к положению пользователя, но может препятствовать просмотру содержимого ключа, в соответствии с которым пользователь должен изменить свое расположение.</span><span class="sxs-lookup"><span data-stu-id="4b416-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="4b416-376">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="4b416-377">Элементы пользовательского интерфейса теряются или блокируются во время перемещения, что приводит к неестественному возврату элементов управления (или поиска).</span><span class="sxs-lookup"><span data-stu-id="4b416-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="4b416-378">Элементы пользовательского интерфейса ограничивают представление основного содержимого.</span><span class="sxs-lookup"><span data-stu-id="4b416-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="4b416-379">Перемещение пользовательского интерфейса не оптимизировано для просмотра расстояния и длительности, особенно с элементами пользовательского интерфейса, <a href="billboarding-and-tag-along.md">основанными на тегах</a> .</span><span class="sxs-lookup"><span data-stu-id="4b416-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="4b416-380">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-380">How to measure</span></span>

* <span data-ttu-id="4b416-381">Все измерения должны выполняться в разумной области сценария.</span><span class="sxs-lookup"><span data-stu-id="4b416-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="4b416-382">В то время как перемещение пользователя будет разным, не пытайтесь заставить приложение использовать экстремальное перемещение пользователей.</span><span class="sxs-lookup"><span data-stu-id="4b416-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="4b416-383">Для элементов пользовательского интерфейса соответствующие элементы управления должны быть доступны независимо от перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="4b416-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="4b416-384">Например, если пользователь просматривает трехмерную карту и обходит ее с помощью масштаба, элемент управления масштабом должен быть доступен пользователю независимо от расположения.</span><span class="sxs-lookup"><span data-stu-id="4b416-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-385">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-385">Recommendations</span></span>

* <span data-ttu-id="4b416-386">Пользователь является камерой и управляет движением.</span><span class="sxs-lookup"><span data-stu-id="4b416-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="4b416-387">Позвольте им управлять.</span><span class="sxs-lookup"><span data-stu-id="4b416-387">Let them drive.</span></span>
* <span data-ttu-id="4b416-388">Рассмотрите возможность объявления для систем с текстом и меню, которые в противном случае были бы заблокированы или скрыты, если бы пользователь мог переместиться по всему миру.</span><span class="sxs-lookup"><span data-stu-id="4b416-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="4b416-389">Используйте тег для содержимого, которое должно следовать за пользователем, не позволяя пользователю видеть, что находится перед ними.</span><span class="sxs-lookup"><span data-stu-id="4b416-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-390">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4b416-391">Документы</span><span class="sxs-lookup"><span data-stu-id="4b416-391">Documentation</span></span>

* [<span data-ttu-id="4b416-392">Проектирование взаимодействия</span><span class="sxs-lookup"><span data-stu-id="4b416-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="4b416-393">Цвет, освещение и материал</span><span class="sxs-lookup"><span data-stu-id="4b416-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="4b416-394">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="4b416-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="4b416-395">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="4b416-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="4b416-396">Самостоятельное перемещение и локомотион пользователя</span><span class="sxs-lookup"><span data-stu-id="4b416-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4b416-397">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="4b416-397">Tools and tutorials</span></span>

* [<span data-ttu-id="4b416-398">Ввод MR 210: взгляд</span><span class="sxs-lookup"><span data-stu-id="4b416-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="4b416-399">Ясность взаимодействия ввода</span><span class="sxs-lookup"><span data-stu-id="4b416-399">Input interaction clarity</span></span>

<span data-ttu-id="4b416-400">Точность входных данных очень важна для удобства использования приложения и включает согласованность входных данных, подход, возможность обнаружения методов взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="4b416-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="4b416-401">Пользователь должен иметь возможность использовать общие взаимодействия всей платформы без повторного изучения.</span><span class="sxs-lookup"><span data-stu-id="4b416-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="4b416-402">Если приложение имеет пользовательский ввод, оно должно быть четко Отправлено и показано.</span><span class="sxs-lookup"><span data-stu-id="4b416-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-403">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-403">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-405"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-405"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-406">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-406">✔️</span></span></td>
        <td><span data-ttu-id="4b416-407">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-407">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-408">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-408">Quality criteria</span></span>

|  <span data-ttu-id="4b416-409">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-409">Best</span></span>  |  <span data-ttu-id="4b416-410">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-410">Meets</span></span> |  <span data-ttu-id="4b416-411">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4b416-412">Методы взаимодействия ввода согласованы с предоставленными [рекомендациями](interaction-fundamentals.md)Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4b416-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="4b416-413">Любые пользовательские входные данные не должны быть избыточными со стандартным входом (вместо использования стандартного взаимодействия) и должны быть четко переданы и продемонстрированы пользователю.</span><span class="sxs-lookup"><span data-stu-id="4b416-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="4b416-414">Похоже на лучшее, но пользовательские входные данные избыточны со стандартными методами ввода.</span><span class="sxs-lookup"><span data-stu-id="4b416-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="4b416-415">Пользователь по-прежнему может достигнуть цели и проделать ход работы с приложением.</span><span class="sxs-lookup"><span data-stu-id="4b416-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="4b416-416">Трудно понять сопоставление метода ввода или кнопки.</span><span class="sxs-lookup"><span data-stu-id="4b416-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="4b416-417">Входные данные сильно настроены, не поддерживают стандартный ввод, не имеют инструкций или, вероятно, не вызывают выносливости и комфортных проблем.</span><span class="sxs-lookup"><span data-stu-id="4b416-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4b416-418">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-418">How to measure</span></span>

* <span data-ttu-id="4b416-419">Приложение использует последовательные [стандартные методы ввода.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="4b416-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="4b416-420">Если приложение имеет пользовательский ввод, оно четко взаимодействует с помощью:</span><span class="sxs-lookup"><span data-stu-id="4b416-420">If the app has custom input, it is clearly communicated through:</span></span>
* <span data-ttu-id="4b416-421">Интерфейс первого запуска</span><span class="sxs-lookup"><span data-stu-id="4b416-421">First-run experience</span></span>
* <span data-ttu-id="4b416-422">Начальные экраны</span><span class="sxs-lookup"><span data-stu-id="4b416-422">Introductory screens</span></span>
* <span data-ttu-id="4b416-423">Подсказки</span><span class="sxs-lookup"><span data-stu-id="4b416-423">Tooltips</span></span>
* <span data-ttu-id="4b416-424">Обучение вручную</span><span class="sxs-lookup"><span data-stu-id="4b416-424">Hand coach</span></span>
* <span data-ttu-id="4b416-425">Раздел справки</span><span class="sxs-lookup"><span data-stu-id="4b416-425">Help section</span></span>
* <span data-ttu-id="4b416-426">Голосовое переработку</span><span class="sxs-lookup"><span data-stu-id="4b416-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-427">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-427">Recommendations</span></span>

* <span data-ttu-id="4b416-428">По возможности используйте стандартные методы ввода.</span><span class="sxs-lookup"><span data-stu-id="4b416-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="4b416-429">Предоставление демонстраций, учебников и подсказок для нестандартных методов ввода.</span><span class="sxs-lookup"><span data-stu-id="4b416-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="4b416-430">Используйте согласованную модель взаимодействия во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="4b416-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-431">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4b416-432">Документы</span><span class="sxs-lookup"><span data-stu-id="4b416-432">Documentation</span></span>

* [<span data-ttu-id="4b416-433">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="4b416-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="4b416-434">Взаимодействующие объекты</span><span class="sxs-lookup"><span data-stu-id="4b416-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="4b416-435">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="4b416-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="4b416-436">Курсоры</span><span class="sxs-lookup"><span data-stu-id="4b416-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="4b416-437">Комфорт и взгляните</span><span class="sxs-lookup"><span data-stu-id="4b416-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="4b416-438">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="4b416-438">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="4b416-439">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="4b416-439">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="4b416-440">Руководство по переносу логики ввода для Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-440">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="4b416-441">Ввод с клавиатуры в Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-441">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="4b416-442">Взгляд в Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-442">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="4b416-443">Жесты и контроллеры движения в Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-443">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="4b416-444">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-444">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="4b416-445">Ввод с помощью клавиатуры, мыши и контроллера в DirectX</span><span class="sxs-lookup"><span data-stu-id="4b416-445">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="4b416-446">Направление головы и взгляда в DirectX</span><span class="sxs-lookup"><span data-stu-id="4b416-446">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="4b416-447">Контроллеры движения и жестов в DirectX</span><span class="sxs-lookup"><span data-stu-id="4b416-447">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="4b416-448">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="4b416-448">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4b416-449">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="4b416-449">Tools and tutorials</span></span>

* [<span data-ttu-id="4b416-450">Пример использования: преимущества дополнительных персональных компьютеров</span><span class="sxs-lookup"><span data-stu-id="4b416-450">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="4b416-451">Исследование приведения: Холостудио пользовательского интерфейса и разработки взаимодействия</span><span class="sxs-lookup"><span data-stu-id="4b416-451">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="4b416-452">Пример приложения: периодическая таблица элементов</span><span class="sxs-lookup"><span data-stu-id="4b416-452">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="4b416-453">Пример приложения: Лунный модуль</span><span class="sxs-lookup"><span data-stu-id="4b416-453">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="4b416-454">Ввод MR 210: взгляд</span><span class="sxs-lookup"><span data-stu-id="4b416-454">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="4b416-455">Ввод MR 211: жесты</span><span class="sxs-lookup"><span data-stu-id="4b416-455">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="4b416-456">Ввод MR 212: Voice</span><span class="sxs-lookup"><span data-stu-id="4b416-456">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="4b416-457">Взаимодействующие объекты</span><span class="sxs-lookup"><span data-stu-id="4b416-457">Interactable objects</span></span>

<span data-ttu-id="4b416-458">Кнопка длиннее метафоры, используемой для активации события в 2D-абстрактном мире.</span><span class="sxs-lookup"><span data-stu-id="4b416-458">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="4b416-459">В мире объемной смешанной реальности мы больше не должны беспокоиться об этом мире абстракции.</span><span class="sxs-lookup"><span data-stu-id="4b416-459">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="4b416-460">Любой может быть взаимодействующим объектом, запускающим событие.</span><span class="sxs-lookup"><span data-stu-id="4b416-460">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="4b416-461">Взаимодействующий объект может быть представлен любым из чашк кофе в таблице в виде всплывающей подсказки, плавающей в воздухе.</span><span class="sxs-lookup"><span data-stu-id="4b416-461">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="4b416-462">Независимо от формы, взаимодействующие объекты должны быть четко распознаны пользователем с помощью визуальных и звуковых подсказок.</span><span class="sxs-lookup"><span data-stu-id="4b416-462">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-463">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-463">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-465"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-465"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-466">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-466">✔️</span></span></td>
        <td><span data-ttu-id="4b416-467">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-467">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-468">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-468">Quality criteria</span></span>

|  <span data-ttu-id="4b416-469">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-469">Best</span></span>  |  <span data-ttu-id="4b416-470">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-470">Meets</span></span> |  <span data-ttu-id="4b416-471">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-471">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4b416-472">Независимо от формы, взаимодействующие объекты распознаются через визуальные и звуковые подсказки в трех состояниях: бездействие, Целевая и выбранная.</span><span class="sxs-lookup"><span data-stu-id="4b416-472">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="4b416-473">«Видите ИТ-подсистемы» — ясно и постоянно используется в ходе работы.</span><span class="sxs-lookup"><span data-stu-id="4b416-473">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="4b416-474">Объекты масштабируются и распределяются для обеспечения бесплатной нацеливания на ошибки.</span><span class="sxs-lookup"><span data-stu-id="4b416-474">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="4b416-475">Пользователь может распознать объект как взаимодействующий через аудио или визуальный отзыв, а также нацелить и активировать объект.</span><span class="sxs-lookup"><span data-stu-id="4b416-475">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="4b416-476">Не имея визуальных или звуковых подсказок, пользователь не сможет распознать взаимодействующий объект.</span><span class="sxs-lookup"><span data-stu-id="4b416-476">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="4b416-477">Взаимодействия могут быть подвержены ошибкам из-за масштабирования объекта или расстояния между объектами.</span><span class="sxs-lookup"><span data-stu-id="4b416-477">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4b416-478">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-478">How to measure</span></span>

* <span data-ttu-id="4b416-479">Взаимодействующие объекты распознаются как "взаимодействующие"; включая кнопки, меню и содержимое, относящееся к приложению.</span><span class="sxs-lookup"><span data-stu-id="4b416-479">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="4b416-480">Как правило, при нацеливании на взаимодействующие объекты должны быть визуальными и звуковыми подсказками.</span><span class="sxs-lookup"><span data-stu-id="4b416-480">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-481">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-481">Recommendations</span></span>

* <span data-ttu-id="4b416-482">Использование визуальных и звуковых отзывов для взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="4b416-482">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="4b416-483">Визуальная обратная связь должна различаться для каждого входящего состояния (неактивно, назначено, выбрано).</span><span class="sxs-lookup"><span data-stu-id="4b416-483">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="4b416-484">Взаимодействующие объекты должны масштабироваться и размещаться для обеспечения бесплатной нацеливания на ошибки.</span><span class="sxs-lookup"><span data-stu-id="4b416-484">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="4b416-485">Сгруппированные взаимодействующие объекты (например, строка меню или список) должны иметь достаточное пространство для нацеливания.</span><span class="sxs-lookup"><span data-stu-id="4b416-485">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="4b416-486">Кнопки и меню, поддерживающие голосовую команду, должны предоставлять текстовые метки для ключевого слова Command (см. раздел, например, ")".</span><span class="sxs-lookup"><span data-stu-id="4b416-486">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-487">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-487">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4b416-488">Документы</span><span class="sxs-lookup"><span data-stu-id="4b416-488">Documentation</span></span>

* [<span data-ttu-id="4b416-489">Активный объект</span><span class="sxs-lookup"><span data-stu-id="4b416-489">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4b416-490">Текст в Unity</span><span class="sxs-lookup"><span data-stu-id="4b416-490">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="4b416-491">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="4b416-491">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="4b416-492">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="4b416-492">Voice input</span></span>](voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4b416-493">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="4b416-493">Tools and tutorials</span></span>

* [<span data-ttu-id="4b416-494">Набор средств для смешанной реальности — UX</span><span class="sxs-lookup"><span data-stu-id="4b416-494">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="4b416-495">Сканирование комнаты</span><span class="sxs-lookup"><span data-stu-id="4b416-495">Room scanning</span></span>

<span data-ttu-id="4b416-496">Приложения, для которых требуются данные пространственного сопоставления, полагаются на устройство для автоматического получения этих данных с течением времени и между сеансами по мере того, как пользователь исследует среду с активным устройством.</span><span class="sxs-lookup"><span data-stu-id="4b416-496">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="4b416-497">Полнота и качество этих данных зависит от ряда факторов, в том числе от количества выполненных пользователем проверок, времени, прошедших с момента исследования и того, были ли объекты, такие как мебель и дверцы, перемещены, так как устройство проверило эту область.</span><span class="sxs-lookup"><span data-stu-id="4b416-497">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="4b416-498">Многие приложения анализируют данные пространственного сопоставления в начале работы, чтобы определить, следует ли пользователю выполнять дополнительные действия, чтобы улучшить полноту и качество пространственной карты.</span><span class="sxs-lookup"><span data-stu-id="4b416-498">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="4b416-499">Если пользователь должен проверить окружение, при сканировании необходимо указать четкие рекомендации.</span><span class="sxs-lookup"><span data-stu-id="4b416-499">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-500">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-500">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-502"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-502"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-503">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-503">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-504">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-504">Quality criteria</span></span>

|  <span data-ttu-id="4b416-505">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-505">Best</span></span>  |  <span data-ttu-id="4b416-506">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-506">Meets</span></span> |  <span data-ttu-id="4b416-507">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-507">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4b416-508">Визуализация пространственной сети указывает, что выполняется проверка пользователей.</span><span class="sxs-lookup"><span data-stu-id="4b416-508">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="4b416-509">Пользователь четко знает, что делать и когда сканирование запускается и останавливается.</span><span class="sxs-lookup"><span data-stu-id="4b416-509">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="4b416-510">Обеспечивается визуализация пространственной сетки, но пользователь может не ясно понять, что делать, а сведения о ходе выполнения не предоставляются.</span><span class="sxs-lookup"><span data-stu-id="4b416-510">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="4b416-511">Отсутствует визуализация сетки.</span><span class="sxs-lookup"><span data-stu-id="4b416-511">No visualization of mesh.</span></span> <span data-ttu-id="4b416-512">Пользователю не предоставлены сведения о том, где искать или когда начинается или останавливается проверка.</span><span class="sxs-lookup"><span data-stu-id="4b416-512">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4b416-513">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-513">How to measure</span></span>

* <span data-ttu-id="4b416-514">При проверке необходимой комнаты предоставляется визуальное и звуковое руководство, указывающее, где искать, а когда запускать и прекращать сканирование.</span><span class="sxs-lookup"><span data-stu-id="4b416-514">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-515">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-515">Recommendations</span></span>

* <span data-ttu-id="4b416-516">Укажите, какая часть общего объема в области пользователей должна быть частью работы.</span><span class="sxs-lookup"><span data-stu-id="4b416-516">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="4b416-517">Взаимодействие при запуске и остановке сканирования, например индикатор выполнения.</span><span class="sxs-lookup"><span data-stu-id="4b416-517">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="4b416-518">Используйте визуализацию сетки во время сканирования.</span><span class="sxs-lookup"><span data-stu-id="4b416-518">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="4b416-519">Предоставьте визуальные и звуковые подсказки, чтобы дать пользователю возможность просматривать и перемещаться по комнате.</span><span class="sxs-lookup"><span data-stu-id="4b416-519">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="4b416-520">Сообщите пользователю, где можно усовершенствовать данные.</span><span class="sxs-lookup"><span data-stu-id="4b416-520">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="4b416-521">Во многих случаях лучше сообщить пользователю, что нужно сделать (например, Взгляните на центр мебели), чтобы получить необходимое качество сканирования.</span><span class="sxs-lookup"><span data-stu-id="4b416-521">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-522">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-522">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4b416-523">Документы</span><span class="sxs-lookup"><span data-stu-id="4b416-523">Documentation</span></span>

* [<span data-ttu-id="4b416-524">Визуализация при сканировании комнаты</span><span class="sxs-lookup"><span data-stu-id="4b416-524">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="4b416-525">Пример использования: расширение возможностей пространственных сопоставлений HoloLens</span><span class="sxs-lookup"><span data-stu-id="4b416-525">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="4b416-526">Пример использования: схема пространственного звука для Холотаур</span><span class="sxs-lookup"><span data-stu-id="4b416-526">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="4b416-527">Пример использования: Создание иммерсивного интерфейса в фрагментах</span><span class="sxs-lookup"><span data-stu-id="4b416-527">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4b416-528">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="4b416-528">Tools and tutorials</span></span>

* [<span data-ttu-id="4b416-529">Набор средств для смешанной реальности — UX</span><span class="sxs-lookup"><span data-stu-id="4b416-529">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="4b416-530">Индикаторы направления</span><span class="sxs-lookup"><span data-stu-id="4b416-530">Directional indicators</span></span>

<span data-ttu-id="4b416-531">В приложении для смешанной реальности содержимое может находиться за пределами поля View или перекрыто по реальным объектам.</span><span class="sxs-lookup"><span data-stu-id="4b416-531">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="4b416-532">Хорошо спроектированное приложение упростит пользователю поиск невидимого содержимого.</span><span class="sxs-lookup"><span data-stu-id="4b416-532">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="4b416-533">Направленные индикаторы предупреждают пользователя о важном содержимом и предоставляют рекомендации по содержимому относительно положения пользователя.</span><span class="sxs-lookup"><span data-stu-id="4b416-533">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="4b416-534">Руководство по невидимому содержимому может принимать форму звуковых датчиков, стрелок направления или прямых визуальных подсказок.</span><span class="sxs-lookup"><span data-stu-id="4b416-534">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-535">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-535">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-537"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-537"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-538">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-538">✔️</span></span></td>
        <td><span data-ttu-id="4b416-539">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-539">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-540">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-540">Quality criteria</span></span>

|  <span data-ttu-id="4b416-541">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-541">Best</span></span>  |  <span data-ttu-id="4b416-542">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-542">Meets</span></span> |  <span data-ttu-id="4b416-543">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-543">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4b416-544">Визуальные и звуковые подсказки непосредственно позволяют пользователю подходящее содержимое за пределами поля представления.</span><span class="sxs-lookup"><span data-stu-id="4b416-544">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="4b416-545">Стрелка или индикатор, указывающий на пользователя в общем направлении содержимого.</span><span class="sxs-lookup"><span data-stu-id="4b416-545">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="4b416-546">Соответствующее содержимое находится за пределами поля представления, и для пользователя не предоставляется никаких инструкций по расположению.</span><span class="sxs-lookup"><span data-stu-id="4b416-546">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4b416-547">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-547">How to measure</span></span>

* <span data-ttu-id="4b416-548">Содержимое, соответствующее содержимому за пределами поля "пользователь", может быть обнаружено с помощью визуальных и (или) звуковых подсказок.</span><span class="sxs-lookup"><span data-stu-id="4b416-548">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-549">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-549">Recommendations</span></span>

* <span data-ttu-id="4b416-550">Если соответствующее содержимое находится вне поля зрения пользователя, используйте индикаторы направления и звуковые подсказки для указания пользователю содержимого.</span><span class="sxs-lookup"><span data-stu-id="4b416-550">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="4b416-551">Во многих случаях непосредственное визуальное направляющее предпочтительнее стрелок направления.</span><span class="sxs-lookup"><span data-stu-id="4b416-551">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="4b416-552">Индикаторы направления не должны быть встроены в курсор.</span><span class="sxs-lookup"><span data-stu-id="4b416-552">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-553">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-553">Resources</span></span>

* [<span data-ttu-id="4b416-554">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="4b416-554">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="4b416-555">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="4b416-555">Data loading</span></span>

<span data-ttu-id="4b416-556">Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.</span><span class="sxs-lookup"><span data-stu-id="4b416-556">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="4b416-557">Это может означать, что пользователь не может взаимодействовать с приложением, когда индикатор хода выполнения является видимым, а также может указать, как долго должно быть установлено время ожидания.</span><span class="sxs-lookup"><span data-stu-id="4b416-557">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4b416-558">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="4b416-558">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b416-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b416-560"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b416-560"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b416-561">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-561">✔️</span></span></td>
        <td><span data-ttu-id="4b416-562">✔️</span><span class="sxs-lookup"><span data-stu-id="4b416-562">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4b416-563">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="4b416-563">Quality criteria</span></span>

|  <span data-ttu-id="4b416-564">Самое</span><span class="sxs-lookup"><span data-stu-id="4b416-564">Best</span></span>  |  <span data-ttu-id="4b416-565">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="4b416-565">Meets</span></span> |  <span data-ttu-id="4b416-566">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="4b416-566">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4b416-567">Анимированный визуальный индикатор в виде индикатора выполнения или кольца, отображающий ход выполнения во время загрузки или обработки данных.</span><span class="sxs-lookup"><span data-stu-id="4b416-567">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="4b416-568">Визуальный индикатор предоставляет рекомендации по продолжительности ожидания.</span><span class="sxs-lookup"><span data-stu-id="4b416-568">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="4b416-569">Пользователь уведомляется о том, что выполняется загрузка данных, но нет никакой информации о том, как долго может быть ожидание.</span><span class="sxs-lookup"><span data-stu-id="4b416-569">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="4b416-570">Ни один индикатор загрузки данных или процесса для задачи не занимает более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="4b416-570">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4b416-571">Как измерять</span><span class="sxs-lookup"><span data-stu-id="4b416-571">How to measure</span></span>

* <span data-ttu-id="4b416-572">Во время загрузки данных убедитесь в отсутствии пустого состояния более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="4b416-572">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4b416-573">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b416-573">Recommendations</span></span>

* <span data-ttu-id="4b416-574">Предоставьте аниматор загрузки данных в любой ситуации, когда пользователь может раскрывать это приложение о зависании или сбое.</span><span class="sxs-lookup"><span data-stu-id="4b416-574">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="4b416-575">Разумное правило для параметра Thumb — это любое действие "Загрузка", которое может занять более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="4b416-575">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="4b416-576">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="4b416-576">Resources</span></span>

* [<span data-ttu-id="4b416-577">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="4b416-577">Displaying progress</span></span>](progress.md)
