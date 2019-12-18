---
title: Пространственный звук в Unity
description: Воспроизведение пространственного звука из определенной трехмерной точки в сцене Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, Пространственный звук, ХРТФ, размер комнаты
ms.openlocfilehash: 3e7d0ea231545d5112d182dffbc02f217ca4a4a7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181994"
---
# <a name="spatial-sound-in-unity"></a>Пространственный звук в Unity

Эта страница содержит ссылки на ресурсы для пространственного звука в Unity.

## <a name="spatializer-options"></a>Параметры спатиализер
Параметры спатиализер для приложений смешанной реальности включают:
* *Спатиализер MS хртф*. Unity предоставляет это как часть дополнительного пакета *Windows Mixed Reality* .
  * Это работает на ЦП в архитектуре с более высоким значением "один источник".
  * Это обеспечивает обратную совместимость с исходными приложениями HoloLens.
* *Microsoft спатиализер*. Это можно найти в [репозитории Microsoft Спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity).
  * В этом случае используется более экономичная архитектура с несколькими источниками.
  * В HoloLens 2 это перегружается в аппаратный ускоритель.

Для новых приложений мы рекомендуем использовать *Microsoft спатиализер*.

## <a name="enable-spatialization"></a>Включить пространственность

Используйте [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , чтобы установить _Microsoft. спатиалаудио. спатиализер. Unity_ , и выберите **Microsoft спатиализер** в параметрах звука проекта. Затем:
* Присоединение **звукового источника** к объекту в иерархии
* Установите флажок " **включить пространственность** "
* Переместить ползунок **пространственного смешения** в "1"

Дополнительные сведения см. в статье о
* [Репозиторий Microsoft спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity)
* [Руководство Майкрософт по спатиализер](unity-spatial-audio-ch1.md)
* [Документация по источнику аудио в Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Документация по спатиализер Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Затухание, связанное с расстоянием
По умолчанию Unity на основе расстояния Decay имеет минимальное расстояние в 1 метра и максимальное расстояние 500 метров с логарифмической роллоффой. Эти параметры могут работать в вашем сценарии, или вы обнаружите, что источники слишком быстро или слишком медленные. Дополнительные сведения см. в статье о
* [Создание звука в смешанной реальности](spatial-sound-design.md) для рекомендуемых параметров.
* В [документации по источнику аудио в Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) приведены инструкции по установке этих кривых.

## <a name="reverb"></a>Переглагол
По умолчанию _Microsoft спатиализер_ отключает эффекты после спатиализер. Для включения переглагола и других эффектов для пространственных источников:
* Присоединение компонента **уровня отправки "воздействие комнаты** " к каждому источнику
* Настройте кривую на уровне отправки для каждого источника, чтобы управлять усилением звука, отправляемого обратно в граф для обработки эффектов.

Дополнительные сведения см. [в главе 5 руководства по спатиализер](unity-spatial-audio-ch5.md) .

## <a name="unity-spatial-sound-examples"></a>Примеры пространственных звуков Unity
Примеры пространственного звука в Unity см. в следующих статьях:
* [Демонстрации МРТК](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Пример проекта Microsoft спатиализер](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-steps"></a>Дальнейшие действия
* [Оформление звука в смешанной реальности](spatial-sound-design.md)
* [Руководство Майкрософт по спатиализер](unity-spatial-audio-ch1.md)

