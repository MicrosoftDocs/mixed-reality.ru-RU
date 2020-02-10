---
title: Меню руки
description: Меню руки позволяют пользователям быстро открыть пользовательский интерфейс, подключенный вручную, для часто используемых функций. Это практические рекомендации и рекомендации для меню вручную.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: рука, меню, кнопка, быстрый доступ, макет
ms.openlocfilehash: 41a936d6041438c1cf1d8e4d4cc8cc30a5167491
ms.sourcegitcommit: 40b37104b0aec4554502dcc7dc430e340a6fa46a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "77092058"
---
# <a name="hand-menu"></a><span data-ttu-id="4bdb0-105">Меню руки</span><span class="sxs-lookup"><span data-stu-id="4bdb0-105">Hand menu</span></span>

![Расположение с улнар стороны](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="4bdb0-107">Меню руки позволяют пользователям быстро открыть пользовательский интерфейс, подключенный вручную, для часто используемых функций.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="4bdb0-108">Ниже приведены лучшие методики, которые были найдены для меню вручную.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="4bdb0-109">Вы также можете найти пример сцены, демонстрирующий меню руки в [мртк](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span><span class="sxs-lookup"><span data-stu-id="4bdb0-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="4bdb0-110">Рекомендации по работе</span><span class="sxs-lookup"><span data-stu-id="4bdb0-110">Behavior best practices</span></span>
<span data-ttu-id="4bdb0-111">О **. сохранить количество кнопок в маленьком виде:** из-за близкого расстояния между закрепленным меню и глазами пользователя, а также с тенденциями сосредоточиться на относительно небольшой визуальной области в любое время (особое внимание уделяется примерно 10 градусам), рекомендуется хранить небольшое количество кнопок.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="4bdb0-112">На основе нашего исследования один столбец с тремя кнопками хорошо работает, сохраняя все содержимое в поле View (фов), даже когда пользователь перемещает свои руки в центр фов.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-112">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="4bdb0-113">**Б. Использование меню "рука" для быстрого действия:** вызов ARM и обслуживание этой должности может легко вызвать выносливости ARM.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="4bdb0-114">Используйте метод, заблокированный вручную, для меню, для которого требуются короткие взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="4bdb0-115">Если меню является сложным и требует расширенного времени взаимодействия, рассмотрите возможность использования блокировки мира или блокировки текста.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="4bdb0-116">**В. угол на кнопке или панели:** меню должны касаться противоположного края и середины головки: Это позволяет естественным образом перемещаться к меню с противоположной рукой и позволяет избежать неприятностей или неудобных позиций при прикосновении к кнопкам.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="4bdb0-117">**Г. Рассмотрите возможность поддержки одноразовой или произвольной операции:** не следует рассчитывать, что обе руки пользователя всегда доступны.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="4bdb0-118">Рассмотрите широкий спектр контекстов, когда одна или обе руки недоступны, и убедитесь, что учетные записи разработки для этих ситуаций.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="4bdb0-119">Для поддержки однопользовательского меню можно попытаться перейти от руки к пункту меню, заблокированному вручную, при переворачивании вручную (идет перенос в карманный ПК).</span><span class="sxs-lookup"><span data-stu-id="4bdb0-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="4bdb0-120">Для сценариев без участия рассмотрите возможность использования команды «Voice» для вызова кнопок меню руки.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="4bdb0-121">**E. вызов из двух шагов:** если вы используете только событие "ручное" в качестве события для запуска меню "рука", оно может показаться ненужным, так как люди перемещают свои руки как можно больше (для взаимодействия и манипуляций с объектами) и случайным образом.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="4bdb0-122">При возникновении ложных срабатываний в приложении рекомендуется добавить дополнительный шаг помимо события Palm, чтобы вызвать меню руки, например полностью открытые пальцы.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="4bdb0-123">**Е. не добавляйте кнопки рядом с кнопкой "наладонь (системная Главная)".** если кнопки меню руки расположены слишком близко к кнопке "Главная", они могут быть случайно активированы при взаимодействии с меню руки.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="4bdb0-124">**Ж. тестирование, тестирование, тестирование:** у людей есть разные тексты с различными пороговыми значениями для удобства и дискомфорт и т. д. Не забудьте протестировать проект и получить отзывы от различных людей.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="4bdb0-125">Рекомендации по размещению меню руки</span><span class="sxs-lookup"><span data-stu-id="4bdb0-125">Hand menu placement best practices</span></span>

<span data-ttu-id="4bdb0-126">В человеческих структурах улнар нервный — это нервный, которое работает вблизи кости улна.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="4bdb0-127">Улна — это длинная кость, найденная в фореарм, которая растягивается от уступа до самого маленького пальца.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="4bdb0-128">Ниже приведено 2 рекомендуемых места на основе наших исследований:</span><span class="sxs-lookup"><span data-stu-id="4bdb0-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="4bdb0-129">![расположение](images/UlnarSideHandMenu.gif) Улнар стороны</span><span class="sxs-lookup"><span data-stu-id="4bdb0-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="4bdb0-130">**A. Улнар внутри карманного компьютера**</span><span class="sxs-lookup"><span data-stu-id="4bdb0-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="4bdb0-131">Это надежное расположение, так как руки не пересекаются друг с другом.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="4bdb0-132">Это важно для точного обнаружения и отслеживания.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="4bdb0-133">![расположение](images/UlnarAboveHandMenu.gif) Улнар стороны</span><span class="sxs-lookup"><span data-stu-id="4bdb0-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="4bdb0-134">**Б. Улнар**</span><span class="sxs-lookup"><span data-stu-id="4bdb0-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="4bdb0-135">Это расположение удобно для пользователей, так как им не нужно слишком много порождать ARM для взаимодействия с меню руки.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="4bdb0-136">Мы рекомендуем располагать меню, **13cm** над Palm, и выровняйте кнопки в улнар Palm.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="4bdb0-137">Подробнее о оптимальном размере кнопки</span><span class="sxs-lookup"><span data-stu-id="4bdb0-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="4bdb0-138">По техническим соображениям мы рекомендуем использовать это расположение с одной требуемой реализацией: разработчику необходимо заморозить меню, когда пользователь, противоположный себе, получит решение о близком взаимодействии с ним.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="4bdb0-139">Это позволит избежать колебаний от перекрывающихся стрелок и позволяет быстрее ориентироваться на кнопки.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="4bdb0-140">Камеры HoloLens 2 точно определяют руки, если они отделены друг от друга.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="4bdb0-141">Любые перекрывающиеся руки могут привести к перемещению меню «рука» из расположения привязки.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="4bdb0-142">Нерекомендуемые расположения меню</span><span class="sxs-lookup"><span data-stu-id="4bdb0-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="4bdb0-143">Мы выполнили исследование пользователей с помощью различных макетов и расположений в меню, поэтому **не рекомендуется использовать**следующие расположения, чтобы найти недостатки каждого исследования ниже:</span><span class="sxs-lookup"><span data-stu-id="4bdb0-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="4bdb0-144">![](images/AboveArm.gif) ARM</span><span class="sxs-lookup"><span data-stu-id="4bdb0-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="4bdb0-145">**Над ARM**</span><span class="sxs-lookup"><span data-stu-id="4bdb0-145">**Above the arm**</span></span><br>
        <span data-ttu-id="4bdb0-146">1 — сложно сохранить хорошее отслеживание</span><span class="sxs-lookup"><span data-stu-id="4bdb0-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="4bdb0-147">2 — вызывает выносливости пользователя из-за неестественного расположения</span><span class="sxs-lookup"><span data-stu-id="4bdb0-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="4bdb0-148">![над пальцами](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="4bdb0-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="4bdb0-149">**Над пальцами**</span><span class="sxs-lookup"><span data-stu-id="4bdb0-149">**Above fingers**</span></span><br>
        <span data-ttu-id="4bdb0-150">1-выносливости из-за длительного хранения</span><span class="sxs-lookup"><span data-stu-id="4bdb0-150">1 - Hand fatigue due to holding out hand for a long time</span></span><br>
        <span data-ttu-id="4bdb0-151">2 — проблемы с отслеживанием индекса и средних пальцев</span><span class="sxs-lookup"><span data-stu-id="4bdb0-151">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="4bdb0-152">![выше](images/handCenter.gif) Center Palm</span><span class="sxs-lookup"><span data-stu-id="4bdb0-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="4bdb0-153">**Выше-Center Palm**</span><span class="sxs-lookup"><span data-stu-id="4bdb0-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="4bdb0-154">1\. проблемы с отслеживанием из-за перекрывающихся стрелок</span><span class="sxs-lookup"><span data-stu-id="4bdb0-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="4bdb0-155">2-выносливости, из-за длительного времени для взаимодействия с меню</span><span class="sxs-lookup"><span data-stu-id="4bdb0-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="4bdb0-156">![сверху под рукой](images/TopFingerTip.gif) в **верхней части экрана**</span><span class="sxs-lookup"><span data-stu-id="4bdb0-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="4bdb0-157">проблемы с отслеживанием 1</span><span class="sxs-lookup"><span data-stu-id="4bdb0-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="4bdb0-158">2-выносливости с удержанием руки над нормальным</span><span class="sxs-lookup"><span data-stu-id="4bdb0-158">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="4bdb0-159">3\. проблемы с нажатием кнопок с другими пальцами случайным образом из-за ограниченного интервала между пальцами</span><span class="sxs-lookup"><span data-stu-id="4bdb0-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="4bdb0-160">![обратно](images/BackOfTheArm.gif) ARM</span><span class="sxs-lookup"><span data-stu-id="4bdb0-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="4bdb0-161">**Задняя часть ARM**</span><span class="sxs-lookup"><span data-stu-id="4bdb0-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="4bdb0-162">1 — может вызвать неслучайно кнопку "домой"</span><span class="sxs-lookup"><span data-stu-id="4bdb0-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="4bdb0-163">2 — неестественное или удобное расположение</span><span class="sxs-lookup"><span data-stu-id="4bdb0-163">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="4bdb0-164">Меню руки в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="4bdb0-164">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="4bdb0-165">**[Мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет сценарии и примеры сцен для меню руки.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="4bdb0-166">Сценарий Хандконстраинтпалмуп Solver позволяет легко подключать любые объекты к ним с помощью различных настраиваемых параметров.</span><span class="sxs-lookup"><span data-stu-id="4bdb0-166">HandConstraintPalmUp solver script allows you easily attach any objects to the hands with various configurable options.</span></span>

* [<span data-ttu-id="4bdb0-167">Меню МРТК с Хандконстраинт и Хандконстраинтпалмуп</span><span class="sxs-lookup"><span data-stu-id="4bdb0-167">MRTK - Hand Menu with HandConstraint and HandConstraintPalmUp </span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a><span data-ttu-id="4bdb0-168">См. также:</span><span class="sxs-lookup"><span data-stu-id="4bdb0-168">See also</span></span>

* [<span data-ttu-id="4bdb0-169">Курсоры</span><span class="sxs-lookup"><span data-stu-id="4bdb0-169">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="4bdb0-170">Телекинез</span><span class="sxs-lookup"><span data-stu-id="4bdb0-170">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="4bdb0-171">Кнопка</span><span class="sxs-lookup"><span data-stu-id="4bdb0-171">Button</span></span>](button.md)
* [<span data-ttu-id="4bdb0-172">Активный объект</span><span class="sxs-lookup"><span data-stu-id="4bdb0-172">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4bdb0-173">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="4bdb0-173">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="4bdb0-174">Оперирование</span><span class="sxs-lookup"><span data-stu-id="4bdb0-174">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4bdb0-175">Меню руки</span><span class="sxs-lookup"><span data-stu-id="4bdb0-175">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="4bdb0-176">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="4bdb0-176">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="4bdb0-177">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="4bdb0-177">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="4bdb0-178">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="4bdb0-178">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="4bdb0-179">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="4bdb0-179">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="4bdb0-180">Подсказка</span><span class="sxs-lookup"><span data-stu-id="4bdb0-180">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="4bdb0-181">Планшет</span><span class="sxs-lookup"><span data-stu-id="4bdb0-181">Slate</span></span>](slate.md)
* [<span data-ttu-id="4bdb0-182">Ползунок</span><span class="sxs-lookup"><span data-stu-id="4bdb0-182">Slider</span></span>](slider.md)
* [<span data-ttu-id="4bdb0-183">Шейдер</span><span class="sxs-lookup"><span data-stu-id="4bdb0-183">Shader</span></span>](shader.md)
* [<span data-ttu-id="4bdb0-184">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="4bdb0-184">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="4bdb0-185">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="4bdb0-185">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="4bdb0-186">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="4bdb0-186">Surface magnetism</span></span>](surface-magnetism.md)
