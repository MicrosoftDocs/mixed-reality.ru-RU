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
# <a name="spatial-sound-in-unity"></a>Пространственный звук в Unity

В этом разделе описывается использование пространственного звука в проектах Unity. Он охватывает необходимые файлы подключаемых модулей, а также компоненты и свойства Unity, которые позволяют использовать пространственный звук.

## <a name="enabling-spatial-sound-in-unity"></a>Включение пространственного звука в Unity

Пространственный звук в Unity включен с помощью подключаемого модуля Audio спатиализер. Файлы подключаемых модулей упаковываются непосредственно в Unity, так что включить Пространственный звук так же просто, как **редактировать > параметры проекта > звук** и изменяя **подключаемый модуль спатиализер** в инспекторе в **MS хртф спатиализер**. Так как Microsoft спатиализер поддерживает только 48000Hz в настоящее время, необходимо также задать частоту выборки системы равным 48000, чтобы предотвратить сбой ХРТФ в редких случаях, когда системное устройство вывода не имеет значение 48000.

![Инспектор для Аудиоманажер](images/audio-250px.png)<br>
*Инспектор для Аудиоманажер*

Теперь проект Unity настроен для использования пространственного звука.

>[!NOTE]
>Если вы не используете компьютер с Windows 10 для разработки, вы не сможете получить Пространственный звук в редакторе и на устройстве (даже если вы используете пакет SDK для Windows 10).

## <a name="using-spatial-sound-in-unity"></a>Использование пространственного звука в Unity

Пространственный звук используется в проекте Unity путем настройки трех параметров для компонентов источника звука. Следующие шаги настраивают компоненты источника звука для пространственного звука.
* На панели **Иерархия** выберите объект Game с подключенным **источником звука**.
* На панели **инспектора** в компоненте " **источник звука** "
    * Проверьте параметр **спатиализе** .
    * Установите для **пространственного перехода** значение **3D** (числовое значение 1).
    * Для получения наилучших результатов разверните **Параметры 3D Sound** и задайте для параметра **Volume Роллофф** значение **Custom роллофф**.

![Панель инспектора в Unity, показывающая источник звука](images/audiosource.png)<br>
*Панель инспектора в Unity, показывающая источник звука*

Теперь ваши звуки реалистично существуют в среде проекта!

Настоятельно рекомендуется ознакомиться с рекомендациями по [проектированию пространственных звуков](spatial-sound-design.md). Эти рекомендации помогут вам легко интегрировать ваш звук в ваш проект, а также для дальнейшего изучения пользователей в созданном вами интерфейсе.

## <a name="setting-spatial-sound-settings"></a>Настройка параметров пространственного звука

Подключаемый модуль пространственного звука (Майкрософт) предоставляет дополнительный параметр, который можно установить для каждого источника звука, чтобы обеспечить дополнительный контроль над имитацией звука. Этот параметр представляет размер имитации комнаты.

### <a name="room-size"></a>Размер комнаты

Размер комнаты, моделируемой пространственным звуком. Приблизительные размеры комнат. Малый (офис в небольшой конференцной комнате), средний (большой конференц-зал) и крупный (Аудиториум). Можно также указать размер комнаты None для имитации внешнего окружения. Размер комнаты по умолчанию — малый.

### <a name="example"></a>Пример

Микседреалититулкит для Unity предоставляет статический класс, который позволяет легко задавать параметры пространственного звука. Этот класс можно найти в [папке микседреалититулкит\спатиалсаунд](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) . его можно вызвать из любого скрипта в проекте. Рекомендуется задавать эти параметры для каждого компонента звукового источника в проекте. В следующем примере показано, как выбрать средний размер для присоединенного звукового источника.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Прямой доступ к параметрам из Unity

Если вы не хотите использовать отличные средства работы со звуком в Микседреалититулкит, вот как можно изменить параметры ХРТФ. Его можно скопировать или вставить в сценарий с именем *SetHRTF.CS* , который будет присоединен к каждому хртф аудиосаурце. Это позволяет изменять параметры, важные для ХРТФ.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Пространственный звук в наборе средств смешанной реальности
- [Холотулкит-ексамплес/Спатиалсаунд/сцены/Уаудиоманажертест. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Следующие примеры из набора средств для смешанной реальности — это общие примеры звуковых эффектов, демонстрирующие способы повышения удобства работы с помощью звука.
- [Холотулкит-ексамплес/Спатиалсаунд/сцены/Аудиолофитест. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [Холотулкит-ексамплес/Спатиалсаунд/сцены/Аудиукклусионтест. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>См. также
* [Пространственный звук](spatial-sound.md)
* [Проектирование пространственного звука](spatial-sound-design.md)
