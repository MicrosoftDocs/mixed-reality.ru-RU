---
title: Пространственные аудио учебники — 5. Использование переглагола для добавления расстояния в пространственный звук
description: Добавьте переглаголные эффекты, чтобы улучшить смысл варианта расстояния до пространственного звука.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук
ms.openlocfilehash: abe78417dc231e6228d1942e03418ba699bc0938
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182741"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="ca034-105">Использование переглагола для добавления расстояния в пространственный звук</span><span class="sxs-lookup"><span data-stu-id="ca034-105">Using reverb to add distance to spatial audio</span></span>

## <a name="objectives"></a><span data-ttu-id="ca034-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="ca034-106">Objectives</span></span>
<span data-ttu-id="ca034-107">В предыдущих главах мы добавили пространственность для звуков, чтобы дать им представление о направлении.</span><span class="sxs-lookup"><span data-stu-id="ca034-107">In previous chapters, we added spatialization to sounds to give them a sense of direction.</span></span> <span data-ttu-id="ca034-108">В этой 5-й главе мы добавим действие с переглаголом, чтобы дать звуковое представление о расстоянии.</span><span class="sxs-lookup"><span data-stu-id="ca034-108">In this 5th chapter, we'll add a reverb effect to give sounds a sense of distance.</span></span> <span data-ttu-id="ca034-109">Наши цели:</span><span class="sxs-lookup"><span data-stu-id="ca034-109">Our objectives are to:</span></span>
* <span data-ttu-id="ca034-110">Улучшение наблюдаемого расстояния источников звука путем добавления переглагола</span><span class="sxs-lookup"><span data-stu-id="ca034-110">Improve perceived distance of sound sources by adding reverb</span></span>
* <span data-ttu-id="ca034-111">Управление воспринимаемым расстоянием звука с помощью расстояния прослушивателя к голограмме</span><span class="sxs-lookup"><span data-stu-id="ca034-111">Control perceived distance of the sound using the listener's distance to the hologram</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="ca034-112">Добавление группы микшера и действия по передействию</span><span class="sxs-lookup"><span data-stu-id="ca034-112">Add a mixer group and a reverb effect</span></span>
<span data-ttu-id="ca034-113">В [главе 2](unity-spatial-audio-ch2.md)мы добавили микшер.</span><span class="sxs-lookup"><span data-stu-id="ca034-113">In [Chapter 2](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="ca034-114">Микшер включает одну **группу** по умолчанию — **master**.</span><span class="sxs-lookup"><span data-stu-id="ca034-114">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="ca034-115">Так как мы хотим применить к некоторым звукам только переглаголные эффекты, добавим вторую **группу** для этих звуков.</span><span class="sxs-lookup"><span data-stu-id="ca034-115">Because we'll only want to apply a reverb effect to some sounds, let's add a second **Group** for those sounds.</span></span> <span data-ttu-id="ca034-116">Чтобы добавить **группу**, щелкните правой кнопкой мыши **главную** группу в **микшере аудио** и выберите **Добавить дочернюю группу**:</span><span class="sxs-lookup"><span data-stu-id="ca034-116">To add a **Group**, right click on the **Master** group in the **Audio Mixer** and choose **Add child group**:</span></span>

![Добавить дочернюю группу](images/spatial-audio/add-child-group.png)

<span data-ttu-id="ca034-118">В этом примере мы назвали новую группу "воздействие на комнату".</span><span class="sxs-lookup"><span data-stu-id="ca034-118">In this example, we've named the new group "Room Effect".</span></span>

<span data-ttu-id="ca034-119">Каждая **Группа** имеет собственный набор эффектов.</span><span class="sxs-lookup"><span data-stu-id="ca034-119">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="ca034-120">Чтобы добавить действие в новую группу, нажмите кнопку **Добавить...** в новой группе и выберите пункт **перекоманда SFX**:</span><span class="sxs-lookup"><span data-stu-id="ca034-120">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Добавление переглагола SFX](images/spatial-audio/add-sfx-reverb.png)

<span data-ttu-id="ca034-122">В терминологии «звук» оригинал, унревербератедный звук называется « _сухой_», а звук после фильтрации с помощью фильтра перезапуска называется «защелка _»._</span><span class="sxs-lookup"><span data-stu-id="ca034-122">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="ca034-123">Оба пути отправляются в выходные данные, и их относительные сильные стороны в этом сочетании называются набором задолженности _/сухой_.</span><span class="sxs-lookup"><span data-stu-id="ca034-123">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="ca034-124">Завлажный или сухой набор сильно влияет на смысл расстояния.</span><span class="sxs-lookup"><span data-stu-id="ca034-124">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="ca034-125">В результате **переглагола SFX** включены элементы управления для корректировки затронутого или сухой набора.</span><span class="sxs-lookup"><span data-stu-id="ca034-125">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="ca034-126">Так как подключаемый модуль **Microsoft спатиализер** обрабатывает сухой путь, мы будем использовать переработку **SFX** только для пути с осторожностью.</span><span class="sxs-lookup"><span data-stu-id="ca034-126">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="ca034-127">На панели **инспектора** **переглагола SFX**:</span><span class="sxs-lookup"><span data-stu-id="ca034-127">On the **Inspector** pane of your **SFX Reverb**:</span></span>
* <span data-ttu-id="ca034-128">Задайте для свойства уровень сухой (-10000 МБ) значение наименьшее.</span><span class="sxs-lookup"><span data-stu-id="ca034-128">Set the Dry Level property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="ca034-129">Задайте для свойства комнаты наибольшее значение (0 МБ).</span><span class="sxs-lookup"><span data-stu-id="ca034-129">Set the Room property to the highest setting (0 mB)</span></span>

<span data-ttu-id="ca034-130">После внесения этих изменений панель **инспектора** в параметре **SFX** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ca034-130">After these changes, the **Inspector** pane of the **SFX Reverb** will look like this:</span></span>

![Свойства переглагола SFX](images/spatial-audio/sfx-reverb-properties.png)

<span data-ttu-id="ca034-132">Другие параметры управляют имитацией комнаты.</span><span class="sxs-lookup"><span data-stu-id="ca034-132">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="ca034-133">В частности, **время Decay** связано с наблюдаемым размером комнаты.</span><span class="sxs-lookup"><span data-stu-id="ca034-133">In particular, **Decay Time** is related to perceived room size.</span></span> 

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="ca034-134">Включение переглагола при воспроизведении видео</span><span class="sxs-lookup"><span data-stu-id="ca034-134">Enable reverb on the video playback</span></span>
<span data-ttu-id="ca034-135">Для включения переглагола в источнике звука необходимо выполнить два действия.</span><span class="sxs-lookup"><span data-stu-id="ca034-135">There are two steps to enable reverb on an audio source:</span></span>
* <span data-ttu-id="ca034-136">Маршрутизация **источника звука** в соответствующую **группу**</span><span class="sxs-lookup"><span data-stu-id="ca034-136">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="ca034-137">Настройка подключаемого модуля **Microsoft спатиализер** для передачи звука в **группу** для обработки</span><span class="sxs-lookup"><span data-stu-id="ca034-137">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="ca034-138">На следующих шагах мы назовем наш сценарий для управления маршрутизацией аудио и подключим сценарий управления, предоставляемый с подключаемым модулем **Microsoft спатиализер** , для передачи данных в переглагол.</span><span class="sxs-lookup"><span data-stu-id="ca034-138">In the following steps, we'll adjust our script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="ca034-139">На панели **инспектора** для **четырех**нажмите кнопку **Добавить компонент** и добавьте сценарий **уровня отправки "действие комнаты** ":</span><span class="sxs-lookup"><span data-stu-id="ca034-139">On the **Inspector** pane for the **Quad**, click **Add Component** and add the **Room Effect Send Level** script:</span></span>

![Добавить скрипт уровня отправки](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> <span data-ttu-id="ca034-141">Если вы не включите **уровень отправки "воздействие на комнату** " в подключаемом модуле **Microsoft спатиализер** , он не отправляет звук обратно в подсистему аудиозаписи Unity для обработки эффектов.</span><span class="sxs-lookup"><span data-stu-id="ca034-141">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="ca034-142">Компонент **уровня отправки "эффекты комнаты** " включает элемент управления "график", который задает уровень звука, отправляемого в подсистему аудиозаписи Unity для обработки в виде переглагола.</span><span class="sxs-lookup"><span data-stu-id="ca034-142">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="ca034-143">Щелкните и перетащите кривую вниз, чтобы установить уровень около-30dB:</span><span class="sxs-lookup"><span data-stu-id="ca034-143">Click and drag the curve downwards to set the level to about -30dB:</span></span>

![Настройка кривой реглагола](images/spatial-audio/adjust-reverb-curve.png)

<span data-ttu-id="ca034-145">Затем раскомментируйте 4 строки с комментариями в сценарии **спатиализеонофф** .</span><span class="sxs-lookup"><span data-stu-id="ca034-145">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="ca034-146">Теперь сценарий будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ca034-146">The script will now look like this:</span></span>
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="ca034-147">Раскомментируя эти строки, добавляет два свойства на панель **инспектора** для скрипта.</span><span class="sxs-lookup"><span data-stu-id="ca034-147">Uncommenting these lines adds two properties to the **Inspector** pane for the script.</span></span> <span data-ttu-id="ca034-148">Чтобы задать их, на панели **инспектора** в компоненте **Спатиализе on** of **четыре**:</span><span class="sxs-lookup"><span data-stu-id="ca034-148">To set these, on the **Inspector** pane of the **Spatialize On Off** component of the **Quad**:</span></span>
* <span data-ttu-id="ca034-149">Установка свойства **группы эффектов комнаты** в новую группу микшеров эффектов комнаты</span><span class="sxs-lookup"><span data-stu-id="ca034-149">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="ca034-150">Задание свойства **главной группы** для главной группы микшера</span><span class="sxs-lookup"><span data-stu-id="ca034-150">Set the **Master Group** property to the Master mixer group</span></span>

<span data-ttu-id="ca034-151">После этих изменений свойства **Спатиализе On Off** будут выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ca034-151">After these changes, the **Spatialize On Off** properties will look like this:</span></span>

![Спатиализе On Off](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a><span data-ttu-id="ca034-153">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="ca034-153">Next steps</span></span>

<span data-ttu-id="ca034-154">Попробуйте приложение в HoloLens 2 или в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="ca034-154">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="ca034-155">Теперь, когда вы намерены нажать кнопку в приложении, чтобы активировать пространственность, сценарий направит звук видео в группу эффектов комнаты, чтобы добавить переглагол.</span><span class="sxs-lookup"><span data-stu-id="ca034-155">Now, when touching the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="ca034-156">При переключении на стерео вы направите звук в главную группу и не добавите команду.</span><span class="sxs-lookup"><span data-stu-id="ca034-156">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

<span data-ttu-id="ca034-157">Вы завершили учебники по пространственному звуку HoloLens 2 для Unity.</span><span class="sxs-lookup"><span data-stu-id="ca034-157">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="ca034-158">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="ca034-158">Congratulations!</span></span>


