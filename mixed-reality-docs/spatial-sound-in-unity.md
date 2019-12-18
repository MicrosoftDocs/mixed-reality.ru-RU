---
title: Пространственный звук в Unity
description: Воспроизведение пространственного звука из определенной трехмерной точки в сцене Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, Пространственный звук, ХРТФ, размер комнаты
ms.openlocfilehash: 3e7d0ea231545d5112d182dffbc02f217ca4a4a7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181994"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="18dd0-104">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="18dd0-104">Spatial sound in Unity</span></span>

<span data-ttu-id="18dd0-105">Эта страница содержит ссылки на ресурсы для пространственного звука в Unity.</span><span class="sxs-lookup"><span data-stu-id="18dd0-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="18dd0-106">Параметры спатиализер</span><span class="sxs-lookup"><span data-stu-id="18dd0-106">Spatializer options</span></span>
<span data-ttu-id="18dd0-107">Параметры спатиализер для приложений смешанной реальности включают:</span><span class="sxs-lookup"><span data-stu-id="18dd0-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="18dd0-108">*Спатиализер MS хртф*.</span><span class="sxs-lookup"><span data-stu-id="18dd0-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="18dd0-109">Unity предоставляет это как часть дополнительного пакета *Windows Mixed Reality* .</span><span class="sxs-lookup"><span data-stu-id="18dd0-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="18dd0-110">Это работает на ЦП в архитектуре с более высоким значением "один источник".</span><span class="sxs-lookup"><span data-stu-id="18dd0-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="18dd0-111">Это обеспечивает обратную совместимость с исходными приложениями HoloLens.</span><span class="sxs-lookup"><span data-stu-id="18dd0-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="18dd0-112">*Microsoft спатиализер*.</span><span class="sxs-lookup"><span data-stu-id="18dd0-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="18dd0-113">Это можно найти в [репозитории Microsoft Спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="18dd0-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="18dd0-114">В этом случае используется более экономичная архитектура с несколькими источниками.</span><span class="sxs-lookup"><span data-stu-id="18dd0-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="18dd0-115">В HoloLens 2 это перегружается в аппаратный ускоритель.</span><span class="sxs-lookup"><span data-stu-id="18dd0-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="18dd0-116">Для новых приложений мы рекомендуем использовать *Microsoft спатиализер*.</span><span class="sxs-lookup"><span data-stu-id="18dd0-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="18dd0-117">Включить пространственность</span><span class="sxs-lookup"><span data-stu-id="18dd0-117">Enable spatialization</span></span>

<span data-ttu-id="18dd0-118">Используйте [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , чтобы установить _Microsoft. спатиалаудио. спатиализер. Unity_ , и выберите **Microsoft спатиализер** в параметрах звука проекта.</span><span class="sxs-lookup"><span data-stu-id="18dd0-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="18dd0-119">Затем:</span><span class="sxs-lookup"><span data-stu-id="18dd0-119">Then:</span></span>
* <span data-ttu-id="18dd0-120">Присоединение **звукового источника** к объекту в иерархии</span><span class="sxs-lookup"><span data-stu-id="18dd0-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="18dd0-121">Установите флажок " **включить пространственность** "</span><span class="sxs-lookup"><span data-stu-id="18dd0-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="18dd0-122">Переместить ползунок **пространственного смешения** в "1"</span><span class="sxs-lookup"><span data-stu-id="18dd0-122">Move the **Spatial Blend** slider to '1'</span></span>

<span data-ttu-id="18dd0-123">Дополнительные сведения см. в статье о</span><span class="sxs-lookup"><span data-stu-id="18dd0-123">For more details, see:</span></span>
* [<span data-ttu-id="18dd0-124">Репозиторий Microsoft спатиализер GitHub</span><span class="sxs-lookup"><span data-stu-id="18dd0-124">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="18dd0-125">Руководство Майкрософт по спатиализер</span><span class="sxs-lookup"><span data-stu-id="18dd0-125">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="18dd0-126">Документация по источнику аудио в Unity</span><span class="sxs-lookup"><span data-stu-id="18dd0-126">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="18dd0-127">Документация по спатиализер Unity</span><span class="sxs-lookup"><span data-stu-id="18dd0-127">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="18dd0-128">Затухание, связанное с расстоянием</span><span class="sxs-lookup"><span data-stu-id="18dd0-128">Distance-based attenuation</span></span>
<span data-ttu-id="18dd0-129">По умолчанию Unity на основе расстояния Decay имеет минимальное расстояние в 1 метра и максимальное расстояние 500 метров с логарифмической роллоффой.</span><span class="sxs-lookup"><span data-stu-id="18dd0-129">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="18dd0-130">Эти параметры могут работать в вашем сценарии, или вы обнаружите, что источники слишком быстро или слишком медленные.</span><span class="sxs-lookup"><span data-stu-id="18dd0-130">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="18dd0-131">Дополнительные сведения см. в статье о</span><span class="sxs-lookup"><span data-stu-id="18dd0-131">For more details, see:</span></span>
* <span data-ttu-id="18dd0-132">[Создание звука в смешанной реальности](spatial-sound-design.md) для рекомендуемых параметров.</span><span class="sxs-lookup"><span data-stu-id="18dd0-132">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="18dd0-133">В [документации по источнику аудио в Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) приведены инструкции по установке этих кривых.</span><span class="sxs-lookup"><span data-stu-id="18dd0-133">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="18dd0-134">Переглагол</span><span class="sxs-lookup"><span data-stu-id="18dd0-134">Reverb</span></span>
<span data-ttu-id="18dd0-135">По умолчанию _Microsoft спатиализер_ отключает эффекты после спатиализер.</span><span class="sxs-lookup"><span data-stu-id="18dd0-135">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="18dd0-136">Для включения переглагола и других эффектов для пространственных источников:</span><span class="sxs-lookup"><span data-stu-id="18dd0-136">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="18dd0-137">Присоединение компонента **уровня отправки "воздействие комнаты** " к каждому источнику</span><span class="sxs-lookup"><span data-stu-id="18dd0-137">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="18dd0-138">Настройте кривую на уровне отправки для каждого источника, чтобы управлять усилением звука, отправляемого обратно в граф для обработки эффектов.</span><span class="sxs-lookup"><span data-stu-id="18dd0-138">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="18dd0-139">Дополнительные сведения см. [в главе 5 руководства по спатиализер](unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="18dd0-139">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="18dd0-140">Примеры пространственных звуков Unity</span><span class="sxs-lookup"><span data-stu-id="18dd0-140">Unity spatial sound examples</span></span>
<span data-ttu-id="18dd0-141">Примеры пространственного звука в Unity см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="18dd0-141">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="18dd0-142">Демонстрации МРТК</span><span class="sxs-lookup"><span data-stu-id="18dd0-142">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="18dd0-143">[Пример проекта Microsoft спатиализер](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="18dd0-143">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="18dd0-144">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="18dd0-144">Next steps</span></span>
* [<span data-ttu-id="18dd0-145">Оформление звука в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="18dd0-145">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="18dd0-146">Руководство Майкрософт по спатиализер</span><span class="sxs-lookup"><span data-stu-id="18dd0-146">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

