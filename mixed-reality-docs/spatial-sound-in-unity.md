---
title: Пространственный звук в Unity
description: Воспроизведение пространственного звука из определенной трехмерной точки в сцене Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, Пространственный звук, ХРТФ, размер комнаты
ms.openlocfilehash: af3f1486c3e931ad93d7b8960d822653ec740c12
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082041"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="73afc-104">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="73afc-104">Spatial sound in Unity</span></span>

<span data-ttu-id="73afc-105">Эта страница содержит ссылки на ресурсы для пространственного звука в Unity.</span><span class="sxs-lookup"><span data-stu-id="73afc-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="73afc-106">Параметры спатиализер</span><span class="sxs-lookup"><span data-stu-id="73afc-106">Spatializer options</span></span>
<span data-ttu-id="73afc-107">Параметры спатиализер для приложений смешанной реальности включают:</span><span class="sxs-lookup"><span data-stu-id="73afc-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="73afc-108">*Спатиализер MS хртф*.</span><span class="sxs-lookup"><span data-stu-id="73afc-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="73afc-109">Unity предоставляет это как часть дополнительного пакета *Windows Mixed Reality* .</span><span class="sxs-lookup"><span data-stu-id="73afc-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="73afc-110">Это работает на ЦП в архитектуре с более высоким значением "один источник".</span><span class="sxs-lookup"><span data-stu-id="73afc-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="73afc-111">Это обеспечивает обратную совместимость с исходными приложениями HoloLens.</span><span class="sxs-lookup"><span data-stu-id="73afc-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="73afc-112">*Microsoft спатиализер*.</span><span class="sxs-lookup"><span data-stu-id="73afc-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="73afc-113">Это можно найти в [репозитории Microsoft Спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="73afc-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="73afc-114">В этом случае используется более экономичная архитектура с несколькими источниками.</span><span class="sxs-lookup"><span data-stu-id="73afc-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="73afc-115">В HoloLens 2 это перегружается в аппаратный ускоритель.</span><span class="sxs-lookup"><span data-stu-id="73afc-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="73afc-116">Для новых приложений мы рекомендуем использовать *Microsoft спатиализер*.</span><span class="sxs-lookup"><span data-stu-id="73afc-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="73afc-117">Включить пространственность</span><span class="sxs-lookup"><span data-stu-id="73afc-117">Enable spatialization</span></span>

<span data-ttu-id="73afc-118">Используйте [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , чтобы установить _Microsoft. спатиалаудио. спатиализер. Unity_ , и выберите **Microsoft спатиализер** в параметрах звука проекта.</span><span class="sxs-lookup"><span data-stu-id="73afc-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="73afc-119">Затем:</span><span class="sxs-lookup"><span data-stu-id="73afc-119">Then:</span></span>
* <span data-ttu-id="73afc-120">Присоединение **звукового источника** к объекту в иерархии</span><span class="sxs-lookup"><span data-stu-id="73afc-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="73afc-121">Установите флажок " **включить пространственность** "</span><span class="sxs-lookup"><span data-stu-id="73afc-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="73afc-122">Переместить ползунок **пространственного смешения** в "1"</span><span class="sxs-lookup"><span data-stu-id="73afc-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="73afc-123">Убедитесь, что на рабочей станции разработчика включен Пространственный звук.</span><span class="sxs-lookup"><span data-stu-id="73afc-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="73afc-124">Включите его, щелкнув значок тома на панели задач правой кнопкой мыши и убедившись, что для пространственного звука задано значение, отличное от "Выкл.".</span><span class="sxs-lookup"><span data-stu-id="73afc-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="73afc-125">Чтобы получить лучшее представление о том, что вы услышите в HoloLens 2, выберите **Windows Sonic для наушников**.</span><span class="sxs-lookup"><span data-stu-id="73afc-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones**.</span></span>

>[!NOTE]
><span data-ttu-id="73afc-126">Если в Unity возникает ошибка о том, что не удается загрузить подключаемый модуль Microsoft. Спатиалаудио. Спатиализер. Unity, поскольку отсутствует одна из его зависимостей, убедитесь, что на компьютере установлена последняя версия [распространяемого C++ пакета Microsoft Visual](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) .</span><span class="sxs-lookup"><span data-stu-id="73afc-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="73afc-127">Дополнительные сведения см. в статье о</span><span class="sxs-lookup"><span data-stu-id="73afc-127">For more details, see:</span></span>
* [<span data-ttu-id="73afc-128">Репозиторий Microsoft спатиализер GitHub</span><span class="sxs-lookup"><span data-stu-id="73afc-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="73afc-129">Руководство Майкрософт по спатиализер</span><span class="sxs-lookup"><span data-stu-id="73afc-129">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="73afc-130">Документация по источнику аудио в Unity</span><span class="sxs-lookup"><span data-stu-id="73afc-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="73afc-131">Документация по спатиализер Unity</span><span class="sxs-lookup"><span data-stu-id="73afc-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="73afc-132">Ослабление на основе расстояния</span><span class="sxs-lookup"><span data-stu-id="73afc-132">Distance-based attenuation</span></span>
<span data-ttu-id="73afc-133">По умолчанию Unity на основе расстояния Decay имеет минимальное расстояние в 1 метра и максимальное расстояние 500 метров с логарифмической роллоффой.</span><span class="sxs-lookup"><span data-stu-id="73afc-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="73afc-134">Эти параметры могут работать в вашем сценарии, или вы обнаружите, что источники слишком быстро или слишком медленные.</span><span class="sxs-lookup"><span data-stu-id="73afc-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="73afc-135">Дополнительные сведения см. в статье о</span><span class="sxs-lookup"><span data-stu-id="73afc-135">For more details, see:</span></span>
* <span data-ttu-id="73afc-136">[Создание звука в смешанной реальности](spatial-sound-design.md) для рекомендуемых параметров.</span><span class="sxs-lookup"><span data-stu-id="73afc-136">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="73afc-137">В [документации по источнику аудио в Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) приведены инструкции по установке этих кривых.</span><span class="sxs-lookup"><span data-stu-id="73afc-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="73afc-138">Переглагол</span><span class="sxs-lookup"><span data-stu-id="73afc-138">Reverb</span></span>
<span data-ttu-id="73afc-139">По умолчанию _Microsoft спатиализер_ отключает эффекты после спатиализер.</span><span class="sxs-lookup"><span data-stu-id="73afc-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="73afc-140">Для включения переглагола и других эффектов для пространственных источников:</span><span class="sxs-lookup"><span data-stu-id="73afc-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="73afc-141">Присоединение компонента **уровня отправки "воздействие комнаты** " к каждому источнику</span><span class="sxs-lookup"><span data-stu-id="73afc-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="73afc-142">Настройте кривую на уровне отправки для каждого источника, чтобы управлять усилением звука, отправляемого обратно в граф для обработки эффектов.</span><span class="sxs-lookup"><span data-stu-id="73afc-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="73afc-143">Дополнительные сведения см. [в главе 5 руководства по спатиализер](unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="73afc-143">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="73afc-144">Примеры пространственных звуков Unity</span><span class="sxs-lookup"><span data-stu-id="73afc-144">Unity spatial sound examples</span></span>
<span data-ttu-id="73afc-145">Примеры пространственного звука в Unity см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="73afc-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="73afc-146">Демонстрации МРТК</span><span class="sxs-lookup"><span data-stu-id="73afc-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="73afc-147">[Пример проекта Microsoft спатиализер](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="73afc-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="73afc-148">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="73afc-148">Next steps</span></span>
* [<span data-ttu-id="73afc-149">Оформление звука в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="73afc-149">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="73afc-150">Руководство Майкрософт по спатиализер</span><span class="sxs-lookup"><span data-stu-id="73afc-150">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

