---
title: Меню руки
description: Меню руки позволяют пользователям быстро открыть пользовательский интерфейс, подключенный вручную, для часто используемых функций. Это практические рекомендации и рекомендации для меню вручную.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: рука, меню, кнопка, быстрый доступ, макет
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061175"
---
# <a name="hand-menu"></a><span data-ttu-id="71a0c-105">Меню руки</span><span class="sxs-lookup"><span data-stu-id="71a0c-105">Hand menu</span></span>

![Расположение с улнар стороны](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="71a0c-107">Меню руки — один из самых уникальных шаблонов UX в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="71a0c-107">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="71a0c-108">Он позволяет быстро открыть пользовательский интерфейс, подключенный вручную.</span><span class="sxs-lookup"><span data-stu-id="71a0c-108">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="71a0c-109">Так как она доступна в любое время и может быть отображена и скрыта, она отлично подходит для быстрых действий.</span><span class="sxs-lookup"><span data-stu-id="71a0c-109">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="71a0c-110">Рекомендации по работе с меню можно найти в списке ниже.</span><span class="sxs-lookup"><span data-stu-id="71a0c-110">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="71a0c-111">Вы также можете найти пример сцены, демонстрирующий меню руки в [мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span><span class="sxs-lookup"><span data-stu-id="71a0c-111">You can also find an example scene demonstrating the hand menu in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span></span>

<br>


---

## <a name="best-practices"></a><span data-ttu-id="71a0c-112">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="71a0c-112">Best practices</span></span>
<span data-ttu-id="71a0c-113">**Как сократить число кнопок**</span><span class="sxs-lookup"><span data-stu-id="71a0c-113">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="71a0c-114">Из-за близкого расстояния между заблокированным меню и глазами пользователя, а также с тенденциями сосредоточиться на относительно небольшой визуальной области в любое время (особое внимание уделяется примерно 10 градусам), рекомендуется хранить небольшое количество кнопок.</span><span class="sxs-lookup"><span data-stu-id="71a0c-114">Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="71a0c-115">На основе нашего исследования один столбец с тремя кнопками хорошо работает, сохраняя все содержимое в поле View (фов), даже когда пользователь перемещает свои руки в центр фов.</span><span class="sxs-lookup"><span data-stu-id="71a0c-115">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="71a0c-116">**Меню "рука" для быстрого действия**</span><span class="sxs-lookup"><span data-stu-id="71a0c-116">**Utilize hand menu for quick action**</span></span> 

<span data-ttu-id="71a0c-117">Создание ARM и обслуживание этой должности могут легко вызвать выносливости ARM.</span><span class="sxs-lookup"><span data-stu-id="71a0c-117">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="71a0c-118">Используйте метод, заблокированный вручную, для меню, для которого требуются короткие взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="71a0c-118">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="71a0c-119">Если меню является сложным и требует расширенного времени взаимодействия, рассмотрите возможность использования блокировки мира или блокировки текста.</span><span class="sxs-lookup"><span data-stu-id="71a0c-119">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="71a0c-120">**Угол для кнопки или панели**</span><span class="sxs-lookup"><span data-stu-id="71a0c-120">**Button / Panel angle**</span></span>

<span data-ttu-id="71a0c-121">Меню должны касаться противоположного края и середины головки: Это позволяет естественным образом перемещаться к меню с противоположной рукой и позволяет избежать неприятностей или неудобных позиций при прикосновении к кнопкам.</span><span class="sxs-lookup"><span data-stu-id="71a0c-121">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="71a0c-122">**Рассмотрите возможность поддержки одноразовых или практических операций**</span><span class="sxs-lookup"><span data-stu-id="71a0c-122">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="71a0c-123">Не следует рассчитывать, что обе руки пользователя всегда доступны.</span><span class="sxs-lookup"><span data-stu-id="71a0c-123">Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="71a0c-124">Рассмотрите широкий спектр контекстов, когда одна или обе руки недоступны, и убедитесь, что учетные записи разработки для этих ситуаций.</span><span class="sxs-lookup"><span data-stu-id="71a0c-124">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="71a0c-125">Для поддержки однопользовательского меню можно попытаться перейти от руки к пункту меню, заблокированному вручную, при переворачивании вручную (идет перенос в карманный ПК).</span><span class="sxs-lookup"><span data-stu-id="71a0c-125">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="71a0c-126">Для сценариев без участия можно использовать команду Voice, чтобы вызвать меню руки.</span><span class="sxs-lookup"><span data-stu-id="71a0c-126">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="71a0c-127">**Избегайте добавления кнопок рядом с кнопкой "наличный" (Главная)**</span><span class="sxs-lookup"><span data-stu-id="71a0c-127">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="71a0c-128">Если кнопки меню «рука» расположены слишком близко к кнопке «Главная», они могут быть случайно вызваны при взаимодействии с меню руки.</span><span class="sxs-lookup"><span data-stu-id="71a0c-128">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="71a0c-129">Меню руки с большими и сложными элементами управления пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="71a0c-129">Hand menu with large and complex UI controls</span></span>
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="71a0c-130">Рекомендуется ограничить число кнопок или элементов управления пользовательского интерфейса в меню, присоединенном к рукой.</span><span class="sxs-lookup"><span data-stu-id="71a0c-130">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="71a0c-131">Это связано с тем, что расширенное взаимодействие с большим количеством элементов пользовательского интерфейса может привести к выносливости ARM.</span><span class="sxs-lookup"><span data-stu-id="71a0c-131">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="71a0c-132">Если для работы требуется большое меню, предоставьте пользователю простой способ блокировки меню.</span><span class="sxs-lookup"><span data-stu-id="71a0c-132">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="71a0c-133">Одним из рекомендуемых подходов является блокировка мира, когда рука удаляется или переворачивается от пользователя.</span><span class="sxs-lookup"><span data-stu-id="71a0c-133">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="71a0c-134">Второй способ — позволить пользователю напрямую захватить меню с другой стороны.</span><span class="sxs-lookup"><span data-stu-id="71a0c-134">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="71a0c-135">Когда пользователь отпускает меню, меню должно блокироваться по всему миру.</span><span class="sxs-lookup"><span data-stu-id="71a0c-135">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="71a0c-136">Таким образом, пользователь может взаимодействовать с различными элементами пользовательского интерфейса и уверенно в течение продолжительного периода времени.</span><span class="sxs-lookup"><span data-stu-id="71a0c-136">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="71a0c-137">Если меню заблокировано по всему миру, необходимо предоставить способ перемещения меню и закрыть меню, когда оно больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="71a0c-137">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="71a0c-138">Сделайте меню перемещаемым, предоставляя маркеры на сторонах или в верхней части меню.</span><span class="sxs-lookup"><span data-stu-id="71a0c-138">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="71a0c-139">Добавьте кнопку Закрыть, чтобы разрешить закрытие меню.</span><span class="sxs-lookup"><span data-stu-id="71a0c-139">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="71a0c-140">Разрешить повторное присоединение меню к ладони, когда пользователь перейдет к пользователю.</span><span class="sxs-lookup"><span data-stu-id="71a0c-140">Allow for the menu to re-attach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="71a0c-141">Также рекомендуется требовать, чтобы пользователи просматривает свою руку, чтобы предотвратить ложные активации (см. ниже).</span><span class="sxs-lookup"><span data-stu-id="71a0c-141">We also recommend requiring that the users gazes at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="71a0c-142">**Большое меню, показывающее проблемы с удобством использования**</span><span class="sxs-lookup"><span data-stu-id="71a0c-142">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="71a0c-143">**Раскрывающееся меню, заблокированное в мире**</span><span class="sxs-lookup"><span data-stu-id="71a0c-143">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="71a0c-144">**Захват вручную & вытягивание в мир — блокировка меню**</span><span class="sxs-lookup"><span data-stu-id="71a0c-144">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="71a0c-145">Как предотвратить ложную активацию</span><span class="sxs-lookup"><span data-stu-id="71a0c-145">How to prevent false activation</span></span>

<span data-ttu-id="71a0c-146">Если вы используете действие "только Ручная архивация" как событие для запуска меню "рука", оно может быть случайно отображено, если оно не требуется (ложный), так как люди перемещают свои руки как намеренно (для взаимодействия и обработки объектов) и непреднамеренно.</span><span class="sxs-lookup"><span data-stu-id="71a0c-146">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="71a0c-147">Чтобы сократить число активаций, добавьте дополнительный шаг помимо события Palm, чтобы вызвать меню руки (например, полностью открытые пальцы или пользователь намеренно облаками в руки).</span><span class="sxs-lookup"><span data-stu-id="71a0c-147">To reduce false activations, add an additional step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="71a0c-148">**Требовать плоский карманный ПК**</span><span class="sxs-lookup"><span data-stu-id="71a0c-148">**Require Flat Palm**</span></span>

<span data-ttu-id="71a0c-149">Если требуется неструктурированная рука, можно предотвратить ложную активацию, которая может произойти, когда пользователь манипулирует объектами или жестами при взаимодействии в среде.</span><span class="sxs-lookup"><span data-stu-id="71a0c-149">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="71a0c-150">**Требовать взгляд**</span><span class="sxs-lookup"><span data-stu-id="71a0c-150">**Require Gaze**</span></span>

<span data-ttu-id="71a0c-151">Если нужно, чтобы пользователь просматривает свою руку (с глазом глаза или с помощью головного взгляда), он предотвращает ложные активации из-за того, что пользователь намеренно направлять свое внимание в качестве вторичного этапа активации (с пороговостью настраиваемого расстояния, используемой для удобства пользователя).</span><span class="sxs-lookup"><span data-stu-id="71a0c-151">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations due to the user having to intentionally direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="71a0c-152">Рекомендации по размещению меню руки</span><span class="sxs-lookup"><span data-stu-id="71a0c-152">Hand menu placement best practices</span></span>

<span data-ttu-id="71a0c-153">В человеческих структурах улнар нервный — это нервный, которое работает вблизи кости улна.</span><span class="sxs-lookup"><span data-stu-id="71a0c-153">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="71a0c-154">Улна — это длинная кость, найденная в фореарм, которая растягивается от уступа до самого маленького пальца.</span><span class="sxs-lookup"><span data-stu-id="71a0c-154">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="71a0c-155">Ниже приведено 2 рекомендуемых места на основе наших исследований:</span><span class="sxs-lookup"><span data-stu-id="71a0c-155">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="71a0c-156">![Расположение с улнар стороны](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="71a0c-156">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="71a0c-157">**A. Улнар внутри карманного компьютера**</span><span class="sxs-lookup"><span data-stu-id="71a0c-157">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="71a0c-158">Это надежное расположение, так как руки не пересекаются друг с другом.</span><span class="sxs-lookup"><span data-stu-id="71a0c-158">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="71a0c-159">Это важно для точного обнаружения и отслеживания.</span><span class="sxs-lookup"><span data-stu-id="71a0c-159">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="71a0c-160">![Расположение с улнар стороны](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="71a0c-160">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="71a0c-161">**Б. Улнар**</span><span class="sxs-lookup"><span data-stu-id="71a0c-161">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="71a0c-162">Это расположение удобно для пользователей, так как им не нужно слишком много порождать ARM для взаимодействия с меню руки.</span><span class="sxs-lookup"><span data-stu-id="71a0c-162">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="71a0c-163">Мы рекомендуем располагать меню, **13cm** над Palm, и выровняйте кнопки в улнар Palm.</span><span class="sxs-lookup"><span data-stu-id="71a0c-163">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="71a0c-164">Подробнее о оптимальном размере кнопки</span><span class="sxs-lookup"><span data-stu-id="71a0c-164">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="71a0c-165">По техническим соображениям мы рекомендуем использовать это расположение с одной требуемой реализацией: разработчику необходимо заморозить меню, когда пользователь, противоположный себе, получит решение о близком взаимодействии с ним.</span><span class="sxs-lookup"><span data-stu-id="71a0c-165">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="71a0c-166">Это позволит избежать колебаний от перекрывающихся стрелок и позволяет быстрее ориентироваться на кнопки.</span><span class="sxs-lookup"><span data-stu-id="71a0c-166">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="71a0c-167">Камеры HoloLens 2 точно определяют руки, если они отделены друг от друга.</span><span class="sxs-lookup"><span data-stu-id="71a0c-167">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="71a0c-168">Любые перекрывающиеся руки могут привести к перемещению меню «рука» из расположения привязки.</span><span class="sxs-lookup"><span data-stu-id="71a0c-168">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="71a0c-169">Нерекомендуемые расположения меню</span><span class="sxs-lookup"><span data-stu-id="71a0c-169">Menu positions that are not recommended</span></span>
<span data-ttu-id="71a0c-170">Мы выполнили исследование пользователей с помощью различных макетов и расположений в меню, поэтому **не рекомендуется использовать**следующие расположения, чтобы найти недостатки каждого исследования ниже:</span><span class="sxs-lookup"><span data-stu-id="71a0c-170">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="71a0c-171">![Выше ARM](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="71a0c-171">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="71a0c-172">**Над ARM**</span><span class="sxs-lookup"><span data-stu-id="71a0c-172">**Above the arm**</span></span><br>
        <span data-ttu-id="71a0c-173">1 — сложно сохранить хорошее отслеживание</span><span class="sxs-lookup"><span data-stu-id="71a0c-173">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="71a0c-174">2 — вызывает выносливости пользователя из-за неестественного расположения</span><span class="sxs-lookup"><span data-stu-id="71a0c-174">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="71a0c-175">![Над пальцами](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="71a0c-175">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="71a0c-176">**Над пальцами**</span><span class="sxs-lookup"><span data-stu-id="71a0c-176">**Above fingers**</span></span><br>
        <span data-ttu-id="71a0c-177">1-выносливости из-за длительного хранения</span><span class="sxs-lookup"><span data-stu-id="71a0c-177">1 - Hand fatigue due to holding out hand for a long time</span></span><br>
        <span data-ttu-id="71a0c-178">2 — проблемы с отслеживанием индекса и средних пальцев</span><span class="sxs-lookup"><span data-stu-id="71a0c-178">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="71a0c-179">![Выше Center Palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="71a0c-179">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="71a0c-180">**Выше-Center Palm**</span><span class="sxs-lookup"><span data-stu-id="71a0c-180">**Above-center palm**</span></span><br>
        <span data-ttu-id="71a0c-181">1. проблемы с отслеживанием из-за перекрывающихся стрелок</span><span class="sxs-lookup"><span data-stu-id="71a0c-181">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="71a0c-182">2-выносливости, из-за длительного времени для взаимодействия с меню</span><span class="sxs-lookup"><span data-stu-id="71a0c-182">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="71a0c-183">![Наиболее удобное ](images/TopFingerTip.gif) **Top fingertip** для вас начало</span><span class="sxs-lookup"><span data-stu-id="71a0c-183">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="71a0c-184">проблемы с отслеживанием 1</span><span class="sxs-lookup"><span data-stu-id="71a0c-184">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="71a0c-185">2-выносливости с удержанием руки над нормальным</span><span class="sxs-lookup"><span data-stu-id="71a0c-185">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="71a0c-186">3. проблемы с нажатием кнопок с другими пальцами случайным образом из-за ограниченного интервала между пальцами</span><span class="sxs-lookup"><span data-stu-id="71a0c-186">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="71a0c-187">![Задняя часть ARM](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="71a0c-187">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="71a0c-188">**Задняя часть ARM**</span><span class="sxs-lookup"><span data-stu-id="71a0c-188">**Back of the arm**</span></span><br>
        <span data-ttu-id="71a0c-189">1 — может вызвать неслучайно кнопку "домой"</span><span class="sxs-lookup"><span data-stu-id="71a0c-189">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="71a0c-190">2 — неестественное или удобное расположение</span><span class="sxs-lookup"><span data-stu-id="71a0c-190">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="71a0c-191">Меню руки в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="71a0c-191">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="71a0c-192">**[Мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет сценарии и примеры сцен для меню руки.</span><span class="sxs-lookup"><span data-stu-id="71a0c-192">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="71a0c-193">Сценарий поиска решения Хандконстраинтпалмуп позволяет вкладывать любые объекты в руки с различными настраиваемыми параметрами.</span><span class="sxs-lookup"><span data-stu-id="71a0c-193">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="71a0c-194">Примеры меню "руки" МРТК включают в себя такие полезные параметры, как плоское карманное ПК и взгляните на необходимость предотвращения ложных активаций.</span><span class="sxs-lookup"><span data-stu-id="71a0c-194">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="71a0c-195">Документы меню "руки"</span><span class="sxs-lookup"><span data-stu-id="71a0c-195">Hand Menu Documentations</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [<span data-ttu-id="71a0c-196">Пример сцены меню руки</span><span class="sxs-lookup"><span data-stu-id="71a0c-196">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="71a0c-197">Вы можете испытать примеры меню в HoloLens 2 с помощью приложения центра МРТК examples.</span><span class="sxs-lookup"><span data-stu-id="71a0c-197">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="71a0c-198">Сцена меню руки в центре примеров МРТК</span><span class="sxs-lookup"><span data-stu-id="71a0c-198">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a><span data-ttu-id="71a0c-199">См. также</span><span class="sxs-lookup"><span data-stu-id="71a0c-199">See also</span></span>

* [<span data-ttu-id="71a0c-200">Курсоры</span><span class="sxs-lookup"><span data-stu-id="71a0c-200">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="71a0c-201">Телекинез</span><span class="sxs-lookup"><span data-stu-id="71a0c-201">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="71a0c-202">Кнопка</span><span class="sxs-lookup"><span data-stu-id="71a0c-202">Button</span></span>](button.md)
* [<span data-ttu-id="71a0c-203">Активный объект</span><span class="sxs-lookup"><span data-stu-id="71a0c-203">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="71a0c-204">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="71a0c-204">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="71a0c-205">Оперирование</span><span class="sxs-lookup"><span data-stu-id="71a0c-205">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="71a0c-206">Меню руки</span><span class="sxs-lookup"><span data-stu-id="71a0c-206">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="71a0c-207">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="71a0c-207">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="71a0c-208">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="71a0c-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="71a0c-209">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="71a0c-209">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="71a0c-210">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="71a0c-210">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="71a0c-211">Подсказка</span><span class="sxs-lookup"><span data-stu-id="71a0c-211">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="71a0c-212">Планшет</span><span class="sxs-lookup"><span data-stu-id="71a0c-212">Slate</span></span>](slate.md)
* [<span data-ttu-id="71a0c-213">Ползунок</span><span class="sxs-lookup"><span data-stu-id="71a0c-213">Slider</span></span>](slider.md)
* [<span data-ttu-id="71a0c-214">Шейдер</span><span class="sxs-lookup"><span data-stu-id="71a0c-214">Shader</span></span>](shader.md)
* [<span data-ttu-id="71a0c-215">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="71a0c-215">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="71a0c-216">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="71a0c-216">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="71a0c-217">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="71a0c-217">Surface magnetism</span></span>](surface-magnetism.md)
