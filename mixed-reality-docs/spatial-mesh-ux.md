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
# <a name="spatial-mesh"></a><span data-ttu-id="03b25-103">Пространственный сетчатый</span><span class="sxs-lookup"><span data-stu-id="03b25-103">Spatial mesh</span></span>

![Пространственный сетчатый](images/UX/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="03b25-105">С помощью визуализации пространственной сетки пользователь может узнать, как устройство воспринимает и понимает физическую среду.</span><span class="sxs-lookup"><span data-stu-id="03b25-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="03b25-106">В дополнение к пространственному контексту, правильная визуализация пространственной сетки может создавать удобство и Magical интерфейс.</span><span class="sxs-lookup"><span data-stu-id="03b25-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="03b25-107">Рекомендации по проектированию</span><span class="sxs-lookup"><span data-stu-id="03b25-107">Design guideline</span></span>
<span data-ttu-id="03b25-108">Поскольку важно позволить пользователю сосредоточиться на содержимом и взаимодействовать с ним, непрерывная и повторная визуализация пространственной сетки в фоновом режиме может отвлечь вас.</span><span class="sxs-lookup"><span data-stu-id="03b25-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="03b25-109">Рекомендуется как можно реже визуализировать среду, либо только один раз при первом запуске, либо когда пользователь показывает четкую намерение для просмотра сети окружающей среды, нацеливание на место и касание воздуха.</span><span class="sxs-lookup"><span data-stu-id="03b25-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="03b25-110">Это поведение можно наблюдать в оболочке HoloLens.</span><span class="sxs-lookup"><span data-stu-id="03b25-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="03b25-111">Визуализация пространственной сетки в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="03b25-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="03b25-112">МРТК предоставляет несколько материалов для визуализации пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="03b25-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="03b25-113">**MRTK_Wireframe. материально, MRTK_Wireframe.** Material: материал статической пространственной сетки по умолчанию, который показывает контур сетки без анимации.</span><span class="sxs-lookup"><span data-stu-id="03b25-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="03b25-114">Этот материал полезен в целях отладки, так как он отображает все геометрические объекты сетки.</span><span class="sxs-lookup"><span data-stu-id="03b25-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="03b25-115">Однако не рекомендуется для рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="03b25-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="03b25-116">**MRTK_SurfaceReconstruction.** материально. этот материал предоставляет анимированный импульсный результат для пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="03b25-116">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="03b25-117">Вы можете использовать этот материал для визуализации среды на конкретный момент работы или на входе пользователя в Air.</span><span class="sxs-lookup"><span data-stu-id="03b25-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="03b25-118">Примеры см. в сцене **пулсешадерексамплес. Unity** .</span><span class="sxs-lookup"><span data-stu-id="03b25-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="03b25-119">Дополнительные сведения см. в разделе [мртк-spatial осведомленность](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) и [Мртк-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) .</span><span class="sxs-lookup"><span data-stu-id="03b25-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="03b25-120">См. также</span><span class="sxs-lookup"><span data-stu-id="03b25-120">See also</span></span>

* [<span data-ttu-id="03b25-121">Курсоры</span><span class="sxs-lookup"><span data-stu-id="03b25-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="03b25-122">Телекинез</span><span class="sxs-lookup"><span data-stu-id="03b25-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="03b25-123">Кнопка</span><span class="sxs-lookup"><span data-stu-id="03b25-123">Button</span></span>](button.md)
* [<span data-ttu-id="03b25-124">Активный объект</span><span class="sxs-lookup"><span data-stu-id="03b25-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="03b25-125">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="03b25-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="03b25-126">Оперирование</span><span class="sxs-lookup"><span data-stu-id="03b25-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="03b25-127">Меню руки</span><span class="sxs-lookup"><span data-stu-id="03b25-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="03b25-128">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="03b25-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="03b25-129">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="03b25-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="03b25-130">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="03b25-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="03b25-131">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="03b25-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="03b25-132">Подсказка</span><span class="sxs-lookup"><span data-stu-id="03b25-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="03b25-133">Планшет</span><span class="sxs-lookup"><span data-stu-id="03b25-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="03b25-134">Ползунок</span><span class="sxs-lookup"><span data-stu-id="03b25-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="03b25-135">Шейдер</span><span class="sxs-lookup"><span data-stu-id="03b25-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="03b25-136">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="03b25-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="03b25-137">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="03b25-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="03b25-138">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="03b25-138">Surface magnetism</span></span>](surface-magnetism.md)
