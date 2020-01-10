---
title: Объявления и теги — вместе
description: Объекты с рекламой всегда ориентированы на себя для пользователя.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, объявление, пометка — вместе
ms.openlocfilehash: 24c4ca8bdc3c6ea1081311102204d4a7f5a95425
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723183"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="74580-104">Объявления и теги — вместе</span><span class="sxs-lookup"><span data-stu-id="74580-104">Billboarding and tag-along</span></span>

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="74580-105">Что такое объявление?</span><span class="sxs-lookup"><span data-stu-id="74580-105">What is billboarding?</span></span>

<span data-ttu-id="74580-106">Объявление — это концепция поведения, которую можно применить к объектам в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="74580-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="74580-107">Объекты с рекламой всегда ориентированы на себя для пользователя.</span><span class="sxs-lookup"><span data-stu-id="74580-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="74580-108">Это особенно полезно при работе с текстовыми и пошаговыми системами, в которых статические объекты, помещаемые в среду пользователя (блокировка по всему миру), в противном случае были бы скрыты или нечитаемы при перемещении пользователя.</span><span class="sxs-lookup"><span data-stu-id="74580-108">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="74580-109">Объекты с включенным объявлением можно свободно переворачивать в пользовательской среде.</span><span class="sxs-lookup"><span data-stu-id="74580-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="74580-110">Они также могут быть ограничены одной осью в зависимости от особенностей проектирования.</span><span class="sxs-lookup"><span data-stu-id="74580-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="74580-111">Не забывайте, что объекты, объявленные на щитах, могут вырезать или окклуде себя, если они помещаются слишком близко к другим объектам или в HoloLens, слишком близко к отсканированным областям.</span><span class="sxs-lookup"><span data-stu-id="74580-111">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="74580-112">Чтобы избежать этого, подумайте об общем объеме места, которое может создать объект при повороте на оси, включенной для использования в качестве рекламного объявления.</span><span class="sxs-lookup"><span data-stu-id="74580-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="74580-113">Что такое тег — вместе?</span><span class="sxs-lookup"><span data-stu-id="74580-113">What is a tag-along?</span></span>

<span data-ttu-id="74580-114">Tag — это понятие поведения, которое можно добавить в голограммы.</span><span class="sxs-lookup"><span data-stu-id="74580-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="74580-115">Объект, расположенный на теге, пытается остаться в диапазоне, который позволяет пользователю взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="74580-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="74580-116">![панель «ПИН-коды HoloLens» является хорошим примером того, как работает тег, а](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="74580-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="74580-117">*Меню Пуск HoloLens — это отличный пример поведения тегов.*</span><span class="sxs-lookup"><span data-stu-id="74580-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="74580-118">У объектов-тегов есть параметры, которые могут точно настраивать способ их поведения.</span><span class="sxs-lookup"><span data-stu-id="74580-118">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="74580-119">Содержимое может находиться в строке пользователя или вне ее, когда пользователь перемещается по своей среде.</span><span class="sxs-lookup"><span data-stu-id="74580-119">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="74580-120">По мере того, как пользователь перемещается, содержимое будет пытаться остаться в периферийноее пользователя путем перемещения к границе представления, в зависимости от того, насколько быстро перемещается пользователь, может оставить содержимое временно недоступным для просмотра.</span><span class="sxs-lookup"><span data-stu-id="74580-120">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="74580-121">Когда пользователь рассматривает объект на основе тега, он становится более полным.</span><span class="sxs-lookup"><span data-stu-id="74580-121">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="74580-122">Содержимое всегда является «кратким», поэтому пользователи никогда не забывают, в каком направлении их содержимого.</span><span class="sxs-lookup"><span data-stu-id="74580-122">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="74580-123">Дополнительные параметры могут привести к присоединению объекта-тега к заголовку пользователя с помощью резиновой полосы.</span><span class="sxs-lookup"><span data-stu-id="74580-123">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="74580-124">Ускорение или замедление приводят к повесу объекта, что делает его более физическим.</span><span class="sxs-lookup"><span data-stu-id="74580-124">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="74580-125">Эта пружинное поведение является дополнением, помогающим пользователю создать точную модель с точностью работы тега.</span><span class="sxs-lookup"><span data-stu-id="74580-125">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="74580-126">Звук помогает предоставлять дополнительные аффорданцес, когда пользователи имеют объекты в режиме "тег".</span><span class="sxs-lookup"><span data-stu-id="74580-126">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="74580-127">Звук должен усилить скорость перемещения; При быстром переходе к концу должно быть выбрано более заметное звуковое воздействие.</span><span class="sxs-lookup"><span data-stu-id="74580-127">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="74580-128">Как и в случае с содержимым, заблокированным в голову, объекты-Теги могут доказать или наусеатинг, если они слишком сильно перемещаются в представлении пользователя.</span><span class="sxs-lookup"><span data-stu-id="74580-128">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="74580-129">По мере того как пользователь просматривает, а затем быстро останавливается, его значение сообщает о том, что они были остановлены.</span><span class="sxs-lookup"><span data-stu-id="74580-129">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="74580-130">Их баланс уведомляет их о том, что их головной компьютер прекратил свою работу, а их концепция видима для выключения мира.</span><span class="sxs-lookup"><span data-stu-id="74580-130">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="74580-131">Однако если тег () поддерживает перемещение при остановке пользователя, он может запутать свое значение.</span><span class="sxs-lookup"><span data-stu-id="74580-131">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="74580-132">Реклама и теги — вместе с МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="74580-132">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="74580-133">**[Мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет скрипты для поведения на основе объявлений и тегов.</span><span class="sxs-lookup"><span data-stu-id="74580-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="74580-134">Просто назначьте сценарий Billboard.cs любому объекту, чтобы добавить поведение для объявления и сделать объект всегда лицом к вам.</span><span class="sxs-lookup"><span data-stu-id="74580-134">Simply assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="74580-135">Чтобы добавить поведение тегов, используйте сценарий RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="74580-135">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="74580-136">Можно настроить различные параметры, например время лерпинг, расстояние и степень.</span><span class="sxs-lookup"><span data-stu-id="74580-136">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="74580-137">МРТК-радиальный просмотр решения</span><span class="sxs-lookup"><span data-stu-id="74580-137">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="74580-138">МРТК-сценарий для рекламы</span><span class="sxs-lookup"><span data-stu-id="74580-138">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="74580-139">См. также статью</span><span class="sxs-lookup"><span data-stu-id="74580-139">See also</span></span>

* [<span data-ttu-id="74580-140">Курсоры</span><span class="sxs-lookup"><span data-stu-id="74580-140">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="74580-141">Телекинез</span><span class="sxs-lookup"><span data-stu-id="74580-141">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="74580-142">Button</span><span class="sxs-lookup"><span data-stu-id="74580-142">Button</span></span>](button.md)
* [<span data-ttu-id="74580-143">Активный объект</span><span class="sxs-lookup"><span data-stu-id="74580-143">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="74580-144">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="74580-144">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="74580-145">Оперирование</span><span class="sxs-lookup"><span data-stu-id="74580-145">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="74580-146">Меню руки</span><span class="sxs-lookup"><span data-stu-id="74580-146">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="74580-147">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="74580-147">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="74580-148">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="74580-148">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="74580-149">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="74580-149">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="74580-150">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="74580-150">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="74580-151">Подсказка</span><span class="sxs-lookup"><span data-stu-id="74580-151">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="74580-152">Планшет</span><span class="sxs-lookup"><span data-stu-id="74580-152">Slate</span></span>](slate.md)
* [<span data-ttu-id="74580-153">Ползунок</span><span class="sxs-lookup"><span data-stu-id="74580-153">Slider</span></span>](slider.md)
* [<span data-ttu-id="74580-154">Шейдер</span><span class="sxs-lookup"><span data-stu-id="74580-154">Shader</span></span>](shader.md)
* [<span data-ttu-id="74580-155">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="74580-155">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="74580-156">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="74580-156">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="74580-157">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="74580-157">Surface magnetism</span></span>](surface-magnetism.md)
