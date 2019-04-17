---
title: Элементом объекта
description: Кнопка уже давно метафоры, вызывающих срабатывание события в мире двухмерной абстрактным. В мире трехмерного смешанной реальности мы не нужно ограничиваться мире больше абстракции.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Смешанная реальность, элементов управления, взаимодействие, пользовательского интерфейса, ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601179"
---
# <a name="interactable-object"></a><span data-ttu-id="eda7d-105">Элементом объекта</span><span class="sxs-lookup"><span data-stu-id="eda7d-105">Interactable object</span></span>

<span data-ttu-id="eda7d-106">Кнопка уже давно метафоры, вызывающих срабатывание события в мире двухмерной абстрактным.</span><span class="sxs-lookup"><span data-stu-id="eda7d-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="eda7d-107">В мире трехмерного смешанной реальности мы не нужно ограничиваться мире больше абстракции.</span><span class="sxs-lookup"><span data-stu-id="eda7d-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="eda7d-108">Что-то может быть **элементом объекта** , запускает событие.</span><span class="sxs-lookup"><span data-stu-id="eda7d-108">Anything can be an **Interactable object** that triggers an event.</span></span> <span data-ttu-id="eda7d-109">Объект элементом может быть представлено как что-либо из чашку кофе в таблице для всплывающей с плавающей запятой в воздухе.</span><span class="sxs-lookup"><span data-stu-id="eda7d-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="eda7d-110">Мы по-прежнему сделать использование традиционных кнопок в конкретной ситуации, например, в диалоговом окне пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eda7d-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="eda7d-111">Визуальное представление кнопки зависит от контекста.</span><span class="sxs-lookup"><span data-stu-id="eda7d-111">The visual representation of the button depends on the context.</span></span>

![Изображение героя interactible объекта](images/640px-interactibleobject-hero-640px.jpg)


<span data-ttu-id="eda7d-113">В  **[смешанной реальности Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, мы создали ряд скриптов Unity и prefabs, которые помогут вам создавать объекты элементом.</span><span class="sxs-lookup"><span data-stu-id="eda7d-113">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, we have created a series of Unity scripts and prefabs that will help you create Interactable objects.</span></span> <span data-ttu-id="eda7d-114">Их можно использовать для создания любого типа объекта, который пользователь может взаимодействовать с ними с помощью этих состояний стандартное взаимодействие: наблюдения, целевые и нажата.</span><span class="sxs-lookup"><span data-stu-id="eda7d-114">You can use these to create any type of object that the user can interact with, using these standard interaction states: observation, targeted and pressed.</span></span> <span data-ttu-id="eda7d-115">Вы можете легко настроить графический Дизайн с помощью собственных средств.</span><span class="sxs-lookup"><span data-stu-id="eda7d-115">You can easily customize the visual design with your own assets.</span></span> <span data-ttu-id="eda7d-116">Создание и назначение соответствующих клипов анимации для взаимодействия состояний в Unity контроллер анимации или используя смещение и масштабирования можно настроить подробные анимации.</span><span class="sxs-lookup"><span data-stu-id="eda7d-116">Detailed animations can be customized by either creating and assigning corresponding animation clips for the interaction states in the Unity's animation controller or using offset and scale.</span></span> 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a><span data-ttu-id="eda7d-117">Визуальную обратную связь для взаимодействия разных входных состояний</span><span class="sxs-lookup"><span data-stu-id="eda7d-117">Visual feedback for the different input interaction states</span></span>

<span data-ttu-id="eda7d-118">В смешанной реальности так как holographic объекты используются переменные типов с реальной среде, это может быть сложно понять, какие объекты будут элементом.</span><span class="sxs-lookup"><span data-stu-id="eda7d-118">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="eda7d-119">Для любых объектов элементом в интерфейсе очень важно для предоставления дифференцированных визуальную обратную связь для каждого входного состояния.</span><span class="sxs-lookup"><span data-stu-id="eda7d-119">For any interactable objects in your experience, it is important to provide differentiated visual feedback for each input state.</span></span> <span data-ttu-id="eda7d-120">Это поможет пользователю понять, какая часть работы элементом и делает пользователь уверены в том, с помощью метода согласованного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="eda7d-120">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

<span data-ttu-id="eda7d-121">Для любых объектов, пользователь может взаимодействовать, рекомендуется иметь разные визуальную обратную связь для этих трех входных состояний:</span><span class="sxs-lookup"><span data-stu-id="eda7d-121">For any objects that user can interact with, we recommended to have different visual feedback for these three input states:</span></span>
* <span data-ttu-id="eda7d-122">**Наблюдение за**: По умолчанию простоя состояние объекта.</span><span class="sxs-lookup"><span data-stu-id="eda7d-122">**Observation**: Default idle state of the object.</span></span>
* <span data-ttu-id="eda7d-123">**Целевые**: Когда объект становится целью с курсором взглядом, пальца указатель с учетом расположения или движения контроллера.</span><span class="sxs-lookup"><span data-stu-id="eda7d-123">**Targeted**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="eda7d-124">**Нажата**: При нажатии объекта с помощью жестов жест касания, нажмите пальца или движения контроллера для кнопки "выбрать".</span><span class="sxs-lookup"><span data-stu-id="eda7d-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="eda7d-125">![Holographic кнопки](images/640px-interactibleobject-holographicbutton-650px.jpg)</span><span class="sxs-lookup"><span data-stu-id="eda7d-125">![Holographic button](images/640px-interactibleobject-holographicbutton-650px.jpg)</span></span><br>
<span data-ttu-id="eda7d-126">*Наблюдение состояния, целевые состояния и нажат*</span><span class="sxs-lookup"><span data-stu-id="eda7d-126">*Observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="eda7d-127">В Windows Mixed Reality вы найдете примеры, визуализировать различные состояния ввода, в меню "Пуск" и кнопок панели приложения.</span><span class="sxs-lookup"><span data-stu-id="eda7d-127">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> <span data-ttu-id="eda7d-128">Методы, такие как выделение или масштабирования можно использовать для предоставления визуальной обратной связи для состояния ввода пользователя.</span><span class="sxs-lookup"><span data-stu-id="eda7d-128">You can use techniques such as highlighting or scaling to provide visual feedback to the user’s input states.</span></span>

<span data-ttu-id="eda7d-129">В 2 HoloLens так как он поддерживает полные руки, отслеживание ввода, мы предоставляем дополнительные читаемости, в зависимости от близости к руки.</span><span class="sxs-lookup"><span data-stu-id="eda7d-129">In HoloLens 2, since it supports fully articulated hand tracking input, we can provide additional affordances based on the proximity to the hands.</span></span> <span data-ttu-id="eda7d-130">[Кнопку в HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) показан этот пример.</span><span class="sxs-lookup"><span data-stu-id="eda7d-130">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows this example.</span></span>

![Pressable кнопки](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a><span data-ttu-id="eda7d-132">Примеры элементом объекта</span><span class="sxs-lookup"><span data-stu-id="eda7d-132">Interactable object samples</span></span>

### <a name="mesh-button"></a><span data-ttu-id="eda7d-133">Кнопка сетки</span><span class="sxs-lookup"><span data-stu-id="eda7d-133">Mesh button</span></span>

![Кнопка сетки](images/640px-interactibleobject-meshbutton.jpg)

<span data-ttu-id="eda7d-135">Ниже приведены примеры, с помощью примитивов и импортированные трехмерных сеток как элементом объекты.</span><span class="sxs-lookup"><span data-stu-id="eda7d-135">These are examples using primitives and imported 3D meshes as Interactable objects.</span></span> <span data-ttu-id="eda7d-136">Можно легко назначить различные значения масштабирования, смещение и цвет реагировать на каждое состояние входного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="eda7d-136">You can easily assign different scale, offset and color values to respond to each input interaction state.</span></span>

### <a name="toolbar"></a><span data-ttu-id="eda7d-137">панель инструментов;</span><span class="sxs-lookup"><span data-stu-id="eda7d-137">Toolbar</span></span>

![панель инструментов;](images/640px-interactibleobject-toolbar.jpg)

<span data-ttu-id="eda7d-139">Панель инструментов — это широко используемый шаблон в смешанной реальности опыт.</span><span class="sxs-lookup"><span data-stu-id="eda7d-139">A toolbar is a widely used pattern in mixed reality experiences.</span></span> <span data-ttu-id="eda7d-140">Это простой коллекции кнопок, дополнительные поведения, такие как [Billboarding и tag-along](billboarding-and-tag-along.md).</span><span class="sxs-lookup"><span data-stu-id="eda7d-140">It is a simple collection of buttons with additional behaviors such as [Billboarding and tag-along](billboarding-and-tag-along.md).</span></span> <span data-ttu-id="eda7d-141">В этом примере скрипта Billboarding и tag-along из MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="eda7d-141">This example uses a Billboarding and tag-along script from the MixedRealityToolkit.</span></span> <span data-ttu-id="eda7d-142">Вы можете управлять подробные поведения, включая расстояние перемещения скорость и пороговое значение.</span><span class="sxs-lookup"><span data-stu-id="eda7d-142">You can control detailed behaviors including distance, moving speed and threshold values.</span></span>

### <a name="traditional-button"></a><span data-ttu-id="eda7d-143">Традиционные кнопки</span><span class="sxs-lookup"><span data-stu-id="eda7d-143">Traditional button</span></span>

![Традиционные кнопки](images/640px-interactibleobject-traditionalbutton.jpg)

<span data-ttu-id="eda7d-145">В этом примере показана кнопка "традиционные 2D".</span><span class="sxs-lookup"><span data-stu-id="eda7d-145">This example shows a traditional 2D style button.</span></span> <span data-ttu-id="eda7d-146">Каждое состояние входного имеет немного другой глубины и анимации свойства.</span><span class="sxs-lookup"><span data-stu-id="eda7d-146">Each input state has a slightly different depth and animation property.</span></span>

### <a name="other-examples"></a><span data-ttu-id="eda7d-147">Другие примеры</span><span class="sxs-lookup"><span data-stu-id="eda7d-147">Other examples</span></span>

<span data-ttu-id="eda7d-148">![Кнопка](images/640px-interactibleobject-pushbutton.jpg)</span><span class="sxs-lookup"><span data-stu-id="eda7d-148">![Push button](images/640px-interactibleobject-pushbutton.jpg)</span></span><br>
<span data-ttu-id="eda7d-149">*Кнопка*</span><span class="sxs-lookup"><span data-stu-id="eda7d-149">*Push button*</span></span>
<br>
<span data-ttu-id="eda7d-150">![Реальный объект жизнь](images/640px-interactibleobject-reallifeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="eda7d-150">![Real Life object](images/640px-interactibleobject-reallifeobject.jpg)</span></span><br>
<span data-ttu-id="eda7d-151">*Реальной жизни объекта*</span><span class="sxs-lookup"><span data-stu-id="eda7d-151">*Real life object*</span></span>

<span data-ttu-id="eda7d-152">С помощью HoloLens вы можете использовать физическое пространство.</span><span class="sxs-lookup"><span data-stu-id="eda7d-152">With HoloLens, you can leverage physical space.</span></span> <span data-ttu-id="eda7d-153">Представьте себе holographic кнопки на физический стене.</span><span class="sxs-lookup"><span data-stu-id="eda7d-153">Imagine a holographic push button on a physical wall.</span></span> <span data-ttu-id="eda7d-154">Или как насчет выпить чашку кофе на реальной?</span><span class="sxs-lookup"><span data-stu-id="eda7d-154">Or how about a coffee cup on a real table?</span></span> <span data-ttu-id="eda7d-155">Использование трехмерных моделей, импортированные из программное обеспечение для моделирования, можно создать объект элементом, который похож на реальной жизни объекта.</span><span class="sxs-lookup"><span data-stu-id="eda7d-155">Using 3D models imported from modeling software, we can create an Interactable object that resembles real life object.</span></span> <span data-ttu-id="eda7d-156">Так как это цифровых объектов, мы можем добавить магического взаимодействий к нему.</span><span class="sxs-lookup"><span data-stu-id="eda7d-156">Since it's a digital object, we can add magical interactions to it.</span></span>

## <a name="interactable-object-in-mixed-reality-toolkit"></a><span data-ttu-id="eda7d-157">Элементом объекта в смешанной реальности Toolkit</span><span class="sxs-lookup"><span data-stu-id="eda7d-157">Interactable object in Mixed Reality Toolkit</span></span>
<span data-ttu-id="eda7d-158">Можно найти [примеры Interactable объекта в смешанной реальности Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span><span class="sxs-lookup"><span data-stu-id="eda7d-158">You can find the [examples of Interactable object in Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span></span>


## <a name="see-also"></a><span data-ttu-id="eda7d-159">См. также</span><span class="sxs-lookup"><span data-stu-id="eda7d-159">See also</span></span>
* [<span data-ttu-id="eda7d-160">Pressable кнопку в смешанной реальности Toolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="eda7d-160">Pressable Button on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="eda7d-161">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="eda7d-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="eda7d-162">Биллбординга и tag-along</span><span class="sxs-lookup"><span data-stu-id="eda7d-162">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
