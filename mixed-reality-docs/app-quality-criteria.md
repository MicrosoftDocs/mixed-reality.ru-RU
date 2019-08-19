---
title: Критерии качества приложения
description: В этом документе описываются лучшие факторы, влияющие на качество приложений смешанной реальности.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: критерии качества приложения, Смешанная реальность, приложение смешанной реальности
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024495"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="81c97-104">Критерии качества приложения</span><span class="sxs-lookup"><span data-stu-id="81c97-104">App quality criteria</span></span>

<span data-ttu-id="81c97-105">В этом документе описываются лучшие факторы, влияющие на качество приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="81c97-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="81c97-106">Для каждого фактора предоставляются следующие сведения.</span><span class="sxs-lookup"><span data-stu-id="81c97-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="81c97-107">Обзор — краткое описание фактора качества и его важность.</span><span class="sxs-lookup"><span data-stu-id="81c97-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="81c97-108">Влияние на устройства: тип устройства Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="81c97-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="81c97-109">Критерии качества — оценка коэффициента качества.</span><span class="sxs-lookup"><span data-stu-id="81c97-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="81c97-110">Способ измерения — методы для измерения (или взаимодействия) проблемы.</span><span class="sxs-lookup"><span data-stu-id="81c97-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="81c97-111">Рекомендации — общие сведения о подходах, обеспечивающих лучшую работу пользователей.</span><span class="sxs-lookup"><span data-stu-id="81c97-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="81c97-112">Ресурсы — соответствующие ресурсы для разработчиков и проектирования, которые полезны для создания лучших возможностей приложений.</span><span class="sxs-lookup"><span data-stu-id="81c97-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="81c97-113">Частота кадров</span><span class="sxs-lookup"><span data-stu-id="81c97-113">Frame rate</span></span>

<span data-ttu-id="81c97-114">Частота кадров — первый основополагающий уровень стабильности и комфорт пользователя.</span><span class="sxs-lookup"><span data-stu-id="81c97-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="81c97-115">Частота кадров ниже рекомендуемых целевых объектов может привести к неблагоприятному снижению голограмм, негативно сказывается на белиевабилити опыта и потенциально выносливости глаз.</span><span class="sxs-lookup"><span data-stu-id="81c97-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="81c97-116">В зависимости от того, какие компьютеры, совместимые с Windows Mixed Reality, вы хотите поддерживать, частота целевого кадра на впечатляющих наушниках Windows Mixed Reality будет либо 60 Гц, либо 90Hz.</span><span class="sxs-lookup"><span data-stu-id="81c97-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="81c97-117">Для HoloLens частота целевого кадра составляет 60 Гц.</span><span class="sxs-lookup"><span data-stu-id="81c97-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-118">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-120"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-121">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-121">✔️</span></span></td>
        <td><span data-ttu-id="81c97-122">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-123">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-123">Quality criteria</span></span>

|  <span data-ttu-id="81c97-124">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-124">Best</span></span>  |  <span data-ttu-id="81c97-125">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-125">Meets</span></span> |  <span data-ttu-id="81c97-126">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="81c97-127">Приложение согласованно соответствует цели кадров в секунду (кадров/с) для целевого устройства: 60fps в HoloLens; 90fps на Ultra PCs; и 60fps на самых распространенных ПК.</span><span class="sxs-lookup"><span data-stu-id="81c97-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="81c97-128">Приложение имеет периодические падения кадров, не мешая основным интерфейсам. или кадр/сек постоянно меньше требуемой цели, но не помешать работе приложения.</span><span class="sxs-lookup"><span data-stu-id="81c97-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="81c97-129">В этом приложении частота кадров в среднем составляет каждые десять секунд или меньше.</span><span class="sxs-lookup"><span data-stu-id="81c97-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="81c97-130">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-130">How to measure</span></span>

* <span data-ttu-id="81c97-131">Диаграмма частоты кадров в реальном времени предоставляется на [портале устройств Windows](using-the-windows-device-portal.md#system-performance) в разделе "производительность системы".</span><span class="sxs-lookup"><span data-stu-id="81c97-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="81c97-132">Для отладки разработки добавьте в приложение счетчик диагностики частоты кадров.</span><span class="sxs-lookup"><span data-stu-id="81c97-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="81c97-133">Пример счетчика см. в разделе ресурсы.</span><span class="sxs-lookup"><span data-stu-id="81c97-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="81c97-134">При этом на устройстве могут возникать частоты кадров, пока приложение работает, перемещая головную часть в сторону.</span><span class="sxs-lookup"><span data-stu-id="81c97-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="81c97-135">Если в голограмме отображается непредвиденное движение с нарушением колебаний, то, скорее всего, причиной является низкая частота кадров или уровень стабильности.</span><span class="sxs-lookup"><span data-stu-id="81c97-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-136">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-136">Recommendations</span></span>

* <span data-ttu-id="81c97-137">Добавьте счетчик частоты кадров в начале работы по разработке.</span><span class="sxs-lookup"><span data-stu-id="81c97-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="81c97-138">Изменения, которые требуют сброса в частоте кадров, должны оцениваться и надлежащим образом разрешаться как ошибки производительности.</span><span class="sxs-lookup"><span data-stu-id="81c97-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-139">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="81c97-140">Документация</span><span class="sxs-lookup"><span data-stu-id="81c97-140">Documentation</span></span>

* [<span data-ttu-id="81c97-141">Основные сведения о производительности смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="81c97-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="81c97-142">Голограмма, стабильность и частота кадров</span><span class="sxs-lookup"><span data-stu-id="81c97-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="81c97-143">Бюджет производительности активов</span><span class="sxs-lookup"><span data-stu-id="81c97-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="81c97-144">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="81c97-145">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="81c97-145">Tools and tutorials</span></span>

* [<span data-ttu-id="81c97-146">Мртулкит, отображение счетчика кадров/с</span><span class="sxs-lookup"><span data-stu-id="81c97-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="81c97-147">Мртулкит, шейдеры</span><span class="sxs-lookup"><span data-stu-id="81c97-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="81c97-148">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="81c97-148">External references</span></span>

* [<span data-ttu-id="81c97-149">Unity, оптимизация мобильных приложений</span><span class="sxs-lookup"><span data-stu-id="81c97-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="81c97-150">Голограмма, стабильность</span><span class="sxs-lookup"><span data-stu-id="81c97-150">Hologram stability</span></span>

<span data-ttu-id="81c97-151">Стабильные голограммы повышают удобство использования и белиевабилити приложения и создают более удобное для пользователя удобство просмотра.</span><span class="sxs-lookup"><span data-stu-id="81c97-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="81c97-152">Качество стабильной работы является результатом хорошей разработки приложений и способности устройства понять (отслеживанию) его среды.</span><span class="sxs-lookup"><span data-stu-id="81c97-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="81c97-153">Хотя Частота кадров — первый основополагающий уровень стабильности, другие факторы могут повлиять на стабильность, включая:</span><span class="sxs-lookup"><span data-stu-id="81c97-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="81c97-154">Использование плоскости стабилизации</span><span class="sxs-lookup"><span data-stu-id="81c97-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="81c97-155">Расстояние до пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="81c97-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="81c97-156">Отслеживание</span><span class="sxs-lookup"><span data-stu-id="81c97-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-157">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-159"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-160">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-160">✔️</span></span></td>
        <td><span data-ttu-id="81c97-161">❌</span><span class="sxs-lookup"><span data-stu-id="81c97-161">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-162">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-162">Quality criteria</span></span>

|  <span data-ttu-id="81c97-163">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-163">Best</span></span>  |  <span data-ttu-id="81c97-164">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-164">Meets</span></span> |  <span data-ttu-id="81c97-165">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-165">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="81c97-166">Голограммы согласованно выглядят стабильно.</span><span class="sxs-lookup"><span data-stu-id="81c97-166">Holograms consistently appear stable.</span></span> | <span data-ttu-id="81c97-167">Во вторичном содержимом возникает непредвиденное перемещение; или непредвиденное перемещение не помешать общей работе приложения.</span><span class="sxs-lookup"><span data-stu-id="81c97-167">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="81c97-168">Основное содержимое в кадре приводит к непредвиденному перемещению.</span><span class="sxs-lookup"><span data-stu-id="81c97-168">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="81c97-169">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-169">How to measure</span></span>

<span data-ttu-id="81c97-170">Людьми устройство и просматривая его работу:</span><span class="sxs-lookup"><span data-stu-id="81c97-170">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="81c97-171">Переместите заголовок с боковой стороны на сторону. Если на голограммах отображается непредвиденное перемещение, то вероятная причина может быть вызвана низкой частотой кадров или неправильным выравниванием области стабильности с фокусом плоскости.</span><span class="sxs-lookup"><span data-stu-id="81c97-171">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="81c97-172">Перемещайтесь по голограммам и окружениям, ищите такие варианты поведения, как дорожки и «переход».</span><span class="sxs-lookup"><span data-stu-id="81c97-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="81c97-173">Этот тип движения, скорее всего, вызван тем, что устройство не отслеживает среду или расстояние до пространственной привязки.</span><span class="sxs-lookup"><span data-stu-id="81c97-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="81c97-174">Если в кадре находятся большие или несколько голограмм, обратите внимание на поведение голограммы с различной глубиной при перемещении головной позиции с стороны в сторону, если шакинесс, вероятно, это вызвано плоскостью стабилизации.</span><span class="sxs-lookup"><span data-stu-id="81c97-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="81c97-175">Рекомендуемых</span><span class="sxs-lookup"><span data-stu-id="81c97-175">Recomendations</span></span>

* <span data-ttu-id="81c97-176">Добавьте счетчик частоты кадров в начале работы по разработке.</span><span class="sxs-lookup"><span data-stu-id="81c97-176">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="81c97-177">Используйте плоскость стабилизации.</span><span class="sxs-lookup"><span data-stu-id="81c97-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="81c97-178">Всегда Визуализируйте закрепленные голограммы в пределах 3 метров их привязки.</span><span class="sxs-lookup"><span data-stu-id="81c97-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="81c97-179">Убедитесь, что в вашей среде настроено правильное отслеживание.</span><span class="sxs-lookup"><span data-stu-id="81c97-179">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="81c97-180">Создайте свой опыт, чтобы избежать голограмм с различными уровнями фокусной глубины внутри рамки.</span><span class="sxs-lookup"><span data-stu-id="81c97-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-181">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="81c97-182">Документация</span><span class="sxs-lookup"><span data-stu-id="81c97-182">Documentation</span></span>

* [<span data-ttu-id="81c97-183">Голограмма, стабильность и частота кадров</span><span class="sxs-lookup"><span data-stu-id="81c97-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="81c97-184">Пример использования с плоскостью стабилизации</span><span class="sxs-lookup"><span data-stu-id="81c97-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="81c97-185">Основные сведения о производительности смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="81c97-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="81c97-186">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-186">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="81c97-187">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="81c97-187">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="81c97-188">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="81c97-188">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="81c97-189">Стационарная рамка ссылки</span><span class="sxs-lookup"><span data-stu-id="81c97-189">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="81c97-190">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="81c97-190">Tools and tutorials</span></span>

* [<span data-ttu-id="81c97-191">Пакет, сопровождающий MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="81c97-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="81c97-192">Расположение голограмм на реальных поверхностях</span><span class="sxs-lookup"><span data-stu-id="81c97-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="81c97-193">Неверное выравнивание голограмм с физическими объектами (если предполагается, что они помещаются в связи друг с другом) является четкой признаком того, что не является объединением голограмм и реального мира.</span><span class="sxs-lookup"><span data-stu-id="81c97-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="81c97-194">Точность размещения должна относиться к потребностям сценария. Например, при размещении в общей области можно использовать пространственное соответствие, но более точное размещение потребует использования маркеров и калибровки.</span><span class="sxs-lookup"><span data-stu-id="81c97-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-195">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-197"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-198">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-198">✔️</span></span></td>
        <td><span data-ttu-id="81c97-199">❌</span><span class="sxs-lookup"><span data-stu-id="81c97-199">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-200">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-200">Quality criteria</span></span>

|  <span data-ttu-id="81c97-201">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-201">Best</span></span>  |  <span data-ttu-id="81c97-202">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-202">Meets</span></span> |  <span data-ttu-id="81c97-203">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-203">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="81c97-204">Голограммы выводятся на поверхность, как правило, в диапазоне от сантиметров до сантиметров.</span><span class="sxs-lookup"><span data-stu-id="81c97-204">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="81c97-205">Если требуется более высокая точность, приложение должно предоставить эффективные средства для совместной работы в пределах требуемой спецификации приложения.</span><span class="sxs-lookup"><span data-stu-id="81c97-205">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="81c97-206">Н/Д</span><span class="sxs-lookup"><span data-stu-id="81c97-206">NA</span></span> | <span data-ttu-id="81c97-207">Голограммы выводятся без согласования с физическим целевым объектом путем его разрыва или появления в плавающей области.</span><span class="sxs-lookup"><span data-stu-id="81c97-207">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="81c97-208">Если требуется точность, голограммы должны соответствовать спецификации близости в сценарии.</span><span class="sxs-lookup"><span data-stu-id="81c97-208">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="81c97-209">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-209">How to measure</span></span>

* <span data-ttu-id="81c97-210">Голограммы, размещенные на пространственной карте, не должны иметь заметного числа с плавающей запятой выше или ниже поверхности.</span><span class="sxs-lookup"><span data-stu-id="81c97-210">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="81c97-211">Голограммы, для которых требуется точное размещение, должны иметь некоторую форму системы маркеров и калибровки, точную для требования сценария.</span><span class="sxs-lookup"><span data-stu-id="81c97-211">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-212">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-212">Recommendations</span></span>

* <span data-ttu-id="81c97-213">Пространственное соответствие удобно использовать для размещения объектов на поверхностях, когда точность не требуется.</span><span class="sxs-lookup"><span data-stu-id="81c97-213">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="81c97-214">Для наилучшей точности используйте маркеры или афиши, чтобы задать голограммы и контроллер Xbox (или какой-либо механизм выравнивания вручную) для окончательной калибровки.</span><span class="sxs-lookup"><span data-stu-id="81c97-214">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="81c97-215">Рассмотрите возможность разбиения очень больших голограмм на логические части и согласования каждой части с поверхностью.</span><span class="sxs-lookup"><span data-stu-id="81c97-215">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="81c97-216">Неправильное задание расстояния интерпупилари (IPD) также может влиять на выравнивание голограмм.</span><span class="sxs-lookup"><span data-stu-id="81c97-216">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="81c97-217">Всегда настраивайте HoloLens для пользователя IPD.</span><span class="sxs-lookup"><span data-stu-id="81c97-217">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-218">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-218">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="81c97-219">Документация</span><span class="sxs-lookup"><span data-stu-id="81c97-219">Documentation</span></span>

* [<span data-ttu-id="81c97-220">Размещение пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="81c97-220">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="81c97-221">Процесс сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="81c97-221">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="81c97-222">Рекомендации по пространственной привязке</span><span class="sxs-lookup"><span data-stu-id="81c97-222">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="81c97-223">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="81c97-223">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="81c97-224">Пространственное сопоставление в Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-224">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="81c97-225">Общие сведения о разработке вуфориа</span><span class="sxs-lookup"><span data-stu-id="81c97-225">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="81c97-226">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="81c97-226">Tools and tutorials</span></span>

* [<span data-ttu-id="81c97-227">230. Пространство в смешанной реальности: пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="81c97-227">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="81c97-228">MR Toolkit, библиотеки пространственных сопоставлений</span><span class="sxs-lookup"><span data-stu-id="81c97-228">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="81c97-229">Комплект поставки пакета MR, пример калибровки афиши</span><span class="sxs-lookup"><span data-stu-id="81c97-229">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="81c97-230">Пакет, сопровождающий MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="81c97-230">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="81c97-231">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="81c97-231">External references</span></span>

* [<span data-ttu-id="81c97-232">Ловес пример, выравнивание точности</span><span class="sxs-lookup"><span data-stu-id="81c97-232">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="81c97-233">Просмотр зоны отдыха</span><span class="sxs-lookup"><span data-stu-id="81c97-233">Viewing zone of comfort</span></span>

<span data-ttu-id="81c97-234">Разработчики приложений контролируют, где соходят глаза пользователей, размещая содержимое и голограммы с различной глубиной.</span><span class="sxs-lookup"><span data-stu-id="81c97-234">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="81c97-235">Пользователи людьми HoloLens всегда будут работать с 2.0 m, чтобы обеспечить четкий образ, так как отображение HoloLens фиксировано на оптическом расстоянии примерно 2,0 млн от пользователя.</span><span class="sxs-lookup"><span data-stu-id="81c97-235">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="81c97-236">Неправильная глубина содержимого может привести к появлению Visual дискомфорт или выносливости.</span><span class="sxs-lookup"><span data-stu-id="81c97-236">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-237">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-237">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-239"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-240">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-240">✔️</span></span></td>
        <td><span data-ttu-id="81c97-241">❌</span><span class="sxs-lookup"><span data-stu-id="81c97-241">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-242">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-242">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="81c97-243">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-243">Best</span></span> </td><td><ul>
<li><span data-ttu-id="81c97-244">Разместите содержимое в 2 MБ.</span><span class="sxs-lookup"><span data-stu-id="81c97-244">Place content at 2m.</span></span></li><li><span data-ttu-id="81c97-245">Если не удается поместить голограммы в 2 МБ, а конфликты между конвергенцией и проживанием не могут быть устранены, оптимальная зона для размещения с голограммами находится между 1,25 м и 5 мин.</span><span class="sxs-lookup"><span data-stu-id="81c97-245">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="81c97-246">В каждом случае разработчики должны структурировать содержимое, чтобы рекомендовать пользователям взаимодействовать с 1 + m (например, настроить размер содержимого и параметры размещения по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="81c97-246">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="81c97-247">Если не требуется специально для сценария, следует реализовать плоскость отсечения с эффектом затухания, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="81c97-247">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="81c97-248">В случаях, когда требуется более близкое наблюдение за голограммой мотионлесс, содержимое не должно быть ближе к 50cm.</span><span class="sxs-lookup"><span data-stu-id="81c97-248">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="81c97-249">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-249">Meets</span></span></td><td> <span data-ttu-id="81c97-250">Содержимое находится в рамках руководства по просмотру и перемещению, но неверно использует или не использует плоскость обрезки.</span><span class="sxs-lookup"><span data-stu-id="81c97-250">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="81c97-251">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-251">Fail</span></span> </td><td> <span data-ttu-id="81c97-252">Содержимое представлено слишком близко (обычно &lt;1,25 м или &lt;50cm для стационарных голограмм, для которых необходимо более внимательное наблюдение).</span><span class="sxs-lookup"><span data-stu-id="81c97-252">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="81c97-253">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-253">How to measure</span></span>

* <span data-ttu-id="81c97-254">Как правило, содержимое должно находиться на расстоянии до 2 МБ, но не ближе к 1,25 или более чем 5 мин.</span><span class="sxs-lookup"><span data-stu-id="81c97-254">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="81c97-255">За некоторыми исключениями расстояние отсечения HoloLens должно быть равно. 85CM с появлением содержимого, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="81c97-255">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="81c97-256">Допишитесь на содержимое и обратите внимание на эффекты обтравочной плоскости.</span><span class="sxs-lookup"><span data-stu-id="81c97-256">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="81c97-257">Стационарное содержимое не должно быть ближе к 50cm.</span><span class="sxs-lookup"><span data-stu-id="81c97-257">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-258">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-258">Recommendations</span></span>

* <span data-ttu-id="81c97-259">Создайте содержимое для оптимального расстояния до 2 МБ.</span><span class="sxs-lookup"><span data-stu-id="81c97-259">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="81c97-260">Установите значение расстояния отрисовки обрезки равным 85cm с появлением содержимого, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="81c97-260">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="81c97-261">Для стационарных голограмм, для которых требуется более близкое к просмотру, плоскость обрезки не должна быть ближе к 30cm, а эффект затухания должен начинаться по крайней мере 10cm от плоскости обрезки.</span><span class="sxs-lookup"><span data-stu-id="81c97-261">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-262">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-262">Resources</span></span>

* [<span data-ttu-id="81c97-263">Расстояние визуализации</span><span class="sxs-lookup"><span data-stu-id="81c97-263">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="81c97-264">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-264">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="81c97-265">Эксперименты с масштабом</span><span class="sxs-lookup"><span data-stu-id="81c97-265">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="81c97-266">Текст, рекомендуемый размер шрифта</span><span class="sxs-lookup"><span data-stu-id="81c97-266">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="81c97-267">Переключение глубины</span><span class="sxs-lookup"><span data-stu-id="81c97-267">Depth switching</span></span>

<span data-ttu-id="81c97-268">Независимо от способа просмотра зоны проблем, требования пользователя к частому или быстрому переключению между ближайшими и далекими объектами (включая голограммы и реальное содержимое) могут привести к окуломотор выносливости и общему дискомфорт.</span><span class="sxs-lookup"><span data-stu-id="81c97-268">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-269">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-269">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-271"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-272">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-272">✔️</span></span></td>
        <td><span data-ttu-id="81c97-273">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-273">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-274">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-274">Quality criteria</span></span>

|  <span data-ttu-id="81c97-275">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-275">Best</span></span>  |  <span data-ttu-id="81c97-276">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-276">Meets</span></span> |  <span data-ttu-id="81c97-277">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-277">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="81c97-278">Ограниченное или естественное изменение глубины, которое не приводит к неестественному переключению пользователя.</span><span class="sxs-lookup"><span data-stu-id="81c97-278">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="81c97-279">Параметр с внезапной глубиной является базовым и разрабатывается в процессе работы приложения или с внезапной глубиной, вызванной непредвиденным реальным содержимым.</span><span class="sxs-lookup"><span data-stu-id="81c97-279">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="81c97-280">Постоянный переключатель глубины или внезапное переключение глубины, которое не требуется или является ядром для работы приложения.</span><span class="sxs-lookup"><span data-stu-id="81c97-280">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="81c97-281">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-281">How to measure</span></span>

* <span data-ttu-id="81c97-282">Если приложение требует, чтобы пользователь постоянно или резко изменил фокус глубины, существует проблема переключения глубины.</span><span class="sxs-lookup"><span data-stu-id="81c97-282">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-283">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-283">Recommendations</span></span>

* <span data-ttu-id="81c97-284">Сделайте основной контент на согласованной плоскости, убедитесь, что плоскость стабилизации соответствует фокальной плоскости.</span><span class="sxs-lookup"><span data-stu-id="81c97-284">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="81c97-285">Это позволит сократить окуломотор выносливости и неожиданное перемещение голограмм.</span><span class="sxs-lookup"><span data-stu-id="81c97-285">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-286">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-286">Resources</span></span>

* [<span data-ttu-id="81c97-287">Расстояние визуализации</span><span class="sxs-lookup"><span data-stu-id="81c97-287">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="81c97-288">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-288">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="81c97-289">Использование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="81c97-289">Use of spatial sound</span></span>

<span data-ttu-id="81c97-290">В Windows Mixed Reality подсистема аудио предоставляет компонент Аурал в режиме смешанной реальности, имитируя трехмерный звук с помощью направления, расстояния и моделирования окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="81c97-290">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="81c97-291">Использование пространственного звука в приложении позволяет разработчикам убедительно размещать звуки в трехмерном пространстве (Sphere) вокруг пользователя.</span><span class="sxs-lookup"><span data-stu-id="81c97-291">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="81c97-292">Эти звуки будут выглядеть так, как будто они поступают от реальных физических объектов или голограмм в смешанной реальности в окружающей среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="81c97-292">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="81c97-293">Пространственный звук — это мощный инструмент для погружения, специальных возможностей и разработки UX в приложениях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="81c97-293">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-294">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-294">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-296"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-297">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-297">✔️</span></span></td>
        <td><span data-ttu-id="81c97-298">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-298">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-299">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-299">Quality criteria</span></span>

|  <span data-ttu-id="81c97-300">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-300">Best</span></span>  |  <span data-ttu-id="81c97-301">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-301">Meets</span></span> |  <span data-ttu-id="81c97-302">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-302">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="81c97-303">Звук логически пространственно, а UX соответствующим образом использует звук, чтобы помочь в обнаружении объектов и отзыве пользователей.</span><span class="sxs-lookup"><span data-stu-id="81c97-303">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="81c97-304">Звук является естественным и относится к объектам и нормализуется в рамках сценария.</span><span class="sxs-lookup"><span data-stu-id="81c97-304">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="81c97-305">Пространственный звук используется соответствующим образом для белиевабилити, но отсутствует как средство для получения отзывов пользователей и возможности обнаружения.</span><span class="sxs-lookup"><span data-stu-id="81c97-305">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="81c97-306">Звук не пространственно, как ожидалось, и (или) недостаток звука, чтобы помочь пользователю в его интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="81c97-306">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="81c97-307">Или пространственный звук не рассматривался или не используется в проектировании сценария.</span><span class="sxs-lookup"><span data-stu-id="81c97-307">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="81c97-308">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-308">How to measure</span></span>

* <span data-ttu-id="81c97-309">Как правило, соответствующие звуки должны выдаваться из голограмм (например, лайного звука, поступающего от Holographic.)</span><span class="sxs-lookup"><span data-stu-id="81c97-309">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="81c97-310">Звуковые подсказки следует использовать по всему внешнему интерфейсу, чтобы помочь пользователю в отзыве или осведомлении о действиях, выходящих за рамки Holographic.</span><span class="sxs-lookup"><span data-stu-id="81c97-310">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-311">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-311">Recommendations</span></span>

* <span data-ttu-id="81c97-312">Используйте Пространственный звук для помощи с обнаружением объектов и пользовательскими интерфейсами.</span><span class="sxs-lookup"><span data-stu-id="81c97-312">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="81c97-313">Реальные звуки работают лучше, чем синтезированный или неестественный звук.</span><span class="sxs-lookup"><span data-stu-id="81c97-313">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="81c97-314">Большинство звуков должно быть пространственно.</span><span class="sxs-lookup"><span data-stu-id="81c97-314">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="81c97-315">Избегайте невидимых передатчиков.</span><span class="sxs-lookup"><span data-stu-id="81c97-315">Avoid invisible emitters.</span></span>
* <span data-ttu-id="81c97-316">Избегайте использования пространственных масок.</span><span class="sxs-lookup"><span data-stu-id="81c97-316">Avoid spatial masking.</span></span>
* <span data-ttu-id="81c97-317">Нормализовать все звуки.</span><span class="sxs-lookup"><span data-stu-id="81c97-317">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-318">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-318">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="81c97-319">Документация</span><span class="sxs-lookup"><span data-stu-id="81c97-319">Documentation</span></span>

* [<span data-ttu-id="81c97-320">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="81c97-320">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="81c97-321">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="81c97-321">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="81c97-322">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-322">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="81c97-323">Пример использования: Пространственный звук для Холотаур</span><span class="sxs-lookup"><span data-stu-id="81c97-323">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="81c97-324">Пример использования пространственного звука в Робораид</span><span class="sxs-lookup"><span data-stu-id="81c97-324">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="81c97-325">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="81c97-325">Tools and tutorials</span></span>

* [<span data-ttu-id="81c97-326">220. Пространство в смешанной реальности: пространственный звук</span><span class="sxs-lookup"><span data-stu-id="81c97-326">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="81c97-327">Мртулкит, Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="81c97-327">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="81c97-328">Фокус на границах в holographic кадрах (фов)</span><span class="sxs-lookup"><span data-stu-id="81c97-328">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="81c97-329">Хорошо спроектированное взаимодействие с пользователем может создать и поддерживать полезный контекст виртуальной среды, который будет расширяться вокруг пользователей.</span><span class="sxs-lookup"><span data-stu-id="81c97-329">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="81c97-330">Устранение последствий границ фов заключается в продуманном проектировании масштабирования и контекста содержимого, использовании пространственных аудио, руководств и расположения пользователей.</span><span class="sxs-lookup"><span data-stu-id="81c97-330">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="81c97-331">Если вы сделали это правильно, то у пользователя будет меньше ограничений, чем границы фов, и удобство работы с приложением.</span><span class="sxs-lookup"><span data-stu-id="81c97-331">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-332">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-332">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-334"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-335">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-335">✔️</span></span></td>
        <td><span data-ttu-id="81c97-336">❌</span><span class="sxs-lookup"><span data-stu-id="81c97-336">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-337">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-337">Quality criteria</span></span>

|  <span data-ttu-id="81c97-338">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-338">Best</span></span>  |  <span data-ttu-id="81c97-339">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-339">Meets</span></span> |  <span data-ttu-id="81c97-340">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-340">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="81c97-341">Пользователь никогда не теряет контекст и не может его просматривать.</span><span class="sxs-lookup"><span data-stu-id="81c97-341">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="81c97-342">Для больших объектов предоставляется помощь по контексту.</span><span class="sxs-lookup"><span data-stu-id="81c97-342">Context assistance is provided for large objects.</span></span> <span data-ttu-id="81c97-343">Для объектов за пределами фрейма предоставляется возможность обнаружения и просмотра.</span><span class="sxs-lookup"><span data-stu-id="81c97-343">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="81c97-344">Как правило, проектирование движения и масштабирование голограмм подходят для удобства просмотра.</span><span class="sxs-lookup"><span data-stu-id="81c97-344">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="81c97-345">Пользователь никогда не теряет контекст, но в ограниченных ситуациях может потребоваться дополнительный перенос горловины.</span><span class="sxs-lookup"><span data-stu-id="81c97-345">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="81c97-346">В ограниченных ситуациях масштаб приводит к тому, что голограммы нарушают вертикальную или горизонтальную рамку, что вызывает некоторое движение горловины для просмотра голограмм.</span><span class="sxs-lookup"><span data-stu-id="81c97-346">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="81c97-347">Пользователь, вероятно, потеряет контекст и (или) одинаковое движение горловины необходимо для просмотра голограмм.</span><span class="sxs-lookup"><span data-stu-id="81c97-347">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="81c97-348">Нет руководства по контексту для больших holographic объектов, перемещение объектов, которые легко потерять за пределами рамки без рекомендаций по обнаружению или высоких голограмм, требует регулярного движения горловины для просмотра.</span><span class="sxs-lookup"><span data-stu-id="81c97-348">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="81c97-349">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-349">How to measure</span></span>

* <span data-ttu-id="81c97-350">Контекст для (большой) голограммы потерян или не распознан из-за усечения в границах.</span><span class="sxs-lookup"><span data-stu-id="81c97-350">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="81c97-351">Расположение голограмм трудно найти в связи с отсутствием менеджеров по обучению или содержимым, которое быстро перемещается в holographic кадр и из него.</span><span class="sxs-lookup"><span data-stu-id="81c97-351">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="81c97-352">В сценарии требуется регулярное и повторяющееся движение головного движения, чтобы полностью увидеть голограмму, полученную в результате выносливости горловины.</span><span class="sxs-lookup"><span data-stu-id="81c97-352">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-353">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-353">Recommendations</span></span>

* <span data-ttu-id="81c97-354">Начните работу с небольшими объектами, которые соответствуют фов, а затем переходите с визуальными подсказками в более крупные версии.</span><span class="sxs-lookup"><span data-stu-id="81c97-354">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="81c97-355">Воспользуйтесь пространственными советами и директорами внимания, чтобы помочь пользователям найти содержимое, находящееся за пределами фов.</span><span class="sxs-lookup"><span data-stu-id="81c97-355">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="81c97-356">По возможности старайтесь не использовать голограммы, которые обфовся по вертикали.</span><span class="sxs-lookup"><span data-stu-id="81c97-356">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="81c97-357">Предоставьте пользователю рекомендации в приложении для наилучшего расположения для просмотра.</span><span class="sxs-lookup"><span data-stu-id="81c97-357">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-358">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-358">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="81c97-359">Документация</span><span class="sxs-lookup"><span data-stu-id="81c97-359">Documentation</span></span>

* [<span data-ttu-id="81c97-360">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="81c97-360">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="81c97-361">Пример внедрения, Холостудио пользовательского интерфейса и разработки взаимодействия</span><span class="sxs-lookup"><span data-stu-id="81c97-361">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="81c97-362">Масштабирование объектов и сред</span><span class="sxs-lookup"><span data-stu-id="81c97-362">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="81c97-363">Курсоры, визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="81c97-363">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="81c97-364">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="81c97-364">External references</span></span>

* [<span data-ttu-id="81c97-365">Множество ADO о фов</span><span class="sxs-lookup"><span data-stu-id="81c97-365">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="81c97-366">Содержимое реагирует на расположение пользователя</span><span class="sxs-lookup"><span data-stu-id="81c97-366">Content reacts to user position</span></span>

<span data-ttu-id="81c97-367">Голограммы должны реагировать на пользовательскую точку примерно так же, как и «реальные» объекты.</span><span class="sxs-lookup"><span data-stu-id="81c97-367">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="81c97-368">Важным аспектом разработки являются элементы пользовательского интерфейса, которые не обязательно предполагают, что положение пользователя является стационарным и адаптируется к перемещению пользователя.</span><span class="sxs-lookup"><span data-stu-id="81c97-368">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="81c97-369">Проектирование приложения, которое правильно адаптируется к положению пользователей, приведет к более белиевабленому интерфейсу и упрощению его использования.</span><span class="sxs-lookup"><span data-stu-id="81c97-369">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-370">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-370">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-372"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-373">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-373">✔️</span></span></td>
        <td><span data-ttu-id="81c97-374">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-374">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-375">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-375">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="81c97-376">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-376">Best</span></span> </td><td> <span data-ttu-id="81c97-377">Содержимое и пользовательский интерфейс адаптируются к позициям пользователей, что позволяет пользователю естественным образом взаимодействовать с содержимым в области ожидаемого перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="81c97-377">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="81c97-378">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-378">Meets</span></span> </td><td> <span data-ttu-id="81c97-379">Пользовательский интерфейс адаптируется к положению пользователя, но может препятствовать просмотру содержимого ключа, в соответствии с которым пользователь должен изменить свое расположение.</span><span class="sxs-lookup"><span data-stu-id="81c97-379">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="81c97-380">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-380">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="81c97-381">Элементы пользовательского интерфейса теряются или блокируются во время перемещения, что приводит к неестественному возврату элементов управления (или поиска).</span><span class="sxs-lookup"><span data-stu-id="81c97-381">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="81c97-382">Элементы пользовательского интерфейса ограничивают представление основного содержимого.</span><span class="sxs-lookup"><span data-stu-id="81c97-382">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="81c97-383">Перемещение пользовательского интерфейса не оптимизировано для просмотра расстояния и длительности, особенно с элементами пользовательского интерфейса, основанными на <a href="billboarding-and-tag-along.md">тегах</a> .</span><span class="sxs-lookup"><span data-stu-id="81c97-383">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="81c97-384">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-384">How to measure</span></span>

* <span data-ttu-id="81c97-385">Все измерения должны выполняться в разумной области сценария.</span><span class="sxs-lookup"><span data-stu-id="81c97-385">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="81c97-386">В то время как перемещение пользователя будет разным, не пытайтесь заставить приложение использовать экстремальное перемещение пользователей.</span><span class="sxs-lookup"><span data-stu-id="81c97-386">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="81c97-387">Для элементов пользовательского интерфейса соответствующие элементы управления должны быть доступны независимо от перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="81c97-387">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="81c97-388">Например, если пользователь просматривает трехмерную карту и обходит ее с помощью масштаба, элемент управления масштабом должен быть доступен пользователю независимо от расположения.</span><span class="sxs-lookup"><span data-stu-id="81c97-388">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-389">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-389">Recommendations</span></span>

* <span data-ttu-id="81c97-390">Пользователь является камерой и управляет движением.</span><span class="sxs-lookup"><span data-stu-id="81c97-390">The user is the camera and they control the movement.</span></span> <span data-ttu-id="81c97-391">Позвольте им управлять.</span><span class="sxs-lookup"><span data-stu-id="81c97-391">Let them drive.</span></span>
* <span data-ttu-id="81c97-392">Рассмотрите возможность объявления для систем с текстом и меню, которые в противном случае были бы заблокированы или скрыты, если бы пользователь мог переместиться по всему миру.</span><span class="sxs-lookup"><span data-stu-id="81c97-392">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="81c97-393">Используйте тег для содержимого, которое должно следовать за пользователем, не позволяя пользователю видеть, что находится перед ними.</span><span class="sxs-lookup"><span data-stu-id="81c97-393">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-394">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-394">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="81c97-395">Документация</span><span class="sxs-lookup"><span data-stu-id="81c97-395">Documentation</span></span>

* [<span data-ttu-id="81c97-396">Проектирование взаимодействия</span><span class="sxs-lookup"><span data-stu-id="81c97-396">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="81c97-397">Цвет, освещение и материал</span><span class="sxs-lookup"><span data-stu-id="81c97-397">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="81c97-398">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="81c97-398">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="81c97-399">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="81c97-399">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="81c97-400">Самостоятельное перемещение и локомотион пользователя</span><span class="sxs-lookup"><span data-stu-id="81c97-400">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="81c97-401">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="81c97-401">Tools and tutorials</span></span>

* [<span data-ttu-id="81c97-402">210. Ввод в смешанной реальности: взгляд</span><span class="sxs-lookup"><span data-stu-id="81c97-402">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="81c97-403">Ясность взаимодействия ввода</span><span class="sxs-lookup"><span data-stu-id="81c97-403">Input interaction clarity</span></span>

<span data-ttu-id="81c97-404">Точность входных данных очень важна для удобства использования приложения и включает согласованность входных данных, подход, возможность обнаружения методов взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="81c97-404">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="81c97-405">Пользователь должен иметь возможность использовать общие взаимодействия всей платформы без повторного изучения.</span><span class="sxs-lookup"><span data-stu-id="81c97-405">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="81c97-406">Если приложение имеет пользовательский ввод, оно должно быть четко Отправлено и показано.</span><span class="sxs-lookup"><span data-stu-id="81c97-406">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-407">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-407">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-409"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-410">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-410">✔️</span></span></td>
        <td><span data-ttu-id="81c97-411">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-411">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-412">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-412">Quality criteria</span></span>

|  <span data-ttu-id="81c97-413">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-413">Best</span></span>  |  <span data-ttu-id="81c97-414">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-414">Meets</span></span> |  <span data-ttu-id="81c97-415">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-415">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="81c97-416">Методы взаимодействия ввода согласованы с предоставленными [рекомендациями](interaction-fundamentals.md) Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="81c97-416">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="81c97-417">Любые пользовательские входные данные не должны быть избыточными со стандартным входом (вместо использования стандартного взаимодействия) и должны быть четко переданы и продемонстрированы пользователю.</span><span class="sxs-lookup"><span data-stu-id="81c97-417">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="81c97-418">Похоже на лучшее, но пользовательские входные данные избыточны со стандартными методами ввода.</span><span class="sxs-lookup"><span data-stu-id="81c97-418">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="81c97-419">Пользователь по-прежнему может достигнуть цели и проделать ход работы с приложением.</span><span class="sxs-lookup"><span data-stu-id="81c97-419">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="81c97-420">Трудно понять сопоставление метода ввода или кнопки.</span><span class="sxs-lookup"><span data-stu-id="81c97-420">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="81c97-421">Входные данные сильно настроены, не поддерживают стандартный ввод, не имеют инструкций или, вероятно, не вызывают выносливости и комфортных проблем.</span><span class="sxs-lookup"><span data-stu-id="81c97-421">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="81c97-422">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-422">How to measure</span></span>

* <span data-ttu-id="81c97-423">Приложение использует последовательные [стандартные методы ввода.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="81c97-423">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="81c97-424">Если приложение имеет пользовательский ввод, оно четко взаимодействует с помощью:</span><span class="sxs-lookup"><span data-stu-id="81c97-424">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="81c97-425">Интерфейс первого запуска</span><span class="sxs-lookup"><span data-stu-id="81c97-425">First-run experience</span></span>
* <span data-ttu-id="81c97-426">Начальные экраны</span><span class="sxs-lookup"><span data-stu-id="81c97-426">Introductory screens</span></span>
* <span data-ttu-id="81c97-427">Подсказки</span><span class="sxs-lookup"><span data-stu-id="81c97-427">Tooltips</span></span>
* <span data-ttu-id="81c97-428">Обучение вручную</span><span class="sxs-lookup"><span data-stu-id="81c97-428">Hand coach</span></span>
* <span data-ttu-id="81c97-429">Раздел справки</span><span class="sxs-lookup"><span data-stu-id="81c97-429">Help section</span></span>
* <span data-ttu-id="81c97-430">Голосовое переработку</span><span class="sxs-lookup"><span data-stu-id="81c97-430">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-431">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-431">Recommendations</span></span>

* <span data-ttu-id="81c97-432">По возможности используйте стандартные методы ввода.</span><span class="sxs-lookup"><span data-stu-id="81c97-432">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="81c97-433">Предоставление демонстраций, учебников и подсказок для нестандартных методов ввода.</span><span class="sxs-lookup"><span data-stu-id="81c97-433">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="81c97-434">Используйте согласованную модель взаимодействия во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="81c97-434">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-435">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-435">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="81c97-436">Документация</span><span class="sxs-lookup"><span data-stu-id="81c97-436">Documentation</span></span>

* [<span data-ttu-id="81c97-437">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="81c97-437">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="81c97-438">Взаимодействующие объекты</span><span class="sxs-lookup"><span data-stu-id="81c97-438">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="81c97-439">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="81c97-439">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="81c97-440">Курсоры</span><span class="sxs-lookup"><span data-stu-id="81c97-440">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="81c97-441">Комфорт и взгляните</span><span class="sxs-lookup"><span data-stu-id="81c97-441">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="81c97-442">Жесты</span><span class="sxs-lookup"><span data-stu-id="81c97-442">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="81c97-443">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="81c97-443">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="81c97-444">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="81c97-444">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="81c97-445">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="81c97-445">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="81c97-446">Руководство по переносу логики ввода для Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-446">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="81c97-447">Ввод с клавиатуры в Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-447">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="81c97-448">Взгляд в Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-448">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="81c97-449">Жесты и контроллеры движения в Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-449">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="81c97-450">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-450">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="81c97-451">Ввод с помощью клавиатуры, мыши и контроллера в DirectX</span><span class="sxs-lookup"><span data-stu-id="81c97-451">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="81c97-452">Направление головы и взгляда в DirectX</span><span class="sxs-lookup"><span data-stu-id="81c97-452">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="81c97-453">Контроллеры движения и жестов в DirectX</span><span class="sxs-lookup"><span data-stu-id="81c97-453">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="81c97-454">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="81c97-454">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="81c97-455">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="81c97-455">Tools and tutorials</span></span>

* [<span data-ttu-id="81c97-456">Пример использования: Преимущества дополнительных персональных компьютеров</span><span class="sxs-lookup"><span data-stu-id="81c97-456">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="81c97-457">Исследование приведений: Сведения о разработке пользовательского интерфейса Холостудио и взаимодействия</span><span class="sxs-lookup"><span data-stu-id="81c97-457">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="81c97-458">Пример приложения: Периодическая таблица элементов</span><span class="sxs-lookup"><span data-stu-id="81c97-458">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="81c97-459">Пример приложения: Лунный модуль</span><span class="sxs-lookup"><span data-stu-id="81c97-459">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="81c97-460">210. Ввод в смешанной реальности: взгляд</span><span class="sxs-lookup"><span data-stu-id="81c97-460">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="81c97-461">211. Ввод в смешанной реальности: Жесты</span><span class="sxs-lookup"><span data-stu-id="81c97-461">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="81c97-462">212. Ввод в смешанной реальности: голос</span><span class="sxs-lookup"><span data-stu-id="81c97-462">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="81c97-463">Взаимодействующие объекты</span><span class="sxs-lookup"><span data-stu-id="81c97-463">Interactable objects</span></span>

<span data-ttu-id="81c97-464">Кнопка длиннее метафоры, используемой для активации события в 2D-абстрактном мире.</span><span class="sxs-lookup"><span data-stu-id="81c97-464">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="81c97-465">В мире объемной смешанной реальности мы больше не должны беспокоиться об этом мире абстракции.</span><span class="sxs-lookup"><span data-stu-id="81c97-465">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="81c97-466">Любой может быть взаимодействующим объектом, запускающим событие.</span><span class="sxs-lookup"><span data-stu-id="81c97-466">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="81c97-467">Взаимодействующий объект может быть представлен любым из чашк кофе в таблице в виде всплывающей подсказки, плавающей в воздухе.</span><span class="sxs-lookup"><span data-stu-id="81c97-467">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="81c97-468">Независимо от формы, взаимодействующие объекты должны быть четко распознаны пользователем с помощью визуальных и звуковых подсказок.</span><span class="sxs-lookup"><span data-stu-id="81c97-468">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-469">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-469">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-471"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-472">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-472">✔️</span></span></td>
        <td><span data-ttu-id="81c97-473">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-473">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-474">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-474">Quality criteria</span></span>

|  <span data-ttu-id="81c97-475">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-475">Best</span></span>  |  <span data-ttu-id="81c97-476">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-476">Meets</span></span> |  <span data-ttu-id="81c97-477">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-477">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="81c97-478">Независимо от формы, взаимодействующие объекты распознаются через визуальные и звуковые подсказки в трех состояниях: бездействие, Целевая и выбранная.</span><span class="sxs-lookup"><span data-stu-id="81c97-478">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="81c97-479">«Видите ИТ-подсистемы» — ясно и постоянно используется в ходе работы.</span><span class="sxs-lookup"><span data-stu-id="81c97-479">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="81c97-480">Объекты масштабируются и распределяются для обеспечения бесплатной нацеливания на ошибки.</span><span class="sxs-lookup"><span data-stu-id="81c97-480">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="81c97-481">Пользователь может распознать объект как взаимодействующий через аудио или визуальный отзыв, а также нацелить и активировать объект.</span><span class="sxs-lookup"><span data-stu-id="81c97-481">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="81c97-482">Не имея визуальных или звуковых подсказок, пользователь не сможет распознать взаимодействующий объект.</span><span class="sxs-lookup"><span data-stu-id="81c97-482">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="81c97-483">Взаимодействия могут быть подвержены ошибкам из-за масштабирования объекта или расстояния между объектами.</span><span class="sxs-lookup"><span data-stu-id="81c97-483">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="81c97-484">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-484">How to measure</span></span>

* <span data-ttu-id="81c97-485">Взаимодействующие объекты распознаются как "взаимодействующие"; включая кнопки, меню и содержимое, относящееся к приложению.</span><span class="sxs-lookup"><span data-stu-id="81c97-485">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="81c97-486">Как правило, при нацеливании на взаимодействующие объекты должны быть визуальными и звуковыми подсказками.</span><span class="sxs-lookup"><span data-stu-id="81c97-486">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-487">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-487">Recommendations</span></span>

* <span data-ttu-id="81c97-488">Использование визуальных и звуковых отзывов для взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="81c97-488">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="81c97-489">Визуальная обратная связь должна различаться для каждого входящего состояния (неактивно, назначено, выбрано).</span><span class="sxs-lookup"><span data-stu-id="81c97-489">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="81c97-490">Взаимодействующие объекты должны масштабироваться и размещаться для обеспечения бесплатной нацеливания на ошибки.</span><span class="sxs-lookup"><span data-stu-id="81c97-490">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="81c97-491">Сгруппированные взаимодействующие объекты (например, строка меню или список) должны иметь достаточное пространство для нацеливания.</span><span class="sxs-lookup"><span data-stu-id="81c97-491">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="81c97-492">Кнопки и меню, поддерживающие голосовую команду, должны предоставлять текстовые метки для ключевого слова Command (см. раздел, например, ")".</span><span class="sxs-lookup"><span data-stu-id="81c97-492">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-493">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-493">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="81c97-494">Документация</span><span class="sxs-lookup"><span data-stu-id="81c97-494">Documentation</span></span>

* [<span data-ttu-id="81c97-495">Активный объект</span><span class="sxs-lookup"><span data-stu-id="81c97-495">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="81c97-496">Текст в Unity</span><span class="sxs-lookup"><span data-stu-id="81c97-496">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="81c97-497">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="81c97-497">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="81c97-498">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="81c97-498">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="81c97-499">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="81c97-499">Tools and tutorials</span></span>

* [<span data-ttu-id="81c97-500">Набор средств для смешанной реальности — UX</span><span class="sxs-lookup"><span data-stu-id="81c97-500">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="81c97-501">Сканирование комнаты</span><span class="sxs-lookup"><span data-stu-id="81c97-501">Room scanning</span></span>

<span data-ttu-id="81c97-502">Приложения, для которых требуются данные пространственного сопоставления, полагаются на устройство для автоматического получения этих данных с течением времени и между сеансами по мере того, как пользователь исследует среду с активным устройством.</span><span class="sxs-lookup"><span data-stu-id="81c97-502">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="81c97-503">Полнота и качество этих данных зависит от ряда факторов, в том числе от количества выполненных пользователем проверок, времени, прошедших с момента исследования и того, были ли объекты, такие как мебель и дверцы, перемещены, так как устройство проверило эту область.</span><span class="sxs-lookup"><span data-stu-id="81c97-503">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="81c97-504">Многие приложения анализируют данные пространственного сопоставления в начале работы, чтобы определить, следует ли пользователю выполнять дополнительные действия, чтобы улучшить полноту и качество пространственной карты.</span><span class="sxs-lookup"><span data-stu-id="81c97-504">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="81c97-505">Если пользователь должен проверить окружение, при сканировании необходимо указать четкие рекомендации.</span><span class="sxs-lookup"><span data-stu-id="81c97-505">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-506">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-506">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-508"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-509">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-509">✔️</span></span></td>
        <td><span data-ttu-id="81c97-510">❌</span><span class="sxs-lookup"><span data-stu-id="81c97-510">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-511">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-511">Quality criteria</span></span>

|  <span data-ttu-id="81c97-512">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-512">Best</span></span>  |  <span data-ttu-id="81c97-513">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-513">Meets</span></span> |  <span data-ttu-id="81c97-514">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-514">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="81c97-515">Визуализация пространственной сети указывает, что выполняется проверка пользователей.</span><span class="sxs-lookup"><span data-stu-id="81c97-515">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="81c97-516">Пользователь четко знает, что делать и когда сканирование запускается и останавливается.</span><span class="sxs-lookup"><span data-stu-id="81c97-516">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="81c97-517">Обеспечивается визуализация пространственной сетки, но пользователь может не ясно понять, что делать, а сведения о ходе выполнения не предоставляются.</span><span class="sxs-lookup"><span data-stu-id="81c97-517">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="81c97-518">Отсутствует визуализация сетки.</span><span class="sxs-lookup"><span data-stu-id="81c97-518">No visualization of mesh.</span></span> <span data-ttu-id="81c97-519">Пользователю не предоставлены сведения о том, где искать или когда начинается или останавливается проверка.</span><span class="sxs-lookup"><span data-stu-id="81c97-519">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="81c97-520">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-520">How to measure</span></span>

* <span data-ttu-id="81c97-521">При проверке необходимой комнаты предоставляется визуальное и звуковое руководство, указывающее, где искать, а когда запускать и прекращать сканирование.</span><span class="sxs-lookup"><span data-stu-id="81c97-521">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-522">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-522">Recommendations</span></span>

* <span data-ttu-id="81c97-523">Укажите, какая часть общего объема в области пользователей должна быть частью работы.</span><span class="sxs-lookup"><span data-stu-id="81c97-523">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="81c97-524">Взаимодействие при запуске и остановке сканирования, например индикатор выполнения.</span><span class="sxs-lookup"><span data-stu-id="81c97-524">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="81c97-525">Используйте визуализацию сетки во время сканирования.</span><span class="sxs-lookup"><span data-stu-id="81c97-525">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="81c97-526">Предоставьте визуальные и звуковые подсказки, чтобы дать пользователю возможность просматривать и перемещаться по комнате.</span><span class="sxs-lookup"><span data-stu-id="81c97-526">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="81c97-527">Сообщите пользователю, где можно усовершенствовать данные.</span><span class="sxs-lookup"><span data-stu-id="81c97-527">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="81c97-528">Во многих случаях лучше сообщить пользователю, что нужно сделать (например, Взгляните на центр мебели), чтобы получить необходимое качество сканирования.</span><span class="sxs-lookup"><span data-stu-id="81c97-528">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-529">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-529">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="81c97-530">Документация</span><span class="sxs-lookup"><span data-stu-id="81c97-530">Documentation</span></span>

* [<span data-ttu-id="81c97-531">Визуализация при сканировании комнаты</span><span class="sxs-lookup"><span data-stu-id="81c97-531">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="81c97-532">Пример использования: Расширение возможностей пространственных сопоставлений HoloLens</span><span class="sxs-lookup"><span data-stu-id="81c97-532">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="81c97-533">Пример использования: Конструкция пространственного звука для Холотаур</span><span class="sxs-lookup"><span data-stu-id="81c97-533">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="81c97-534">Пример использования: Создание иммерсивного интерфейса в фрагментах</span><span class="sxs-lookup"><span data-stu-id="81c97-534">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="81c97-535">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="81c97-535">Tools and tutorials</span></span>

* [<span data-ttu-id="81c97-536">Набор средств для смешанной реальности — UX</span><span class="sxs-lookup"><span data-stu-id="81c97-536">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="81c97-537">Индикаторы направления</span><span class="sxs-lookup"><span data-stu-id="81c97-537">Directional indicators</span></span>

<span data-ttu-id="81c97-538">В приложении для смешанной реальности содержимое может находиться за пределами поля View или перекрыто по реальным объектам.</span><span class="sxs-lookup"><span data-stu-id="81c97-538">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="81c97-539">Хорошо спроектированное приложение упростит пользователю поиск невидимого содержимого.</span><span class="sxs-lookup"><span data-stu-id="81c97-539">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="81c97-540">Направленные индикаторы предупреждают пользователя о важном содержимом и предоставляют рекомендации по содержимому относительно положения пользователя.</span><span class="sxs-lookup"><span data-stu-id="81c97-540">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="81c97-541">Руководство по невидимому содержимому может принимать форму звуковых датчиков, стрелок направления или прямых визуальных подсказок.</span><span class="sxs-lookup"><span data-stu-id="81c97-541">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-542">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-542">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-544"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-545">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-545">✔️</span></span></td>
        <td><span data-ttu-id="81c97-546">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-546">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-547">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-547">Quality criteria</span></span>

|  <span data-ttu-id="81c97-548">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-548">Best</span></span>  |  <span data-ttu-id="81c97-549">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-549">Meets</span></span> |  <span data-ttu-id="81c97-550">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-550">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="81c97-551">Визуальные и звуковые подсказки непосредственно позволяют пользователю подходящее содержимое за пределами поля представления.</span><span class="sxs-lookup"><span data-stu-id="81c97-551">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="81c97-552">Стрелка или индикатор, указывающий на пользователя в общем направлении содержимого.</span><span class="sxs-lookup"><span data-stu-id="81c97-552">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="81c97-553">Соответствующее содержимое находится за пределами поля представления, и для пользователя не предоставляется никаких инструкций по расположению.</span><span class="sxs-lookup"><span data-stu-id="81c97-553">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="81c97-554">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-554">How to measure</span></span>

* <span data-ttu-id="81c97-555">Содержимое, соответствующее содержимому за пределами поля "пользователь", может быть обнаружено с помощью визуальных и (или) звуковых подсказок.</span><span class="sxs-lookup"><span data-stu-id="81c97-555">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-556">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-556">Recommendations</span></span>

* <span data-ttu-id="81c97-557">Если соответствующее содержимое находится вне поля зрения пользователя, используйте индикаторы направления и звуковые подсказки для указания пользователю содержимого.</span><span class="sxs-lookup"><span data-stu-id="81c97-557">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="81c97-558">Во многих случаях непосредственное визуальное направляющее предпочтительнее стрелок направления.</span><span class="sxs-lookup"><span data-stu-id="81c97-558">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="81c97-559">Индикаторы направления не должны быть встроены в курсор.</span><span class="sxs-lookup"><span data-stu-id="81c97-559">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-560">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-560">Resources</span></span>

* [<span data-ttu-id="81c97-561">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="81c97-561">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="81c97-562">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="81c97-562">Data loading</span></span>

<span data-ttu-id="81c97-563">Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.</span><span class="sxs-lookup"><span data-stu-id="81c97-563">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="81c97-564">Это может означать, что пользователь не может взаимодействовать с приложением, когда индикатор хода выполнения является видимым, а также может указать, как долго должно быть установлено время ожидания.</span><span class="sxs-lookup"><span data-stu-id="81c97-564">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="81c97-565">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="81c97-565">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81c97-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81c97-567"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="81c97-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81c97-568">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-568">✔️</span></span></td>
        <td><span data-ttu-id="81c97-569">✔️</span><span class="sxs-lookup"><span data-stu-id="81c97-569">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="81c97-570">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="81c97-570">Quality criteria</span></span>

|  <span data-ttu-id="81c97-571">Самое</span><span class="sxs-lookup"><span data-stu-id="81c97-571">Best</span></span>  |  <span data-ttu-id="81c97-572">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="81c97-572">Meets</span></span> |  <span data-ttu-id="81c97-573">Cчетчик</span><span class="sxs-lookup"><span data-stu-id="81c97-573">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="81c97-574">Анимированный визуальный индикатор в виде индикатора выполнения или кольца, отображающий ход выполнения во время загрузки или обработки данных.</span><span class="sxs-lookup"><span data-stu-id="81c97-574">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="81c97-575">Визуальный индикатор предоставляет рекомендации по продолжительности ожидания.</span><span class="sxs-lookup"><span data-stu-id="81c97-575">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="81c97-576">Пользователь уведомляется о том, что выполняется загрузка данных, но нет никакой информации о том, как долго может быть ожидание.</span><span class="sxs-lookup"><span data-stu-id="81c97-576">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="81c97-577">Ни один индикатор загрузки данных или процесса для задачи не занимает более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="81c97-577">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="81c97-578">Как измерять</span><span class="sxs-lookup"><span data-stu-id="81c97-578">How to measure</span></span>

* <span data-ttu-id="81c97-579">Во время загрузки данных убедитесь в отсутствии пустого состояния более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="81c97-579">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="81c97-580">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="81c97-580">Recommendations</span></span>

* <span data-ttu-id="81c97-581">Предоставьте аниматор загрузки данных в любой ситуации, когда пользователь может раскрывать это приложение о зависании или сбое.</span><span class="sxs-lookup"><span data-stu-id="81c97-581">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="81c97-582">Разумное правило для параметра Thumb — это любое действие "Загрузка", которое может занять более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="81c97-582">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="81c97-583">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="81c97-583">Resources</span></span>

* [<span data-ttu-id="81c97-584">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="81c97-584">Displaying progress</span></span>](progress.md)
