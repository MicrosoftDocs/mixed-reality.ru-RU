---
title: Курсоры
description: Курсор или индикатор целевого вектора обеспечивает непрерывную обратную связь пользователя, чтобы понять, что HoloLens понимает о своих намерения.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1-й общий), HoloLens 2, Смешанная реальность, курсоры, нацеленность, взгляд, жесты
ms.openlocfilehash: 719e7a573e8c8bc682ec0f960d9f3c8f8c8e5a4a
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105754"
---
# <a name="cursors"></a><span data-ttu-id="a40c8-104">Курсоры</span><span class="sxs-lookup"><span data-stu-id="a40c8-104">Cursors</span></span>

![Курсоры](images/UX/UX_Hero_Cursor.jpg)

<span data-ttu-id="a40c8-106">Курсор или индикатор текущего целевого вектора, предоставляет пользователю возможность непрерывной обратной связи, чтобы понять, где в это время на гарнитуре находится текущий фокус.</span><span class="sxs-lookup"><span data-stu-id="a40c8-106">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="a40c8-107">Курсор позволяет пользователю понять текущую целевую точку и действует как отзыв, чтобы указать, какая область, голограмма или точка будет реагировать на входные данные.</span><span class="sxs-lookup"><span data-stu-id="a40c8-107">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="a40c8-108">Это цифровое представление, где устройство понимает внимание пользователя (хотя это может быть не так же, как при определении каких-либо действий).</span><span class="sxs-lookup"><span data-stu-id="a40c8-108">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="a40c8-109">Обратная связь, предоставляемая курсором, дает пользователям возможность предвидеть, как будет реагировать система, использовать этот сигнал в качестве отзыва для лучшего общения с устройством и, в конечном итоге, более уверенности в их взаимодействии.</span><span class="sxs-lookup"><span data-stu-id="a40c8-109">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="a40c8-110">Существует три вида курсоров: **палец, луч**и **head-взгляд**.</span><span class="sxs-lookup"><span data-stu-id="a40c8-110">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="a40c8-111">Эти курсоры работают с различными входными модальностей на HoloLens, HoloLens 2 и впечатляющих гарнитурах.</span><span class="sxs-lookup"><span data-stu-id="a40c8-111">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="a40c8-112">Ниже приведены рекомендации по использованию типа курсора для каждого типа гарнитуры и модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a40c8-112">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="a40c8-113">В наборе средств для смешанной реальности (МРТК) мы создали модули курсоров с поддержкой перетаскивания, которые помогут вам создать правильный указатель мыши.</span><span class="sxs-lookup"><span data-stu-id="a40c8-113">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="a40c8-114">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="a40c8-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a40c8-115"><strong>Функциями</strong></span><span class="sxs-lookup"><span data-stu-id="a40c8-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a40c8-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a40c8-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a40c8-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a40c8-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a40c8-118"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="a40c8-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a40c8-119">Курсор пальца</span><span class="sxs-lookup"><span data-stu-id="a40c8-119">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a40c8-120">✔️</span><span class="sxs-lookup"><span data-stu-id="a40c8-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="a40c8-121">Лучающий курсор</span><span class="sxs-lookup"><span data-stu-id="a40c8-121">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a40c8-122">✔️</span><span class="sxs-lookup"><span data-stu-id="a40c8-122">✔️</span></span></td>
        <td><span data-ttu-id="a40c8-123">✔️</span><span class="sxs-lookup"><span data-stu-id="a40c8-123">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a40c8-124">Курсор Head</span><span class="sxs-lookup"><span data-stu-id="a40c8-124">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="a40c8-125">✔️</span><span class="sxs-lookup"><span data-stu-id="a40c8-125">✔️</span></span></td>
        <td><span data-ttu-id="a40c8-126">✔️</span><span class="sxs-lookup"><span data-stu-id="a40c8-126">✔️</span></span></td>
        <td><span data-ttu-id="a40c8-127">✔️</span><span class="sxs-lookup"><span data-stu-id="a40c8-127">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="a40c8-128">Курсор пальца</span><span class="sxs-lookup"><span data-stu-id="a40c8-128">Finger cursor</span></span>
<span data-ttu-id="a40c8-129">Курсор пальца доступен только в HoloLens 2, чтобы улучшить режим взаимодействия «[непосредственное управление](direct-manipulation.md)».</span><span class="sxs-lookup"><span data-stu-id="a40c8-129">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="a40c8-130">Чтобы лучше понять, куда направлен палец, мы присоединенные кольца к советам по обоим указателям.</span><span class="sxs-lookup"><span data-stu-id="a40c8-130">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="a40c8-131">Размер кольца основан на близости от пальца к поверхности пользовательского интерфейса (чем ближе палец, тем меньше кольцо) и будет уменьшаться до формы точки, когда палец совершает контакт с пользовательским интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="a40c8-131">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="a40c8-132">![](images/finger-cursor.png) курсора пальца</span><span class="sxs-lookup"><span data-stu-id="a40c8-132">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="a40c8-133">**Визуальные состояния обратной связи для курсора "палец** " 1: кольцо сжимается до точки.</span><span class="sxs-lookup"><span data-stu-id="a40c8-133">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="a40c8-134">2: кольцо соответствует поверхности.</span><span class="sxs-lookup"><span data-stu-id="a40c8-134">2: The ring aligns with surface.</span></span> <span data-ttu-id="a40c8-135">3: кольцо перпендикулярно вектору пальца.</span><span class="sxs-lookup"><span data-stu-id="a40c8-135">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="a40c8-136">4: нет кольца.</span><span class="sxs-lookup"><span data-stu-id="a40c8-136">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="a40c8-137">Лучающий курсор</span><span class="sxs-lookup"><span data-stu-id="a40c8-137">Ray cursor</span></span>
<span data-ttu-id="a40c8-138">Курсоры типа «луч» присоединяются к концу дальней точки, чтобы разрешить манипуляции с объектами, находящиеся за пределами руки.</span><span class="sxs-lookup"><span data-stu-id="a40c8-138">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="a40c8-139">В впечатляющих головных гарнитурах лучи прокрутки от контроллеров движения и заканчиваются курсорами точки.</span><span class="sxs-lookup"><span data-stu-id="a40c8-139">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="a40c8-140">В HoloLens 2 мы используем модель лучей этих лучающих контроллеров движения и спроектированные лучи, которые берутся из Палмс и заканчиваются курсорами в форме круга, которые согласуются с курсорами пальца, используемыми в непосредственной манипуляции.</span><span class="sxs-lookup"><span data-stu-id="a40c8-140">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="a40c8-141">![контроллера курсора луча](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="a40c8-141">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="a40c8-142">**Лучаовые курсоры контроллеров движения**</span><span class="sxs-lookup"><span data-stu-id="a40c8-142">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a40c8-143">](images/ray-cursor-hand.png) курсора ![Ray</span><span class="sxs-lookup"><span data-stu-id="a40c8-143">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="a40c8-144">**Лучающие курсоры**</span><span class="sxs-lookup"><span data-stu-id="a40c8-144">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="a40c8-145">Курсор Head</span><span class="sxs-lookup"><span data-stu-id="a40c8-145">Head-gaze cursor</span></span>
<span data-ttu-id="a40c8-146">Курсор «Heading-взгляд» — это точка, которая подключается к концу невидимого вектора «Head-взгляд», который использует позицию и поворот головной точки.</span><span class="sxs-lookup"><span data-stu-id="a40c8-146">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="a40c8-147">Для выполнения действий этот указывающий курсор связывается с различными входными данными фиксации, такими как воздушное касание, Voice Commands, вдаваясь и нажатие кнопки.</span><span class="sxs-lookup"><span data-stu-id="a40c8-147">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="a40c8-148">В HoloLens 2 Руководитель лучше всего связан с любыми входными данными фиксации, которые не являются воздушными потоками, так как между воздушным приводами и дальней наладоней возникает конфликт взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a40c8-148">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="a40c8-149">![](images/head-gaze-cursor-hand.png) курсора с заголовком</span><span class="sxs-lookup"><span data-stu-id="a40c8-149">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="a40c8-150">**Курсор в виде заголовка с помощью жеста руки**</span><span class="sxs-lookup"><span data-stu-id="a40c8-150">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a40c8-151">![ный](images/head-gaze-cursor-voice.png) с курсором в виде головного взгляда</span><span class="sxs-lookup"><span data-stu-id="a40c8-151">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="a40c8-152">**Курсор в виде заголовка с голосовым командой**</span><span class="sxs-lookup"><span data-stu-id="a40c8-152">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="a40c8-153">Рекомендации по настройке курсора</span><span class="sxs-lookup"><span data-stu-id="a40c8-153">Cursor customization recommendations</span></span>
<span data-ttu-id="a40c8-154">Если вы хотите настроить поведение и внешний вид обратной связи с курсором, ниже приведены некоторые рекомендации по проектированию.</span><span class="sxs-lookup"><span data-stu-id="a40c8-154">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="a40c8-155">Масштабирование курсора</span><span class="sxs-lookup"><span data-stu-id="a40c8-155">Cursor scale</span></span>
* <span data-ttu-id="a40c8-156">Курсор должен быть не больше доступных целевых объектов, что позволяет пользователям легко взаимодействовать с содержимым и просматривать его.</span><span class="sxs-lookup"><span data-stu-id="a40c8-156">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="a40c8-157">В зависимости от того, что вы создаете, масштабирование курсора по мере того, как пользователь смотрит, также является важным фактором.</span><span class="sxs-lookup"><span data-stu-id="a40c8-157">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="a40c8-158">Например, по мере того, как пользователь просматривает свой опыт, курсор не должен стать слишком маленьким, чтобы он был потерян.</span><span class="sxs-lookup"><span data-stu-id="a40c8-158">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="a40c8-159">При масштабировании курсора рассмотрите возможность применения мягкой анимации к ней при масштабировании, чтобы придать ему ощущение.</span><span class="sxs-lookup"><span data-stu-id="a40c8-159">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="a40c8-160">Избегайте неблизкого содержимого.</span><span class="sxs-lookup"><span data-stu-id="a40c8-160">Avoid obstructing content.</span></span> <span data-ttu-id="a40c8-161">Голограммы — это то, что делает ваш опыт, и курсор не должен отойти от них.</span><span class="sxs-lookup"><span data-stu-id="a40c8-161">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="a40c8-162">Форма двунаправленного курсора</span><span class="sxs-lookup"><span data-stu-id="a40c8-162">Directionless cursor shape</span></span>
* <span data-ttu-id="a40c8-163">Хотя ни одна фигура с правой стороны не существует, рекомендуется использовать форму без направления, например Торус.</span><span class="sxs-lookup"><span data-stu-id="a40c8-163">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="a40c8-164">Курсор, указывающий в каком-либо направлении (например, в традиционном курсоре со стрелкой), может запутать пользователя, чтобы всегда выглядеть таким образом.</span><span class="sxs-lookup"><span data-stu-id="a40c8-164">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="a40c8-165">Исключением является использование курсора для обмена инструкциями взаимодействия с пользователем.</span><span class="sxs-lookup"><span data-stu-id="a40c8-165">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="a40c8-166">Например, при масштабировании голограмм в операционной системе Mixed Reality курсор временно включает стрелки, указывающие пользователю, как переместить руку, чтобы масштабировать голограмму.</span><span class="sxs-lookup"><span data-stu-id="a40c8-166">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="a40c8-167">Внешний вид</span><span class="sxs-lookup"><span data-stu-id="a40c8-167">Look and feel</span></span>
* <span data-ttu-id="a40c8-168">Курсор в форме кольца или Торус работает для множества приложений.</span><span class="sxs-lookup"><span data-stu-id="a40c8-168">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="a40c8-169">Выберите цвет и форму, которые наилучшим образом представляют создаваемые вами возможности.</span><span class="sxs-lookup"><span data-stu-id="a40c8-169">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="a40c8-170">Курсоры особенно уязвимы для [разделения цветов](hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="a40c8-170">Cursors are especially prone to [color separation](hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="a40c8-171">Небольшой курсор с сбалансированной непрозрачностью обеспечивает ИТ-подсистему, не наполняя визуальную иерархию.</span><span class="sxs-lookup"><span data-stu-id="a40c8-171">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="a40c8-172">Компания cognizant с помощью теней или выделений, расположенных за курсором, так как они могут помешать содержимому и отвлечь за собой ненужные задачи.</span><span class="sxs-lookup"><span data-stu-id="a40c8-172">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="a40c8-173">Курсоры должны быть согласованы с областями в приложении и Хуг на них. Это даст пользователю ощущение того, что система сможет увидеть, где они ищутся, но также что система осведомлена о своей окружающей обстановке.</span><span class="sxs-lookup"><span data-stu-id="a40c8-173">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="a40c8-174">Например, в ОС смешанной реальности курсор будет выровняться по поверхности мира пользователя, создавая привлекательность мира, даже если пользователь не смотрит непосредственно на голограмме.</span><span class="sxs-lookup"><span data-stu-id="a40c8-174">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="a40c8-175">Магнитная Блокировка курсора на интерактивный элемент, когда он находится в пределах близкого близости, может помочь улучшить уверенность, что пользователь будет взаимодействовать с этим элементом при выполнении действия выбора.</span><span class="sxs-lookup"><span data-stu-id="a40c8-175">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="a40c8-176">Визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="a40c8-176">Visual cues</span></span>
* <span data-ttu-id="a40c8-177">Если ваш опыт сосредоточен на одной голограмме, то курсор должен выдать и Хуг только эту голограмму и изменить форму, когда вы пройдете с этой голограммы.</span><span class="sxs-lookup"><span data-stu-id="a40c8-177">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="a40c8-178">Это может передать пользователю, что голограмма является практичной и может взаимодействовать с ней.</span><span class="sxs-lookup"><span data-stu-id="a40c8-178">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="a40c8-179">Если приложение использует пространственное сопоставление, то курсор может выстроиться и Хуг каждую отображаемую им поверхность.</span><span class="sxs-lookup"><span data-stu-id="a40c8-179">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="a40c8-180">Это дает отзыв пользователям, которые HoloLens и приложение могут видеть свое пространство.</span><span class="sxs-lookup"><span data-stu-id="a40c8-180">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="a40c8-181">Это усиливает тот факт, что голограммы являются реальными и в нашем мире, и помогают преодолеть разрыв между реальными и виртуальными.</span><span class="sxs-lookup"><span data-stu-id="a40c8-181">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="a40c8-182">Иметь представление о том, что должен делать курсор при отсутствии голограмм или поверхностей в представлении.</span><span class="sxs-lookup"><span data-stu-id="a40c8-182">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="a40c8-183">Его размещение на заранее определенном расстоянии перед пользователем является одним из вариантов.</span><span class="sxs-lookup"><span data-stu-id="a40c8-183">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="a40c8-184">Возможные действия</span><span class="sxs-lookup"><span data-stu-id="a40c8-184">Possible actions</span></span>
* <span data-ttu-id="a40c8-185">Курсор может быть представлен разными значками для передачи возможных действий, которые может выполнить голограмма, например для масштабирования или вращения.</span><span class="sxs-lookup"><span data-stu-id="a40c8-185">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="a40c8-186">Добавляйте в курсор дополнительные сведения, если это означает что-то для пользователя.</span><span class="sxs-lookup"><span data-stu-id="a40c8-186">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="a40c8-187">В противном случае пользователи могут не заметить изменения состояния или выпутать курсор.</span><span class="sxs-lookup"><span data-stu-id="a40c8-187">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="a40c8-188">Входное состояние</span><span class="sxs-lookup"><span data-stu-id="a40c8-188">Input state</span></span>
* <span data-ttu-id="a40c8-189">Можно использовать курсор для отображения состояния или намерений ввода пользователя.</span><span class="sxs-lookup"><span data-stu-id="a40c8-189">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="a40c8-190">Например, можно отобразить значок, сообщающий пользователю, что система видит свое состояние, и что приложение знает, что они готовы принять меры.</span><span class="sxs-lookup"><span data-stu-id="a40c8-190">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="a40c8-191">Можно также использовать курсор, чтобы показывать пользователям, что система настроила голосовое меню при смене цвета</span><span class="sxs-lookup"><span data-stu-id="a40c8-191">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="a40c8-192">Следующие состояния курсора могут быть реализованы различными способами.</span><span class="sxs-lookup"><span data-stu-id="a40c8-192">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="a40c8-193">Вы можете реализовать эти различные состояния, моделирующие курсор как конечный автомат.</span><span class="sxs-lookup"><span data-stu-id="a40c8-193">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="a40c8-194">Пример</span><span class="sxs-lookup"><span data-stu-id="a40c8-194">For example:</span></span>
    * <span data-ttu-id="a40c8-195">Состояние простоя показывает курсор по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a40c8-195">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="a40c8-196">Состояние готовности — когда вы обнаружили руку пользователя в месте готовности.</span><span class="sxs-lookup"><span data-stu-id="a40c8-196">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="a40c8-197">Состояние взаимодействия — это когда пользователь выполняет определенное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="a40c8-197">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="a40c8-198">Состояние возможных действий или состояние наведения указателя — это то, что можно передать возможные действия, которые могут быть выполнены на голограмме.</span><span class="sxs-lookup"><span data-stu-id="a40c8-198">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="a40c8-199">Эти состояния также можно реализовать с помощью обложки таким образом, чтобы можно было отображать различные графические ресурсы при обнаружении различных состояний.</span><span class="sxs-lookup"><span data-stu-id="a40c8-199">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="a40c8-200">Переход на «свободный курсор»</span><span class="sxs-lookup"><span data-stu-id="a40c8-200">Going "cursor-free"</span></span>
<span data-ttu-id="a40c8-201">Проектирование без курсора рекомендуется, если смысл возникнет в качестве ключевого компонента интерфейса и при указании взаимодействий (с помощью взгляда и жеста) не требуется значительная точность.</span><span class="sxs-lookup"><span data-stu-id="a40c8-201">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="a40c8-202">Система по-прежнему должна удовлетворять потребности, которые обычно выполняются курсором, предоставляя пользователям непрерывную обратную связь над пониманием системы и помогая им уверенно передавать свои намерения в систему.</span><span class="sxs-lookup"><span data-stu-id="a40c8-202">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="a40c8-203">Это может быть достижимо с помощью других заметных изменений состояния.</span><span class="sxs-lookup"><span data-stu-id="a40c8-203">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="a40c8-204">Курсор в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="a40c8-204">Cursor in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="a40c8-205">По умолчанию **[мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет курсор prefab ([дефаулткурсор. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)), который имеет то же визуальное состояние, что и системный курсор оболочки.</span><span class="sxs-lookup"><span data-stu-id="a40c8-205">By default, **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="a40c8-206">Он назначается входным профилем МРТК в разделе указатели.</span><span class="sxs-lookup"><span data-stu-id="a40c8-206">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="a40c8-207">Вы можете заменить или настроить этот курсор для работы.</span><span class="sxs-lookup"><span data-stu-id="a40c8-207">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="a40c8-208">Для удобства ввода с отслеживанием взгляда МРТК также предоставляет Эйегазекурсор, который имеет тонкий визуальный элемент для снижения числа невыполнений.</span><span class="sxs-lookup"><span data-stu-id="a40c8-208">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="a40c8-209">МРТК — профиль указателя</span><span class="sxs-lookup"><span data-stu-id="a40c8-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="a40c8-210">МРТК система ввода</span><span class="sxs-lookup"><span data-stu-id="a40c8-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="a40c8-211">МРТК — указатели</span><span class="sxs-lookup"><span data-stu-id="a40c8-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="a40c8-212">См. также</span><span class="sxs-lookup"><span data-stu-id="a40c8-212">See also</span></span>
* [<span data-ttu-id="a40c8-213">Жесты</span><span class="sxs-lookup"><span data-stu-id="a40c8-213">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a40c8-214">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="a40c8-214">Head-gaze and commit</span></span>](gaze-and-commit.md)
