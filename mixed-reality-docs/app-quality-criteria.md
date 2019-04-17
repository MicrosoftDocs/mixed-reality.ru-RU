---
title: Критерии контроля качества приложения
description: В этом документе описываются top факторы, влияющие на качество приложения смешанной реальности.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: критерии контроля качества приложений, смешанной реальности, смешанный реальности
ms.openlocfilehash: 8070a434be462a636b314527c59f299ca77fb6d4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602379"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="d9647-104">Критерии контроля качества приложения</span><span class="sxs-lookup"><span data-stu-id="d9647-104">App quality criteria</span></span>

<span data-ttu-id="d9647-105">В этом документе описываются top факторы, влияющие на качество приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d9647-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="d9647-106">Для каждого фактора предоставляется следующая информация</span><span class="sxs-lookup"><span data-stu-id="d9647-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="d9647-107">Обзор — краткое описание коэффициент качества и почему она важна.</span><span class="sxs-lookup"><span data-stu-id="d9647-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="d9647-108">Влияние устройства — это влияет на тип устройства окно смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d9647-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="d9647-109">Критерии качества, как вычислить коэффициент качества.</span><span class="sxs-lookup"><span data-stu-id="d9647-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="d9647-110">Как измерить — методы для измерения (или возникнуть) проблема.</span><span class="sxs-lookup"><span data-stu-id="d9647-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="d9647-111">Рекомендации — Сводка подходов для повышения удобства работы пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="d9647-112">Ресурсы — соответствующие разработчика и ресурсы для разработки, которые полезны для создания лучших результатов приложения.</span><span class="sxs-lookup"><span data-stu-id="d9647-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="d9647-113">Частота кадров</span><span class="sxs-lookup"><span data-stu-id="d9647-113">Frame rate</span></span>

<span data-ttu-id="d9647-114">Частота кадров — это главным условием голограмма комфорта стабильность и пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="d9647-115">Частота кадров ниже рекомендуемые целевых объектов может привести к голограммы отображаются перебои управления, отрицательно влияет на believability работы и что может привести к усталости глаз.</span><span class="sxs-lookup"><span data-stu-id="d9647-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="d9647-116">Частота кадров целевого для работы в Windows Mixed Reality иммерсивную будет либо или 60 Гц 90, в зависимости от того, какие смешанной реальности совместимых компьютеров под управлением Windows, которая должна поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="d9647-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="d9647-117">Для HoloLens частота кадров целевого — 60 Гц.</span><span class="sxs-lookup"><span data-stu-id="d9647-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-118">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-118">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-120"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-121">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-121">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d9647-122">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-122">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-123">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-123">Quality criteria</span></span>

|  <span data-ttu-id="d9647-124">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-124">Best</span></span>  |  <span data-ttu-id="d9647-125">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-125">Meets</span></span> |  <span data-ttu-id="d9647-126">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="d9647-127">Приложение постоянно соответствует кадров в Вторая цель (кадров/с) для целевого устройства: 60 кадров/с на HoloLens; 90 кадров/с на Ultra компьютеров; и 60 кадров/с на основных компьютерах.</span><span class="sxs-lookup"><span data-stu-id="d9647-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="d9647-128">Приложение имеет удаляет временные рамки, не излагает опыт core; или ниже, чем целевое кадров/с, но не влияет на взаимодействие с приложениями.</span><span class="sxs-lookup"><span data-stu-id="d9647-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="d9647-129">Приложение наблюдается снижение частоты кадров в среднем каждые десять секунд или менее.</span><span class="sxs-lookup"><span data-stu-id="d9647-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d9647-130">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-130">How to measure</span></span>

* <span data-ttu-id="d9647-131">График частота кадров в режиме реального времени предоставляется через [Windows Device Portal](using-the-windows-device-portal.md#system-performance) в разделе «Производительность системы».</span><span class="sxs-lookup"><span data-stu-id="d9647-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="d9647-132">Для отладки разработки, добавьте счетчик диагностики частота кадров в приложение.</span><span class="sxs-lookup"><span data-stu-id="d9647-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="d9647-133">Ознакомьтесь с ресурсами образца счетчика.</span><span class="sxs-lookup"><span data-stu-id="d9647-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="d9647-134">Падения частоты кадров может возникать в устройстве во время работы приложения, перемещая голове в сторону.</span><span class="sxs-lookup"><span data-stu-id="d9647-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="d9647-135">Если она отображается непредвиденный перебои управления перемещения, затем низкая частота кадров или стабильности плоскости она может вызвать.</span><span class="sxs-lookup"><span data-stu-id="d9647-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-136">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-136">Recommendations</span></span>

* <span data-ttu-id="d9647-137">Добавьте счетчик частота кадров в начале процесса разработки.</span><span class="sxs-lookup"><span data-stu-id="d9647-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="d9647-138">Изменения, которые повлечь Снижение частоты кадров следует вычислить и соответствующим образом равна устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="d9647-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-139">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9647-140">Документация</span><span class="sxs-lookup"><span data-stu-id="d9647-140">Documentation</span></span>

* [<span data-ttu-id="d9647-141">Основные сведения о производительности для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="d9647-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="d9647-142">Голограмма стабильность и частоте кадров</span><span class="sxs-lookup"><span data-stu-id="d9647-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="d9647-143">Средства производительности в бюджет</span><span class="sxs-lookup"><span data-stu-id="d9647-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="d9647-144">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9647-145">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="d9647-145">Tools and tutorials</span></span>

* [<span data-ttu-id="d9647-146">MRToolkit, отображение счетчика кадров/с</span><span class="sxs-lookup"><span data-stu-id="d9647-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="d9647-147">MRToolkit, шейдеры</span><span class="sxs-lookup"><span data-stu-id="d9647-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="d9647-148">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="d9647-148">External references</span></span>

* [<span data-ttu-id="d9647-149">Unity, оптимизация приложений для мобильных устройств</span><span class="sxs-lookup"><span data-stu-id="d9647-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="d9647-150">Голограмма стабильность</span><span class="sxs-lookup"><span data-stu-id="d9647-150">Hologram stability</span></span>

<span data-ttu-id="d9647-151">Стабильные голограммы повысить удобство использования и believability приложения и создавать более комфортную работу Просмотр для пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="d9647-152">Качество голограмма стабильности является результатом хорошее приложение разработки, а также возможность устройства понять (отслеживание) его среды.</span><span class="sxs-lookup"><span data-stu-id="d9647-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="d9647-153">Частота кадров является главным условием стабильность, другие факторы могут повлиять на стабильность включая:</span><span class="sxs-lookup"><span data-stu-id="d9647-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="d9647-154">Использование плоскости стабилизации</span><span class="sxs-lookup"><span data-stu-id="d9647-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="d9647-155">Расстояние до пространственных привязки</span><span class="sxs-lookup"><span data-stu-id="d9647-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="d9647-156">Отслеживание</span><span class="sxs-lookup"><span data-stu-id="d9647-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-157">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-157">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-158"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-158"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-159"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-159"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-160">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-160">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-161">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-161">Quality criteria</span></span>

|  <span data-ttu-id="d9647-162">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-162">Best</span></span>  |  <span data-ttu-id="d9647-163">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-163">Meets</span></span> |  <span data-ttu-id="d9647-164">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9647-165">Голограммы постоянно появляются стабильной.</span><span class="sxs-lookup"><span data-stu-id="d9647-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="d9647-166">Вторичный содержимое характеризуется Непредвиденная перемещения; или Непредвиденная перемещения не страдает работы всего приложения.</span><span class="sxs-lookup"><span data-stu-id="d9647-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="d9647-167">Основного содержимого в кадре характеризуется Непредвиденная перемещения.</span><span class="sxs-lookup"><span data-stu-id="d9647-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d9647-168">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-168">How to measure</span></span>

<span data-ttu-id="d9647-169">Хотя наши устройства и условия для просмотра:</span><span class="sxs-lookup"><span data-stu-id="d9647-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="d9647-170">Переместить головой из стороны в сторону, если голограммы двигаться Непредвиденная затем низкая частота кадров или вероятной причиной является неправильное выравнивание стабильности плоскости на плоскости.</span><span class="sxs-lookup"><span data-stu-id="d9647-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="d9647-171">Перемещение по голограммы и среды, обратите внимание на поведение, например различных и jumpiness.</span><span class="sxs-lookup"><span data-stu-id="d9647-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="d9647-172">Этот тип движения, скорее всего связано с устройства, не отслеживая среды или расстояние для привязки пространственных.</span><span class="sxs-lookup"><span data-stu-id="d9647-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="d9647-173">При большом или нескольких голограммы во фрейме, наблюдать за поведением голограмма в различные глубины, хотя перемещение на вашей головной позицию в сторону, если shakiness отображается, это может вызвано стабилизации плоскости.</span><span class="sxs-lookup"><span data-stu-id="d9647-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="d9647-174">Recomendations</span><span class="sxs-lookup"><span data-stu-id="d9647-174">Recomendations</span></span>

* <span data-ttu-id="d9647-175">Добавьте счетчик частота кадров в начале процесса разработки.</span><span class="sxs-lookup"><span data-stu-id="d9647-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="d9647-176">С помощью стабилизации плоскости.</span><span class="sxs-lookup"><span data-stu-id="d9647-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="d9647-177">Всегда выводить привязанного голограммы в трех ваттметров их привязки.</span><span class="sxs-lookup"><span data-stu-id="d9647-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="d9647-178">Убедитесь, что ваша среда настроена для правильного отслеживания.</span><span class="sxs-lookup"><span data-stu-id="d9647-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="d9647-179">Проектирование работы во избежание голограммы на различных уровнях фокальной глубины внутри фрейма.</span><span class="sxs-lookup"><span data-stu-id="d9647-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-180">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9647-181">Документация</span><span class="sxs-lookup"><span data-stu-id="d9647-181">Documentation</span></span>

* [<span data-ttu-id="d9647-182">Голограмма стабильность и частоте кадров</span><span class="sxs-lookup"><span data-stu-id="d9647-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="d9647-183">Пример использования можно с помощью плоскости стабилизации</span><span class="sxs-lookup"><span data-stu-id="d9647-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="d9647-184">Основные сведения о производительности для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="d9647-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="d9647-185">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="d9647-186">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="d9647-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="d9647-187">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="d9647-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="d9647-188">Стационарной системой отсчета координат</span><span class="sxs-lookup"><span data-stu-id="d9647-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9647-189">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="d9647-189">Tools and tutorials</span></span>

* [<span data-ttu-id="d9647-190">Набор MR Companion, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="d9647-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="d9647-191">Позиция голограммы на реальных поверхностях</span><span class="sxs-lookup"><span data-stu-id="d9647-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="d9647-192">Misalignments из голограммы с физические объекты (если предполагается располагаться относительно друг друга) становится понятно из относящихся к объединениям голограммы и реального мира.</span><span class="sxs-lookup"><span data-stu-id="d9647-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="d9647-193">Точность размещение должен указываться относительно потребностями сценария; например общие поверхности размещения можно использовать Пространственные карты, но более точного размещения потребует некоторых использование маркеров и калибровки.</span><span class="sxs-lookup"><span data-stu-id="d9647-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-194">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-194">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-195"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-195"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-196"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-196"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-197">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-197">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-198">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-198">Quality criteria</span></span>

|  <span data-ttu-id="d9647-199">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-199">Best</span></span>  |  <span data-ttu-id="d9647-200">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-200">Meets</span></span> |  <span data-ttu-id="d9647-201">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="d9647-202">Голограммы выровнять область обычно сантиметры диапазон дюймов.</span><span class="sxs-lookup"><span data-stu-id="d9647-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="d9647-203">Если требуется более высокой точностью, приложение должно предоставляет эффективные средства для совместной работы в рамках спецификации нужное приложение.</span><span class="sxs-lookup"><span data-stu-id="d9647-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="d9647-204">Н/Д</span><span class="sxs-lookup"><span data-stu-id="d9647-204">NA</span></span> | <span data-ttu-id="d9647-205">Голограммы отображаются невыровненных с физической целевой объект критические поверхности плоскости или на число с плавающей запятой от рабочей области.</span><span class="sxs-lookup"><span data-stu-id="d9647-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="d9647-206">Если требуется точность, голограммы должна соответствовать спецификации выражение с учетом сценария.</span><span class="sxs-lookup"><span data-stu-id="d9647-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9647-207">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-207">How to measure</span></span>

* <span data-ttu-id="d9647-208">Не должны отображаться голограммы, помещенные на карте Пространственные значительно плавать выше или ниже области.</span><span class="sxs-lookup"><span data-stu-id="d9647-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="d9647-209">Голограммы, требующие размещения точных должны иметь определенные виды маркера и калибровки система, округленное до требования сценария.</span><span class="sxs-lookup"><span data-stu-id="d9647-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-210">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-210">Recommendations</span></span>

* <span data-ttu-id="d9647-211">Пространственные карты удобен для помещения объектов на поверхностях, при точности не требуется.</span><span class="sxs-lookup"><span data-stu-id="d9647-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="d9647-212">Для наиболее точности, маркеры плакаты для задания используется или голограммы и контроллера Xbox (или какой-либо механизм вручную выравнивание) для окончательного калибровки.</span><span class="sxs-lookup"><span data-stu-id="d9647-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="d9647-213">Рассмотрите возможность разбиения очень большой голограммы на логические части и выравнивание каждая часть в область.</span><span class="sxs-lookup"><span data-stu-id="d9647-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="d9647-214">Неправильно interpupilary расстоянии (IPD) также влияет на выравнивание голограмма.</span><span class="sxs-lookup"><span data-stu-id="d9647-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="d9647-215">Всегда настраивайте HoloLens в IPD пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-216">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9647-217">Документация</span><span class="sxs-lookup"><span data-stu-id="d9647-217">Documentation</span></span>

* [<span data-ttu-id="d9647-218">Размещение пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="d9647-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="d9647-219">Место выполнения сканирования</span><span class="sxs-lookup"><span data-stu-id="d9647-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="d9647-220">Рекомендации по использованию пространственных привязки</span><span class="sxs-lookup"><span data-stu-id="d9647-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="d9647-221">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="d9647-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="d9647-222">Пространственное сопоставление в Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="d9647-223">Общие сведения о разработке Vuforia</span><span class="sxs-lookup"><span data-stu-id="d9647-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9647-224">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="d9647-224">Tools and tutorials</span></span>

* [<span data-ttu-id="d9647-225">MR пространственных 230: Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="d9647-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="d9647-226">Набор MR средств, библиотек пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="d9647-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="d9647-227">Комплект Companion MR, пример плакат калибровки</span><span class="sxs-lookup"><span data-stu-id="d9647-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="d9647-228">Набор MR Companion, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="d9647-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="d9647-229">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="d9647-229">External references</span></span>

* [<span data-ttu-id="d9647-230">Практический пример Lowes, выравнивание точности</span><span class="sxs-lookup"><span data-stu-id="d9647-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="d9647-231">Просмотр зоны комфорта</span><span class="sxs-lookup"><span data-stu-id="d9647-231">Viewing zone of comfort</span></span>

<span data-ttu-id="d9647-232">Где сходятся глаза пользователей путем размещения содержимого и голограммы в различные глубины управления для разработчиков приложений.</span><span class="sxs-lookup"><span data-stu-id="d9647-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="d9647-233">Пользователи, то HoloLens будет всегда рассчитан на работу до 2.0m для поддержания понятность изображения так, как отображаются HoloLens фиксируются на расстоянии оптические около 2.0m от пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="d9647-234">Неправильная глубины может привести к visual discomfort или усталости.</span><span class="sxs-lookup"><span data-stu-id="d9647-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-235">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-235">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-236"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-236"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-237"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-237"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-238">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-238">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-239">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="d9647-240">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="d9647-241">Вставка содержимого 2 МБ.</span><span class="sxs-lookup"><span data-stu-id="d9647-241">Place content at 2m.</span></span></li><li><span data-ttu-id="d9647-242">Голограммы нельзя разместить в 2 МБ и не избежать конфликтов между конвергенции и услуги размещения, оптимальной зоны для размещения голограмма при между 1,25 m и 5 мин.</span><span class="sxs-lookup"><span data-stu-id="d9647-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="d9647-243">В каждом случае конструкторы требуемую структуру для содержимого, чтобы рекомендовать пользователям взаимодействовать 1 + m нет на месте (например размер содержимого, и по умолчанию параметры размещения).</span><span class="sxs-lookup"><span data-stu-id="d9647-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="d9647-244">Если специально не требуется в сценарии, плоскости отсечения следует реализовать с помощью fadeout, начиная с 1 млн.</span><span class="sxs-lookup"><span data-stu-id="d9647-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="d9647-245">В случаях, где требуется подробное наблюдение за над голограмма содержимое должно быть не более чем 50cm.</span><span class="sxs-lookup"><span data-stu-id="d9647-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="d9647-246">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-246">Meets</span></span></td><td> <span data-ttu-id="d9647-247">Содержимое находится в пределах движения и просматривать рекомендации, но неправильное использование или use плоскости отсечения.</span><span class="sxs-lookup"><span data-stu-id="d9647-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9647-248">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-248">Fail</span></span> </td><td> <span data-ttu-id="d9647-249">Содержимое представляется слишком близко (обычно &lt;1,25 m, или &lt;50 cm для стационарных голограммы, требуя ближе наблюдения.)</span><span class="sxs-lookup"><span data-stu-id="d9647-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="d9647-250">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-250">How to measure</span></span>

* <span data-ttu-id="d9647-251">Содержимого обычно нужно 2 МБ размещения, но не ближе чем 1,25 или дальше, чем в 5 мин.</span><span class="sxs-lookup"><span data-stu-id="d9647-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="d9647-252">За некоторыми исключениями расстояние отрисовки обрезки HoloLens должно быть присвоено .85CM с fadeout содержимого, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="d9647-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="d9647-253">Подход содержимое и обратите внимание на результат плоскости отсечения.</span><span class="sxs-lookup"><span data-stu-id="d9647-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="d9647-254">Стационарные содержимое не должно быть ближе, чем от 50cm.</span><span class="sxs-lookup"><span data-stu-id="d9647-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-255">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-255">Recommendations</span></span>

* <span data-ttu-id="d9647-256">Разрабатывать содержимое для оптимального просмотра расстояние до 2 МБ.</span><span class="sxs-lookup"><span data-stu-id="d9647-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="d9647-257">Значение расстояния отрисовки обрезки 85cm с fadeout содержимого, начиная с 1 млн.</span><span class="sxs-lookup"><span data-stu-id="d9647-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="d9647-258">Стационарные голограммы, которые должны ближе Просмотр плоскости отсечения должна быть не ближе чем 30cm а fadeout следует запустить по крайней мере 10cm от плоскости отсечения.</span><span class="sxs-lookup"><span data-stu-id="d9647-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-259">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-259">Resources</span></span>

* [<span data-ttu-id="d9647-260">Визуализации расстояния</span><span class="sxs-lookup"><span data-stu-id="d9647-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="d9647-261">Точку фокуса в Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="d9647-262">Поэкспериментировав с масштабом</span><span class="sxs-lookup"><span data-stu-id="d9647-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="d9647-263">Текст, размер шрифта рекомендуется</span><span class="sxs-lookup"><span data-stu-id="d9647-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="d9647-264">Переключение глубины</span><span class="sxs-lookup"><span data-stu-id="d9647-264">Depth switching</span></span>

<span data-ttu-id="d9647-265">Независимо от просмотра зоны комфорта проблем практически, а также гораздо фокальной объекты (включая голограммы и реальных содержимое) может привести к oculomotor усталости и общие discomfort требует пользователю переключаться между часто или быстро.</span><span class="sxs-lookup"><span data-stu-id="d9647-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-266">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-266">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-267"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-267"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-268"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-268"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-269">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-269">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d9647-270">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-270">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-271">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-271">Quality criteria</span></span>

|  <span data-ttu-id="d9647-272">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-272">Best</span></span>  |  <span data-ttu-id="d9647-273">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-273">Meets</span></span> |  <span data-ttu-id="d9647-274">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9647-275">Ограниченные или обеспечения естественного глубины, переключение не вызывает пользователю unnaturally изменения фокуса.</span><span class="sxs-lookup"><span data-stu-id="d9647-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="d9647-276">Резкое глубины коммутатора core и масштабируемости взаимодействие с приложениями, или внезапные глубины коммутатора, вызванное Непредвиденное содержимое в реальных условиях.</span><span class="sxs-lookup"><span data-stu-id="d9647-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="d9647-277">Согласованные глубины коммутатора, или неожиданном глубины переключения, не является обязательным или core взаимодействие с приложениями.</span><span class="sxs-lookup"><span data-stu-id="d9647-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9647-278">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-278">How to measure</span></span>

* <span data-ttu-id="d9647-279">Если приложению требуется пользователю постоянно и/или резко изменять глубину фокус, нет глубины, переключение проблему.</span><span class="sxs-lookup"><span data-stu-id="d9647-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-280">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-280">Recommendations</span></span>

* <span data-ttu-id="d9647-281">Оставьте основного содержимого в согласованное плоскости и обеспечить соответствие плоскости стабилизации плоскости.</span><span class="sxs-lookup"><span data-stu-id="d9647-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="d9647-282">Это позволит устранить oculomotor усталости и Непредвиденная голограмма перемещения.</span><span class="sxs-lookup"><span data-stu-id="d9647-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-283">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-283">Resources</span></span>

* [<span data-ttu-id="d9647-284">Визуализации расстояния</span><span class="sxs-lookup"><span data-stu-id="d9647-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="d9647-285">Точку фокуса в Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="d9647-286">Использование пространственных звука</span><span class="sxs-lookup"><span data-stu-id="d9647-286">Use of spatial sound</span></span>

<span data-ttu-id="d9647-287">В Windows Mixed Reality ядро аудио предоставляет звукового компонента работы смешанной реальности, имитируя 3D звука с помощью направление, расстояние и моделирование окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="d9647-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="d9647-288">Использование пространственных звука в приложении позволяет разработчикам convincingly поместите звуков в 3 мерном пространстве (сфера) по всему пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="d9647-289">Затем эти звуки покажется так, как если бы они поступали от физического объектов или голограммы смешанной реальности в окружения пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="d9647-290">Пространственные звук — это мощное средство для общения, доступности и проектирование взаимодействия с Пользователем в приложениях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d9647-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-291">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-291">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-292"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-292"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-293"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-293"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-294">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-294">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d9647-295">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-295">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-296">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-296">Quality criteria</span></span>

|  <span data-ttu-id="d9647-297">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-297">Best</span></span>  |  <span data-ttu-id="d9647-298">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-298">Meets</span></span> |  <span data-ttu-id="d9647-299">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9647-300">Звук будет логически spatialized и UX соответствующим образом использует звук для помощи с объект обнаружения и сбора отзывов.</span><span class="sxs-lookup"><span data-stu-id="d9647-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="d9647-301">Звук естественным и относящиеся к объектам и нормализованное через сценарий.</span><span class="sxs-lookup"><span data-stu-id="d9647-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="d9647-302">Пространственные аудио используется соответствующим образом для believability, но отсутствующие в качестве средства для облегчения отзывы пользователей и возможность обнаружения.</span><span class="sxs-lookup"><span data-stu-id="d9647-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="d9647-303">Звук не является spatialized, как и ожидалось, и/или отсутствие звука для помощи пользователю в UI.</span><span class="sxs-lookup"><span data-stu-id="d9647-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="d9647-304">Или пространственных аудио был не рассматривались или применялись в разработке сценария.</span><span class="sxs-lookup"><span data-stu-id="d9647-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9647-305">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-305">How to measure</span></span>

* <span data-ttu-id="d9647-306">В общем случае должен выдавать соответствующие звуков из целевой голограммы (например:., звуков bark от holographic dog.)</span><span class="sxs-lookup"><span data-stu-id="d9647-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="d9647-307">Чтобы помочь пользователю оставить отзывы или осведомленности в области действий вне holographic рамки можно использовать звуковые сигналы на протяжении всего пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d9647-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-308">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-308">Recommendations</span></span>

* <span data-ttu-id="d9647-309">Используйте Пространственные аудио для помощи с объект обнаружения и пользовательских интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="d9647-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="d9647-310">Реальные звуки работают лучше, чем синтеза или понятном и естественном звук.</span><span class="sxs-lookup"><span data-stu-id="d9647-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="d9647-311">Должен быть spatialized большинства звуков.</span><span class="sxs-lookup"><span data-stu-id="d9647-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="d9647-312">Избегайте невидимым отправители.</span><span class="sxs-lookup"><span data-stu-id="d9647-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="d9647-313">Избегайте пространственных маски.</span><span class="sxs-lookup"><span data-stu-id="d9647-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="d9647-314">Нормализация все звуки.</span><span class="sxs-lookup"><span data-stu-id="d9647-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-315">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9647-316">Документация</span><span class="sxs-lookup"><span data-stu-id="d9647-316">Documentation</span></span>

* [<span data-ttu-id="d9647-317">Пространственные звука</span><span class="sxs-lookup"><span data-stu-id="d9647-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="d9647-318">Пространственные систему</span><span class="sxs-lookup"><span data-stu-id="d9647-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="d9647-319">Пространственные звук в Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="d9647-320">Пример использования, звук для HoloTour пространственный индекс</span><span class="sxs-lookup"><span data-stu-id="d9647-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="d9647-321">Пример использования можно с помощью пространственных звук в RoboRaid</span><span class="sxs-lookup"><span data-stu-id="d9647-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9647-322">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="d9647-322">Tools and tutorials</span></span>

* [<span data-ttu-id="d9647-323">MR пространственных 220: Пространственные звука</span><span class="sxs-lookup"><span data-stu-id="d9647-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="d9647-324">MRToolkit пространственных аудио</span><span class="sxs-lookup"><span data-stu-id="d9647-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="d9647-325">Сосредоточиться на границы holographic фрейма (FOV)</span><span class="sxs-lookup"><span data-stu-id="d9647-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="d9647-326">Хорошо спроектированный взаимодействия с пользователями можно создать и обслуживать полезный контекст виртуальной среды, который расширяет о пользователях.</span><span class="sxs-lookup"><span data-stu-id="d9647-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="d9647-327">Сдерживание последствия границы FOV включает в себя продуманный разработки содержимого масштаба и контекста, использование пространственных аудио-, руководство по системам и положение пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="d9647-328">Если попросить правильно, он будет считаете, что меньше ограничено границами FOV во время работы приложения с уверенно.</span><span class="sxs-lookup"><span data-stu-id="d9647-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-329">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-329">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-330"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-330"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-331"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-331"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-332">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-332">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-333">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-333">Quality criteria</span></span>

|  <span data-ttu-id="d9647-334">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-334">Best</span></span>  |  <span data-ttu-id="d9647-335">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-335">Meets</span></span> |  <span data-ttu-id="d9647-336">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9647-337">Пользователь никогда не теряет контекста и ознакомившись просмотра.</span><span class="sxs-lookup"><span data-stu-id="d9647-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="d9647-338">Контекст помощь предоставляется для больших объектов.</span><span class="sxs-lookup"><span data-stu-id="d9647-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="d9647-339">Возможность обнаружения и просмотр руководство предоставляется для объектов вне рамки.</span><span class="sxs-lookup"><span data-stu-id="d9647-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="d9647-340">Как правило конструктор перемещения и масштаб голограммы подходят для прекрасные впечатления от просмотра.</span><span class="sxs-lookup"><span data-stu-id="d9647-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="d9647-341">Пользователь никогда не теряет контекст, но дополнительные горлышка движения может потребоваться в ограниченных ситуациях.</span><span class="sxs-lookup"><span data-stu-id="d9647-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="d9647-342">В ограниченных ситуациях масштабирования вызывает голограммы прервать либо вызывает некоторые виды движений шея просмотреть голограммы кадр вертикальной или горизонтальной.</span><span class="sxs-lookup"><span data-stu-id="d9647-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="d9647-343">Для просмотра голограммы необходим пользователь скорее всего, потерять контекста и/или согласованное шея движения.</span><span class="sxs-lookup"><span data-stu-id="d9647-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="d9647-344">Нет контекста рекомендаций для больших объектов holographic перемещения объектов легко потерять вне рамки без возможности обнаружения рекомендации или высоту голограммы требует регулярного шея движения для просмотра.</span><span class="sxs-lookup"><span data-stu-id="d9647-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9647-345">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-345">How to measure</span></span>

* <span data-ttu-id="d9647-346">Контекст для (крупный) голограмма потерян или не распознан из-за были усечены на границах.</span><span class="sxs-lookup"><span data-stu-id="d9647-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="d9647-347">Расположение голограммы не удается найти из-за отсутствия директоров внимания или содержимое, которое быстро перемещает и из него holographic кадра.</span><span class="sxs-lookup"><span data-stu-id="d9647-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="d9647-348">Сценарий требует обычные и повторяющиеся вверх и вниз головной движение, чтобы полностью см. в разделе голограмма, приводит к усталости шея.</span><span class="sxs-lookup"><span data-stu-id="d9647-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-349">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-349">Recommendations</span></span>

* <span data-ttu-id="d9647-350">Начните работу с небольших объектов, которые соответствуют FOV, то переход с визуальные подсказки для больших версий.</span><span class="sxs-lookup"><span data-stu-id="d9647-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="d9647-351">Используйте Пространственные директоров аудио- и внимания для поиска содержимого пользователя, которое находится за пределами FOV.</span><span class="sxs-lookup"><span data-stu-id="d9647-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="d9647-352">Насколько возможно Избегайте голограммы, по вертикали обрезать FOV.</span><span class="sxs-lookup"><span data-stu-id="d9647-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="d9647-353">Предоставьте пользователю с указаниями в приложении для удобства просмотра расположение.</span><span class="sxs-lookup"><span data-stu-id="d9647-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-354">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9647-355">Документация</span><span class="sxs-lookup"><span data-stu-id="d9647-355">Documentation</span></span>

* [<span data-ttu-id="d9647-356">Holographic кадра</span><span class="sxs-lookup"><span data-stu-id="d9647-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="d9647-357">Пример использования, HoloStudio пользовательского интерфейса и полученные данные разработки для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d9647-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="d9647-358">Масштабирование объектов и сред</span><span class="sxs-lookup"><span data-stu-id="d9647-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="d9647-359">Курсоры, визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="d9647-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="d9647-360">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="d9647-360">External references</span></span>

* [<span data-ttu-id="d9647-361">FOV «Шумиха» ado</span><span class="sxs-lookup"><span data-stu-id="d9647-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="d9647-362">Содержимое реагирует на позиции пользователя</span><span class="sxs-lookup"><span data-stu-id="d9647-362">Content reacts to user position</span></span>

<span data-ttu-id="d9647-363">Голограммы должен реагировать на них положение пользователя примерно теми же способами, сделать «реальные» объекты.</span><span class="sxs-lookup"><span data-stu-id="d9647-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="d9647-364">Важное соображение — элементы пользовательского интерфейса, нельзя рассчитывать обязательно пользователя позиции мыши останавливается и адаптироваться к перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="d9647-365">Разработка приложения, которое правильно адаптируется к позиции пользователя более проверите работы и упростить использование.</span><span class="sxs-lookup"><span data-stu-id="d9647-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-366">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-366">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-367"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-367"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-368"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-368"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-369">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-369">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d9647-370">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-370">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-371">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="d9647-372">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-372">Best</span></span> </td><td> <span data-ttu-id="d9647-373">Содержимое и пользовательского интерфейса адаптироваться к должности пользователя, позволяя пользователю естественным образом взаимодействуют с содержимым в пределах ожидаемого числа пользователей перемещения.</span><span class="sxs-lookup"><span data-stu-id="d9647-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9647-374">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-374">Meets</span></span> </td><td> <span data-ttu-id="d9647-375">Пользовательский Интерфейс адаптируется к позиции пользователя, но может препятствовать представление ключа содержимого, требующее от пользователя для изменения их положения.</span><span class="sxs-lookup"><span data-stu-id="d9647-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9647-376">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="d9647-377">Элементы пользовательского интерфейса при утере или заблокирован во время перемещения вызывающие пользователю unnaturally вернуться к (или найти) элементов управления.</span><span class="sxs-lookup"><span data-stu-id="d9647-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="d9647-378">Элементы пользовательского интерфейса ограничить представление основного содержимого.</span><span class="sxs-lookup"><span data-stu-id="d9647-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="d9647-379">Перемещение пользовательского интерфейса не оптимизировано для просмотра расстояние и импульса, особенно при работе с <a href="billboarding-and-tag-along.md">tag-along</a> элементы пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d9647-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="d9647-380">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-380">How to measure</span></span>

* <span data-ttu-id="d9647-381">Все измерения должны выполняться в пределах разумного области сценария.</span><span class="sxs-lookup"><span data-stu-id="d9647-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="d9647-382">Во время перемещения пользователя, могут меняться, не следует пытаться обмануть приложения с перемещением extreme пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="d9647-383">Для элементов пользовательского интерфейса соответствующие элементы управления должны быть доступны вне зависимости от перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="d9647-384">К примеру Если пользователь Просмотр и прогулке по трехмерной карты с zoom, элемент управления масштабом должны быть легко доступна пользователю независимо от их расположения.</span><span class="sxs-lookup"><span data-stu-id="d9647-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-385">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-385">Recommendations</span></span>

* <span data-ttu-id="d9647-386">Пользователь является камеры, и они управляют перемещение.</span><span class="sxs-lookup"><span data-stu-id="d9647-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="d9647-387">Let их диска.</span><span class="sxs-lookup"><span data-stu-id="d9647-387">Let them drive.</span></span>
* <span data-ttu-id="d9647-388">Рассмотрим биллбординга для текста и были перелета систем, которые в противном случае будет быть заблокирован мира или закрыты, если пользователь для перемещения.</span><span class="sxs-lookup"><span data-stu-id="d9647-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="d9647-389">Используйте tag-along для содержимого, которое должен выполнить пользователь по-прежнему предоставляя пользователю видеть, что такое перед их.</span><span class="sxs-lookup"><span data-stu-id="d9647-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-390">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9647-391">Документация</span><span class="sxs-lookup"><span data-stu-id="d9647-391">Documentation</span></span>

* [<span data-ttu-id="d9647-392">Разработка взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d9647-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="d9647-393">Цвет света и материал</span><span class="sxs-lookup"><span data-stu-id="d9647-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="d9647-394">Биллбординга и tag-along</span><span class="sxs-lookup"><span data-stu-id="d9647-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d9647-395">Основы взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d9647-395">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="d9647-396">Самостоятельно движения и locomotion пользователя</span><span class="sxs-lookup"><span data-stu-id="d9647-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9647-397">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="d9647-397">Tools and tutorials</span></span>

* [<span data-ttu-id="d9647-398">Входные данные MR 210: Взглядом</span><span class="sxs-lookup"><span data-stu-id="d9647-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="d9647-399">Ясности входной взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d9647-399">Input interaction clarity</span></span>

<span data-ttu-id="d9647-400">Входной взаимодействия ясности критично для удобства использования приложения и включает в себя входные согласованности, approachability, возможность обнаружения методы взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d9647-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="d9647-401">Пользователь должен иметь возможность использовать распространенные взаимодействия всей платформы без relearning.</span><span class="sxs-lookup"><span data-stu-id="d9647-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="d9647-402">Если приложение имеет пользовательским вводом, он должен четко оценить и подтвердить.</span><span class="sxs-lookup"><span data-stu-id="d9647-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-403">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-403">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-404"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-404"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-405"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-405"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-406">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-406">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d9647-407">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-407">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-408">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-408">Quality criteria</span></span>

|  <span data-ttu-id="d9647-409">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-409">Best</span></span>  |  <span data-ttu-id="d9647-410">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-410">Meets</span></span> |  <span data-ttu-id="d9647-411">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9647-412">Методы ввода interaction согласованы с Windows Mixed Reality предоставленные [рекомендации](interaction-fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="d9647-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="d9647-413">Любой пользовательским вводом не нужно дублировать с помощью стандартного ввода (вместо использования взаимодействия со стандартной) и должны четко оценить и подтвердить для пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="d9647-414">С помощью стандартных методов ввода избыточны аналогичен рекомендации, но пользовательских входных данных.</span><span class="sxs-lookup"><span data-stu-id="d9647-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="d9647-415">Пользователь по-прежнему возможна, цель и ход процесса при помощи взаимодействие с приложениями.</span><span class="sxs-lookup"><span data-stu-id="d9647-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="d9647-416">Сложны для понимания входной сопоставление метода или кнопки.</span><span class="sxs-lookup"><span data-stu-id="d9647-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="d9647-417">Входные данные серьезную пользовательскую настройку, не поддерживает стандартный ввод каких-либо указаний, или может вызвать проблемы усталости и комфорта.</span><span class="sxs-lookup"><span data-stu-id="d9647-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9647-418">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-418">How to measure</span></span>

* <span data-ttu-id="d9647-419">Приложение использует согласованную [standard входные данные методы.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="d9647-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="d9647-420">Если приложение имеет входные данные заказчиков, очевидно, что передается через:</span><span class="sxs-lookup"><span data-stu-id="d9647-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="d9647-421">При первом запуске</span><span class="sxs-lookup"><span data-stu-id="d9647-421">First-run experience</span></span>
* <span data-ttu-id="d9647-422">Вводные экранов</span><span class="sxs-lookup"><span data-stu-id="d9647-422">Introductory screens</span></span>
* <span data-ttu-id="d9647-423">Подсказки</span><span class="sxs-lookup"><span data-stu-id="d9647-423">Tooltips</span></span>
* <span data-ttu-id="d9647-424">Советы от руки</span><span class="sxs-lookup"><span data-stu-id="d9647-424">Hand coach</span></span>
* <span data-ttu-id="d9647-425">Раздел справки</span><span class="sxs-lookup"><span data-stu-id="d9647-425">Help section</span></span>
* <span data-ttu-id="d9647-426">Голосовая связь через</span><span class="sxs-lookup"><span data-stu-id="d9647-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-427">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-427">Recommendations</span></span>

* <span data-ttu-id="d9647-428">Используйте стандартные методы ввода, когда это возможно.</span><span class="sxs-lookup"><span data-stu-id="d9647-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="d9647-429">Укажите демонстрации, учебники и подсказки для нестандартных методов ввода.</span><span class="sxs-lookup"><span data-stu-id="d9647-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="d9647-430">Используйте модель согласованное взаимодействие в приложении.</span><span class="sxs-lookup"><span data-stu-id="d9647-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-431">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9647-432">Документация</span><span class="sxs-lookup"><span data-stu-id="d9647-432">Documentation</span></span>

* [<span data-ttu-id="d9647-433">Основы взаимодействия Windows MR</span><span class="sxs-lookup"><span data-stu-id="d9647-433">Windows MR interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="d9647-434">Элементом объектов</span><span class="sxs-lookup"><span data-stu-id="d9647-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="d9647-435">Нацеливание взглядом</span><span class="sxs-lookup"><span data-stu-id="d9647-435">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="d9647-436">Курсоры</span><span class="sxs-lookup"><span data-stu-id="d9647-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d9647-437">Комфорт и взглядом</span><span class="sxs-lookup"><span data-stu-id="d9647-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="d9647-438">Жесты</span><span class="sxs-lookup"><span data-stu-id="d9647-438">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="d9647-439">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="d9647-439">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="d9647-440">Проектирование голоса</span><span class="sxs-lookup"><span data-stu-id="d9647-440">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="d9647-441">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="d9647-441">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="d9647-442">Руководство по для Unity переносу входных данных</span><span class="sxs-lookup"><span data-stu-id="d9647-442">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="d9647-443">Ввод с клавиатуры в Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-443">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="d9647-444">Помощи в Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-444">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="d9647-445">Жестов и контроллеры движения в Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-445">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="d9647-446">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-446">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="d9647-447">Входные данные контроллера в DirectX, клавиатуры и мыши</span><span class="sxs-lookup"><span data-stu-id="d9647-447">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="d9647-448">Взглядом, жестов и контроллеры движения в DirectX</span><span class="sxs-lookup"><span data-stu-id="d9647-448">Gaze, gesture, and motion controllers in DirectX</span></span>](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="d9647-449">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="d9647-449">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9647-450">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="d9647-450">Tools and tutorials</span></span>

* [<span data-ttu-id="d9647-451">Пример внедрения: Для достижения более персональных компьютерах</span><span class="sxs-lookup"><span data-stu-id="d9647-451">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="d9647-452">Приведен пример использования: Пользовательский Интерфейс HoloStudio и полученные данные разработки для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d9647-452">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="d9647-453">Пример приложения. Периодическая таблица элементов</span><span class="sxs-lookup"><span data-stu-id="d9647-453">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="d9647-454">Пример приложения. Модуль лунного</span><span class="sxs-lookup"><span data-stu-id="d9647-454">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="d9647-455">Входные данные MR 210: Взглядом</span><span class="sxs-lookup"><span data-stu-id="d9647-455">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="d9647-456">Входные данные MR 211: Жесты</span><span class="sxs-lookup"><span data-stu-id="d9647-456">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="d9647-457">Входные данные MR 212: Голоса</span><span class="sxs-lookup"><span data-stu-id="d9647-457">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="d9647-458">Элементом объектов</span><span class="sxs-lookup"><span data-stu-id="d9647-458">Interactable objects</span></span>

<span data-ttu-id="d9647-459">Кнопка уже давно метафоры, вызывающих срабатывание события в мире двухмерной абстрактным.</span><span class="sxs-lookup"><span data-stu-id="d9647-459">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="d9647-460">В мире трехмерного смешанной реальности мы не нужно ограничиваться мире больше абстракции.</span><span class="sxs-lookup"><span data-stu-id="d9647-460">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="d9647-461">Что-то может быть элементом объект, который запускает событие.</span><span class="sxs-lookup"><span data-stu-id="d9647-461">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="d9647-462">Объект элементом может быть представлено как что-либо из чашку кофе в таблице для всплывающей с плавающей запятой в воздухе.</span><span class="sxs-lookup"><span data-stu-id="d9647-462">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="d9647-463">Независимо от формы элементом объектов должно быть ясно узнаваемые пользователем с помощью звуковые и подсказки.</span><span class="sxs-lookup"><span data-stu-id="d9647-463">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-464">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-464">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-465"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-465"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-466"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-466"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-467">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-467">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d9647-468">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-468">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-469">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-469">Quality criteria</span></span>

|  <span data-ttu-id="d9647-470">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-470">Best</span></span>  |  <span data-ttu-id="d9647-471">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-471">Meets</span></span> |  <span data-ttu-id="d9647-472">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-472">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9647-473">Независимо от формы, элементом объектов содержит понятные через звуковые и подсказок для трех состояний: простаивает, целевые и выбран.</span><span class="sxs-lookup"><span data-stu-id="d9647-473">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="d9647-474">«Кажется, скажите» очистить и постоянно используется работы.</span><span class="sxs-lookup"><span data-stu-id="d9647-474">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="d9647-475">Объекты масштабируются и распределенных для нацеливания без ошибок.</span><span class="sxs-lookup"><span data-stu-id="d9647-475">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="d9647-476">Пользователей можно распознать объект как элементом с помощью обратной связи аудио- или visual и могут целевой и активировать объект.</span><span class="sxs-lookup"><span data-stu-id="d9647-476">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="d9647-477">Учитывая нет подсказок visual или аудио, пользователь не может распознать элементом объекта.</span><span class="sxs-lookup"><span data-stu-id="d9647-477">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="d9647-478">Взаимодействия являются ошибками из-за масштаба объекта или расстояние между объектами.</span><span class="sxs-lookup"><span data-stu-id="d9647-478">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9647-479">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-479">How to measure</span></span>

* <span data-ttu-id="d9647-480">Элементом объекты являются распознаются как «элементом»; включая кнопки, меню и приложение конкретного содержимого.</span><span class="sxs-lookup"><span data-stu-id="d9647-480">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="d9647-481">Как правило должно быть звуковые и подсказки при нацеливании элементом объектов.</span><span class="sxs-lookup"><span data-stu-id="d9647-481">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-482">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-482">Recommendations</span></span>

* <span data-ttu-id="d9647-483">Используйте звуковые и обратной связи для взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="d9647-483">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="d9647-484">Визуальную обратную связь должно отличаться для каждого входного состояния (простоя, целевых, выбранных)</span><span class="sxs-lookup"><span data-stu-id="d9647-484">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="d9647-485">Элементом объектов следует масштабировать и для нацеливания без ошибок.</span><span class="sxs-lookup"><span data-stu-id="d9647-485">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="d9647-486">Сгруппированные объекты элементом (например, в строке меню или список) должны иметь нужный интервал для нацеливания.</span><span class="sxs-lookup"><span data-stu-id="d9647-486">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="d9647-487">Кнопки и меню, которые поддерживают голосовых команд должен предоставлять текстовые метки для ключевого слова команды («см. в разделе, он, скажите»)</span><span class="sxs-lookup"><span data-stu-id="d9647-487">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-488">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-488">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9647-489">Документация</span><span class="sxs-lookup"><span data-stu-id="d9647-489">Documentation</span></span>

* [<span data-ttu-id="d9647-490">Элементом объекта</span><span class="sxs-lookup"><span data-stu-id="d9647-490">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d9647-491">Текст в Unity</span><span class="sxs-lookup"><span data-stu-id="d9647-491">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="d9647-492">Панель приложения и ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="d9647-492">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d9647-493">Проектирование голоса</span><span class="sxs-lookup"><span data-stu-id="d9647-493">Voice design</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9647-494">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="d9647-494">Tools and tutorials</span></span>

* [<span data-ttu-id="d9647-495">Набор средств для смешанной реальности - UX</span><span class="sxs-lookup"><span data-stu-id="d9647-495">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="d9647-496">Сканирование комнаты</span><span class="sxs-lookup"><span data-stu-id="d9647-496">Room scanning</span></span>

<span data-ttu-id="d9647-497">Приложения, которым требуются пространственное сопоставление данных полагаться на устройстве, чтобы автоматически собирать эти данные со временем и во всех сеансах, как пользователь изучает их среды с устройством active.</span><span class="sxs-lookup"><span data-stu-id="d9647-497">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="d9647-498">Полноты и качества этих данных зависит от ряда факторов, включая количество исследований, которые пользователь выполнит, сколько времени прошло с момента просмотра и ли объекты, такие как мебель и двери были перемещены, так как устройство сканирования области.</span><span class="sxs-lookup"><span data-stu-id="d9647-498">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="d9647-499">Во многих приложениях проанализирует пространственное сопоставление данных в начале работы, имела ли пользователь должен выполнить дополнительные действия для повышения качества пространственных карты и полноты.</span><span class="sxs-lookup"><span data-stu-id="d9647-499">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="d9647-500">Если пользователь является необходимым условием для поиска в среду, очевидно, что рекомендации, которые необходимо указать во время сканирования.</span><span class="sxs-lookup"><span data-stu-id="d9647-500">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-501">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-501">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-502"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-502"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-503"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-503"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-504">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-504">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-505">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-505">Quality criteria</span></span>

|  <span data-ttu-id="d9647-506">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-506">Best</span></span>  |  <span data-ttu-id="d9647-507">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-507">Meets</span></span> |  <span data-ttu-id="d9647-508">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-508">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9647-509">Визуализация пространственных сетки сообщить, что пользователи сканирование выполняется.</span><span class="sxs-lookup"><span data-stu-id="d9647-509">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="d9647-510">Пользователь, безусловно, известна, что делать, и когда сканирование начинается и останавливается.</span><span class="sxs-lookup"><span data-stu-id="d9647-510">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="d9647-511">Визуализации пространственных сетки предоставляется, но пользователь может не знать четко что делать, и предоставляется без сведений о ходе выполнения.</span><span class="sxs-lookup"><span data-stu-id="d9647-511">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="d9647-512">Нет визуализации сетки.</span><span class="sxs-lookup"><span data-stu-id="d9647-512">No visualization of mesh.</span></span> <span data-ttu-id="d9647-513">Нет рекомендации сведений, предоставленных пользователю сведения о область поиска, или при сканировании запускает или останавливает.</span><span class="sxs-lookup"><span data-stu-id="d9647-513">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d9647-514">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-514">How to measure</span></span>

* <span data-ttu-id="d9647-515">Во время проверки необходимых комнаты звуковые и указаний, указывающее, где искать и время запуска и остановки сканирования.</span><span class="sxs-lookup"><span data-stu-id="d9647-515">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-516">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-516">Recommendations</span></span>

* <span data-ttu-id="d9647-517">Указывает, сколько всего тома окружающими пользователей должен быть частью работы.</span><span class="sxs-lookup"><span data-stu-id="d9647-517">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="d9647-518">Взаимодействия при сканировании начинается и останавливается например индикатор хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="d9647-518">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="d9647-519">Используйте визуализации сетки во время проверки.</span><span class="sxs-lookup"><span data-stu-id="d9647-519">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="d9647-520">Укажите звуковые и подсказки для пользователя, чтобы выглядеть и перемещать комнате.</span><span class="sxs-lookup"><span data-stu-id="d9647-520">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="d9647-521">Сообщения куда обратиться, чтобы улучшить данные.</span><span class="sxs-lookup"><span data-stu-id="d9647-521">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="d9647-522">Во многих случаях, возможно, следует сообщить пользователю, какие возможности нужны (например Обратите внимание на округление вверх, просмотрите за мебель), чтобы получить необходимые проверки качества.</span><span class="sxs-lookup"><span data-stu-id="d9647-522">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-523">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-523">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9647-524">Документация</span><span class="sxs-lookup"><span data-stu-id="d9647-524">Documentation</span></span>

* [<span data-ttu-id="d9647-525">Визуализация сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="d9647-525">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="d9647-526">Пример внедрения: Расширение пространственных сопоставление возможности HoloLens</span><span class="sxs-lookup"><span data-stu-id="d9647-526">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="d9647-527">Пример внедрения: Пространственные систему для HoloTour</span><span class="sxs-lookup"><span data-stu-id="d9647-527">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="d9647-528">Пример внедрения: Создание присутствия в фрагментов</span><span class="sxs-lookup"><span data-stu-id="d9647-528">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9647-529">Инструменты и учебники</span><span class="sxs-lookup"><span data-stu-id="d9647-529">Tools and tutorials</span></span>

* [<span data-ttu-id="d9647-530">Набор средств для смешанной реальности - UX</span><span class="sxs-lookup"><span data-stu-id="d9647-530">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="d9647-531">Направления индикаторы</span><span class="sxs-lookup"><span data-stu-id="d9647-531">Directional indicators</span></span>

<span data-ttu-id="d9647-532">В приложении смешанной реальности содержимое может находиться за пределами поле зрения или перекрыто объектами реального мира.</span><span class="sxs-lookup"><span data-stu-id="d9647-532">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="d9647-533">Хорошо спроектированные приложения упростит для пользователя для поиска без видимого содержимого.</span><span class="sxs-lookup"><span data-stu-id="d9647-533">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="d9647-534">Индикаторы направления предупреждения пользователя важное содержимое и советы для содержимого относительно его положения.</span><span class="sxs-lookup"><span data-stu-id="d9647-534">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="d9647-535">Рекомендации, которые не видимого содержимого может принимать форму звуковой отправители, направленными стрелками или прямой визуальные подсказки.</span><span class="sxs-lookup"><span data-stu-id="d9647-535">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-536">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-536">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-537"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-537"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-538"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-538"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-539">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-539">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d9647-540">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-540">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-541">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-541">Quality criteria</span></span>

|  <span data-ttu-id="d9647-542">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-542">Best</span></span>  |  <span data-ttu-id="d9647-543">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-543">Meets</span></span> |  <span data-ttu-id="d9647-544">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-544">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9647-545">Звуковые и подсказки непосредственно помочь пользователю для соответствующего содержимого вне поля зрения.</span><span class="sxs-lookup"><span data-stu-id="d9647-545">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="d9647-546">Стрелка или некоторые индикатор, который указывает пользователь в общее направление содержимого.</span><span class="sxs-lookup"><span data-stu-id="d9647-546">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="d9647-547">Соответствующее содержимое находится вне поля зрения и низкая или нет расположение указаний для пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9647-547">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9647-548">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-548">How to measure</span></span>

* <span data-ttu-id="d9647-549">Соответствующее содержимое за пределами поле зрения пользователя обнаружить с помощью подсказок visual и/или аудиоданных.</span><span class="sxs-lookup"><span data-stu-id="d9647-549">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-550">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-550">Recommendations</span></span>

* <span data-ttu-id="d9647-551">Необходимое содержимое, находится вне поля зрения пользователя, используйте направления индикаторы и звуковые эффекты для пользователя к содержимому.</span><span class="sxs-lookup"><span data-stu-id="d9647-551">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="d9647-552">Во многих случаях прямой визуальную подсказку предпочтительнее направленными стрелками.</span><span class="sxs-lookup"><span data-stu-id="d9647-552">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="d9647-553">Направления индикаторы не должен быть построен в курсор.</span><span class="sxs-lookup"><span data-stu-id="d9647-553">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-554">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-554">Resources</span></span>

* [<span data-ttu-id="d9647-555">Holographic кадра</span><span class="sxs-lookup"><span data-stu-id="d9647-555">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="d9647-556">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="d9647-556">Data loading</span></span>

<span data-ttu-id="d9647-557">Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.</span><span class="sxs-lookup"><span data-stu-id="d9647-557">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="d9647-558">Это может означать, что пользователь не может взаимодействовать с приложением, когда индикатор хода выполнения отображается, а также можно указать, сколько может быть время ожидания.</span><span class="sxs-lookup"><span data-stu-id="d9647-558">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9647-559">Влияние на устройства</span><span class="sxs-lookup"><span data-stu-id="d9647-559">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="d9647-560"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9647-560"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9647-561"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="d9647-561"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="d9647-562">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-562">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d9647-563">✔️</span><span class="sxs-lookup"><span data-stu-id="d9647-563">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9647-564">Критерии контроля качества</span><span class="sxs-lookup"><span data-stu-id="d9647-564">Quality criteria</span></span>

|  <span data-ttu-id="d9647-565">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-565">Best</span></span>  |  <span data-ttu-id="d9647-566">Соответствует</span><span class="sxs-lookup"><span data-stu-id="d9647-566">Meets</span></span> |  <span data-ttu-id="d9647-567">Сбой</span><span class="sxs-lookup"><span data-stu-id="d9647-567">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9647-568">Анимированный визуальный индикатор, в виде индикатор хода выполнения или кольца, отображая ход выполнения во время загрузки и обработки любых данных.</span><span class="sxs-lookup"><span data-stu-id="d9647-568">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="d9647-569">Визуальный индикатор приведены инструкции по время ожидания может быть.</span><span class="sxs-lookup"><span data-stu-id="d9647-569">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="d9647-570">Пользователю сообщается, что загрузка данных выполняется, но нет никаких признаков того, как долго может быть время ожидания.</span><span class="sxs-lookup"><span data-stu-id="d9647-570">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="d9647-571">Загрузка данных ни индикаторы процесса для задачи, более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="d9647-571">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d9647-572">Как измерить</span><span class="sxs-lookup"><span data-stu-id="d9647-572">How to measure</span></span>

* <span data-ttu-id="d9647-573">Во время загрузки данных убедитесь, что имеется пустое состояние не более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="d9647-573">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9647-574">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="d9647-574">Recommendations</span></span>

* <span data-ttu-id="d9647-575">Укажите animator загрузки данных, отображая ход выполнения в любой ситуации, когда пользователь может заметить это приложение остановлено или произошел сбой.</span><span class="sxs-lookup"><span data-stu-id="d9647-575">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="d9647-576">Разумное правило — это любое действие «загрузка», которое может занять более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="d9647-576">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="d9647-577">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="d9647-577">Resources</span></span>

* [<span data-ttu-id="d9647-578">Отображение хода выполнения</span><span class="sxs-lookup"><span data-stu-id="d9647-578">Displaying progress</span></span>](progress.md)
