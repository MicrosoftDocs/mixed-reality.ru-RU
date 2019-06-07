---
title: Критерии контроля качества приложения
description: В этом документе описываются top факторы, влияющие на качество приложения смешанной реальности.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: критерии контроля качества приложений, смешанной реальности, смешанный реальности
ms.openlocfilehash: dfa1390190fad8d84982171dfbcfa101b20501dc
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750315"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="a7b2d-104">Критерии контроля качества приложения</span><span class="sxs-lookup"><span data-stu-id="a7b2d-104">App quality criteria</span></span>

<span data-ttu-id="a7b2d-105">В этом документе описываются top факторы, влияющие на качество приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="a7b2d-106">Для каждого фактора предоставляется следующая информация</span><span class="sxs-lookup"><span data-stu-id="a7b2d-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="a7b2d-107">Обзор — краткое описание коэффициент качества и почему она важна.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="a7b2d-108">Влияние устройства — это влияет на тип устройства окно смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="a7b2d-109">Критерии качества, как вычислить коэффициент качества.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="a7b2d-110">Как измерить — методы для измерения (или возникнуть) проблема.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="a7b2d-111">Рекомендации — Сводка подходов для повышения удобства работы пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="a7b2d-112">Ресурсы — соответствующие разработчика и ресурсы для разработки, которые полезны для создания лучших результатов приложения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="a7b2d-113">Частота кадров</span><span class="sxs-lookup"><span data-stu-id="a7b2d-113">Frame rate</span></span>

<span data-ttu-id="a7b2d-114">Частота кадров — это главным условием голограмма комфорта стабильность и пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="a7b2d-115">Частота кадров ниже рекомендуемые целевых объектов может привести к голограммы отображаются перебои управления, отрицательно влияет на believability работы и что может привести к усталости глаз.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="a7b2d-116">Частота кадров целевого для работы в Windows Mixed Reality иммерсивную будет либо или 60 Гц 90, в зависимости от того, какие смешанной реальности совместимых компьютеров под управлением Windows, которая должна поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="a7b2d-117">Для HoloLens частота кадров целевого — 60 Гц.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-118">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-120"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-121">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-121">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-122">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-123">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-123">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-124">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-124">Best</span></span>  |  <span data-ttu-id="a7b2d-125">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-125">Meets</span></span> |  <span data-ttu-id="a7b2d-126">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="a7b2d-127">Приложение постоянно соответствует кадров в Вторая цель (кадров/с) для целевого устройства: 60 кадров/с на HoloLens; 90 кадров/с на Ultra компьютеров; и 60 кадров/с на основных компьютерах.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="a7b2d-128">Приложение имеет удаляет временные рамки, не излагает опыт core; или ниже, чем целевое кадров/с, но не влияет на взаимодействие с приложениями.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="a7b2d-129">Приложение наблюдается снижение частоты кадров в среднем каждые десять секунд или менее.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-130">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-130">How to measure</span></span>

* <span data-ttu-id="a7b2d-131">График частота кадров в режиме реального времени предоставляется через [Windows Device Portal](using-the-windows-device-portal.md#system-performance) в разделе «Производительность системы».</span><span class="sxs-lookup"><span data-stu-id="a7b2d-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="a7b2d-132">Для отладки разработки, добавьте счетчик диагностики частота кадров в приложение.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="a7b2d-133">Ознакомьтесь с ресурсами образца счетчика.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="a7b2d-134">Падения частоты кадров может возникать в устройстве во время работы приложения, перемещая голове в сторону.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="a7b2d-135">Если она отображается непредвиденный перебои управления перемещения, затем низкая частота кадров или стабильности плоскости она может вызвать.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-136">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-136">Recommendations</span></span>

* <span data-ttu-id="a7b2d-137">Добавьте счетчик частота кадров в начале процесса разработки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="a7b2d-138">Изменения, которые повлечь Снижение частоты кадров следует вычислить и соответствующим образом равна устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-139">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="a7b2d-140">Документация</span><span class="sxs-lookup"><span data-stu-id="a7b2d-140">Documentation</span></span>

* [<span data-ttu-id="a7b2d-141">Основные сведения о производительности для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="a7b2d-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="a7b2d-142">Голограмма стабильность и частоте кадров</span><span class="sxs-lookup"><span data-stu-id="a7b2d-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="a7b2d-143">Средства производительности в бюджет</span><span class="sxs-lookup"><span data-stu-id="a7b2d-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="a7b2d-144">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="a7b2d-145">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="a7b2d-145">Tools and tutorials</span></span>

* [<span data-ttu-id="a7b2d-146">MRToolkit, отображение счетчика кадров/с</span><span class="sxs-lookup"><span data-stu-id="a7b2d-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="a7b2d-147">MRToolkit, шейдеры</span><span class="sxs-lookup"><span data-stu-id="a7b2d-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="a7b2d-148">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-148">External references</span></span>

* [<span data-ttu-id="a7b2d-149">Unity, оптимизация приложений для мобильных устройств</span><span class="sxs-lookup"><span data-stu-id="a7b2d-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="a7b2d-150">Голограмма стабильность</span><span class="sxs-lookup"><span data-stu-id="a7b2d-150">Hologram stability</span></span>

<span data-ttu-id="a7b2d-151">Стабильные голограммы повысить удобство использования и believability приложения и создавать более комфортную работу Просмотр для пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="a7b2d-152">Качество голограмма стабильности является результатом хорошее приложение разработки, а также возможность устройства понять (отслеживание) его среды.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="a7b2d-153">Частота кадров является главным условием стабильность, другие факторы могут повлиять на стабильность включая:</span><span class="sxs-lookup"><span data-stu-id="a7b2d-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="a7b2d-154">Использование плоскости стабилизации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="a7b2d-155">Расстояние до пространственных привязки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="a7b2d-156">Отслеживание</span><span class="sxs-lookup"><span data-stu-id="a7b2d-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-157">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-159"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-160">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-160">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-161">❌</span><span class="sxs-lookup"><span data-stu-id="a7b2d-161">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-162">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-162">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-163">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-163">Best</span></span>  |  <span data-ttu-id="a7b2d-164">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-164">Meets</span></span> |  <span data-ttu-id="a7b2d-165">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-165">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="a7b2d-166">Голограммы постоянно появляются стабильной.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-166">Holograms consistently appear stable.</span></span> | <span data-ttu-id="a7b2d-167">Вторичный содержимое характеризуется Непредвиденная перемещения; или Непредвиденная перемещения не страдает работы всего приложения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-167">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="a7b2d-168">Основного содержимого в кадре характеризуется Непредвиденная перемещения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-168">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-169">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-169">How to measure</span></span>

<span data-ttu-id="a7b2d-170">Хотя наши устройства и условия для просмотра:</span><span class="sxs-lookup"><span data-stu-id="a7b2d-170">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="a7b2d-171">Переместить головой из стороны в сторону, если голограммы двигаться Непредвиденная затем низкая частота кадров или вероятной причиной является неправильное выравнивание стабильности плоскости на плоскости.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-171">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="a7b2d-172">Перемещение по голограммы и среды, обратите внимание на поведение, например различных и jumpiness.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="a7b2d-173">Этот тип движения, скорее всего связано с устройства, не отслеживая среды или расстояние для привязки пространственных.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="a7b2d-174">При большом или нескольких голограммы во фрейме, наблюдать за поведением голограмма в различные глубины, хотя перемещение на вашей головной позицию в сторону, если shakiness отображается, это может вызвано стабилизации плоскости.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="a7b2d-175">Recomendations</span><span class="sxs-lookup"><span data-stu-id="a7b2d-175">Recomendations</span></span>

* <span data-ttu-id="a7b2d-176">Добавьте счетчик частота кадров в начале процесса разработки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-176">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="a7b2d-177">С помощью стабилизации плоскости.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="a7b2d-178">Всегда выводить привязанного голограммы в трех ваттметров их привязки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="a7b2d-179">Убедитесь, что ваша среда настроена для правильного отслеживания.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-179">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="a7b2d-180">Проектирование работы во избежание голограммы на различных уровнях фокальной глубины внутри фрейма.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-181">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="a7b2d-182">Документация</span><span class="sxs-lookup"><span data-stu-id="a7b2d-182">Documentation</span></span>

* [<span data-ttu-id="a7b2d-183">Голограмма стабильность и частоте кадров</span><span class="sxs-lookup"><span data-stu-id="a7b2d-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="a7b2d-184">Пример использования можно с помощью плоскости стабилизации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="a7b2d-185">Основные сведения о производительности для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="a7b2d-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="a7b2d-186">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-186">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="a7b2d-187">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-187">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="a7b2d-188">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="a7b2d-188">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="a7b2d-189">Стационарной системой отсчета координат</span><span class="sxs-lookup"><span data-stu-id="a7b2d-189">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="a7b2d-190">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="a7b2d-190">Tools and tutorials</span></span>

* [<span data-ttu-id="a7b2d-191">Набор MR Companion, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="a7b2d-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="a7b2d-192">Позиция голограммы на реальных поверхностях</span><span class="sxs-lookup"><span data-stu-id="a7b2d-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="a7b2d-193">Misalignments из голограммы с физические объекты (если предполагается располагаться относительно друг друга) становится понятно из относящихся к объединениям голограммы и реального мира.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="a7b2d-194">Точность размещение должен указываться относительно потребностями сценария; например общие поверхности размещения можно использовать Пространственные карты, но более точного размещения потребует некоторых использование маркеров и калибровки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-195">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-197"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-198">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-198">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-199">❌</span><span class="sxs-lookup"><span data-stu-id="a7b2d-199">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-200">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-200">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-201">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-201">Best</span></span>  |  <span data-ttu-id="a7b2d-202">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-202">Meets</span></span> |  <span data-ttu-id="a7b2d-203">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-203">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="a7b2d-204">Голограммы выровнять область обычно сантиметры диапазон дюймов.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-204">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="a7b2d-205">Если требуется более высокой точностью, приложение должно предоставляет эффективные средства для совместной работы в рамках спецификации нужное приложение.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-205">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="a7b2d-206">Н/Д</span><span class="sxs-lookup"><span data-stu-id="a7b2d-206">NA</span></span> | <span data-ttu-id="a7b2d-207">Голограммы отображаются невыровненных с физической целевой объект критические поверхности плоскости или на число с плавающей запятой от рабочей области.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-207">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="a7b2d-208">Если требуется точность, голограммы должна соответствовать спецификации выражение с учетом сценария.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-208">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-209">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-209">How to measure</span></span>

* <span data-ttu-id="a7b2d-210">Не должны отображаться голограммы, помещенные на карте Пространственные значительно плавать выше или ниже области.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-210">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="a7b2d-211">Голограммы, требующие размещения точных должны иметь определенные виды маркера и калибровки система, округленное до требования сценария.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-211">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-212">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-212">Recommendations</span></span>

* <span data-ttu-id="a7b2d-213">Пространственные карты удобен для помещения объектов на поверхностях, при точности не требуется.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-213">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="a7b2d-214">Для наиболее точности, маркеры плакаты для задания используется или голограммы и контроллера Xbox (или какой-либо механизм вручную выравнивание) для окончательного калибровки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-214">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="a7b2d-215">Рассмотрите возможность разбиения очень большой голограммы на логические части и выравнивание каждая часть в область.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-215">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="a7b2d-216">Неправильно interpupilary расстоянии (IPD) также влияет на выравнивание голограмма.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-216">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="a7b2d-217">Всегда настраивайте HoloLens в IPD пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-217">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-218">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-218">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="a7b2d-219">Документация</span><span class="sxs-lookup"><span data-stu-id="a7b2d-219">Documentation</span></span>

* [<span data-ttu-id="a7b2d-220">Размещение пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="a7b2d-220">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="a7b2d-221">Место выполнения сканирования</span><span class="sxs-lookup"><span data-stu-id="a7b2d-221">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="a7b2d-222">Рекомендации по использованию пространственных привязки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-222">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="a7b2d-223">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="a7b2d-223">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="a7b2d-224">Пространственное сопоставление в Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-224">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="a7b2d-225">Общие сведения о разработке Vuforia</span><span class="sxs-lookup"><span data-stu-id="a7b2d-225">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="a7b2d-226">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="a7b2d-226">Tools and tutorials</span></span>

* [<span data-ttu-id="a7b2d-227">230. Пространство в смешанной реальности: пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="a7b2d-227">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="a7b2d-228">Набор MR средств, библиотек пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="a7b2d-228">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="a7b2d-229">Комплект Companion MR, пример плакат калибровки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-229">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="a7b2d-230">Набор MR Companion, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="a7b2d-230">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="a7b2d-231">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-231">External references</span></span>

* [<span data-ttu-id="a7b2d-232">Практический пример Lowes, выравнивание точности</span><span class="sxs-lookup"><span data-stu-id="a7b2d-232">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="a7b2d-233">Просмотр зоны комфорта</span><span class="sxs-lookup"><span data-stu-id="a7b2d-233">Viewing zone of comfort</span></span>

<span data-ttu-id="a7b2d-234">Где сходятся глаза пользователей путем размещения содержимого и голограммы в различные глубины управления для разработчиков приложений.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-234">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="a7b2d-235">Пользователи, то HoloLens будет всегда рассчитан на работу до 2.0m для поддержания понятность изображения так, как отображаются HoloLens фиксируются на расстоянии оптические около 2.0m от пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-235">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="a7b2d-236">Неправильная глубины может привести к visual discomfort или усталости.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-236">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-237">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-237">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-239"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-240">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-240">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-241">❌</span><span class="sxs-lookup"><span data-stu-id="a7b2d-241">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-242">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-242">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="a7b2d-243">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-243">Best</span></span> </td><td><ul>
<li><span data-ttu-id="a7b2d-244">Вставка содержимого 2 МБ.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-244">Place content at 2m.</span></span></li><li><span data-ttu-id="a7b2d-245">Голограммы нельзя разместить в 2 МБ и не избежать конфликтов между конвергенции и услуги размещения, оптимальной зоны для размещения голограмма при между 1,25 m и 5 мин.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-245">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="a7b2d-246">В каждом случае конструкторы требуемую структуру для содержимого, чтобы рекомендовать пользователям взаимодействовать 1 + m нет на месте (например размер содержимого, и по умолчанию параметры размещения).</span><span class="sxs-lookup"><span data-stu-id="a7b2d-246">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="a7b2d-247">Если специально не требуется в сценарии, плоскости отсечения следует реализовать с помощью fadeout, начиная с 1 млн.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-247">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="a7b2d-248">В случаях, где требуется подробное наблюдение за над голограмма содержимое должно быть не более чем 50cm.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-248">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="a7b2d-249">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-249">Meets</span></span></td><td> <span data-ttu-id="a7b2d-250">Содержимое находится в пределах движения и просматривать рекомендации, но неправильное использование или use плоскости отсечения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-250">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a7b2d-251">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-251">Fail</span></span> </td><td> <span data-ttu-id="a7b2d-252">Содержимое представляется слишком близко (обычно &lt;1,25 m, или &lt;50 cm для стационарных голограммы, требуя ближе наблюдения.)</span><span class="sxs-lookup"><span data-stu-id="a7b2d-252">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-253">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-253">How to measure</span></span>

* <span data-ttu-id="a7b2d-254">Содержимого обычно нужно 2 МБ размещения, но не ближе чем 1,25 или дальше, чем в 5 мин.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-254">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="a7b2d-255">За некоторыми исключениями расстояние отрисовки обрезки HoloLens должно быть присвоено .85CM с fadeout содержимого, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-255">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="a7b2d-256">Подход содержимое и обратите внимание на результат плоскости отсечения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-256">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="a7b2d-257">Стационарные содержимое не должно быть ближе, чем от 50cm.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-257">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-258">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-258">Recommendations</span></span>

* <span data-ttu-id="a7b2d-259">Разрабатывать содержимое для оптимального просмотра расстояние до 2 МБ.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-259">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="a7b2d-260">Значение расстояния отрисовки обрезки 85cm с fadeout содержимого, начиная с 1 млн.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-260">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="a7b2d-261">Стационарные голограммы, которые должны ближе Просмотр плоскости отсечения должна быть не ближе чем 30cm а fadeout следует запустить по крайней мере 10cm от плоскости отсечения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-261">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-262">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-262">Resources</span></span>

* [<span data-ttu-id="a7b2d-263">Визуализации расстояния</span><span class="sxs-lookup"><span data-stu-id="a7b2d-263">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="a7b2d-264">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-264">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="a7b2d-265">Поэкспериментировав с масштабом</span><span class="sxs-lookup"><span data-stu-id="a7b2d-265">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="a7b2d-266">Текст, размер шрифта рекомендуется</span><span class="sxs-lookup"><span data-stu-id="a7b2d-266">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="a7b2d-267">Переключение глубины</span><span class="sxs-lookup"><span data-stu-id="a7b2d-267">Depth switching</span></span>

<span data-ttu-id="a7b2d-268">Независимо от просмотра зоны комфорта проблем практически, а также гораздо фокальной объекты (включая голограммы и реальных содержимое) может привести к oculomotor усталости и общие discomfort требует пользователю переключаться между часто или быстро.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-268">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-269">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-269">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-271"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-272">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-272">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-273">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-273">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-274">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-274">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-275">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-275">Best</span></span>  |  <span data-ttu-id="a7b2d-276">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-276">Meets</span></span> |  <span data-ttu-id="a7b2d-277">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-277">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="a7b2d-278">Ограниченные или обеспечения естественного глубины, переключение не вызывает пользователю unnaturally изменения фокуса.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-278">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="a7b2d-279">Резкое глубины коммутатора core и масштабируемости взаимодействие с приложениями, или внезапные глубины коммутатора, вызванное Непредвиденное содержимое в реальных условиях.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-279">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="a7b2d-280">Согласованные глубины коммутатора, или неожиданном глубины переключения, не является обязательным или core взаимодействие с приложениями.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-280">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-281">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-281">How to measure</span></span>

* <span data-ttu-id="a7b2d-282">Если приложению требуется пользователю постоянно и/или резко изменять глубину фокус, нет глубины, переключение проблему.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-282">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-283">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-283">Recommendations</span></span>

* <span data-ttu-id="a7b2d-284">Оставьте основного содержимого в согласованное плоскости и обеспечить соответствие плоскости стабилизации плоскости.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-284">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="a7b2d-285">Это позволит устранить oculomotor усталости и Непредвиденная голограмма перемещения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-285">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-286">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-286">Resources</span></span>

* [<span data-ttu-id="a7b2d-287">Визуализации расстояния</span><span class="sxs-lookup"><span data-stu-id="a7b2d-287">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="a7b2d-288">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-288">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="a7b2d-289">Использование пространственных звука</span><span class="sxs-lookup"><span data-stu-id="a7b2d-289">Use of spatial sound</span></span>

<span data-ttu-id="a7b2d-290">В Windows Mixed Reality ядро аудио предоставляет звукового компонента работы смешанной реальности, имитируя 3D звука с помощью направление, расстояние и моделирование окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-290">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="a7b2d-291">Использование пространственных звука в приложении позволяет разработчикам convincingly поместите звуков в 3 мерном пространстве (сфера) по всему пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-291">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="a7b2d-292">Затем эти звуки покажется так, как если бы они поступали от физического объектов или голограммы смешанной реальности в окружения пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-292">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="a7b2d-293">Пространственные звук — это мощное средство для общения, доступности и проектирование взаимодействия с Пользователем в приложениях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-293">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-294">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-294">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-296"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-297">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-297">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-298">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-298">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-299">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-299">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-300">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-300">Best</span></span>  |  <span data-ttu-id="a7b2d-301">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-301">Meets</span></span> |  <span data-ttu-id="a7b2d-302">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-302">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="a7b2d-303">Звук будет логически spatialized и UX соответствующим образом использует звук для помощи с объект обнаружения и сбора отзывов.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-303">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="a7b2d-304">Звук естественным и относящиеся к объектам и нормализованное через сценарий.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-304">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="a7b2d-305">Пространственные аудио используется соответствующим образом для believability, но отсутствующие в качестве средства для облегчения отзывы пользователей и возможность обнаружения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-305">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="a7b2d-306">Звук не является spatialized, как и ожидалось, и/или отсутствие звука для помощи пользователю в UI.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-306">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="a7b2d-307">Или пространственных аудио был не рассматривались или применялись в разработке сценария.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-307">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-308">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-308">How to measure</span></span>

* <span data-ttu-id="a7b2d-309">В общем случае должен выдавать соответствующие звуков из целевой голограммы (например:., звуков bark от holographic dog.)</span><span class="sxs-lookup"><span data-stu-id="a7b2d-309">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="a7b2d-310">Чтобы помочь пользователю оставить отзывы или осведомленности в области действий вне holographic рамки можно использовать звуковые сигналы на протяжении всего пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-310">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-311">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-311">Recommendations</span></span>

* <span data-ttu-id="a7b2d-312">Используйте Пространственные аудио для помощи с объект обнаружения и пользовательских интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-312">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="a7b2d-313">Реальные звуки работают лучше, чем синтеза или понятном и естественном звук.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-313">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="a7b2d-314">Должен быть spatialized большинства звуков.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-314">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="a7b2d-315">Избегайте невидимым отправители.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-315">Avoid invisible emitters.</span></span>
* <span data-ttu-id="a7b2d-316">Избегайте пространственных маски.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-316">Avoid spatial masking.</span></span>
* <span data-ttu-id="a7b2d-317">Нормализация все звуки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-317">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-318">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-318">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="a7b2d-319">Документация</span><span class="sxs-lookup"><span data-stu-id="a7b2d-319">Documentation</span></span>

* [<span data-ttu-id="a7b2d-320">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="a7b2d-320">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="a7b2d-321">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="a7b2d-321">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="a7b2d-322">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-322">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="a7b2d-323">Пример использования, звук для HoloTour пространственный индекс</span><span class="sxs-lookup"><span data-stu-id="a7b2d-323">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="a7b2d-324">Пример использования можно с помощью пространственных звук в RoboRaid</span><span class="sxs-lookup"><span data-stu-id="a7b2d-324">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="a7b2d-325">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="a7b2d-325">Tools and tutorials</span></span>

* [<span data-ttu-id="a7b2d-326">220. Пространство в смешанной реальности: пространственный звук</span><span class="sxs-lookup"><span data-stu-id="a7b2d-326">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="a7b2d-327">MRToolkit пространственных аудио</span><span class="sxs-lookup"><span data-stu-id="a7b2d-327">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="a7b2d-328">Сосредоточиться на границы holographic фрейма (FOV)</span><span class="sxs-lookup"><span data-stu-id="a7b2d-328">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="a7b2d-329">Хорошо спроектированный взаимодействия с пользователями можно создать и обслуживать полезный контекст виртуальной среды, который расширяет о пользователях.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-329">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="a7b2d-330">Сдерживание последствия границы FOV включает в себя продуманный разработки содержимого масштаба и контекста, использование пространственных аудио-, руководство по системам и положение пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-330">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="a7b2d-331">Если попросить правильно, он будет считаете, что меньше ограничено границами FOV во время работы приложения с уверенно.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-331">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-332">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-332">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-334"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-335">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-335">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-336">❌</span><span class="sxs-lookup"><span data-stu-id="a7b2d-336">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-337">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-337">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-338">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-338">Best</span></span>  |  <span data-ttu-id="a7b2d-339">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-339">Meets</span></span> |  <span data-ttu-id="a7b2d-340">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-340">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="a7b2d-341">Пользователь никогда не теряет контекста и ознакомившись просмотра.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-341">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="a7b2d-342">Контекст помощь предоставляется для больших объектов.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-342">Context assistance is provided for large objects.</span></span> <span data-ttu-id="a7b2d-343">Возможность обнаружения и просмотр руководство предоставляется для объектов вне рамки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-343">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="a7b2d-344">Как правило конструктор перемещения и масштаб голограммы подходят для прекрасные впечатления от просмотра.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-344">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="a7b2d-345">Пользователь никогда не теряет контекст, но дополнительные горлышка движения может потребоваться в ограниченных ситуациях.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-345">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="a7b2d-346">В ограниченных ситуациях масштабирования вызывает голограммы прервать либо вызывает некоторые виды движений шея просмотреть голограммы кадр вертикальной или горизонтальной.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-346">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="a7b2d-347">Для просмотра голограммы необходим пользователь скорее всего, потерять контекста и/или согласованное шея движения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-347">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="a7b2d-348">Нет контекста рекомендаций для больших объектов holographic перемещения объектов легко потерять вне рамки без возможности обнаружения рекомендации или высоту голограммы требует регулярного шея движения для просмотра.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-348">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-349">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-349">How to measure</span></span>

* <span data-ttu-id="a7b2d-350">Контекст для (крупный) голограмма потерян или не распознан из-за были усечены на границах.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-350">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="a7b2d-351">Расположение голограммы не удается найти из-за отсутствия директоров внимания или содержимое, которое быстро перемещает и из него holographic кадра.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-351">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="a7b2d-352">Сценарий требует обычные и повторяющиеся вверх и вниз головной движение, чтобы полностью см. в разделе голограмма, приводит к усталости шея.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-352">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-353">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-353">Recommendations</span></span>

* <span data-ttu-id="a7b2d-354">Начните работу с небольших объектов, которые соответствуют FOV, то переход с визуальные подсказки для больших версий.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-354">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="a7b2d-355">Используйте Пространственные директоров аудио- и внимания для поиска содержимого пользователя, которое находится за пределами FOV.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-355">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="a7b2d-356">Насколько возможно Избегайте голограммы, по вертикали обрезать FOV.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-356">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="a7b2d-357">Предоставьте пользователю с указаниями в приложении для удобства просмотра расположение.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-357">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-358">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-358">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="a7b2d-359">Документация</span><span class="sxs-lookup"><span data-stu-id="a7b2d-359">Documentation</span></span>

* [<span data-ttu-id="a7b2d-360">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="a7b2d-360">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="a7b2d-361">Пример использования, HoloStudio пользовательского интерфейса и полученные данные разработки для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a7b2d-361">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="a7b2d-362">Масштабирование объектов и сред</span><span class="sxs-lookup"><span data-stu-id="a7b2d-362">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="a7b2d-363">Курсоры, визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-363">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="a7b2d-364">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-364">External references</span></span>

* [<span data-ttu-id="a7b2d-365">FOV «Шумиха» ado</span><span class="sxs-lookup"><span data-stu-id="a7b2d-365">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="a7b2d-366">Содержимое реагирует на позиции пользователя</span><span class="sxs-lookup"><span data-stu-id="a7b2d-366">Content reacts to user position</span></span>

<span data-ttu-id="a7b2d-367">Голограммы должен реагировать на них положение пользователя примерно теми же способами, сделать «реальные» объекты.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-367">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="a7b2d-368">Важное соображение — элементы пользовательского интерфейса, нельзя рассчитывать обязательно пользователя позиции мыши останавливается и адаптироваться к перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-368">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="a7b2d-369">Разработка приложения, которое правильно адаптируется к позиции пользователя более проверите работы и упростить использование.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-369">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-370">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-370">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-372"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-373">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-373">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-374">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-374">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-375">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-375">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="a7b2d-376">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-376">Best</span></span> </td><td> <span data-ttu-id="a7b2d-377">Содержимое и пользовательского интерфейса адаптироваться к должности пользователя, позволяя пользователю естественным образом взаимодействуют с содержимым в пределах ожидаемого числа пользователей перемещения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-377">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a7b2d-378">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-378">Meets</span></span> </td><td> <span data-ttu-id="a7b2d-379">Пользовательский Интерфейс адаптируется к позиции пользователя, но может препятствовать представление ключа содержимого, требующее от пользователя для изменения их положения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-379">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a7b2d-380">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-380">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="a7b2d-381">Элементы пользовательского интерфейса при утере или заблокирован во время перемещения вызывающие пользователю unnaturally вернуться к (или найти) элементов управления.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-381">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="a7b2d-382">Элементы пользовательского интерфейса ограничить представление основного содержимого.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-382">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="a7b2d-383">Перемещение пользовательского интерфейса не оптимизировано для просмотра расстояние и импульса, особенно при работе с <a href="billboarding-and-tag-along.md">tag-along</a> элементы пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-383">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-384">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-384">How to measure</span></span>

* <span data-ttu-id="a7b2d-385">Все измерения должны выполняться в пределах разумного области сценария.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-385">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="a7b2d-386">Во время перемещения пользователя, могут меняться, не следует пытаться обмануть приложения с перемещением extreme пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-386">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="a7b2d-387">Для элементов пользовательского интерфейса соответствующие элементы управления должны быть доступны вне зависимости от перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-387">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="a7b2d-388">К примеру Если пользователь Просмотр и прогулке по трехмерной карты с zoom, элемент управления масштабом должны быть легко доступна пользователю независимо от их расположения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-388">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-389">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-389">Recommendations</span></span>

* <span data-ttu-id="a7b2d-390">Пользователь является камеры, и они управляют перемещение.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-390">The user is the camera and they control the movement.</span></span> <span data-ttu-id="a7b2d-391">Let их диска.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-391">Let them drive.</span></span>
* <span data-ttu-id="a7b2d-392">Рассмотрим биллбординга для текста и были перелета систем, которые в противном случае будет быть заблокирован мира или закрыты, если пользователь для перемещения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-392">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="a7b2d-393">Используйте tag-along для содержимого, которое должен выполнить пользователь по-прежнему предоставляя пользователю видеть, что такое перед их.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-393">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-394">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-394">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="a7b2d-395">Документация</span><span class="sxs-lookup"><span data-stu-id="a7b2d-395">Documentation</span></span>

* [<span data-ttu-id="a7b2d-396">Разработка взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a7b2d-396">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="a7b2d-397">Цвет света и материал</span><span class="sxs-lookup"><span data-stu-id="a7b2d-397">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="a7b2d-398">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="a7b2d-398">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a7b2d-399">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="a7b2d-399">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="a7b2d-400">Самостоятельно движения и locomotion пользователя</span><span class="sxs-lookup"><span data-stu-id="a7b2d-400">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="a7b2d-401">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="a7b2d-401">Tools and tutorials</span></span>

* [<span data-ttu-id="a7b2d-402">210. Ввод в смешанной реальности: взгляд</span><span class="sxs-lookup"><span data-stu-id="a7b2d-402">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="a7b2d-403">Ясности входной взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a7b2d-403">Input interaction clarity</span></span>

<span data-ttu-id="a7b2d-404">Входной взаимодействия ясности критично для удобства использования приложения и включает в себя входные согласованности, approachability, возможность обнаружения методы взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-404">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="a7b2d-405">Пользователь должен иметь возможность использовать распространенные взаимодействия всей платформы без relearning.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-405">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="a7b2d-406">Если приложение имеет пользовательским вводом, он должен четко оценить и подтвердить.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-406">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-407">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-407">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-409"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-410">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-410">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-411">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-411">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-412">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-412">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-413">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-413">Best</span></span>  |  <span data-ttu-id="a7b2d-414">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-414">Meets</span></span> |  <span data-ttu-id="a7b2d-415">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-415">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="a7b2d-416">Методы ввода interaction согласованы с Windows Mixed Reality предоставленные [рекомендации](interaction-fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="a7b2d-416">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="a7b2d-417">Любой пользовательским вводом не нужно дублировать с помощью стандартного ввода (вместо использования взаимодействия со стандартной) и должны четко оценить и подтвердить для пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-417">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="a7b2d-418">С помощью стандартных методов ввода избыточны аналогичен рекомендации, но пользовательских входных данных.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-418">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="a7b2d-419">Пользователь по-прежнему возможна, цель и ход процесса при помощи взаимодействие с приложениями.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-419">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="a7b2d-420">Сложны для понимания входной сопоставление метода или кнопки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-420">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="a7b2d-421">Входные данные серьезную пользовательскую настройку, не поддерживает стандартный ввод каких-либо указаний, или может вызвать проблемы усталости и комфорта.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-421">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-422">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-422">How to measure</span></span>

* <span data-ttu-id="a7b2d-423">Приложение использует согласованную [standard входные данные методы.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="a7b2d-423">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="a7b2d-424">Если приложение имеет входные данные заказчиков, очевидно, что передается через:</span><span class="sxs-lookup"><span data-stu-id="a7b2d-424">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="a7b2d-425">При первом запуске</span><span class="sxs-lookup"><span data-stu-id="a7b2d-425">First-run experience</span></span>
* <span data-ttu-id="a7b2d-426">Вводные экранов</span><span class="sxs-lookup"><span data-stu-id="a7b2d-426">Introductory screens</span></span>
* <span data-ttu-id="a7b2d-427">Подсказки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-427">Tooltips</span></span>
* <span data-ttu-id="a7b2d-428">Советы от руки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-428">Hand coach</span></span>
* <span data-ttu-id="a7b2d-429">Раздел справки</span><span class="sxs-lookup"><span data-stu-id="a7b2d-429">Help section</span></span>
* <span data-ttu-id="a7b2d-430">Голосовая связь через</span><span class="sxs-lookup"><span data-stu-id="a7b2d-430">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-431">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-431">Recommendations</span></span>

* <span data-ttu-id="a7b2d-432">Используйте стандартные методы ввода, когда это возможно.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-432">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="a7b2d-433">Укажите демонстрации, учебники и подсказки для нестандартных методов ввода.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-433">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="a7b2d-434">Используйте модель согласованное взаимодействие в приложении.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-434">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-435">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-435">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="a7b2d-436">Документация</span><span class="sxs-lookup"><span data-stu-id="a7b2d-436">Documentation</span></span>

* [<span data-ttu-id="a7b2d-437">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="a7b2d-437">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="a7b2d-438">Элементом объектов</span><span class="sxs-lookup"><span data-stu-id="a7b2d-438">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="a7b2d-439">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="a7b2d-439">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="a7b2d-440">Курсоры</span><span class="sxs-lookup"><span data-stu-id="a7b2d-440">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a7b2d-441">Комфорт и взглядом</span><span class="sxs-lookup"><span data-stu-id="a7b2d-441">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="a7b2d-442">Жесты</span><span class="sxs-lookup"><span data-stu-id="a7b2d-442">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="a7b2d-443">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="a7b2d-443">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="a7b2d-444">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="a7b2d-444">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="a7b2d-445">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="a7b2d-445">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="a7b2d-446">Руководство по переносу логики ввода для Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-446">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="a7b2d-447">Ввод с клавиатуры в Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-447">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="a7b2d-448">Взгляд в Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-448">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="a7b2d-449">Жесты и контроллеры движения в Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-449">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="a7b2d-450">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-450">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="a7b2d-451">Ввод с помощью клавиатуры, мыши и контроллера в DirectX</span><span class="sxs-lookup"><span data-stu-id="a7b2d-451">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="a7b2d-452">Направление головы и взгляда в DirectX</span><span class="sxs-lookup"><span data-stu-id="a7b2d-452">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="a7b2d-453">Контроллеры движения и жестов в DirectX</span><span class="sxs-lookup"><span data-stu-id="a7b2d-453">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="a7b2d-454">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="a7b2d-454">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="a7b2d-455">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="a7b2d-455">Tools and tutorials</span></span>

* [<span data-ttu-id="a7b2d-456">Пример внедрения: Для достижения более персональных компьютерах</span><span class="sxs-lookup"><span data-stu-id="a7b2d-456">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="a7b2d-457">Приведен пример использования: Пользовательский Интерфейс HoloStudio и полученные данные разработки для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a7b2d-457">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="a7b2d-458">Пример приложения. Периодическая таблица элементов</span><span class="sxs-lookup"><span data-stu-id="a7b2d-458">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="a7b2d-459">Пример приложения. Модуль лунного</span><span class="sxs-lookup"><span data-stu-id="a7b2d-459">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="a7b2d-460">210. Ввод в смешанной реальности: взгляд</span><span class="sxs-lookup"><span data-stu-id="a7b2d-460">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="a7b2d-461">211. Ввод в смешанной реальности: Жесты</span><span class="sxs-lookup"><span data-stu-id="a7b2d-461">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="a7b2d-462">212. Ввод в смешанной реальности: голос</span><span class="sxs-lookup"><span data-stu-id="a7b2d-462">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="a7b2d-463">Элементом объектов</span><span class="sxs-lookup"><span data-stu-id="a7b2d-463">Interactable objects</span></span>

<span data-ttu-id="a7b2d-464">Кнопка уже давно метафоры, вызывающих срабатывание события в мире двухмерной абстрактным.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-464">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="a7b2d-465">В мире трехмерного смешанной реальности мы не нужно ограничиваться мире больше абстракции.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-465">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="a7b2d-466">Что-то может быть элементом объект, который запускает событие.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-466">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="a7b2d-467">Объект элементом может быть представлено как что-либо из чашку кофе в таблице для всплывающей с плавающей запятой в воздухе.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-467">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="a7b2d-468">Независимо от формы элементом объектов должно быть ясно узнаваемые пользователем с помощью звуковые и подсказки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-468">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-469">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-469">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-471"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-472">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-472">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-473">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-473">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-474">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-474">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-475">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-475">Best</span></span>  |  <span data-ttu-id="a7b2d-476">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-476">Meets</span></span> |  <span data-ttu-id="a7b2d-477">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-477">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="a7b2d-478">Независимо от формы, элементом объектов содержит понятные через звуковые и подсказок для трех состояний: простаивает, целевые и выбран.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-478">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="a7b2d-479">«Кажется, скажите» очистить и постоянно используется работы.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-479">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="a7b2d-480">Объекты масштабируются и распределенных для нацеливания без ошибок.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-480">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="a7b2d-481">Пользователей можно распознать объект как элементом с помощью обратной связи аудио- или visual и могут целевой и активировать объект.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-481">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="a7b2d-482">Учитывая нет подсказок visual или аудио, пользователь не может распознать элементом объекта.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-482">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="a7b2d-483">Взаимодействия являются ошибками из-за масштаба объекта или расстояние между объектами.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-483">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-484">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-484">How to measure</span></span>

* <span data-ttu-id="a7b2d-485">Элементом объекты являются распознаются как «элементом»; включая кнопки, меню и приложение конкретного содержимого.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-485">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="a7b2d-486">Как правило должно быть звуковые и подсказки при нацеливании элементом объектов.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-486">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-487">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-487">Recommendations</span></span>

* <span data-ttu-id="a7b2d-488">Используйте звуковые и обратной связи для взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-488">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="a7b2d-489">Визуальную обратную связь должно отличаться для каждого входного состояния (простоя, целевых, выбранных)</span><span class="sxs-lookup"><span data-stu-id="a7b2d-489">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="a7b2d-490">Элементом объектов следует масштабировать и для нацеливания без ошибок.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-490">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="a7b2d-491">Сгруппированные объекты элементом (например, в строке меню или список) должны иметь нужный интервал для нацеливания.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-491">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="a7b2d-492">Кнопки и меню, которые поддерживают голосовых команд должен предоставлять текстовые метки для ключевого слова команды («см. в разделе, он, скажите»)</span><span class="sxs-lookup"><span data-stu-id="a7b2d-492">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-493">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-493">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="a7b2d-494">Документация</span><span class="sxs-lookup"><span data-stu-id="a7b2d-494">Documentation</span></span>

* [<span data-ttu-id="a7b2d-495">Активный объект</span><span class="sxs-lookup"><span data-stu-id="a7b2d-495">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a7b2d-496">Текст в Unity</span><span class="sxs-lookup"><span data-stu-id="a7b2d-496">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="a7b2d-497">Панель приложения и ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="a7b2d-497">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a7b2d-498">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="a7b2d-498">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="a7b2d-499">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="a7b2d-499">Tools and tutorials</span></span>

* [<span data-ttu-id="a7b2d-500">Набор средств для смешанной реальности - UX</span><span class="sxs-lookup"><span data-stu-id="a7b2d-500">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="a7b2d-501">Сканирование комнаты</span><span class="sxs-lookup"><span data-stu-id="a7b2d-501">Room scanning</span></span>

<span data-ttu-id="a7b2d-502">Приложения, которым требуются пространственное сопоставление данных полагаться на устройстве, чтобы автоматически собирать эти данные со временем и во всех сеансах, как пользователь изучает их среды с устройством active.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-502">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="a7b2d-503">Полноты и качества этих данных зависит от ряда факторов, включая количество исследований, которые пользователь выполнит, сколько времени прошло с момента просмотра и ли объекты, такие как мебель и двери были перемещены, так как устройство сканирования области.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-503">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="a7b2d-504">Во многих приложениях проанализирует пространственное сопоставление данных в начале работы, имела ли пользователь должен выполнить дополнительные действия для повышения качества пространственных карты и полноты.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-504">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="a7b2d-505">Если пользователь является необходимым условием для поиска в среду, очевидно, что рекомендации, которые необходимо указать во время сканирования.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-505">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-506">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-506">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-508"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-509">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-509">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-510">❌</span><span class="sxs-lookup"><span data-stu-id="a7b2d-510">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-511">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-511">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-512">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-512">Best</span></span>  |  <span data-ttu-id="a7b2d-513">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-513">Meets</span></span> |  <span data-ttu-id="a7b2d-514">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-514">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="a7b2d-515">Визуализация пространственных сетки сообщить, что пользователи сканирование выполняется.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-515">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="a7b2d-516">Пользователь, безусловно, известна, что делать, и когда сканирование начинается и останавливается.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-516">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="a7b2d-517">Визуализации пространственных сетки предоставляется, но пользователь может не знать четко что делать, и предоставляется без сведений о ходе выполнения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-517">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="a7b2d-518">Нет визуализации сетки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-518">No visualization of mesh.</span></span> <span data-ttu-id="a7b2d-519">Нет рекомендации сведений, предоставленных пользователю сведения о область поиска, или при сканировании запускает или останавливает.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-519">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-520">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-520">How to measure</span></span>

* <span data-ttu-id="a7b2d-521">Во время проверки необходимых комнаты звуковые и указаний, указывающее, где искать и время запуска и остановки сканирования.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-521">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-522">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-522">Recommendations</span></span>

* <span data-ttu-id="a7b2d-523">Указывает, сколько всего тома окружающими пользователей должен быть частью работы.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-523">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="a7b2d-524">Взаимодействия при сканировании начинается и останавливается например индикатор хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-524">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="a7b2d-525">Используйте визуализации сетки во время проверки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-525">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="a7b2d-526">Укажите звуковые и подсказки для пользователя, чтобы выглядеть и перемещать комнате.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-526">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="a7b2d-527">Сообщения куда обратиться, чтобы улучшить данные.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-527">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="a7b2d-528">Во многих случаях, возможно, следует сообщить пользователю, какие возможности нужны (например Обратите внимание на округление вверх, просмотрите за мебель), чтобы получить необходимые проверки качества.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-528">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-529">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-529">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="a7b2d-530">Документация</span><span class="sxs-lookup"><span data-stu-id="a7b2d-530">Documentation</span></span>

* [<span data-ttu-id="a7b2d-531">Визуализация при сканировании комнаты</span><span class="sxs-lookup"><span data-stu-id="a7b2d-531">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="a7b2d-532">Пример внедрения: Расширение пространственных сопоставление возможности HoloLens</span><span class="sxs-lookup"><span data-stu-id="a7b2d-532">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="a7b2d-533">Пример внедрения: Пространственные систему для HoloTour</span><span class="sxs-lookup"><span data-stu-id="a7b2d-533">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="a7b2d-534">Пример внедрения: Создание присутствия в фрагментов</span><span class="sxs-lookup"><span data-stu-id="a7b2d-534">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="a7b2d-535">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="a7b2d-535">Tools and tutorials</span></span>

* [<span data-ttu-id="a7b2d-536">Набор средств для смешанной реальности - UX</span><span class="sxs-lookup"><span data-stu-id="a7b2d-536">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="a7b2d-537">Направления индикаторы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-537">Directional indicators</span></span>

<span data-ttu-id="a7b2d-538">В приложении смешанной реальности содержимое может находиться за пределами поле зрения или перекрыто объектами реального мира.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-538">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="a7b2d-539">Хорошо спроектированные приложения упростит для пользователя для поиска без видимого содержимого.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-539">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="a7b2d-540">Индикаторы направления предупреждения пользователя важное содержимое и советы для содержимого относительно его положения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-540">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="a7b2d-541">Рекомендации, которые не видимого содержимого может принимать форму звуковой отправители, направленными стрелками или прямой визуальные подсказки.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-541">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-542">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-542">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-544"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-545">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-545">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-546">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-546">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-547">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-547">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-548">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-548">Best</span></span>  |  <span data-ttu-id="a7b2d-549">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-549">Meets</span></span> |  <span data-ttu-id="a7b2d-550">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-550">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="a7b2d-551">Звуковые и подсказки непосредственно помочь пользователю для соответствующего содержимого вне поля зрения.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-551">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="a7b2d-552">Стрелка или некоторые индикатор, который указывает пользователь в общее направление содержимого.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-552">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="a7b2d-553">Соответствующее содержимое находится вне поля зрения и низкая или нет расположение указаний для пользователя.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-553">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-554">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-554">How to measure</span></span>

* <span data-ttu-id="a7b2d-555">Соответствующее содержимое за пределами поле зрения пользователя обнаружить с помощью подсказок visual и/или аудиоданных.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-555">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-556">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-556">Recommendations</span></span>

* <span data-ttu-id="a7b2d-557">Необходимое содержимое, находится вне поля зрения пользователя, используйте направления индикаторы и звуковые эффекты для пользователя к содержимому.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-557">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="a7b2d-558">Во многих случаях прямой визуальную подсказку предпочтительнее направленными стрелками.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-558">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="a7b2d-559">Направления индикаторы не должен быть построен в курсор.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-559">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-560">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-560">Resources</span></span>

* [<span data-ttu-id="a7b2d-561">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="a7b2d-561">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="a7b2d-562">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="a7b2d-562">Data loading</span></span>

<span data-ttu-id="a7b2d-563">Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-563">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="a7b2d-564">Это может означать, что пользователь не может взаимодействовать с приложением, когда индикатор хода выполнения отображается, а также можно указать, сколько может быть время ожидания.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-564">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="a7b2d-565">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="a7b2d-565">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7b2d-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a7b2d-567"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7b2d-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7b2d-568">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-568">✔️</span></span></td>
        <td><span data-ttu-id="a7b2d-569">✔️</span><span class="sxs-lookup"><span data-stu-id="a7b2d-569">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="a7b2d-570">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="a7b2d-570">Quality criteria</span></span>

|  <span data-ttu-id="a7b2d-571">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-571">Best</span></span>  |  <span data-ttu-id="a7b2d-572">Соответствует</span><span class="sxs-lookup"><span data-stu-id="a7b2d-572">Meets</span></span> |  <span data-ttu-id="a7b2d-573">Сбой</span><span class="sxs-lookup"><span data-stu-id="a7b2d-573">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="a7b2d-574">Анимированный визуальный индикатор, в виде индикатор хода выполнения или кольца, отображая ход выполнения во время загрузки и обработки любых данных.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-574">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="a7b2d-575">Визуальный индикатор приведены инструкции по время ожидания может быть.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-575">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="a7b2d-576">Пользователю сообщается, что загрузка данных выполняется, но нет никаких признаков того, как долго может быть время ожидания.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-576">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="a7b2d-577">Загрузка данных ни индикаторы процесса для задачи, более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-577">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="a7b2d-578">Как измерить</span><span class="sxs-lookup"><span data-stu-id="a7b2d-578">How to measure</span></span>

* <span data-ttu-id="a7b2d-579">Во время загрузки данных убедитесь, что имеется пустое состояние не более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-579">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="a7b2d-580">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="a7b2d-580">Recommendations</span></span>

* <span data-ttu-id="a7b2d-581">Укажите animator загрузки данных, отображая ход выполнения в любой ситуации, когда пользователь может заметить это приложение остановлено или произошел сбой.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-581">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="a7b2d-582">Разумное правило — это любое действие «загрузка», которое может занять более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-582">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="a7b2d-583">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a7b2d-583">Resources</span></span>

* [<span data-ttu-id="a7b2d-584">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="a7b2d-584">Displaying progress</span></span>](progress.md)
