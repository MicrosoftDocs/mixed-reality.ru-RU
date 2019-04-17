---
title: Пространственные звук в Unity
description: Воспроизведение звука Пространственные, поступают из определенного трехмерной точки в пределах вашей сцене Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, пространственных звук HRTF, размер области колебания
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597516"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="f48ab-104">Пространственные звук в Unity</span><span class="sxs-lookup"><span data-stu-id="f48ab-104">Spatial sound in Unity</span></span>

<span data-ttu-id="f48ab-105">В этом разделе описывается использование пространственный звук в ваших проектов Unity.</span><span class="sxs-lookup"><span data-stu-id="f48ab-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="f48ab-106">Рассматриваются файлы необходимый подключаемый модуль, а также компоненты Unity и свойства, позволяющие пространственный звук.</span><span class="sxs-lookup"><span data-stu-id="f48ab-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="f48ab-107">Включение пространственных звук в Unity</span><span class="sxs-lookup"><span data-stu-id="f48ab-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="f48ab-108">Звук пространственный индекс, в Unity, включается с помощью подключаемого модуля spatializer аудио.</span><span class="sxs-lookup"><span data-stu-id="f48ab-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="f48ab-109">Файлами подключаемого модуля объединяются непосредственно в Unity, поэтому включение пространственных звук так же просто, как будет **изменить > Параметры проекта > аудио** и изменив **подключаемый модуль Spatializer** в инспекторе для  **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="f48ab-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="f48ab-110">Так как только Microsoft spatializer в настоящее время поддерживает 48000 Гц, также следует задать 48000 во избежание сбоя HRTF в тех редких случаях, что устройства вывода системы не присвоено 48000 уже частота выборки вашей системы:</span><span class="sxs-lookup"><span data-stu-id="f48ab-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="f48ab-111">![Инспектор для AudioManager](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="f48ab-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="f48ab-112">*Инспектор для AudioManager*</span><span class="sxs-lookup"><span data-stu-id="f48ab-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="f48ab-113">Чтобы использовать звуковой пространственный теперь настроен проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="f48ab-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="f48ab-114">Если вы не используете ПК с Windows 10 для разработки, вы не получите пространственный звук в редакторе, а также на устройстве (даже если вы используете пакет SDK для Windows 10).</span><span class="sxs-lookup"><span data-stu-id="f48ab-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="f48ab-115">С помощью пространственных звук в Unity</span><span class="sxs-lookup"><span data-stu-id="f48ab-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="f48ab-116">Звук пространственный индекс используется в проекте Unity с помощью трех параметров на компоненты источника аудио.</span><span class="sxs-lookup"><span data-stu-id="f48ab-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="f48ab-117">Следующие действия будут настроить компоненты источника звука для звука пространственный индекс.</span><span class="sxs-lookup"><span data-stu-id="f48ab-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="f48ab-118">В **иерархии** панели, выберите объект игры с вложенным **источника аудио**.</span><span class="sxs-lookup"><span data-stu-id="f48ab-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="f48ab-119">В **инспектор** панели **источника аудио** компонента</span><span class="sxs-lookup"><span data-stu-id="f48ab-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="f48ab-120">Проверьте **Spatialize** параметр.</span><span class="sxs-lookup"><span data-stu-id="f48ab-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="f48ab-121">Задайте **пространственных Blend** для **3D** (числовое значение 1).</span><span class="sxs-lookup"><span data-stu-id="f48ab-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="f48ab-122">Для получения наилучших результатов разверните **3D Параметры звука** и задайте **Rolloff тома** для **Custom Rolloff**.</span><span class="sxs-lookup"><span data-stu-id="f48ab-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="f48ab-123">![Панели инспектора в Unity, отображающее источник аудио](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="f48ab-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="f48ab-124">*Панели инспектора в Unity, отображающее источник аудио*</span><span class="sxs-lookup"><span data-stu-id="f48ab-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="f48ab-125">Звук теперь в действительности существуют внутри среды проекта!</span><span class="sxs-lookup"><span data-stu-id="f48ab-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="f48ab-126">Настоятельно рекомендуется ознакомиться с [рекомендации по проектированию звук пространственный](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="f48ab-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="f48ab-127">Эти рекомендации помогут вам без проблем интегрировать звукового в проект и Дополнительно установите пользователей в среду, которую вы создали.</span><span class="sxs-lookup"><span data-stu-id="f48ab-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="f48ab-128">Параметры пространственных звука</span><span class="sxs-lookup"><span data-stu-id="f48ab-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="f48ab-129">Подключаемый модуль Microsoft пространственный звук предоставляет дополнительный параметр, который может быть задано, на основе Аудиоисточник, чтобы разрешить дополнительное управление аудио имитации.</span><span class="sxs-lookup"><span data-stu-id="f48ab-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="f48ab-130">Этот параметр является размер имитации комнате.</span><span class="sxs-lookup"><span data-stu-id="f48ab-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="f48ab-131">Размер области колебания</span><span class="sxs-lookup"><span data-stu-id="f48ab-131">Room Size</span></span>

<span data-ttu-id="f48ab-132">Размер места, которое моделируется с помощью звукового сигнала пространственный индекс.</span><span class="sxs-lookup"><span data-stu-id="f48ab-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="f48ab-133">Приблизительные размеры комнаты являются; небольшой (office для небольших конференц-зале), Средний (большой конференц-зале) и крупных (на английском языке).</span><span class="sxs-lookup"><span data-stu-id="f48ab-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="f48ab-134">Также можно указать размер комнаты нет для имитации наружной среды.</span><span class="sxs-lookup"><span data-stu-id="f48ab-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="f48ab-135">Имеет небольшой размер места по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f48ab-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="f48ab-136">Пример</span><span class="sxs-lookup"><span data-stu-id="f48ab-136">Example</span></span>

<span data-ttu-id="f48ab-137">MixedRealityToolkit для Unity предоставляет статический класс, который делает задание параметров звук пространственный легко.</span><span class="sxs-lookup"><span data-stu-id="f48ab-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="f48ab-138">Этот класс можно найти в [MixedRealityToolkit\SpatialSound папку](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) и могут вызываться из любого скрипта в проекте.</span><span class="sxs-lookup"><span data-stu-id="f48ab-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="f48ab-139">Рекомендуется задать эти параметры для каждого компонента источника аудио в проекте.</span><span class="sxs-lookup"><span data-stu-id="f48ab-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="f48ab-140">В следующем примере показано, выбрав размер среднего комнаты для присоединенного источника аудио.</span><span class="sxs-lookup"><span data-stu-id="f48ab-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="f48ab-141">Непосредственно доступ к параметрам из Unity</span><span class="sxs-lookup"><span data-stu-id="f48ab-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="f48ab-142">Если вы не хотите использовать отличные средства аудио в MixedRealityToolkit, вот как изменить параметры HRTF.</span><span class="sxs-lookup"><span data-stu-id="f48ab-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="f48ab-143">Вы можете скопировать и вставить это в сценарий с именем *SetHRTF.cs* , требуется подключение к каждой AudioSource HRTF.</span><span class="sxs-lookup"><span data-stu-id="f48ab-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="f48ab-144">Он позволяет изменить важные параметры на HRTF.</span><span class="sxs-lookup"><span data-stu-id="f48ab-144">It lets you change parameters important to HRTF.</span></span>

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="f48ab-145">Пространственные звук в наборе средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="f48ab-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="f48ab-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="f48ab-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="f48ab-147">В следующих примерах из набора средств смешанной реальности показаны общие аудио эффект примеры, демонстрирующие способы сделать более подробная своими впечатлениями с помощью звук.</span><span class="sxs-lookup"><span data-stu-id="f48ab-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="f48ab-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span><span class="sxs-lookup"><span data-stu-id="f48ab-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="f48ab-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span><span class="sxs-lookup"><span data-stu-id="f48ab-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="f48ab-150">См. также</span><span class="sxs-lookup"><span data-stu-id="f48ab-150">See also</span></span>
* [<span data-ttu-id="f48ab-151">Пространственные звука</span><span class="sxs-lookup"><span data-stu-id="f48ab-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="f48ab-152">Пространственные систему</span><span class="sxs-lookup"><span data-stu-id="f48ab-152">Spatial sound design</span></span>](spatial-sound-design.md)
