---
title: Визуализация пространственной сетки
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Смешанная реальность, HoloLens, элементы управления ИП, взаимодействие, Пользовательский интерфейс, UX, проектирование UX, пространственный пользовательский интерфейс, пространственное взаимодействие, трехмерный Пользовательский интерфейс, трехмерный UI
ms.openlocfilehash: 17a799dcaba5caf4dd7018f8289cad02b40f1277
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2020
ms.locfileid: "85346135"
---
# <a name="spatial-mesh"></a>Пространственный сетчатый

![Пространственный сетчатый](images/UX/MRTK_PulseShader_SpatialMesh.gif)

С помощью визуализации пространственной сетки пользователь может узнать, как устройство воспринимает и понимает физическую среду. В дополнение к пространственному контексту, правильная визуализация пространственной сетки может создавать удобство и Magical интерфейс.  

## <a name="design-guideline"></a>Рекомендации по проектированию
Поскольку важно позволить пользователю сосредоточиться на содержимом и взаимодействовать с ним, непрерывная и повторная визуализация пространственной сетки в фоновом режиме может отвлечь вас. Рекомендуется как можно реже визуализировать среду, либо только один раз при первом запуске, либо когда пользователь показывает четкую намерение для просмотра сети окружающей среды, нацеливание на место и касание воздуха. Это поведение можно наблюдать в оболочке HoloLens.
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Визуализация пространственной сетки в МРТК (набор средств для смешанной реальности) для Unity
МРТК предоставляет несколько материалов для визуализации пространственной сетки.

- **MRTK_Wireframe. материально, MRTK_Wireframe.** Material: материал статической пространственной сетки по умолчанию, который показывает контур сетки без анимации. Этот материал полезен в целях отладки, так как он отображает все геометрические объекты сетки. Однако не рекомендуется для рабочей среды.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction.** материально. этот материал предоставляет анимированный импульсный результат для пространственной сетки. Вы можете использовать этот материал для визуализации среды на конкретный момент работы или на входе пользователя в Air. Примеры см. в сцене **пулсешадерексамплес. Unity** .
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* Дополнительные сведения см. в разделе [мртк-spatial осведомленность](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) и [Мртк-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) .

<br>

---

## <a name="see-also"></a>См. также

* [Курсоры](cursors.md)
* [Телекинез](point-and-commit.md)
* [Кнопка](button.md)
* [Активный объект](interactable-object.md)
* [Ограничивающая рамка и панель приложения](app-bar-and-bounding-box.md)
* [Оперирование](direct-manipulation.md)
* [Меню руки](hand-menu.md)
* [Быстрое меню](near-menu.md)
* [Коллекция объектов](object-collection.md)
* [Голосовая команда](voice-input.md)
* [Клавиатура](keyboard.md)
* [Подсказка](tooltip.md)
* [Планшет](slate.md)
* [Ползунок](slider.md)
* [Шейдер](shader.md)
* [Биллбординг и закрепление элемента в пространстве](billboarding-and-tag-along.md)
* [Индикация хода выполнения](progress.md)
* [Притяжение к поверхности](surface-magnetism.md)
