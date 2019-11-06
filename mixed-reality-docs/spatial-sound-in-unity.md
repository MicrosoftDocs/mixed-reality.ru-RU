---
title: Пространственный звук в Unity
description: Воспроизведение пространственного звука, поступающих из определенной трехмерной точки в сцене Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, Пространственный звук, ХРТФ, размер комнаты
ms.openlocfilehash: c96717d9df9b89fbb09f0b4466ee3a9bf5c8a149
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641073"
---
# <a name="spatial-sound-in-unity"></a>Пространственный звук в Unity

На этой странице содержатся ссылки на ресурсы, которые помогут вам использовать и спроектировать Microsoft ХРТФ спатиализер в проектах Unity Mixed Reality.

## <a name="enable-spatialization"></a>Включить пространственность

Включите параметр **MS Хртф спатиализер** в параметрах звука вашего проекта. Дополнительные сведения см. в [документации по Спатиализер Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html). 

Подключите **звуковой источник** к объекту в иерархии и включите пространственность, установив флажок **включить пространственность** и переместив ползунок **пространственного смешения** в значение 1. Дополнительные сведения см. в [документации по источнику аудио в Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html). 

## <a name="design-with-spatialization"></a>Проектирование с использованием пространственных

### <a name="distance-based-attenuation"></a>Ослабление на основе расстояния
По умолчанию Unity на основе расстояния Decay имеет минимальное расстояние в 1 метра и максимальное расстояние 500 метров с логарифмической роллоффой. Это может работать в вашем сценарии, иначе источники могут оказаться слишком быстрыми или слишком медленными. Сведения о настройке кривых в Unity см. в статье о [разработке звука в смешанной реальности](spatial-sound-design.md) рекомендуемых параметров для Decay расстояний. см. [документацию по источнику аудио в Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) .

### <a name="environment"></a>Среда
**MS Хртф спатиализер** включает компонент переглагола комнаты с [четырьмя параметрами перенастройки](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) и значением по умолчанию "Small". Параметр комнаты можно изменить программным способом для каждого источника звука, присоединив следующий C# скрипт к каждому объекту в Unity, имеющему пространственный источник аудио:

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

## <a name="unity-spatial-sound-examples"></a>Примеры пространственных звуков Unity
Набор средств для смешанной реальности (МРТК) включает примеры способов применения звуковых эффектов в смешанной реальности: [демонстрации мртк](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).

