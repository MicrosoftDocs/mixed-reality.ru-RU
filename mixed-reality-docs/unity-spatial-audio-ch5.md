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
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a>Использование переглагола для добавления расстояния в пространственный звук

## <a name="objectives"></a>Задачи
В предыдущих главах мы добавили пространственность для звуков, чтобы дать им представление о направлении. В этой 5-й главе мы добавим действие с переглаголом, чтобы дать звуковое представление о расстоянии. Наши цели:
* Улучшение наблюдаемого расстояния источников звука путем добавления переглагола
* Управление воспринимаемым расстоянием звука с помощью расстояния прослушивателя к голограмме

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Добавление группы микшера и действия по передействию
В [главе 2](unity-spatial-audio-ch2.md)мы добавили микшер. Микшер включает одну **группу** по умолчанию — **master**. Так как мы хотим применить к некоторым звукам только переглаголные эффекты, добавим вторую **группу** для этих звуков. Чтобы добавить **группу**, щелкните правой кнопкой мыши **главную** группу в **микшере аудио** и выберите **Добавить дочернюю группу**:

![Добавить дочернюю группу](images/spatial-audio/add-child-group.png)

В этом примере мы назвали новую группу "воздействие на комнату".

Каждая **Группа** имеет собственный набор эффектов. Чтобы добавить действие в новую группу, нажмите кнопку **Добавить...** в новой группе и выберите пункт **перекоманда SFX**:

![Добавление переглагола SFX](images/spatial-audio/add-sfx-reverb.png)

В терминологии «звук» оригинал, унревербератедный звук называется « _сухой_», а звук после фильтрации с помощью фильтра перезапуска называется «защелка _»._ Оба пути отправляются в выходные данные, и их относительные сильные стороны в этом сочетании называются набором задолженности _/сухой_. Завлажный или сухой набор сильно влияет на смысл расстояния.

В результате **переглагола SFX** включены элементы управления для корректировки затронутого или сухой набора. Так как подключаемый модуль **Microsoft спатиализер** обрабатывает сухой путь, мы будем использовать переработку **SFX** только для пути с осторожностью. На панели **инспектора** **переглагола SFX**:
* Задайте для свойства уровень сухой (-10000 МБ) значение наименьшее.
* Задайте для свойства комнаты наибольшее значение (0 МБ).

После внесения этих изменений панель **инспектора** в параметре **SFX** будет выглядеть следующим образом:

![Свойства переглагола SFX](images/spatial-audio/sfx-reverb-properties.png)

Другие параметры управляют имитацией комнаты. В частности, **время Decay** связано с наблюдаемым размером комнаты. 

## <a name="enable-reverb-on-the-video-playback"></a>Включение переглагола при воспроизведении видео
Для включения переглагола в источнике звука необходимо выполнить два действия.
* Маршрутизация **источника звука** в соответствующую **группу**
* Настройка подключаемого модуля **Microsoft спатиализер** для передачи звука в **группу** для обработки

На следующих шагах мы назовем наш сценарий для управления маршрутизацией аудио и подключим сценарий управления, предоставляемый с подключаемым модулем **Microsoft спатиализер** , для передачи данных в переглагол.

На панели **инспектора** для **четырех**нажмите кнопку **Добавить компонент** и добавьте сценарий **уровня отправки "действие комнаты** ":

![Добавить скрипт уровня отправки](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> Если вы не включите **уровень отправки "воздействие на комнату** " в подключаемом модуле **Microsoft спатиализер** , он не отправляет звук обратно в подсистему аудиозаписи Unity для обработки эффектов.

Компонент **уровня отправки "эффекты комнаты** " включает элемент управления "график", который задает уровень звука, отправляемого в подсистему аудиозаписи Unity для обработки в виде переглагола. Щелкните и перетащите кривую вниз, чтобы установить уровень около-30dB:

![Настройка кривой реглагола](images/spatial-audio/adjust-reverb-curve.png)

Затем раскомментируйте 4 строки с комментариями в сценарии **спатиализеонофф** . Теперь сценарий будет выглядеть следующим образом:
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

Раскомментируя эти строки, добавляет два свойства на панель **инспектора** для скрипта. Чтобы задать их, на панели **инспектора** в компоненте **Спатиализе on** of **четыре**:
* Установка свойства **группы эффектов комнаты** в новую группу микшеров эффектов комнаты
* Задание свойства **главной группы** для главной группы микшера

После этих изменений свойства **Спатиализе On Off** будут выглядеть следующим образом:

![Спатиализе On Off](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a>Дальнейшие действия

Попробуйте приложение в HoloLens 2 или в редакторе Unity. Теперь, когда вы намерены нажать кнопку в приложении, чтобы активировать пространственность, сценарий направит звук видео в группу эффектов комнаты, чтобы добавить переглагол. При переключении на стерео вы направите звук в главную группу и не добавите команду.

Вы завершили учебники по пространственному звуку HoloLens 2 для Unity. Поздравляем!

