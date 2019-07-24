---
title: Пространственный звук в Unity
description: Воспроизведение пространственного звука, поступающих из определенной трехмерной точки в сцене Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Пространственный звук, ХРТФ, размер комнаты
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549081"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="24b54-104">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="24b54-104">Spatial sound in Unity</span></span>

<span data-ttu-id="24b54-105">В этом разделе описывается использование пространственного звука в проектах Unity.</span><span class="sxs-lookup"><span data-stu-id="24b54-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="24b54-106">Он охватывает необходимые файлы подключаемых модулей, а также компоненты и свойства Unity, которые позволяют использовать пространственный звук.</span><span class="sxs-lookup"><span data-stu-id="24b54-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="24b54-107">Включение пространственного звука в Unity</span><span class="sxs-lookup"><span data-stu-id="24b54-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="24b54-108">Пространственный звук в Unity включен с помощью подключаемого модуля Audio спатиализер.</span><span class="sxs-lookup"><span data-stu-id="24b54-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="24b54-109">Файлы подключаемых модулей упаковываются непосредственно в Unity, так что включить Пространственный звук так же просто, как **редактировать > параметры проекта > звук** и изменяя **подключаемый модуль спатиализер** в инспекторе в **MS хртф спатиализер**.</span><span class="sxs-lookup"><span data-stu-id="24b54-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="24b54-110">Так как Microsoft спатиализер поддерживает только 48000Hz в настоящее время, необходимо также задать частоту выборки системы равным 48000, чтобы предотвратить сбой ХРТФ в редких случаях, когда системное устройство вывода не имеет значение 48000.</span><span class="sxs-lookup"><span data-stu-id="24b54-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="24b54-111">![Инспектор для Аудиоманажер](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="24b54-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="24b54-112">*Инспектор для Аудиоманажер*</span><span class="sxs-lookup"><span data-stu-id="24b54-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="24b54-113">Теперь проект Unity настроен для использования пространственного звука.</span><span class="sxs-lookup"><span data-stu-id="24b54-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="24b54-114">Если вы не используете компьютер с Windows 10 для разработки, вы не сможете получить Пространственный звук в редакторе и на устройстве (даже если вы используете пакет SDK для Windows 10).</span><span class="sxs-lookup"><span data-stu-id="24b54-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="24b54-115">Использование пространственного звука в Unity</span><span class="sxs-lookup"><span data-stu-id="24b54-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="24b54-116">Пространственный звук используется в проекте Unity путем настройки трех параметров для компонентов источника звука.</span><span class="sxs-lookup"><span data-stu-id="24b54-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="24b54-117">Следующие шаги настраивают компоненты источника звука для пространственного звука.</span><span class="sxs-lookup"><span data-stu-id="24b54-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="24b54-118">На панели **Иерархия** выберите объект Game с подключенным **источником звука**.</span><span class="sxs-lookup"><span data-stu-id="24b54-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="24b54-119">На панели **инспектора** в компоненте " **источник звука** "</span><span class="sxs-lookup"><span data-stu-id="24b54-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="24b54-120">Проверьте параметр **спатиализе** .</span><span class="sxs-lookup"><span data-stu-id="24b54-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="24b54-121">Установите для **пространственного перехода** значение **3D** (числовое значение 1).</span><span class="sxs-lookup"><span data-stu-id="24b54-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="24b54-122">Для получения наилучших результатов разверните **Параметры 3D Sound** и задайте для параметра **Volume Роллофф** значение **Custom роллофф**.</span><span class="sxs-lookup"><span data-stu-id="24b54-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="24b54-123">![Панель инспектора в Unity, показывающая источник звука](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="24b54-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="24b54-124">*Панель инспектора в Unity, показывающая источник звука*</span><span class="sxs-lookup"><span data-stu-id="24b54-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="24b54-125">Теперь ваши звуки реалистично существуют в среде проекта!</span><span class="sxs-lookup"><span data-stu-id="24b54-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="24b54-126">Настоятельно рекомендуется ознакомиться с рекомендациями по [проектированию пространственных звуков](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="24b54-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="24b54-127">Эти рекомендации помогут вам легко интегрировать ваш звук в ваш проект, а также для дальнейшего изучения пользователей в созданном вами интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="24b54-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="24b54-128">Настройка параметров пространственного звука</span><span class="sxs-lookup"><span data-stu-id="24b54-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="24b54-129">Подключаемый модуль пространственного звука (Майкрософт) предоставляет дополнительный параметр, который можно установить для каждого источника звука, чтобы обеспечить дополнительный контроль над имитацией звука.</span><span class="sxs-lookup"><span data-stu-id="24b54-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="24b54-130">Этот параметр представляет размер имитации комнаты.</span><span class="sxs-lookup"><span data-stu-id="24b54-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="24b54-131">Размер комнаты</span><span class="sxs-lookup"><span data-stu-id="24b54-131">Room Size</span></span>

<span data-ttu-id="24b54-132">Размер комнаты, моделируемой пространственным звуком.</span><span class="sxs-lookup"><span data-stu-id="24b54-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="24b54-133">Приблизительные размеры комнат. Малый (офис в небольшой конференцной комнате), средний (большой конференц-зал) и крупный (Аудиториум).</span><span class="sxs-lookup"><span data-stu-id="24b54-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="24b54-134">Можно также указать размер комнаты None для имитации внешнего окружения.</span><span class="sxs-lookup"><span data-stu-id="24b54-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="24b54-135">Размер комнаты по умолчанию — малый.</span><span class="sxs-lookup"><span data-stu-id="24b54-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="24b54-136">Пример</span><span class="sxs-lookup"><span data-stu-id="24b54-136">Example</span></span>

<span data-ttu-id="24b54-137">Микседреалититулкит для Unity предоставляет статический класс, который позволяет легко задавать параметры пространственного звука.</span><span class="sxs-lookup"><span data-stu-id="24b54-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="24b54-138">Этот класс можно найти в [папке микседреалититулкит\спатиалсаунд](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) . его можно вызвать из любого скрипта в проекте.</span><span class="sxs-lookup"><span data-stu-id="24b54-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="24b54-139">Рекомендуется задавать эти параметры для каждого компонента звукового источника в проекте.</span><span class="sxs-lookup"><span data-stu-id="24b54-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="24b54-140">В следующем примере показано, как выбрать средний размер для присоединенного звукового источника.</span><span class="sxs-lookup"><span data-stu-id="24b54-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="24b54-141">Прямой доступ к параметрам из Unity</span><span class="sxs-lookup"><span data-stu-id="24b54-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="24b54-142">Если вы не хотите использовать отличные средства работы со звуком в Микседреалититулкит, вот как можно изменить параметры ХРТФ.</span><span class="sxs-lookup"><span data-stu-id="24b54-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="24b54-143">Его можно скопировать или вставить в сценарий с именем *SetHRTF.CS* , который будет присоединен к каждому хртф аудиосаурце.</span><span class="sxs-lookup"><span data-stu-id="24b54-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="24b54-144">Это позволяет изменять параметры, важные для ХРТФ.</span><span class="sxs-lookup"><span data-stu-id="24b54-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="24b54-145">Пространственный звук в наборе средств смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="24b54-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="24b54-146">Холотулкит-ексамплес/Спатиалсаунд/сцены/Уаудиоманажертест. Unity</span><span class="sxs-lookup"><span data-stu-id="24b54-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="24b54-147">Следующие примеры из набора средств для смешанной реальности — это общие примеры звуковых эффектов, демонстрирующие способы повышения удобства работы с помощью звука.</span><span class="sxs-lookup"><span data-stu-id="24b54-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="24b54-148">Холотулкит-ексамплес/Спатиалсаунд/сцены/Аудиолофитест. Unity</span><span class="sxs-lookup"><span data-stu-id="24b54-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="24b54-149">Холотулкит-ексамплес/Спатиалсаунд/сцены/Аудиукклусионтест. Unity</span><span class="sxs-lookup"><span data-stu-id="24b54-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="24b54-150">См. также</span><span class="sxs-lookup"><span data-stu-id="24b54-150">See also</span></span>
* [<span data-ttu-id="24b54-151">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="24b54-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="24b54-152">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="24b54-152">Spatial sound design</span></span>](spatial-sound-design.md)
