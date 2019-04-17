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
# <a name="spatial-sound-in-unity"></a>Пространственные звук в Unity

В этом разделе описывается использование пространственный звук в ваших проектов Unity. Рассматриваются файлы необходимый подключаемый модуль, а также компоненты Unity и свойства, позволяющие пространственный звук.

## <a name="enabling-spatial-sound-in-unity"></a>Включение пространственных звук в Unity

Звук пространственный индекс, в Unity, включается с помощью подключаемого модуля spatializer аудио. Файлами подключаемого модуля объединяются непосредственно в Unity, поэтому включение пространственных звук так же просто, как будет **изменить > Параметры проекта > аудио** и изменив **подключаемый модуль Spatializer** в инспекторе для  **MS HRTF Spatializer**. Так как только Microsoft spatializer в настоящее время поддерживает 48000 Гц, также следует задать 48000 во избежание сбоя HRTF в тех редких случаях, что устройства вывода системы не присвоено 48000 уже частота выборки вашей системы:

![Инспектор для AudioManager](images/audio-250px.png)<br>
*Инспектор для AudioManager*

Чтобы использовать звуковой пространственный теперь настроен проекта Unity.

>[!NOTE]
>Если вы не используете ПК с Windows 10 для разработки, вы не получите пространственный звук в редакторе, а также на устройстве (даже если вы используете пакет SDK для Windows 10).

## <a name="using-spatial-sound-in-unity"></a>С помощью пространственных звук в Unity

Звук пространственный индекс используется в проекте Unity с помощью трех параметров на компоненты источника аудио. Следующие действия будут настроить компоненты источника звука для звука пространственный индекс.
* В **иерархии** панели, выберите объект игры с вложенным **источника аудио**.
* В **инспектор** панели **источника аудио** компонента
    * Проверьте **Spatialize** параметр.
    * Задайте **пространственных Blend** для **3D** (числовое значение 1).
    * Для получения наилучших результатов разверните **3D Параметры звука** и задайте **Rolloff тома** для **Custom Rolloff**.

![Панели инспектора в Unity, отображающее источник аудио](images/audiosource.png)<br>
*Панели инспектора в Unity, отображающее источник аудио*

Звук теперь в действительности существуют внутри среды проекта!

Настоятельно рекомендуется ознакомиться с [рекомендации по проектированию звук пространственный](spatial-sound-design.md). Эти рекомендации помогут вам без проблем интегрировать звукового в проект и Дополнительно установите пользователей в среду, которую вы создали.

## <a name="setting-spatial-sound-settings"></a>Параметры пространственных звука

Подключаемый модуль Microsoft пространственный звук предоставляет дополнительный параметр, который может быть задано, на основе Аудиоисточник, чтобы разрешить дополнительное управление аудио имитации. Этот параметр является размер имитации комнате.

### <a name="room-size"></a>Размер области колебания

Размер места, которое моделируется с помощью звукового сигнала пространственный индекс. Приблизительные размеры комнаты являются; небольшой (office для небольших конференц-зале), Средний (большой конференц-зале) и крупных (на английском языке). Также можно указать размер комнаты нет для имитации наружной среды. Имеет небольшой размер места по умолчанию.

### <a name="example"></a>Пример

MixedRealityToolkit для Unity предоставляет статический класс, который делает задание параметров звук пространственный легко. Этот класс можно найти в [MixedRealityToolkit\SpatialSound папку](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) и могут вызываться из любого скрипта в проекте. Рекомендуется задать эти параметры для каждого компонента источника аудио в проекте. В следующем примере показано, выбрав размер среднего комнаты для присоединенного источника аудио.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Непосредственно доступ к параметрам из Unity

Если вы не хотите использовать отличные средства аудио в MixedRealityToolkit, вот как изменить параметры HRTF. Вы можете скопировать и вставить это в сценарий с именем *SetHRTF.cs* , требуется подключение к каждой AudioSource HRTF. Он позволяет изменить важные параметры на HRTF.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Пространственные звук в наборе средств для смешанной реальности
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

В следующих примерах из набора средств смешанной реальности показаны общие аудио эффект примеры, демонстрирующие способы сделать более подробная своими впечатлениями с помощью звук.
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>См. также
* [Пространственные звука](spatial-sound.md)
* [Пространственные систему](spatial-sound-design.md)
