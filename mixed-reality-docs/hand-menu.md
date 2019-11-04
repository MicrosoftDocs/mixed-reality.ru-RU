---
title: Меню руки
description: Меню руки позволяют пользователям быстро открыть пользовательский интерфейс, подключенный вручную, для часто используемых функций. Это практические рекомендации и рекомендации для меню вручную.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: рука, меню, кнопка, быстрый доступ, макет
ms.openlocfilehash: ee958806ac462535b33164bb4faa4bf1aa29e709
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439255"
---
# <a name="hand-menu"></a><span data-ttu-id="ee41d-105">Меню руки</span><span class="sxs-lookup"><span data-stu-id="ee41d-105">Hand menu</span></span>

![Расположение с улнар стороны](images/MRTK_UX_HandMenu.png)

<span data-ttu-id="ee41d-107">Меню руки позволяют пользователям быстро открыть пользовательский интерфейс, подключенный вручную, для часто используемых функций.</span><span class="sxs-lookup"><span data-stu-id="ee41d-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="ee41d-108">Ниже приведены лучшие методики, которые были найдены для меню вручную.</span><span class="sxs-lookup"><span data-stu-id="ee41d-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="ee41d-109">Вы также можете найти пример сцены, демонстрирующий меню руки в [мртк](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span><span class="sxs-lookup"><span data-stu-id="ee41d-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="ee41d-110">Рекомендации по работе</span><span class="sxs-lookup"><span data-stu-id="ee41d-110">Behavior best practices</span></span>
<span data-ttu-id="ee41d-111">О. не закрывайте **несколько кнопок:** из-за близкого расстояния между заблокированным меню и глазами, а также с тенденциями пользователя сосредоточиться на относительно небольшой визуальной области в любое время (в любом случае особое внимание уделяется примерно 10 градусам), мы рекомендуем Хранение большого числа кнопок.</span><span class="sxs-lookup"><span data-stu-id="ee41d-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="ee41d-112">На основе нашего исследования один столбец с тремя кнопками хорошо работает, сохраняя все содержимое в поле View (фов), даже если пользователи перемещают свои руки в центр фов.</span><span class="sxs-lookup"><span data-stu-id="ee41d-112">Based on our exploration, one column with three buttons work well by keeping all the content within the field of view (FOV) even when users move their hands to the center of the FOV.</span></span> 

<span data-ttu-id="ee41d-113">**Б. Использование меню "рука" для быстрого действия:** вызов ARM и обслуживание этой должности может легко вызвать выносливости ARM.</span><span class="sxs-lookup"><span data-stu-id="ee41d-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="ee41d-114">Используйте метод, заблокированный вручную, для меню, для которого требуются короткие взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="ee41d-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="ee41d-115">Если меню является сложным и требует расширенного времени взаимодействия, рассмотрите возможность использования блокировки мира или блокировки текста.</span><span class="sxs-lookup"><span data-stu-id="ee41d-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="ee41d-116">**В. угол для кнопки или панели:** меню должны касаться противоположного края и середины головки: Это позволяет естественным образом перемещаться к меню с противоположной рукой и позволяет избежать неприятностей или неудобных позиций при касании кнопки.</span><span class="sxs-lookup"><span data-stu-id="ee41d-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="ee41d-117">**Г. Рассмотрите возможность поддержки одноразовой или произвольной операции:** не следует рассчитывать, что обе руки пользователя всегда доступны.</span><span class="sxs-lookup"><span data-stu-id="ee41d-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="ee41d-118">Рассмотрите широкий спектр контекстов, когда одна или обе руки недоступны, и убедитесь, что учетные записи разработки для этих ситуаций.</span><span class="sxs-lookup"><span data-stu-id="ee41d-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="ee41d-119">Для поддержки однопользовательского меню можно попытаться перейти от руки к пункту меню, заблокированному вручную, при переворачивании вручную (идет перенос в карманный ПК).</span><span class="sxs-lookup"><span data-stu-id="ee41d-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="ee41d-120">Для сценариев без участия рассмотрите возможность использования команды «Voice» для вызова кнопок меню руки.</span><span class="sxs-lookup"><span data-stu-id="ee41d-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="ee41d-121">**E. двухэтапный вызов.** если вы используете только ручное действие как событие для активации меню руки, оно может быть случайно отображено, если оно не требуется (ложный), так как люди перемещают свои руки в обоих случаях (для взаимодействия и обработки объектов). и непреднамеренно.</span><span class="sxs-lookup"><span data-stu-id="ee41d-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="ee41d-122">При возникновении ложных срабатываний в приложении рекомендуется добавить дополнительный шаг помимо события Palm, чтобы вызвать меню руки, например полностью открытые пальцы.</span><span class="sxs-lookup"><span data-stu-id="ee41d-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="ee41d-123">**Е. не добавляйте кнопки рядом с кнопкой "наладонь (системная Главная)".** если кнопки меню руки расположены слишком близко к кнопке "Главная", они могут быть случайно активированы при взаимодействии с меню руки.</span><span class="sxs-lookup"><span data-stu-id="ee41d-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="ee41d-124">**Ж. тестирование, тестирование, тестирование:** у людей есть разные тексты с различными пороговыми значениями для удобства и дискомфорт и т. д. Не забудьте протестировать проект и получить отзывы от различных людей.</span><span class="sxs-lookup"><span data-stu-id="ee41d-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="ee41d-125">Рекомендации по размещению меню руки</span><span class="sxs-lookup"><span data-stu-id="ee41d-125">Hand menu placement best practices</span></span>

<span data-ttu-id="ee41d-126">В человеческих структурах улнар нервный — это нервный, которое работает вблизи кости улна.</span><span class="sxs-lookup"><span data-stu-id="ee41d-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="ee41d-127">Улна — это длинная кость, найденная в фореарм, которая растягивается от уступа до самого маленького пальца.</span><span class="sxs-lookup"><span data-stu-id="ee41d-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="ee41d-128">Ниже приведено 2 рекомендуемых места на основе наших исследований:</span><span class="sxs-lookup"><span data-stu-id="ee41d-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="ee41d-129">![расположение](images/UlnarSideHandMenu.gif) Улнар стороны</span><span class="sxs-lookup"><span data-stu-id="ee41d-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="ee41d-130">**A. Улнар внутри карманного компьютера**</span><span class="sxs-lookup"><span data-stu-id="ee41d-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="ee41d-131">Это надежное расположение, так как руки не пересекаются друг с другом.</span><span class="sxs-lookup"><span data-stu-id="ee41d-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="ee41d-132">Это важно для точного обнаружения и отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ee41d-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ee41d-133">![расположение](images/UlnarAboveHandMenu.gif) Улнар стороны</span><span class="sxs-lookup"><span data-stu-id="ee41d-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="ee41d-134">**Б. Улнар**</span><span class="sxs-lookup"><span data-stu-id="ee41d-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="ee41d-135">Это расположение удобно для пользователей, так как им не нужно слишком много порождать ARM для взаимодействия с меню руки.</span><span class="sxs-lookup"><span data-stu-id="ee41d-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="ee41d-136">Мы рекомендуем располагать меню, **13cm** над Palm, и выровняйте кнопки в улнар Palm.</span><span class="sxs-lookup"><span data-stu-id="ee41d-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="ee41d-137">Подробнее о оптимальном размере кнопки</span><span class="sxs-lookup"><span data-stu-id="ee41d-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="ee41d-138">По техническим соображениям мы рекомендуем использовать это расположение с одной требуемой реализацией: разработчику необходимо заморозить меню, когда пользователь, противоположный себе, получит решение о близком взаимодействии с ним.</span><span class="sxs-lookup"><span data-stu-id="ee41d-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="ee41d-139">Это позволит избежать колебаний от перекрывающихся стрелок и позволяет быстрее ориентироваться на кнопки.</span><span class="sxs-lookup"><span data-stu-id="ee41d-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="ee41d-140">Камеры HoloLens 2 точно определяют руки, если они отделены друг от друга.</span><span class="sxs-lookup"><span data-stu-id="ee41d-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="ee41d-141">Любые перекрывающиеся руки могут привести к перемещению меню «рука» из расположения привязки.</span><span class="sxs-lookup"><span data-stu-id="ee41d-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="ee41d-142">Нерекомендуемые расположения меню</span><span class="sxs-lookup"><span data-stu-id="ee41d-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="ee41d-143">Мы выполнили исследование пользователей с помощью различных макетов и расположений в меню, поэтому **не рекомендуется использовать**следующие расположения, чтобы найти недостатки каждого исследования ниже:</span><span class="sxs-lookup"><span data-stu-id="ee41d-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="ee41d-144">![](images/AboveArm.gif) ARM</span><span class="sxs-lookup"><span data-stu-id="ee41d-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="ee41d-145">**Над ARM**</span><span class="sxs-lookup"><span data-stu-id="ee41d-145">**Above the arm**</span></span><br>
        <span data-ttu-id="ee41d-146">1 — сложно сохранить хорошее отслеживание</span><span class="sxs-lookup"><span data-stu-id="ee41d-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="ee41d-147">2 — вызывает выносливости пользователя из-за неестественного расположения</span><span class="sxs-lookup"><span data-stu-id="ee41d-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ee41d-148">![над пальцами](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="ee41d-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="ee41d-149">**Над пальцами**</span><span class="sxs-lookup"><span data-stu-id="ee41d-149">**Above fingers**</span></span><br>
        <span data-ttu-id="ee41d-150">1-выносливости, из-за длительного времени</span><span class="sxs-lookup"><span data-stu-id="ee41d-150">1 - Hand fatigue due to holding hand for long time</span></span><br>
        <span data-ttu-id="ee41d-151">две проблемы отслеживания по индексу и посередине пальца</span><span class="sxs-lookup"><span data-stu-id="ee41d-151">2 - Hand tracking issues on index and middle finger</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="ee41d-152">![выше](images/handCenter.gif) Center Palm</span><span class="sxs-lookup"><span data-stu-id="ee41d-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="ee41d-153">**Выше-Center Palm**</span><span class="sxs-lookup"><span data-stu-id="ee41d-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="ee41d-154">1\. проблемы с отслеживанием из-за перекрывающихся стрелок</span><span class="sxs-lookup"><span data-stu-id="ee41d-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="ee41d-155">2-выносливости, из-за длительного времени для взаимодействия с меню</span><span class="sxs-lookup"><span data-stu-id="ee41d-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ee41d-156">![сверху под рукой](images/TopFingerTip.gif) в **верхней части экрана**</span><span class="sxs-lookup"><span data-stu-id="ee41d-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="ee41d-157">проблемы с отслеживанием 1</span><span class="sxs-lookup"><span data-stu-id="ee41d-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="ee41d-158">2-выносливостиная рука, удерживающие руку над нормальным</span><span class="sxs-lookup"><span data-stu-id="ee41d-158">2 - Hand fatigue holding hand above normal posture</span></span><br>
        <span data-ttu-id="ee41d-159">3\. проблемы с нажатием кнопок с другими пальцами случайным образом из-за ограниченного интервала между пальцами</span><span class="sxs-lookup"><span data-stu-id="ee41d-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="ee41d-160">![обратно](images/BackOfTheArm.gif) ARM</span><span class="sxs-lookup"><span data-stu-id="ee41d-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="ee41d-161">**Задняя часть ARM**</span><span class="sxs-lookup"><span data-stu-id="ee41d-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="ee41d-162">1 — может вызвать неслучайно кнопку "домой"</span><span class="sxs-lookup"><span data-stu-id="ee41d-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="ee41d-163">2 — неестественное или удобное расположение для пользователей</span><span class="sxs-lookup"><span data-stu-id="ee41d-163">2 - Not a natural or comfortable position for users</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a><span data-ttu-id="ee41d-164">См. также</span><span class="sxs-lookup"><span data-stu-id="ee41d-164">See also</span></span>

* [<span data-ttu-id="ee41d-165">Активный объект</span><span class="sxs-lookup"><span data-stu-id="ee41d-165">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ee41d-166">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="ee41d-166">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ee41d-167">Руки и контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="ee41d-167">Hands and motion controllers</span></span>](hands-and-tools.md)