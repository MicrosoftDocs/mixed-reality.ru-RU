---
title: Основы взаимодействия
description: Как мы создали взаимодействия между HoloLens (1-го поколения), HoloLens 2 и иммерсивную, мы начали записывать некоторые вещи, мы обнаружили удобен для совместного использования.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Смешанной реальности, взаимодействие, проектирование
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597549"
---
# <a name="interaction-fundamentals"></a><span data-ttu-id="42663-104">Основы взаимодействия</span><span class="sxs-lookup"><span data-stu-id="42663-104">Interaction fundamentals</span></span>

<span data-ttu-id="42663-105">Как мы создали возможности HoloLens и иммерсивную, мы начали, начать записывать некоторые действия, которые мы нашли удобен для совместного использования.</span><span class="sxs-lookup"><span data-stu-id="42663-105">As we've built experiences across HoloLens and immersive headsets, we've started writing down some things we found useful to share.</span></span> <span data-ttu-id="42663-106">Следует воспринимать как основные стандартные блоки для смешанной реальности Разработка взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="42663-106">Think of these as the fundamental building blocks for mixed reality interaction design.</span></span>

## <a name="device-support"></a><span data-ttu-id="42663-107">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="42663-107">Device support</span></span>

<span data-ttu-id="42663-108">Вот в доступных статьях разработки взаимодействия и какие устройства или типов они относятся к структуре.</span><span class="sxs-lookup"><span data-stu-id="42663-108">Here's an outline of the available Interaction design articles and which device type or types they apply to.</span></span>
<br>

<table>

<th>
<tr>

<td style="width:150px;"><span data-ttu-id="42663-109"><strong>Входные данные</strong></span><span class="sxs-lookup"><span data-stu-id="42663-109"><strong>Input</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="42663-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="42663-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="42663-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="42663-111"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="42663-112"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="42663-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
 
<tr>
<td> <span data-ttu-id="42663-113"><a href="gestures.md">Ясно сформулированные руки</a></span><span class="sxs-lookup"><span data-stu-id="42663-113"><a href="gestures.md">Articulated hands</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="42663-114">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-114">✔️</span></span></td><td></td>

</tr><tr>
<td> <span data-ttu-id="42663-115"><a href="gaze-targeting.md">Предназначенные для глаз</a></span><span class="sxs-lookup"><span data-stu-id="42663-115"><a href="gaze-targeting.md">Eye targeting</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="42663-116">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-116">✔️</span></span></td><td style="text-align: center;"></td>
</tr><tr>
<td> <span data-ttu-id="42663-117"><a href="gaze-targeting.md">Нацеливание взглядом</a></span><span class="sxs-lookup"><span data-stu-id="42663-117"><a href="gaze-targeting.md">Gaze targeting</a></span></span></td><td style="text-align: center;"><span data-ttu-id="42663-118">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-118">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-119">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-119">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-120">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-120">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="42663-121"><a href="gestures.md">Жесты</a></span><span class="sxs-lookup"><span data-stu-id="42663-121"><a href="gestures.md">Gestures</a></span></span></td><td style="text-align: center;"><span data-ttu-id="42663-122">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-122">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-123">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-123">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="42663-124"><a href="voice-design.md">Проектирование голоса</a></span><span class="sxs-lookup"><span data-stu-id="42663-124"><a href="voice-design.md">Voice design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="42663-125">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-125">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-126">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-126">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-127">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-127">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="42663-128">Геймпад</span><span class="sxs-lookup"><span data-stu-id="42663-128">Gamepad</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-129">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-129">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-130">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-130">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-131">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-131">✔️</span></span></td>
</tr>
<tr>
<td> <span data-ttu-id="42663-132"><a href="motion-controllers.md">Контроллеры движения</a></span><span class="sxs-lookup"><span data-stu-id="42663-132"><a href="motion-controllers.md">Motion controllers</a></span></span></td><td></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="42663-133">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-133">✔️</span></span></td>

</tr>
<th>
<tr>
<td style="width:150px;"><span data-ttu-id="42663-134"><strong>Восприятие и функции обработки пространственных данных</strong></span><span class="sxs-lookup"><span data-stu-id="42663-134"><strong>Perception and spatial features</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="42663-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="42663-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="42663-136"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="42663-136"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="42663-137"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="42663-137"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
<tr>

<td> <span data-ttu-id="42663-138"><a href="spatial-sound-design.md">Пространственные систему</a></span><span class="sxs-lookup"><span data-stu-id="42663-138"><a href="spatial-sound-design.md">Spatial sound design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="42663-139">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-139">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-140">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-140">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-141">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-141">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="42663-142"><a href="spatial-mapping-design.md">Пространственное сопоставление конструктора</a></span><span class="sxs-lookup"><span data-stu-id="42663-142"><a href="spatial-mapping-design.md">Spatial mapping design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="42663-143">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-143">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-144">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-144">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="42663-145"><a href="hologram.md">Голограммы</a></span><span class="sxs-lookup"><span data-stu-id="42663-145"><a href="hologram.md">Holograms</a></span></span></td><td style="text-align: center;"><span data-ttu-id="42663-146">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-146">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="42663-147">✔️</span><span class="sxs-lookup"><span data-stu-id="42663-147">✔️</span></span></td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a><span data-ttu-id="42663-148">Пользователь является камеры</span><span class="sxs-lookup"><span data-stu-id="42663-148">The user is the camera</span></span>

![Пользователь является камеры](images/useriscamera-640px.jpg)

<span data-ttu-id="42663-150">В их мире реальных и виртуальных всегда думайте о, разработанной для точки зрения пользователя.</span><span class="sxs-lookup"><span data-stu-id="42663-150">Always think about design for your user's point of view as they move about their real and virtual worlds.</span></span>

<span data-ttu-id="42663-151">**Решить вопросы**</span><span class="sxs-lookup"><span data-stu-id="42663-151">**Some questions to ask**</span></span>
* <span data-ttu-id="42663-152">Пользователь сидите, откидная спинка, репутацию или прохода при использовании процесс?</span><span class="sxs-lookup"><span data-stu-id="42663-152">Is the user sitting, reclining, standing, or walking while using your experience?</span></span>
* <span data-ttu-id="42663-153">Как содержимое скорректировать в различных положениях.</span><span class="sxs-lookup"><span data-stu-id="42663-153">How does your content adjust to different positions?</span></span>
* <span data-ttu-id="42663-154">Можно, пользователь изменять ее?</span><span class="sxs-lookup"><span data-stu-id="42663-154">Can the user adjust it?</span></span>
* <span data-ttu-id="42663-155">Смогут ли пользователи получать уверенно используете приложения?</span><span class="sxs-lookup"><span data-stu-id="42663-155">Will the user be comfortable using your app?</span></span>

<span data-ttu-id="42663-156">**Рекомендации**</span><span class="sxs-lookup"><span data-stu-id="42663-156">**Best practices**</span></span>
* <span data-ttu-id="42663-157">Пользователь является камеры, и они управляют перемещение.</span><span class="sxs-lookup"><span data-stu-id="42663-157">The user is the camera and they control the movement.</span></span> <span data-ttu-id="42663-158">Let их диска.</span><span class="sxs-lookup"><span data-stu-id="42663-158">Let them drive.</span></span>
* <span data-ttu-id="42663-159">Если вам нужно практически транспорта пользователя, быть важны для проблемы, связанные с vestibular discomfort.</span><span class="sxs-lookup"><span data-stu-id="42663-159">If you need to virtually transport the user, be sensitive to issues around vestibular discomfort.</span></span>
* <span data-ttu-id="42663-160">Используйте более короткие анимации</span><span class="sxs-lookup"><span data-stu-id="42663-160">Use shorter animations</span></span>
* <span data-ttu-id="42663-161">Анимация из вниз, влево и вправо или появление вместо Z</span><span class="sxs-lookup"><span data-stu-id="42663-161">Animate from down/left/right or fade in instead of Z</span></span>
* <span data-ttu-id="42663-162">Замедление времени</span><span class="sxs-lookup"><span data-stu-id="42663-162">Slow down timing</span></span>
* <span data-ttu-id="42663-163">Разрешить пользователю см. в разделе мира в фоновом режиме</span><span class="sxs-lookup"><span data-stu-id="42663-163">Allow user to see the world in the background</span></span>

<span data-ttu-id="42663-164">**Чего следует избегать**</span><span class="sxs-lookup"><span data-stu-id="42663-164">**What to avoid**</span></span>
* <span data-ttu-id="42663-165">Не встряхните камеры или намеренно привязать ее к 3DOF (только ориентации, без преобразования), можно сделать пользователей неудобно.</span><span class="sxs-lookup"><span data-stu-id="42663-165">Don't shake the camera or purposely lock it to 3DOF (only orientation, no translation), it can make users feel uncomfortable.</span></span>
* <span data-ttu-id="42663-166">Перемещения не освободиться.</span><span class="sxs-lookup"><span data-stu-id="42663-166">No abrupt movement.</span></span> <span data-ttu-id="42663-167">Если вам нужно перенести содержимое для или от пользователя, переместив ее медленно и беспрепятственно их для максимального удобства.</span><span class="sxs-lookup"><span data-stu-id="42663-167">If you need to bring content to or from the user, move it slowly and smoothly toward them for maximum comfort.</span></span> <span data-ttu-id="42663-168">Пользователи будут реагировать на больших меню, поступающих на них.</span><span class="sxs-lookup"><span data-stu-id="42663-168">Users will react to large menus coming at them.</span></span>
* <span data-ttu-id="42663-169">Не ускорение или включить камере пользователя.</span><span class="sxs-lookup"><span data-stu-id="42663-169">Don't accelerate or turn the user's camera.</span></span> <span data-ttu-id="42663-170">Пользователи чувствительны к ускорение (angular и трансляционная).</span><span class="sxs-lookup"><span data-stu-id="42663-170">Users are sensitive to acceleration (both angular and translational).</span></span>

## <a name="leverage-the-users-perspective"></a><span data-ttu-id="42663-171">Использовать точки зрения пользователя</span><span class="sxs-lookup"><span data-stu-id="42663-171">Leverage the user's perspective</span></span>

<span data-ttu-id="42663-172">Пользователи увидят мире смешанной реальности через отображает на иммерсивных и holographic устройств.</span><span class="sxs-lookup"><span data-stu-id="42663-172">Users see the world of mixed reality through displays on immersive and holographic devices.</span></span> <span data-ttu-id="42663-173">На HoloLens, такое отображение называется [holographic кадра](holographic-frame.md).</span><span class="sxs-lookup"><span data-stu-id="42663-173">On the HoloLens, this display is called the [holographic frame](holographic-frame.md).</span></span>

<span data-ttu-id="42663-174">В двухмерных разработки часто запрашиваемое содержимое и параметры могут быть помещены в углу экрана, чтобы сделать их легко доступными.</span><span class="sxs-lookup"><span data-stu-id="42663-174">In 2D development, frequently accessed content and settings may be placed in the corners of a screen to make them easily accessible.</span></span> <span data-ttu-id="42663-175">Тем не менее в holographic приложениях содержимое углы представление пользователя может быть слишком неудобным для доступа.</span><span class="sxs-lookup"><span data-stu-id="42663-175">However, in holographic apps, content in the corners of the user's view may be uncomfortable to access.</span></span> <span data-ttu-id="42663-176">В этом случае центр holographic кадра является ярким расположение для содержимого.</span><span class="sxs-lookup"><span data-stu-id="42663-176">In this case, the center of the holographic frame is the prime location for content.</span></span>

<span data-ttu-id="42663-177">Ему может потребоваться в соответствии с инструкциями для поиска важных событий или объекты за пределами их немедленное представление.</span><span class="sxs-lookup"><span data-stu-id="42663-177">The user may need to be guided to help locate important events or objects beyond their immediate view.</span></span> <span data-ttu-id="42663-178">Можно использовать кнопки со стрелками, света след, символ перемещения, пузырьки мысль, указатели, пространственных звук и голосовые инструкции помогают пользователю важное содержимое в приложении.</span><span class="sxs-lookup"><span data-stu-id="42663-178">You can use arrows, light trails, character head movement, thought bubbles, pointers, spatial sound, and voice prompts to help guide the user to important content in your app.</span></span>

<span data-ttu-id="42663-179">Рекомендуется не блокировки содержимое на экране для удобства пользователя.</span><span class="sxs-lookup"><span data-stu-id="42663-179">It is recommended to not lock content to the screen for the user's comfort.</span></span> <span data-ttu-id="42663-180">Если необходимо сохранить в представлении содержимого, поместите его в мире и предоставить доступ к содержимому «tag-along», как и в меню "Пуск".</span><span class="sxs-lookup"><span data-stu-id="42663-180">If you need to keep content in view, place it in the world and make the content "tag-along" like the Start menu.</span></span> <span data-ttu-id="42663-181">Содержимое, которое возвращает вместе с точки зрения пользователя станет более естественным в среде.</span><span class="sxs-lookup"><span data-stu-id="42663-181">Content that gets pulled along with the user's perspective will feel more natural in the environment.</span></span>

<span data-ttu-id="42663-182">![Меню "Пуск" следует представление пользователя, при достижении границы рамки](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="42663-182">![The start menu follows the user's view when it reaches the edge of the frame](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="42663-183">*Меню "Пуск" следует представление пользователя, при достижении границы рамки*</span><span class="sxs-lookup"><span data-stu-id="42663-183">*The Start menu follows the user's view when it reaches the edge of the frame*</span></span>

<span data-ttu-id="42663-184">На HoloLens голограммы вы реальных, когда они помещаются внутри окна holographic, так как они не обрезаны.</span><span class="sxs-lookup"><span data-stu-id="42663-184">On HoloLens, holograms feel real when they fit within the holographic frame since they don't get cut off.</span></span> <span data-ttu-id="42663-185">Пользователям будет переместить, чтобы см. в разделе границы голограмма внутри фрейма.</span><span class="sxs-lookup"><span data-stu-id="42663-185">Users will move in order to see the bounds of a hologram within the frame.</span></span> <span data-ttu-id="42663-186">На HoloLens очень важно для упрощения пользовательского интерфейса в представление пользователя и сохранять внимание на главное действие.</span><span class="sxs-lookup"><span data-stu-id="42663-186">On HoloLens, it's important to simplify your UI to fit within the user's view and keep your focus on the main action.</span></span> <span data-ttu-id="42663-187">Для иммерсивную важно поддерживать иллюзию постоянный виртуальный мир, в поле зрения устройства.</span><span class="sxs-lookup"><span data-stu-id="42663-187">For immersive headsets, it's important to maintain the illusion of a persistent virtual world within the device's field of view.</span></span>

## <a name="user-comfort"></a><span data-ttu-id="42663-188">Удобства пользователя</span><span class="sxs-lookup"><span data-stu-id="42663-188">User comfort</span></span>

<span data-ttu-id="42663-189">Чтобы обеспечить максимально [комфорта](comfort.md) на вывод разделов, подключаемая head, очень важно для дизайнерам и разработчикам создавать и представление содержимого способом, который имитирует, как люди интерпретировать трехмерных фигур и относительное положение объектов в натуральный мир.</span><span class="sxs-lookup"><span data-stu-id="42663-189">To ensure maximum [comfort](comfort.md) on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how humans interpret 3D shapes and the relative position of objects in the natural world.</span></span> <span data-ttu-id="42663-190">С точки зрения физического также важно разработать содержимое, которое не требует fatiguing движения горлышка или оружию.</span><span class="sxs-lookup"><span data-stu-id="42663-190">From a physical perspective, it is also important to design content that does not require fatiguing motions of the neck or arms.</span></span>

<span data-ttu-id="42663-191">Ли разработке для HoloLens или иммерсивную, очень важно для отрисовки визуальных элементов для обоих глаза.</span><span class="sxs-lookup"><span data-stu-id="42663-191">Whether developing for HoloLens or immersive headsets, it is important to render visuals for both eyes.</span></span> <span data-ttu-id="42663-192">Подготовка к просмотру индикации в один глаз только можно сделать интерфейс трудными для понимания, а также приводит к uneasiness глаз и вычислительных мощностей пользователя.</span><span class="sxs-lookup"><span data-stu-id="42663-192">Rendering a heads-up display in one eye only can make an interface hard to understand, as well as causing uneasiness to the user's eye and brain.</span></span>

## <a name="share-your-experience"></a><span data-ttu-id="42663-193">Оставьте свой отзыв</span><span class="sxs-lookup"><span data-stu-id="42663-193">Share your experience</span></span>

<span data-ttu-id="42663-194">С помощью [смешанный реальности записи](mixed-reality-capture.md), можно записать фото или видео взаимодействия с ними в любое время.</span><span class="sxs-lookup"><span data-stu-id="42663-194">Using [mixed reality capture](mixed-reality-capture.md), users can capture a photo or video of their experience at any time.</span></span> <span data-ttu-id="42663-195">Рассмотрите возможность работы в приложении, где требуется рассылать моментальные снимки или видео.</span><span class="sxs-lookup"><span data-stu-id="42663-195">Consider experiences in your app where you may want to encourage snapshots or videos.</span></span>

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a><span data-ttu-id="42663-196">Использовать основные элементы пользовательского интерфейса Windows Mixed Reality home</span><span class="sxs-lookup"><span data-stu-id="42663-196">Leverage basic UI elements of the Windows Mixed Reality home</span></span>

<span data-ttu-id="42663-197">Так же, как запуске планшетными ПК Windows с рабочим столом Windows Mixed Reality начинается с дома.</span><span class="sxs-lookup"><span data-stu-id="42663-197">Just like the Windows PC experience starts with the desktop, Windows Mixed Reality starts with the home.</span></span> <span data-ttu-id="42663-198">[Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md) использует наши система дает возможность понять и перейти 3D местах.</span><span class="sxs-lookup"><span data-stu-id="42663-198">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) leverages our innate ability to understand and navigate 3D places.</span></span> <span data-ttu-id="42663-199">С HoloLens готова в физическом пространстве.</span><span class="sxs-lookup"><span data-stu-id="42663-199">With HoloLens, your home is your physical space.</span></span> <span data-ttu-id="42663-200">С помощью иммерсивную домашней сети — это виртуальный место.</span><span class="sxs-lookup"><span data-stu-id="42663-200">With immersive headsets, your home is a virtual place.</span></span>

<span data-ttu-id="42663-201">Также является домашней сети где меню "Пуск" будет использоваться для открытия и разместить приложения и содержимого.</span><span class="sxs-lookup"><span data-stu-id="42663-201">Your home is also where you’ll use the Start menu to open and place apps and content.</span></span> <span data-ttu-id="42663-202">Можно заполнить дома содержимым смешанной реальности и справляется с помощью нескольких приложений одновременно.</span><span class="sxs-lookup"><span data-stu-id="42663-202">You can fill your home with mixed reality content and multitask by using multiple apps at the same time.</span></span> <span data-ttu-id="42663-203">То, что вы помещаете домашней сети остаются там, даже при перезагрузке устройства.</span><span class="sxs-lookup"><span data-stu-id="42663-203">The things you place in your home stay there, even if you restart your device.</span></span>

## <a name="see-also"></a><span data-ttu-id="42663-204">См. также</span><span class="sxs-lookup"><span data-stu-id="42663-204">See also</span></span>
* [<span data-ttu-id="42663-205">Нацеливание взглядом</span><span class="sxs-lookup"><span data-stu-id="42663-205">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="42663-206">Жесты</span><span class="sxs-lookup"><span data-stu-id="42663-206">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="42663-207">Проектирование голоса</span><span class="sxs-lookup"><span data-stu-id="42663-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="42663-208">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="42663-208">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="42663-209">Пространственные систему</span><span class="sxs-lookup"><span data-stu-id="42663-209">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="42663-210">Пространственное сопоставление конструктора</span><span class="sxs-lookup"><span data-stu-id="42663-210">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="42663-211">Комфорта</span><span class="sxs-lookup"><span data-stu-id="42663-211">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="42663-212">Перемещение Windows Mixed Reality home</span><span class="sxs-lookup"><span data-stu-id="42663-212">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
