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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="44743-104">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="44743-104">Spatial Sound in Unity</span></span>

<span data-ttu-id="44743-105">На этой странице содержатся ссылки на ресурсы, которые помогут вам использовать и спроектировать Microsoft ХРТФ спатиализер в проектах Unity Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="44743-105">This page links to resources to help you use and design with the Microsoft HRTF spatializer in your Unity mixed reality projects.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="44743-106">Включить пространственность</span><span class="sxs-lookup"><span data-stu-id="44743-106">Enable spatialization</span></span>

<span data-ttu-id="44743-107">Включите параметр **MS Хртф спатиализер** в параметрах звука вашего проекта.</span><span class="sxs-lookup"><span data-stu-id="44743-107">Enable the **MS HRTF Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="44743-108">Дополнительные сведения см. в [документации по Спатиализер Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span><span class="sxs-lookup"><span data-stu-id="44743-108">For more details, see [Unity's spatializer documentation](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span></span> 

<span data-ttu-id="44743-109">Подключите **звуковой источник** к объекту в иерархии и включите пространственность, установив флажок **включить пространственность** и переместив ползунок **пространственного смешения** в значение 1.</span><span class="sxs-lookup"><span data-stu-id="44743-109">Attach an **Audio Source** to an object in the hierarchy, and enable spatialization by checking the **Enable spatialization** checkbox and moving the **Spatial Blend** slider to '1'.</span></span> <span data-ttu-id="44743-110">Дополнительные сведения см. в [документации по источнику аудио в Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span><span class="sxs-lookup"><span data-stu-id="44743-110">For more details, see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span></span> 

## <a name="design-with-spatialization"></a><span data-ttu-id="44743-111">Проектирование с использованием пространственных</span><span class="sxs-lookup"><span data-stu-id="44743-111">Design with spatialization</span></span>

### <a name="distance-based-attenuation"></a><span data-ttu-id="44743-112">Ослабление на основе расстояния</span><span class="sxs-lookup"><span data-stu-id="44743-112">Distance-based attenuation</span></span>
<span data-ttu-id="44743-113">По умолчанию Unity на основе расстояния Decay имеет минимальное расстояние в 1 метра и максимальное расстояние 500 метров с логарифмической роллоффой.</span><span class="sxs-lookup"><span data-stu-id="44743-113">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="44743-114">Это может работать в вашем сценарии, иначе источники могут оказаться слишком быстрыми или слишком медленными.</span><span class="sxs-lookup"><span data-stu-id="44743-114">This may work for your scenario, or you may find sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="44743-115">Сведения о настройке кривых в Unity см. в статье о [разработке звука в смешанной реальности](spatial-sound-design.md) рекомендуемых параметров для Decay расстояний. см. [документацию по источнику аудио в Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) .</span><span class="sxs-lookup"><span data-stu-id="44743-115">See [sound design in mixed reality](spatial-sound-design.md) for recommended settings for distance decay curves, and see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for information on setting these curves in Unity.</span></span>

### <a name="environment"></a><span data-ttu-id="44743-116">Среда</span><span class="sxs-lookup"><span data-stu-id="44743-116">Environment</span></span>
<span data-ttu-id="44743-117">**MS Хртф спатиализер** включает компонент переглагола комнаты с [четырьмя параметрами перенастройки](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) и значением по умолчанию "Small".</span><span class="sxs-lookup"><span data-stu-id="44743-117">The **MS HRTF Spatializer** includes a room reverb component with [four reverb settings](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) and a default of 'small'.</span></span> <span data-ttu-id="44743-118">Параметр комнаты можно изменить программным способом для каждого источника звука, присоединив следующий C# скрипт к каждому объекту в Unity, имеющему пространственный источник аудио:</span><span class="sxs-lookup"><span data-stu-id="44743-118">The room setting can be changed programmatically for each audio source by attaching the following C# script to each object in Unity that has a spatialized Audio Source:</span></span>

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

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="44743-119">Примеры пространственных звуков Unity</span><span class="sxs-lookup"><span data-stu-id="44743-119">Unity spatial sound examples</span></span>
<span data-ttu-id="44743-120">Набор средств для смешанной реальности (МРТК) включает примеры способов применения звуковых эффектов в смешанной реальности: [демонстрации мртк](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span><span class="sxs-lookup"><span data-stu-id="44743-120">The Mixed Reality Toolkit (MRTK) includes examples of ways to apply audio effects in mixed reality: [MRTK demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span></span>

