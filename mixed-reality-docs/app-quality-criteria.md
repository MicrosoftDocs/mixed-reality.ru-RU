---
title: Критерии контроля качества приложения
description: В этом документе описываются top факторы, влияющие на качество приложения смешанной реальности.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: критерии контроля качества приложений, смешанной реальности, смешанный реальности
ms.openlocfilehash: 756bc148f290aa3406c9ac8bb7003d463c62772c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974742"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="8c8bc-104">Критерии контроля качества приложения</span><span class="sxs-lookup"><span data-stu-id="8c8bc-104">App quality criteria</span></span>

<span data-ttu-id="8c8bc-105">В этом документе описываются top факторы, влияющие на качество приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="8c8bc-106">Для каждого фактора предоставляется следующая информация</span><span class="sxs-lookup"><span data-stu-id="8c8bc-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="8c8bc-107">Обзор — краткое описание коэффициент качества и почему она важна.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="8c8bc-108">Влияние устройства — это влияет на тип устройства окно смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="8c8bc-109">Критерии качества, как вычислить коэффициент качества.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="8c8bc-110">Как измерить — методы для измерения (или возникнуть) проблема.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="8c8bc-111">Рекомендации — Сводка подходов для повышения удобства работы пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="8c8bc-112">Ресурсы — соответствующие разработчика и ресурсы для разработки, которые полезны для создания лучших результатов приложения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="8c8bc-113">Частота кадров</span><span class="sxs-lookup"><span data-stu-id="8c8bc-113">Frame rate</span></span>

<span data-ttu-id="8c8bc-114">Частота кадров — это главным условием голограмма комфорта стабильность и пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="8c8bc-115">Частота кадров ниже рекомендуемые целевых объектов может привести к голограммы отображаются перебои управления, отрицательно влияет на believability работы и что может привести к усталости глаз.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="8c8bc-116">Частота кадров целевого для работы в Windows Mixed Reality иммерсивную будет либо или 60 Гц 90, в зависимости от того, какие смешанной реальности совместимых компьютеров под управлением Windows, которая должна поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="8c8bc-117">Для HoloLens частота кадров целевого — 60 Гц.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-118">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-118">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-120"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-121">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-121">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c8bc-122">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-122">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-123">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-123">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-124">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-124">Best</span></span>  |  <span data-ttu-id="8c8bc-125">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-125">Meets</span></span> |  <span data-ttu-id="8c8bc-126">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="8c8bc-127">Приложение постоянно соответствует кадров в Вторая цель (кадров/с) для целевого устройства: 60 кадров/с на HoloLens; 90 кадров/с на Ultra компьютеров; и 60 кадров/с на основных компьютерах.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="8c8bc-128">Приложение имеет удаляет временные рамки, не излагает опыт core; или ниже, чем целевое кадров/с, но не влияет на взаимодействие с приложениями.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="8c8bc-129">Приложение наблюдается снижение частоты кадров в среднем каждые десять секунд или менее.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-130">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-130">How to measure</span></span>

* <span data-ttu-id="8c8bc-131">График частота кадров в режиме реального времени предоставляется через [Windows Device Portal](using-the-windows-device-portal.md#system-performance) в разделе «Производительность системы».</span><span class="sxs-lookup"><span data-stu-id="8c8bc-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="8c8bc-132">Для отладки разработки, добавьте счетчик диагностики частота кадров в приложение.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="8c8bc-133">Ознакомьтесь с ресурсами образца счетчика.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="8c8bc-134">Падения частоты кадров может возникать в устройстве во время работы приложения, перемещая голове в сторону.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="8c8bc-135">Если она отображается непредвиденный перебои управления перемещения, затем низкая частота кадров или стабильности плоскости она может вызвать.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-136">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-136">Recommendations</span></span>

* <span data-ttu-id="8c8bc-137">Добавьте счетчик частота кадров в начале процесса разработки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="8c8bc-138">Изменения, которые повлечь Снижение частоты кадров следует вычислить и соответствующим образом равна устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-139">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8c8bc-140">Документация</span><span class="sxs-lookup"><span data-stu-id="8c8bc-140">Documentation</span></span>

* [<span data-ttu-id="8c8bc-141">Основные сведения о производительности для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="8c8bc-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="8c8bc-142">Голограмма стабильность и частоте кадров</span><span class="sxs-lookup"><span data-stu-id="8c8bc-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="8c8bc-143">Средства производительности в бюджет</span><span class="sxs-lookup"><span data-stu-id="8c8bc-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="8c8bc-144">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8c8bc-145">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="8c8bc-145">Tools and tutorials</span></span>

* [<span data-ttu-id="8c8bc-146">MRToolkit, отображение счетчика кадров/с</span><span class="sxs-lookup"><span data-stu-id="8c8bc-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="8c8bc-147">MRToolkit, шейдеры</span><span class="sxs-lookup"><span data-stu-id="8c8bc-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="8c8bc-148">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-148">External references</span></span>

* [<span data-ttu-id="8c8bc-149">Unity, оптимизация приложений для мобильных устройств</span><span class="sxs-lookup"><span data-stu-id="8c8bc-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="8c8bc-150">Голограмма стабильность</span><span class="sxs-lookup"><span data-stu-id="8c8bc-150">Hologram stability</span></span>

<span data-ttu-id="8c8bc-151">Стабильные голограммы повысить удобство использования и believability приложения и создавать более комфортную работу Просмотр для пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="8c8bc-152">Качество голограмма стабильности является результатом хорошее приложение разработки, а также возможность устройства понять (отслеживание) его среды.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="8c8bc-153">Частота кадров является главным условием стабильность, другие факторы могут повлиять на стабильность включая:</span><span class="sxs-lookup"><span data-stu-id="8c8bc-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="8c8bc-154">Использование плоскости стабилизации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="8c8bc-155">Расстояние до пространственных привязки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="8c8bc-156">Отслеживание</span><span class="sxs-lookup"><span data-stu-id="8c8bc-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-157">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-157">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-158"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-158"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-159"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-159"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-160">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-160">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-161">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-161">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-162">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-162">Best</span></span>  |  <span data-ttu-id="8c8bc-163">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-163">Meets</span></span> |  <span data-ttu-id="8c8bc-164">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8c8bc-165">Голограммы постоянно появляются стабильной.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="8c8bc-166">Вторичный содержимое характеризуется Непредвиденная перемещения; или Непредвиденная перемещения не страдает работы всего приложения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="8c8bc-167">Основного содержимого в кадре характеризуется Непредвиденная перемещения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-168">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-168">How to measure</span></span>

<span data-ttu-id="8c8bc-169">Хотя наши устройства и условия для просмотра:</span><span class="sxs-lookup"><span data-stu-id="8c8bc-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="8c8bc-170">Переместить головой из стороны в сторону, если голограммы двигаться Непредвиденная затем низкая частота кадров или вероятной причиной является неправильное выравнивание стабильности плоскости на плоскости.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="8c8bc-171">Перемещение по голограммы и среды, обратите внимание на поведение, например различных и jumpiness.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="8c8bc-172">Этот тип движения, скорее всего связано с устройства, не отслеживая среды или расстояние для привязки пространственных.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="8c8bc-173">При большом или нескольких голограммы во фрейме, наблюдать за поведением голограмма в различные глубины, хотя перемещение на вашей головной позицию в сторону, если shakiness отображается, это может вызвано стабилизации плоскости.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="8c8bc-174">Recomendations</span><span class="sxs-lookup"><span data-stu-id="8c8bc-174">Recomendations</span></span>

* <span data-ttu-id="8c8bc-175">Добавьте счетчик частота кадров в начале процесса разработки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="8c8bc-176">С помощью стабилизации плоскости.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="8c8bc-177">Всегда выводить привязанного голограммы в трех ваттметров их привязки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="8c8bc-178">Убедитесь, что ваша среда настроена для правильного отслеживания.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="8c8bc-179">Проектирование работы во избежание голограммы на различных уровнях фокальной глубины внутри фрейма.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-180">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8c8bc-181">Документация</span><span class="sxs-lookup"><span data-stu-id="8c8bc-181">Documentation</span></span>

* [<span data-ttu-id="8c8bc-182">Голограмма стабильность и частоте кадров</span><span class="sxs-lookup"><span data-stu-id="8c8bc-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="8c8bc-183">Пример использования можно с помощью плоскости стабилизации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="8c8bc-184">Основные сведения о производительности для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="8c8bc-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="8c8bc-185">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="8c8bc-186">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="8c8bc-187">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="8c8bc-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="8c8bc-188">Стационарной системой отсчета координат</span><span class="sxs-lookup"><span data-stu-id="8c8bc-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8c8bc-189">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="8c8bc-189">Tools and tutorials</span></span>

* [<span data-ttu-id="8c8bc-190">Набор MR Companion, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="8c8bc-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="8c8bc-191">Позиция голограммы на реальных поверхностях</span><span class="sxs-lookup"><span data-stu-id="8c8bc-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="8c8bc-192">Misalignments из голограммы с физические объекты (если предполагается располагаться относительно друг друга) становится понятно из относящихся к объединениям голограммы и реального мира.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="8c8bc-193">Точность размещение должен указываться относительно потребностями сценария; например общие поверхности размещения можно использовать Пространственные карты, но более точного размещения потребует некоторых использование маркеров и калибровки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-194">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-194">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-195"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-195"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-196"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-196"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-197">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-197">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-198">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-198">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-199">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-199">Best</span></span>  |  <span data-ttu-id="8c8bc-200">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-200">Meets</span></span> |  <span data-ttu-id="8c8bc-201">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="8c8bc-202">Голограммы выровнять область обычно сантиметры диапазон дюймов.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="8c8bc-203">Если требуется более высокой точностью, приложение должно предоставляет эффективные средства для совместной работы в рамках спецификации нужное приложение.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="8c8bc-204">Н/Д</span><span class="sxs-lookup"><span data-stu-id="8c8bc-204">NA</span></span> | <span data-ttu-id="8c8bc-205">Голограммы отображаются невыровненных с физической целевой объект критические поверхности плоскости или на число с плавающей запятой от рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="8c8bc-206">Если требуется точность, голограммы должна соответствовать спецификации выражение с учетом сценария.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-207">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-207">How to measure</span></span>

* <span data-ttu-id="8c8bc-208">Не должны отображаться голограммы, помещенные на карте Пространственные значительно плавать выше или ниже области.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="8c8bc-209">Голограммы, требующие размещения точных должны иметь определенные виды маркера и калибровки система, округленное до требования сценария.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-210">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-210">Recommendations</span></span>

* <span data-ttu-id="8c8bc-211">Пространственные карты удобен для помещения объектов на поверхностях, при точности не требуется.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="8c8bc-212">Для наиболее точности, маркеры плакаты для задания используется или голограммы и контроллера Xbox (или какой-либо механизм вручную выравнивание) для окончательного калибровки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="8c8bc-213">Рассмотрите возможность разбиения очень большой голограммы на логические части и выравнивание каждая часть в область.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="8c8bc-214">Неправильно interpupilary расстоянии (IPD) также влияет на выравнивание голограмма.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="8c8bc-215">Всегда настраивайте HoloLens в IPD пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-216">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8c8bc-217">Документация</span><span class="sxs-lookup"><span data-stu-id="8c8bc-217">Documentation</span></span>

* [<span data-ttu-id="8c8bc-218">Размещение пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="8c8bc-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="8c8bc-219">Место выполнения сканирования</span><span class="sxs-lookup"><span data-stu-id="8c8bc-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="8c8bc-220">Рекомендации по использованию пространственных привязки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="8c8bc-221">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="8c8bc-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="8c8bc-222">Пространственное сопоставление в Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="8c8bc-223">Общие сведения о разработке Vuforia</span><span class="sxs-lookup"><span data-stu-id="8c8bc-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8c8bc-224">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="8c8bc-224">Tools and tutorials</span></span>

* [<span data-ttu-id="8c8bc-225">230. Пространство в смешанной реальности: пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="8c8bc-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="8c8bc-226">Набор MR средств, библиотек пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="8c8bc-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="8c8bc-227">Комплект Companion MR, пример плакат калибровки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="8c8bc-228">Набор MR Companion, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="8c8bc-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="8c8bc-229">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-229">External references</span></span>

* [<span data-ttu-id="8c8bc-230">Практический пример Lowes, выравнивание точности</span><span class="sxs-lookup"><span data-stu-id="8c8bc-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="8c8bc-231">Просмотр зоны комфорта</span><span class="sxs-lookup"><span data-stu-id="8c8bc-231">Viewing zone of comfort</span></span>

<span data-ttu-id="8c8bc-232">Где сходятся глаза пользователей путем размещения содержимого и голограммы в различные глубины управления для разработчиков приложений.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="8c8bc-233">Пользователи, то HoloLens будет всегда рассчитан на работу до 2.0m для поддержания понятность изображения так, как отображаются HoloLens фиксируются на расстоянии оптические около 2.0m от пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="8c8bc-234">Неправильная глубины может привести к visual discomfort или усталости.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-235">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-235">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-236"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-236"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-237"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-237"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-238">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-238">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-239">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="8c8bc-240">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="8c8bc-241">Вставка содержимого 2 МБ.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-241">Place content at 2m.</span></span></li><li><span data-ttu-id="8c8bc-242">Голограммы нельзя разместить в 2 МБ и не избежать конфликтов между конвергенции и услуги размещения, оптимальной зоны для размещения голограмма при между 1,25 m и 5 мин.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="8c8bc-243">В каждом случае конструкторы требуемую структуру для содержимого, чтобы рекомендовать пользователям взаимодействовать 1 + m нет на месте (например размер содержимого, и по умолчанию параметры размещения).</span><span class="sxs-lookup"><span data-stu-id="8c8bc-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="8c8bc-244">Если специально не требуется в сценарии, плоскости отсечения следует реализовать с помощью fadeout, начиная с 1 млн.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="8c8bc-245">В случаях, где требуется подробное наблюдение за над голограмма содержимое должно быть не более чем 50cm.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="8c8bc-246">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-246">Meets</span></span></td><td> <span data-ttu-id="8c8bc-247">Содержимое находится в пределах движения и просматривать рекомендации, но неправильное использование или use плоскости отсечения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8c8bc-248">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-248">Fail</span></span> </td><td> <span data-ttu-id="8c8bc-249">Содержимое представляется слишком близко (обычно &lt;1,25 m, или &lt;50 cm для стационарных голограммы, требуя ближе наблюдения.)</span><span class="sxs-lookup"><span data-stu-id="8c8bc-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-250">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-250">How to measure</span></span>

* <span data-ttu-id="8c8bc-251">Содержимого обычно нужно 2 МБ размещения, но не ближе чем 1,25 или дальше, чем в 5 мин.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="8c8bc-252">За некоторыми исключениями расстояние отрисовки обрезки HoloLens должно быть присвоено .85CM с fadeout содержимого, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="8c8bc-253">Подход содержимое и обратите внимание на результат плоскости отсечения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="8c8bc-254">Стационарные содержимое не должно быть ближе, чем от 50cm.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-255">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-255">Recommendations</span></span>

* <span data-ttu-id="8c8bc-256">Разрабатывать содержимое для оптимального просмотра расстояние до 2 МБ.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="8c8bc-257">Значение расстояния отрисовки обрезки 85cm с fadeout содержимого, начиная с 1 млн.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="8c8bc-258">Стационарные голограммы, которые должны ближе Просмотр плоскости отсечения должна быть не ближе чем 30cm а fadeout следует запустить по крайней мере 10cm от плоскости отсечения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-259">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-259">Resources</span></span>

* [<span data-ttu-id="8c8bc-260">Визуализации расстояния</span><span class="sxs-lookup"><span data-stu-id="8c8bc-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="8c8bc-261">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="8c8bc-262">Поэкспериментировав с масштабом</span><span class="sxs-lookup"><span data-stu-id="8c8bc-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="8c8bc-263">Текст, размер шрифта рекомендуется</span><span class="sxs-lookup"><span data-stu-id="8c8bc-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="8c8bc-264">Переключение глубины</span><span class="sxs-lookup"><span data-stu-id="8c8bc-264">Depth switching</span></span>

<span data-ttu-id="8c8bc-265">Независимо от просмотра зоны комфорта проблем практически, а также гораздо фокальной объекты (включая голограммы и реальных содержимое) может привести к oculomotor усталости и общие discomfort требует пользователю переключаться между часто или быстро.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-266">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-266">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-267"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-267"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-268"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-268"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-269">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-269">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c8bc-270">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-270">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-271">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-271">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-272">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-272">Best</span></span>  |  <span data-ttu-id="8c8bc-273">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-273">Meets</span></span> |  <span data-ttu-id="8c8bc-274">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8c8bc-275">Ограниченные или обеспечения естественного глубины, переключение не вызывает пользователю unnaturally изменения фокуса.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="8c8bc-276">Резкое глубины коммутатора core и масштабируемости взаимодействие с приложениями, или внезапные глубины коммутатора, вызванное Непредвиденное содержимое в реальных условиях.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="8c8bc-277">Согласованные глубины коммутатора, или неожиданном глубины переключения, не является обязательным или core взаимодействие с приложениями.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-278">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-278">How to measure</span></span>

* <span data-ttu-id="8c8bc-279">Если приложению требуется пользователю постоянно и/или резко изменять глубину фокус, нет глубины, переключение проблему.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-280">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-280">Recommendations</span></span>

* <span data-ttu-id="8c8bc-281">Оставьте основного содержимого в согласованное плоскости и обеспечить соответствие плоскости стабилизации плоскости.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="8c8bc-282">Это позволит устранить oculomotor усталости и Непредвиденная голограмма перемещения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-283">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-283">Resources</span></span>

* [<span data-ttu-id="8c8bc-284">Визуализации расстояния</span><span class="sxs-lookup"><span data-stu-id="8c8bc-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="8c8bc-285">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="8c8bc-286">Использование пространственных звука</span><span class="sxs-lookup"><span data-stu-id="8c8bc-286">Use of spatial sound</span></span>

<span data-ttu-id="8c8bc-287">В Windows Mixed Reality ядро аудио предоставляет звукового компонента работы смешанной реальности, имитируя 3D звука с помощью направление, расстояние и моделирование окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="8c8bc-288">Использование пространственных звука в приложении позволяет разработчикам convincingly поместите звуков в 3 мерном пространстве (сфера) по всему пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="8c8bc-289">Затем эти звуки покажется так, как если бы они поступали от физического объектов или голограммы смешанной реальности в окружения пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="8c8bc-290">Пространственные звук — это мощное средство для общения, доступности и проектирование взаимодействия с Пользователем в приложениях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-291">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-291">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-292"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-292"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-293"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-293"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-294">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-294">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c8bc-295">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-295">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-296">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-296">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-297">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-297">Best</span></span>  |  <span data-ttu-id="8c8bc-298">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-298">Meets</span></span> |  <span data-ttu-id="8c8bc-299">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8c8bc-300">Звук будет логически spatialized и UX соответствующим образом использует звук для помощи с объект обнаружения и сбора отзывов.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="8c8bc-301">Звук естественным и относящиеся к объектам и нормализованное через сценарий.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="8c8bc-302">Пространственные аудио используется соответствующим образом для believability, но отсутствующие в качестве средства для облегчения отзывы пользователей и возможность обнаружения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="8c8bc-303">Звук не является spatialized, как и ожидалось, и/или отсутствие звука для помощи пользователю в UI.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="8c8bc-304">Или пространственных аудио был не рассматривались или применялись в разработке сценария.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-305">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-305">How to measure</span></span>

* <span data-ttu-id="8c8bc-306">В общем случае должен выдавать соответствующие звуков из целевой голограммы (например:., звуков bark от holographic dog.)</span><span class="sxs-lookup"><span data-stu-id="8c8bc-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="8c8bc-307">Чтобы помочь пользователю оставить отзывы или осведомленности в области действий вне holographic рамки можно использовать звуковые сигналы на протяжении всего пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-308">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-308">Recommendations</span></span>

* <span data-ttu-id="8c8bc-309">Используйте Пространственные аудио для помощи с объект обнаружения и пользовательских интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="8c8bc-310">Реальные звуки работают лучше, чем синтеза или понятном и естественном звук.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="8c8bc-311">Должен быть spatialized большинства звуков.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="8c8bc-312">Избегайте невидимым отправители.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="8c8bc-313">Избегайте пространственных маски.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="8c8bc-314">Нормализация все звуки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-315">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8c8bc-316">Документация</span><span class="sxs-lookup"><span data-stu-id="8c8bc-316">Documentation</span></span>

* [<span data-ttu-id="8c8bc-317">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="8c8bc-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="8c8bc-318">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="8c8bc-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="8c8bc-319">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="8c8bc-320">Пример использования, звук для HoloTour пространственный индекс</span><span class="sxs-lookup"><span data-stu-id="8c8bc-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="8c8bc-321">Пример использования можно с помощью пространственных звук в RoboRaid</span><span class="sxs-lookup"><span data-stu-id="8c8bc-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8c8bc-322">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="8c8bc-322">Tools and tutorials</span></span>

* [<span data-ttu-id="8c8bc-323">220. Пространство в смешанной реальности: пространственный звук</span><span class="sxs-lookup"><span data-stu-id="8c8bc-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="8c8bc-324">MRToolkit пространственных аудио</span><span class="sxs-lookup"><span data-stu-id="8c8bc-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="8c8bc-325">Сосредоточиться на границы holographic фрейма (FOV)</span><span class="sxs-lookup"><span data-stu-id="8c8bc-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="8c8bc-326">Хорошо спроектированный взаимодействия с пользователями можно создать и обслуживать полезный контекст виртуальной среды, который расширяет о пользователях.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="8c8bc-327">Сдерживание последствия границы FOV включает в себя продуманный разработки содержимого масштаба и контекста, использование пространственных аудио-, руководство по системам и положение пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="8c8bc-328">Если попросить правильно, он будет считаете, что меньше ограничено границами FOV во время работы приложения с уверенно.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-329">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-329">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-330"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-330"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-331"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-331"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-332">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-332">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-333">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-333">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-334">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-334">Best</span></span>  |  <span data-ttu-id="8c8bc-335">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-335">Meets</span></span> |  <span data-ttu-id="8c8bc-336">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8c8bc-337">Пользователь никогда не теряет контекста и ознакомившись просмотра.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="8c8bc-338">Контекст помощь предоставляется для больших объектов.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="8c8bc-339">Возможность обнаружения и просмотр руководство предоставляется для объектов вне рамки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="8c8bc-340">Как правило конструктор перемещения и масштаб голограммы подходят для прекрасные впечатления от просмотра.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="8c8bc-341">Пользователь никогда не теряет контекст, но дополнительные горлышка движения может потребоваться в ограниченных ситуациях.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="8c8bc-342">В ограниченных ситуациях масштабирования вызывает голограммы прервать либо вызывает некоторые виды движений шея просмотреть голограммы кадр вертикальной или горизонтальной.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="8c8bc-343">Для просмотра голограммы необходим пользователь скорее всего, потерять контекста и/или согласованное шея движения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="8c8bc-344">Нет контекста рекомендаций для больших объектов holographic перемещения объектов легко потерять вне рамки без возможности обнаружения рекомендации или высоту голограммы требует регулярного шея движения для просмотра.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-345">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-345">How to measure</span></span>

* <span data-ttu-id="8c8bc-346">Контекст для (крупный) голограмма потерян или не распознан из-за были усечены на границах.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="8c8bc-347">Расположение голограммы не удается найти из-за отсутствия директоров внимания или содержимое, которое быстро перемещает и из него holographic кадра.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="8c8bc-348">Сценарий требует обычные и повторяющиеся вверх и вниз головной движение, чтобы полностью см. в разделе голограмма, приводит к усталости шея.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-349">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-349">Recommendations</span></span>

* <span data-ttu-id="8c8bc-350">Начните работу с небольших объектов, которые соответствуют FOV, то переход с визуальные подсказки для больших версий.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="8c8bc-351">Используйте Пространственные директоров аудио- и внимания для поиска содержимого пользователя, которое находится за пределами FOV.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="8c8bc-352">Насколько возможно Избегайте голограммы, по вертикали обрезать FOV.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="8c8bc-353">Предоставьте пользователю с указаниями в приложении для удобства просмотра расположение.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-354">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8c8bc-355">Документация</span><span class="sxs-lookup"><span data-stu-id="8c8bc-355">Documentation</span></span>

* [<span data-ttu-id="8c8bc-356">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="8c8bc-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="8c8bc-357">Пример использования, HoloStudio пользовательского интерфейса и полученные данные разработки для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="8c8bc-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="8c8bc-358">Масштабирование объектов и сред</span><span class="sxs-lookup"><span data-stu-id="8c8bc-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="8c8bc-359">Курсоры, визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="8c8bc-360">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-360">External references</span></span>

* [<span data-ttu-id="8c8bc-361">FOV «Шумиха» ado</span><span class="sxs-lookup"><span data-stu-id="8c8bc-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="8c8bc-362">Содержимое реагирует на позиции пользователя</span><span class="sxs-lookup"><span data-stu-id="8c8bc-362">Content reacts to user position</span></span>

<span data-ttu-id="8c8bc-363">Голограммы должен реагировать на них положение пользователя примерно теми же способами, сделать «реальные» объекты.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="8c8bc-364">Важное соображение — элементы пользовательского интерфейса, нельзя рассчитывать обязательно пользователя позиции мыши останавливается и адаптироваться к перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="8c8bc-365">Разработка приложения, которое правильно адаптируется к позиции пользователя более проверите работы и упростить использование.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-366">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-366">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-367"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-367"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-368"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-368"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-369">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-369">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c8bc-370">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-370">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-371">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="8c8bc-372">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-372">Best</span></span> </td><td> <span data-ttu-id="8c8bc-373">Содержимое и пользовательского интерфейса адаптироваться к должности пользователя, позволяя пользователю естественным образом взаимодействуют с содержимым в пределах ожидаемого числа пользователей перемещения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8c8bc-374">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-374">Meets</span></span> </td><td> <span data-ttu-id="8c8bc-375">Пользовательский Интерфейс адаптируется к позиции пользователя, но может препятствовать представление ключа содержимого, требующее от пользователя для изменения их положения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8c8bc-376">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="8c8bc-377">Элементы пользовательского интерфейса при утере или заблокирован во время перемещения вызывающие пользователю unnaturally вернуться к (или найти) элементов управления.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="8c8bc-378">Элементы пользовательского интерфейса ограничить представление основного содержимого.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="8c8bc-379">Перемещение пользовательского интерфейса не оптимизировано для просмотра расстояние и импульса, особенно при работе с <a href="billboarding-and-tag-along.md">tag-along</a> элементы пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-380">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-380">How to measure</span></span>

* <span data-ttu-id="8c8bc-381">Все измерения должны выполняться в пределах разумного области сценария.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="8c8bc-382">Во время перемещения пользователя, могут меняться, не следует пытаться обмануть приложения с перемещением extreme пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="8c8bc-383">Для элементов пользовательского интерфейса соответствующие элементы управления должны быть доступны вне зависимости от перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="8c8bc-384">К примеру Если пользователь Просмотр и прогулке по трехмерной карты с zoom, элемент управления масштабом должны быть легко доступна пользователю независимо от их расположения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-385">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-385">Recommendations</span></span>

* <span data-ttu-id="8c8bc-386">Пользователь является камеры, и они управляют перемещение.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="8c8bc-387">Let их диска.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-387">Let them drive.</span></span>
* <span data-ttu-id="8c8bc-388">Рассмотрим биллбординга для текста и были перелета систем, которые в противном случае будет быть заблокирован мира или закрыты, если пользователь для перемещения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="8c8bc-389">Используйте tag-along для содержимого, которое должен выполнить пользователь по-прежнему предоставляя пользователю видеть, что такое перед их.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-390">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8c8bc-391">Документация</span><span class="sxs-lookup"><span data-stu-id="8c8bc-391">Documentation</span></span>

* [<span data-ttu-id="8c8bc-392">Разработка взаимодействия</span><span class="sxs-lookup"><span data-stu-id="8c8bc-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="8c8bc-393">Цвет света и материал</span><span class="sxs-lookup"><span data-stu-id="8c8bc-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="8c8bc-394">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="8c8bc-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8c8bc-395">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="8c8bc-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="8c8bc-396">Самостоятельно движения и locomotion пользователя</span><span class="sxs-lookup"><span data-stu-id="8c8bc-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8c8bc-397">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="8c8bc-397">Tools and tutorials</span></span>

* [<span data-ttu-id="8c8bc-398">210. Ввод в смешанной реальности: взгляд</span><span class="sxs-lookup"><span data-stu-id="8c8bc-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="8c8bc-399">Ясности входной взаимодействия</span><span class="sxs-lookup"><span data-stu-id="8c8bc-399">Input interaction clarity</span></span>

<span data-ttu-id="8c8bc-400">Входной взаимодействия ясности критично для удобства использования приложения и включает в себя входные согласованности, approachability, возможность обнаружения методы взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="8c8bc-401">Пользователь должен иметь возможность использовать распространенные взаимодействия всей платформы без relearning.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="8c8bc-402">Если приложение имеет пользовательским вводом, он должен четко оценить и подтвердить.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-403">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-403">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-404"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-404"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-405"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-405"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-406">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-406">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c8bc-407">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-407">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-408">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-408">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-409">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-409">Best</span></span>  |  <span data-ttu-id="8c8bc-410">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-410">Meets</span></span> |  <span data-ttu-id="8c8bc-411">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8c8bc-412">Методы ввода interaction согласованы с Windows Mixed Reality предоставленные [рекомендации](interaction-fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="8c8bc-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="8c8bc-413">Любой пользовательским вводом не нужно дублировать с помощью стандартного ввода (вместо использования взаимодействия со стандартной) и должны четко оценить и подтвердить для пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="8c8bc-414">С помощью стандартных методов ввода избыточны аналогичен рекомендации, но пользовательских входных данных.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="8c8bc-415">Пользователь по-прежнему возможна, цель и ход процесса при помощи взаимодействие с приложениями.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="8c8bc-416">Сложны для понимания входной сопоставление метода или кнопки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="8c8bc-417">Входные данные серьезную пользовательскую настройку, не поддерживает стандартный ввод каких-либо указаний, или может вызвать проблемы усталости и комфорта.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-418">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-418">How to measure</span></span>

* <span data-ttu-id="8c8bc-419">Приложение использует согласованную [standard входные данные методы.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="8c8bc-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="8c8bc-420">Если приложение имеет входные данные заказчиков, очевидно, что передается через:</span><span class="sxs-lookup"><span data-stu-id="8c8bc-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="8c8bc-421">При первом запуске</span><span class="sxs-lookup"><span data-stu-id="8c8bc-421">First-run experience</span></span>
* <span data-ttu-id="8c8bc-422">Вводные экранов</span><span class="sxs-lookup"><span data-stu-id="8c8bc-422">Introductory screens</span></span>
* <span data-ttu-id="8c8bc-423">Подсказки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-423">Tooltips</span></span>
* <span data-ttu-id="8c8bc-424">Советы от руки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-424">Hand coach</span></span>
* <span data-ttu-id="8c8bc-425">Раздел справки</span><span class="sxs-lookup"><span data-stu-id="8c8bc-425">Help section</span></span>
* <span data-ttu-id="8c8bc-426">Голосовая связь через</span><span class="sxs-lookup"><span data-stu-id="8c8bc-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-427">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-427">Recommendations</span></span>

* <span data-ttu-id="8c8bc-428">Используйте стандартные методы ввода, когда это возможно.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="8c8bc-429">Укажите демонстрации, учебники и подсказки для нестандартных методов ввода.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="8c8bc-430">Используйте модель согласованное взаимодействие в приложении.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-431">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8c8bc-432">Документация</span><span class="sxs-lookup"><span data-stu-id="8c8bc-432">Documentation</span></span>

* [<span data-ttu-id="8c8bc-433">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="8c8bc-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="8c8bc-434">Элементом объектов</span><span class="sxs-lookup"><span data-stu-id="8c8bc-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="8c8bc-435">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="8c8bc-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="8c8bc-436">Курсоры</span><span class="sxs-lookup"><span data-stu-id="8c8bc-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8c8bc-437">Комфорт и взглядом</span><span class="sxs-lookup"><span data-stu-id="8c8bc-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="8c8bc-438">Жесты</span><span class="sxs-lookup"><span data-stu-id="8c8bc-438">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="8c8bc-439">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="8c8bc-439">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="8c8bc-440">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="8c8bc-440">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="8c8bc-441">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="8c8bc-441">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="8c8bc-442">Руководство по переносу логики ввода для Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-442">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="8c8bc-443">Ввод с клавиатуры в Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-443">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="8c8bc-444">Взгляд в Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-444">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="8c8bc-445">Жесты и контроллеры движения в Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-445">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="8c8bc-446">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-446">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="8c8bc-447">Ввод с помощью клавиатуры, мыши и контроллера в DirectX</span><span class="sxs-lookup"><span data-stu-id="8c8bc-447">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="8c8bc-448">Направление головы и взгляда в DirectX</span><span class="sxs-lookup"><span data-stu-id="8c8bc-448">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="8c8bc-449">Контроллеры движения и жестов в DirectX</span><span class="sxs-lookup"><span data-stu-id="8c8bc-449">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="8c8bc-450">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="8c8bc-450">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8c8bc-451">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="8c8bc-451">Tools and tutorials</span></span>

* [<span data-ttu-id="8c8bc-452">Пример внедрения: Для достижения более персональных компьютерах</span><span class="sxs-lookup"><span data-stu-id="8c8bc-452">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="8c8bc-453">Приведен пример использования: Пользовательский Интерфейс HoloStudio и полученные данные разработки для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="8c8bc-453">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="8c8bc-454">Пример приложения. Периодическая таблица элементов</span><span class="sxs-lookup"><span data-stu-id="8c8bc-454">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="8c8bc-455">Пример приложения. Модуль лунного</span><span class="sxs-lookup"><span data-stu-id="8c8bc-455">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="8c8bc-456">210. Ввод в смешанной реальности: взгляд</span><span class="sxs-lookup"><span data-stu-id="8c8bc-456">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="8c8bc-457">211. Ввод в смешанной реальности: Жесты</span><span class="sxs-lookup"><span data-stu-id="8c8bc-457">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="8c8bc-458">212. Ввод в смешанной реальности: голос</span><span class="sxs-lookup"><span data-stu-id="8c8bc-458">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="8c8bc-459">Элементом объектов</span><span class="sxs-lookup"><span data-stu-id="8c8bc-459">Interactable objects</span></span>

<span data-ttu-id="8c8bc-460">Кнопка уже давно метафоры, вызывающих срабатывание события в мире двухмерной абстрактным.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-460">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="8c8bc-461">В мире трехмерного смешанной реальности мы не нужно ограничиваться мире больше абстракции.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-461">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="8c8bc-462">Что-то может быть элементом объект, который запускает событие.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-462">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="8c8bc-463">Объект элементом может быть представлено как что-либо из чашку кофе в таблице для всплывающей с плавающей запятой в воздухе.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-463">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="8c8bc-464">Независимо от формы элементом объектов должно быть ясно узнаваемые пользователем с помощью звуковые и подсказки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-464">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-465">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-465">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-466"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-466"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-467"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-467"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-468">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-468">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c8bc-469">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-469">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-470">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-470">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-471">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-471">Best</span></span>  |  <span data-ttu-id="8c8bc-472">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-472">Meets</span></span> |  <span data-ttu-id="8c8bc-473">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-473">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8c8bc-474">Независимо от формы, элементом объектов содержит понятные через звуковые и подсказок для трех состояний: простаивает, целевые и выбран.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-474">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="8c8bc-475">«Кажется, скажите» очистить и постоянно используется работы.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-475">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="8c8bc-476">Объекты масштабируются и распределенных для нацеливания без ошибок.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-476">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="8c8bc-477">Пользователей можно распознать объект как элементом с помощью обратной связи аудио- или visual и могут целевой и активировать объект.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-477">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="8c8bc-478">Учитывая нет подсказок visual или аудио, пользователь не может распознать элементом объекта.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-478">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="8c8bc-479">Взаимодействия являются ошибками из-за масштаба объекта или расстояние между объектами.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-479">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-480">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-480">How to measure</span></span>

* <span data-ttu-id="8c8bc-481">Элементом объекты являются распознаются как «элементом»; включая кнопки, меню и приложение конкретного содержимого.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-481">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="8c8bc-482">Как правило должно быть звуковые и подсказки при нацеливании элементом объектов.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-482">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-483">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-483">Recommendations</span></span>

* <span data-ttu-id="8c8bc-484">Используйте звуковые и обратной связи для взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-484">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="8c8bc-485">Визуальную обратную связь должно отличаться для каждого входного состояния (простоя, целевых, выбранных)</span><span class="sxs-lookup"><span data-stu-id="8c8bc-485">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="8c8bc-486">Элементом объектов следует масштабировать и для нацеливания без ошибок.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-486">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="8c8bc-487">Сгруппированные объекты элементом (например, в строке меню или список) должны иметь нужный интервал для нацеливания.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-487">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="8c8bc-488">Кнопки и меню, которые поддерживают голосовых команд должен предоставлять текстовые метки для ключевого слова команды («см. в разделе, он, скажите»)</span><span class="sxs-lookup"><span data-stu-id="8c8bc-488">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-489">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-489">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8c8bc-490">Документация</span><span class="sxs-lookup"><span data-stu-id="8c8bc-490">Documentation</span></span>

* [<span data-ttu-id="8c8bc-491">Активный объект</span><span class="sxs-lookup"><span data-stu-id="8c8bc-491">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8c8bc-492">Текст в Unity</span><span class="sxs-lookup"><span data-stu-id="8c8bc-492">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="8c8bc-493">Панель приложения и ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="8c8bc-493">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8c8bc-494">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="8c8bc-494">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8c8bc-495">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="8c8bc-495">Tools and tutorials</span></span>

* [<span data-ttu-id="8c8bc-496">Набор средств для смешанной реальности - UX</span><span class="sxs-lookup"><span data-stu-id="8c8bc-496">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="8c8bc-497">Сканирование комнаты</span><span class="sxs-lookup"><span data-stu-id="8c8bc-497">Room scanning</span></span>

<span data-ttu-id="8c8bc-498">Приложения, которым требуются пространственное сопоставление данных полагаться на устройстве, чтобы автоматически собирать эти данные со временем и во всех сеансах, как пользователь изучает их среды с устройством active.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-498">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="8c8bc-499">Полноты и качества этих данных зависит от ряда факторов, включая количество исследований, которые пользователь выполнит, сколько времени прошло с момента просмотра и ли объекты, такие как мебель и двери были перемещены, так как устройство сканирования области.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-499">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="8c8bc-500">Во многих приложениях проанализирует пространственное сопоставление данных в начале работы, имела ли пользователь должен выполнить дополнительные действия для повышения качества пространственных карты и полноты.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-500">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="8c8bc-501">Если пользователь является необходимым условием для поиска в среду, очевидно, что рекомендации, которые необходимо указать во время сканирования.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-501">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-502">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-502">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-503"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-503"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-504"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-504"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-505">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-505">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-506">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-506">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-507">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-507">Best</span></span>  |  <span data-ttu-id="8c8bc-508">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-508">Meets</span></span> |  <span data-ttu-id="8c8bc-509">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-509">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8c8bc-510">Визуализация пространственных сетки сообщить, что пользователи сканирование выполняется.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-510">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="8c8bc-511">Пользователь, безусловно, известна, что делать, и когда сканирование начинается и останавливается.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-511">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="8c8bc-512">Визуализации пространственных сетки предоставляется, но пользователь может не знать четко что делать, и предоставляется без сведений о ходе выполнения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-512">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="8c8bc-513">Нет визуализации сетки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-513">No visualization of mesh.</span></span> <span data-ttu-id="8c8bc-514">Нет рекомендации сведений, предоставленных пользователю сведения о область поиска, или при сканировании запускает или останавливает.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-514">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-515">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-515">How to measure</span></span>

* <span data-ttu-id="8c8bc-516">Во время проверки необходимых комнаты звуковые и указаний, указывающее, где искать и время запуска и остановки сканирования.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-516">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-517">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-517">Recommendations</span></span>

* <span data-ttu-id="8c8bc-518">Указывает, сколько всего тома окружающими пользователей должен быть частью работы.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-518">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="8c8bc-519">Взаимодействия при сканировании начинается и останавливается например индикатор хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-519">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="8c8bc-520">Используйте визуализации сетки во время проверки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-520">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="8c8bc-521">Укажите звуковые и подсказки для пользователя, чтобы выглядеть и перемещать комнате.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-521">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="8c8bc-522">Сообщения куда обратиться, чтобы улучшить данные.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-522">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="8c8bc-523">Во многих случаях, возможно, следует сообщить пользователю, какие возможности нужны (например Обратите внимание на округление вверх, просмотрите за мебель), чтобы получить необходимые проверки качества.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-523">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-524">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-524">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8c8bc-525">Документация</span><span class="sxs-lookup"><span data-stu-id="8c8bc-525">Documentation</span></span>

* [<span data-ttu-id="8c8bc-526">Визуализация при сканировании комнаты</span><span class="sxs-lookup"><span data-stu-id="8c8bc-526">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="8c8bc-527">Пример внедрения: Расширение пространственных сопоставление возможности HoloLens</span><span class="sxs-lookup"><span data-stu-id="8c8bc-527">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="8c8bc-528">Пример внедрения: Пространственные систему для HoloTour</span><span class="sxs-lookup"><span data-stu-id="8c8bc-528">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="8c8bc-529">Пример внедрения: Создание присутствия в фрагментов</span><span class="sxs-lookup"><span data-stu-id="8c8bc-529">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8c8bc-530">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="8c8bc-530">Tools and tutorials</span></span>

* [<span data-ttu-id="8c8bc-531">Набор средств для смешанной реальности - UX</span><span class="sxs-lookup"><span data-stu-id="8c8bc-531">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="8c8bc-532">Направления индикаторы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-532">Directional indicators</span></span>

<span data-ttu-id="8c8bc-533">В приложении смешанной реальности содержимое может находиться за пределами поле зрения или перекрыто объектами реального мира.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-533">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="8c8bc-534">Хорошо спроектированные приложения упростит для пользователя для поиска без видимого содержимого.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-534">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="8c8bc-535">Индикаторы направления предупреждения пользователя важное содержимое и советы для содержимого относительно его положения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-535">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="8c8bc-536">Рекомендации, которые не видимого содержимого может принимать форму звуковой отправители, направленными стрелками или прямой визуальные подсказки.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-536">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-537">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-537">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-538"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-538"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-539"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-539"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-540">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-540">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c8bc-541">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-541">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-542">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-542">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-543">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-543">Best</span></span>  |  <span data-ttu-id="8c8bc-544">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-544">Meets</span></span> |  <span data-ttu-id="8c8bc-545">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-545">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8c8bc-546">Звуковые и подсказки непосредственно помочь пользователю для соответствующего содержимого вне поля зрения.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-546">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="8c8bc-547">Стрелка или некоторые индикатор, который указывает пользователь в общее направление содержимого.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-547">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="8c8bc-548">Соответствующее содержимое находится вне поля зрения и низкая или нет расположение указаний для пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-548">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-549">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-549">How to measure</span></span>

* <span data-ttu-id="8c8bc-550">Соответствующее содержимое за пределами поле зрения пользователя обнаружить с помощью подсказок visual и/или аудиоданных.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-550">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-551">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-551">Recommendations</span></span>

* <span data-ttu-id="8c8bc-552">Необходимое содержимое, находится вне поля зрения пользователя, используйте направления индикаторы и звуковые эффекты для пользователя к содержимому.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-552">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="8c8bc-553">Во многих случаях прямой визуальную подсказку предпочтительнее направленными стрелками.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-553">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="8c8bc-554">Направления индикаторы не должен быть построен в курсор.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-554">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-555">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-555">Resources</span></span>

* [<span data-ttu-id="8c8bc-556">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="8c8bc-556">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="8c8bc-557">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="8c8bc-557">Data loading</span></span>

<span data-ttu-id="8c8bc-558">Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-558">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="8c8bc-559">Это может означать, что пользователь не может взаимодействовать с приложением, когда индикатор хода выполнения отображается, а также можно указать, сколько может быть время ожидания.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-559">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8c8bc-560">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="8c8bc-560">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="8c8bc-561"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-561"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c8bc-562"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="8c8bc-562"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="8c8bc-563">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-563">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c8bc-564">✔️</span><span class="sxs-lookup"><span data-stu-id="8c8bc-564">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8c8bc-565">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="8c8bc-565">Quality criteria</span></span>

|  <span data-ttu-id="8c8bc-566">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-566">Best</span></span>  |  <span data-ttu-id="8c8bc-567">Соответствует</span><span class="sxs-lookup"><span data-stu-id="8c8bc-567">Meets</span></span> |  <span data-ttu-id="8c8bc-568">Сбой</span><span class="sxs-lookup"><span data-stu-id="8c8bc-568">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8c8bc-569">Анимированный визуальный индикатор, в виде индикатор хода выполнения или кольца, отображая ход выполнения во время загрузки и обработки любых данных.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-569">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="8c8bc-570">Визуальный индикатор приведены инструкции по время ожидания может быть.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-570">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="8c8bc-571">Пользователю сообщается, что загрузка данных выполняется, но нет никаких признаков того, как долго может быть время ожидания.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-571">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="8c8bc-572">Загрузка данных ни индикаторы процесса для задачи, более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-572">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="8c8bc-573">Как измерить</span><span class="sxs-lookup"><span data-stu-id="8c8bc-573">How to measure</span></span>

* <span data-ttu-id="8c8bc-574">Во время загрузки данных убедитесь, что имеется пустое состояние не более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-574">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8c8bc-575">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8c8bc-575">Recommendations</span></span>

* <span data-ttu-id="8c8bc-576">Укажите animator загрузки данных, отображая ход выполнения в любой ситуации, когда пользователь может заметить это приложение остановлено или произошел сбой.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-576">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="8c8bc-577">Разумное правило — это любое действие «загрузка», которое может занять более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="8c8bc-577">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="8c8bc-578">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="8c8bc-578">Resources</span></span>

* [<span data-ttu-id="8c8bc-579">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="8c8bc-579">Displaying progress</span></span>](progress.md)
