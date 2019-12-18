---
title: Пространственные аудио учебники — 4. Включение и отключение пространственного звука во время выполнения
description: Используйте кнопку, чтобы включить или отключить пространственность звука во время выполнения.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук
ms.openlocfilehash: 3fc9b56dc58d4c19f229d92f4562f04cbca0e7a6
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182871"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="aee56-105">Включение и отключение пространственности во время выполнения</span><span class="sxs-lookup"><span data-stu-id="aee56-105">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="aee56-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="aee56-106">Objectives</span></span>
<span data-ttu-id="aee56-107">В этой 4-ой главе вы выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="aee56-107">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="aee56-108">Добавление нового скрипта для управления пространственностью игрового объекта</span><span class="sxs-lookup"><span data-stu-id="aee56-108">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="aee56-109">Использование сценария управления пространственными из действий кнопки</span><span class="sxs-lookup"><span data-stu-id="aee56-109">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="aee56-110">Добавление скрипта управления пространственными</span><span class="sxs-lookup"><span data-stu-id="aee56-110">Add spatialization control script</span></span>
<span data-ttu-id="aee56-111">Щелкните правой кнопкой мыши в области **проекта** и создайте новый C# скрипт, выбрав **Создать-> C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="aee56-111">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="aee56-112">Присвойте своему скрипту имя "Спатиализеонофф".</span><span class="sxs-lookup"><span data-stu-id="aee56-112">Name your script "SpatializeOnOff".</span></span>

![Создать скрипт](images/spatial-audio/create-script.png)

<span data-ttu-id="aee56-114">Дважды щелкните скрипт в области **проекта** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aee56-114">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="aee56-115">Замените содержимое скрипта по умолчанию следующим:</span><span class="sxs-lookup"><span data-stu-id="aee56-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="aee56-116">Несколько строк сценария заносятся в комментарий. Эти строки будут раскомментироваться в [главе 5](unity-spatial-audio-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="aee56-116">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="aee56-117">Чтобы включить или отключить пространственность, скрипт настраивает только свойство **спатиалбленд** , при этом свойство **пространственное** значение включено.</span><span class="sxs-lookup"><span data-stu-id="aee56-117">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="aee56-118">В этом режиме Unity по-прежнему применяет кривую **тома** .</span><span class="sxs-lookup"><span data-stu-id="aee56-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="aee56-119">В противном случае, если пользователю пришлось отключить пространственное расстояние от источника, он будет слышать внезапное увеличение объема данных.</span><span class="sxs-lookup"><span data-stu-id="aee56-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="aee56-120">Если вы предпочитаете полностью отключить пространственность, измените скрипт, чтобы также настроить логическое свойство **пространственности** для переменной **объект SourceObject** .</span><span class="sxs-lookup"><span data-stu-id="aee56-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="aee56-121">Присоединение сценария и его добавление с помощью кнопки</span><span class="sxs-lookup"><span data-stu-id="aee56-121">Attach your script and drive it from the button</span></span>
<span data-ttu-id="aee56-122">На панели **инспектора** в окне « **четыре**» нажмите кнопку **Добавить компонент** и добавьте сценарий **спатиализе On Off** :</span><span class="sxs-lookup"><span data-stu-id="aee56-122">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![Добавить сценарий к четырем](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="aee56-124">В компоненте **Спатиализе on** of **четыре**:</span><span class="sxs-lookup"><span data-stu-id="aee56-124">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="aee56-125">Поиск подобъекта **PressableButtonHoloLens2-> иконандтекст-> текстмешпро** в **иерархии**</span><span class="sxs-lookup"><span data-stu-id="aee56-125">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subobject in the **Hierarchy**</span></span>
2. <span data-ttu-id="aee56-126">Перетащите **текстмешпро** субожект в поле **Буттонтекстобжект** компонента **спатиализе вкл** .</span><span class="sxs-lookup"><span data-stu-id="aee56-126">Drag the **TextMeshPro** suboject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="aee56-127">После этих изменений компонент **Спатиализе on** of **четырехъядерия** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aee56-127">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Спатиализе на отключенном базовом](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="aee56-129">Чтобы установить кнопку для вызова сценария **Спатиализе On Off** при отпускании кнопки, откройте панель **инспектора** объекта **PressableButtonHoloLens2** , найдите **взаимодействующий** компонент и выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="aee56-129">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="aee56-130">Поиск региона **OnClick ()** подраздела **событий**</span><span class="sxs-lookup"><span data-stu-id="aee56-130">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="aee56-131">Перетащите **Quad** из **иерархии** в область целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="aee56-131">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="aee56-132">Выберите **спатиализеонофф. свапспатиализатион** из раскрывающегося списка действие.</span><span class="sxs-lookup"><span data-stu-id="aee56-132">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="aee56-133">После этих изменений **взаимодействующий** компонент будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aee56-133">After these changes, the **Interactable** component will look like this:</span></span>

![Параметры действия кнопки](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="aee56-135">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="aee56-135">Next steps</span></span>
<span data-ttu-id="aee56-136">Попробуйте приложение в HoloLens 2 или в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="aee56-136">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="aee56-137">Теперь в приложении можно нажать кнопку, чтобы активировать и деактивировать пространственность в видео.</span><span class="sxs-lookup"><span data-stu-id="aee56-137">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="aee56-138">При тестировании в редакторе Unity нажмите клавишу пробел и прокрутите прокрутку с помощью колесика прокрутки, чтобы активировать моделирование руки.</span><span class="sxs-lookup"><span data-stu-id="aee56-138">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

<span data-ttu-id="aee56-139">Перейдите к [главе 5](unity-spatial-audio-ch5.md) , чтобы добавить наблюдаемое расстояние к звуковым источникам с помощью переглагола.</span><span class="sxs-lookup"><span data-stu-id="aee56-139">Continue on to [Chapter 5](unity-spatial-audio-ch5.md) to add perceived distance to sound sources using reverb.</span></span>

