---
title: Модуль лунного
description: LunarModule — это приложение открытым исходным кодом примера лабораторных занятий смешанной реальности разработки корпорации Майкрософт. С этим проектом Узнайте, как расширить Hololens базовых жестов, использующих обе руки при отслеживании и контроллера Xbox входных данных, создания объектов, которые заключаются в реагировании на поверхности сопоставления и поиск плоскости и реализации систем простого меню.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows смешанной реальности, пример приложения, разработки, HoloLens
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602486"
---
# <a name="lunar-module"></a><span data-ttu-id="7561d-105">Модуль лунного</span><span class="sxs-lookup"><span data-stu-id="7561d-105">Lunar Module</span></span>

>[!NOTE]
><span data-ttu-id="7561d-106">В этой статье рассматривается пример произвольного тестирования, мы создали в [смешанной реальности разработки Labs](https://github.com/Microsoft/MRDesignLabs_Unity), это место, мы передаем результатов работы о и подсказок для смешанного реальности разработки приложений.</span><span class="sxs-lookup"><span data-stu-id="7561d-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="7561d-107">Наши статьи, связанных с проектированием и код будет развиваться, как мы появления новых.</span><span class="sxs-lookup"><span data-stu-id="7561d-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="7561d-108">[Модуль лунного](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) является открытым исходным кодом примера приложения лабораторных занятий смешанной реальности разработки корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="7561d-108">[Lunar Module](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="7561d-109">С этим проектом Узнайте, как расширить Hololens базовых жестов, использующих обе руки при отслеживании и контроллера Xbox входных данных, создания объектов, которые заключаются в реагировании на поверхности сопоставления и поиск плоскости и реализации систем простого меню.</span><span class="sxs-lookup"><span data-stu-id="7561d-109">With this project, you can learn how to extend Hololens' base gestures with two-handed tracking and Xbox controller input, create objects that are reactive to surface mapping and plane finding and implement simple menu systems.</span></span> <span data-ttu-id="7561d-110">Все компоненты проекта доступны для использования в собственных элементов взаимодействия приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="7561d-110">All of the project's components are available for use in your own mixed reality app experiences.</span></span>

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a><span data-ttu-id="7561d-111">Переосмысление классический интерфейс для Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="7561d-111">Rethinking classic experiences for Windows Mixed Reality</span></span>

<span data-ttu-id="7561d-112">Высокий уровень вверх в атмосферу небольшой отгрузки, напоминающим модуля Apollo методично обзоры массивов ландшафта ниже.</span><span class="sxs-lookup"><span data-stu-id="7561d-112">High up in the atmosphere, a small ship reminiscent of the Apollo module methodically surveys jagged terrain below.</span></span> <span data-ttu-id="7561d-113">Наши мощные пилотный проект spots подходящий зону.</span><span class="sxs-lookup"><span data-stu-id="7561d-113">Our fearless pilot spots a suitable landing area.</span></span> <span data-ttu-id="7561d-114">Спуск — затруднительно, но к счастью, для этого путешествия уже внесено много раз, прежде чем...</span><span class="sxs-lookup"><span data-stu-id="7561d-114">The descent is arduous but thankfully, this journey has been made many times before...</span></span>

<span data-ttu-id="7561d-115">![Исходный интерфейс из Atari в 1979 лунный Lander](images/640px-atari-lunar-lander.png)</span><span class="sxs-lookup"><span data-stu-id="7561d-115">![Original interface from Atari’s 1979 Lunar Lander](images/640px-atari-lunar-lander.png)</span></span><br>
<span data-ttu-id="7561d-116">*Исходный интерфейс из Atari в 1979 лунный Lander*</span><span class="sxs-lookup"><span data-stu-id="7561d-116">*Original interface from Atari’s 1979 Lunar Lander*</span></span>

<span data-ttu-id="7561d-117">[Лунный Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) — классические аркадные, где игроки пытаюсь Пилотное lander луну на плоской место из лунный ландшафта.</span><span class="sxs-lookup"><span data-stu-id="7561d-117">[Lunar Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) is an arcade classic where players attempt to pilot a moon lander onto a flat spot of lunar terrain.</span></span> <span data-ttu-id="7561d-118">Любой пользователь в 1970-х скорее потратил времени в arcade с их глаза, этот вектор отгрузки, plummeting с неба привязку.</span><span class="sxs-lookup"><span data-stu-id="7561d-118">Anyone born in the 1970s has most likely spent hours in an arcade with their eyes glued to this vector ship plummeting from the sky.</span></span> <span data-ttu-id="7561d-119">Проигрыватель переходит их поставки к области необходимую целевую область масштабируется для отображения постепенно более подробно.</span><span class="sxs-lookup"><span data-stu-id="7561d-119">As a player navigates their ship toward a desired landing area the terrain scales to reveal progressively more detail.</span></span> <span data-ttu-id="7561d-120">Успех означает, что целевая безопасном границах, горизонтальной и вертикальной скоростью.</span><span class="sxs-lookup"><span data-stu-id="7561d-120">Success means landing within the safe threshold of horizontal and vertical speed.</span></span> <span data-ttu-id="7561d-121">Баллы присуждаются время, затраченное на целевой и оставшихся топлива, в зависимости от размера области целевой множителя.</span><span class="sxs-lookup"><span data-stu-id="7561d-121">Points are awarded for time spent landing and remaining fuel, with a multiplier based on the size of the landing area.</span></span>

<span data-ttu-id="7561d-122">Помимо игровой процесс в эпоху аркадные игры оперативный постоянных инноваций схем управления.</span><span class="sxs-lookup"><span data-stu-id="7561d-122">Aside from the gameplay, the arcade era of games brought constant innovation of control schemes.</span></span> <span data-ttu-id="7561d-123">Из простой джойстика четырехкратного конфигураций кнопки (преобразованного в значок в [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) в строго определенных и сложные схемы, в конце 90-х годах и 00 с (как в Гольф симуляторах и стрелялки rail).</span><span class="sxs-lookup"><span data-stu-id="7561d-123">From the simplest 4-way joystick and button configurations (seen in the iconic [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) to the highly specific and complicated schemes seen in the late 90s and 00s (like those in golf simulators and rail shooters).</span></span> <span data-ttu-id="7561d-124">Входной схему, используемую на машине лунный Lander особенно захватывающим по двум причинам: предпринимаются привлекательность и общения.</span><span class="sxs-lookup"><span data-stu-id="7561d-124">The input scheme used in the Lunar Lander machine is particularly intriguing for two reasons: curb appeal and immersion.</span></span>

<span data-ttu-id="7561d-125">![Лунный Lander Atari arcade консоли](images/atariconsole.png)</span><span class="sxs-lookup"><span data-stu-id="7561d-125">![Atari’s Lunar Lander’s arcade console](images/atariconsole.png)</span></span><br>
<span data-ttu-id="7561d-126">*Atari лунный Lander arcade консоли*</span><span class="sxs-lookup"><span data-stu-id="7561d-126">*Atari's Lunar Lander arcade console*</span></span>

<span data-ttu-id="7561d-127">Почему было Atari и множество других игр компаний утверждено пересмотреть входных данных?</span><span class="sxs-lookup"><span data-stu-id="7561d-127">Why did Atari and so many other game companies decide to rethink input?</span></span>

<span data-ttu-id="7561d-128">Kid, принципа arcade, естественным образом быть intrigued самому новому, flashiest компьютером.</span><span class="sxs-lookup"><span data-stu-id="7561d-128">A kid walking through an arcade will naturally be intrigued by the newest, flashiest machine.</span></span> <span data-ttu-id="7561d-129">Но лунный Lander функции novel входной механику, который отличалась из общей массы.</span><span class="sxs-lookup"><span data-stu-id="7561d-129">But Lunar Lander features a novel input mechanic that stood out from the crowd.</span></span>

<span data-ttu-id="7561d-130">Лунный Lander использует две кнопки для смены корабль левого и правого и **бегунка Осевая сила** для управления объемом создает корабль Осевая сила.</span><span class="sxs-lookup"><span data-stu-id="7561d-130">Lunar Lander uses two buttons for rotating the ship left and right and a **thrust lever** to control the amount of thrust the ship produces.</span></span> <span data-ttu-id="7561d-131">Этот уровень предоставляет пользователям умелого регулярных джойстик не может предоставлять определенный уровень.</span><span class="sxs-lookup"><span data-stu-id="7561d-131">This lever gives users a certain level of finesse a regular joystick can’t provide.</span></span> <span data-ttu-id="7561d-132">Это также происходит как компонент, общие для современных aviation панелей.</span><span class="sxs-lookup"><span data-stu-id="7561d-132">It is also happens to be a component common to modern aviation cockpits.</span></span> <span data-ttu-id="7561d-133">Atari требовалась лунный Lander для эффектов, пользователь в чувства, что они на самом деле Пилотное развертывание лунного модуля.</span><span class="sxs-lookup"><span data-stu-id="7561d-133">Atari wanted Lunar Lander to immerse the user in the feeling that they were in fact piloting a lunar module.</span></span> <span data-ttu-id="7561d-134">Эта концепция называется **tactile погружения**.</span><span class="sxs-lookup"><span data-stu-id="7561d-134">This concept is known as **tactile immersion**.</span></span>

<span data-ttu-id="7561d-135">Tactile погружения возможности экстрасенсорное обратной связи от выполнения повторяющихся действий.</span><span class="sxs-lookup"><span data-stu-id="7561d-135">Tactile immersion is the experience of sensory feedback from performing repetitious actions.</span></span> <span data-ttu-id="7561d-136">В этом случае повторяющиеся действия для настройки регулирования бегунка и поворота, который этот момент посмотрите и послушайте наши уши, помогает подключения проигрывателя в ACT целевой корабль на поверхности луны.</span><span class="sxs-lookup"><span data-stu-id="7561d-136">In this case, the repetitive action of adjusting the throttle lever and rotation which our eyes see and our ears hear, helps connect the player to the act of landing a ship on the moon’s surface.</span></span> <span data-ttu-id="7561d-137">Эта концепция могут быть привязаны к психологической понятие «поток».</span><span class="sxs-lookup"><span data-stu-id="7561d-137">This concept can be tied to the psychological concept of "flow."</span></span> <span data-ttu-id="7561d-138">Там, где пользователь является полностью поглощает в задачу, которая имеет правой смесь запрос и reward или проще говоря более, в которых они расположены «зона».</span><span class="sxs-lookup"><span data-stu-id="7561d-138">Where a user is fully absorbed in a task that has the right mixture of challenge and reward, or put more simply, they’re “in the zone.”</span></span>

<span data-ttu-id="7561d-139">Пожалуй наиболее выдающейся тип погружения в смешанной реальности — Пространственные погружения.</span><span class="sxs-lookup"><span data-stu-id="7561d-139">Arguably, the most prominent type of immersion in mixed reality is spatial immersion.</span></span> <span data-ttu-id="7561d-140">Весь смысл смешанной реальности является обмануть сами обмануть эти цифровые объекты существуют в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="7561d-140">The whole point of mixed reality is to fool ourselves into believing these digital objects exist in the real world.</span></span> <span data-ttu-id="7561d-141">Мы создав голограммы в нашей окружающей среды, пространственно занимается целых сред и примерах.</span><span class="sxs-lookup"><span data-stu-id="7561d-141">We’re synthesizing holograms in our surroundings, spatially immersed in entire environments and experiences.</span></span> <span data-ttu-id="7561d-142">Это не означает, что мы не может по-прежнему применять другие виды погружения в нашем опыте работы так же, как Atari с tactile погружения в Lander лунный календарь.</span><span class="sxs-lookup"><span data-stu-id="7561d-142">This doesn’t mean we can’t still employ other types of immersion in our experiences just as Atari did with tactile immersion in Lunar Lander.</span></span>

## <a name="designing-with-immersion"></a><span data-ttu-id="7561d-143">При разработке погружения</span><span class="sxs-lookup"><span data-stu-id="7561d-143">Designing with immersion</span></span>

<span data-ttu-id="7561d-144">Как может применить tactile погружения к обновленным, объемные продолжение в классическом Atari?</span><span class="sxs-lookup"><span data-stu-id="7561d-144">How might we apply tactile immersion to an updated, volumetric sequel to the Atari classic?</span></span> <span data-ttu-id="7561d-145">Прежде чем браться входной схемы, необходимо предусмотреть игр конструкции для трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="7561d-145">Before tackling the input scheme, the game construct for 3-dimensional space needs to be addressed.</span></span>

<span data-ttu-id="7561d-146">![Визуализация поверхности сопоставления в HoloLens](images/surfacemapping.png)</span><span class="sxs-lookup"><span data-stu-id="7561d-146">![Visualizing surface mapping in HoloLens](images/surfacemapping.png)</span></span><br>
<span data-ttu-id="7561d-147">*Визуализация пространственное сопоставление в HoloLens*</span><span class="sxs-lookup"><span data-stu-id="7561d-147">*Visualizing spatial mapping in HoloLens*</span></span>

<span data-ttu-id="7561d-148">За счет использования окружения пользователя, мы фактически способами бесконечный ландшафта целевая нашего лунного модуля.</span><span class="sxs-lookup"><span data-stu-id="7561d-148">By leveraging a user’s surroundings, we effectively have infinite terrain options for landing our lunar module.</span></span> <span data-ttu-id="7561d-149">Создать наиболее исходное название игры, пользователь потенциально может управлять и поместите дополняет целевой различных трудностей в своей среде.</span><span class="sxs-lookup"><span data-stu-id="7561d-149">To make the game most like the original title, a user could potentially manipulate and place landing pads of varying difficulties in their environment.</span></span>

<span data-ttu-id="7561d-150">![Некоторые вещи лунного модуля](images/640px-lm-hero.jpg)</span><span class="sxs-lookup"><span data-stu-id="7561d-150">![Flying the Lunar Module](images/640px-lm-hero.jpg)</span></span><br>
<span data-ttu-id="7561d-151">*Некоторые вещи лунного модуля*</span><span class="sxs-lookup"><span data-stu-id="7561d-151">*Flying the Lunar Module*</span></span>

<span data-ttu-id="7561d-152">Пользователю нужно было Узнайте входной схемы, управлять корабля, а также иметь маленьких целевых должны переходить на очень много для запроса.</span><span class="sxs-lookup"><span data-stu-id="7561d-152">Requiring the user to learn the input scheme, control the ship, and have a small target to land on is a lot to ask.</span></span> <span data-ttu-id="7561d-153">Успешно игр возможности справа смешивать запрос и reward.</span><span class="sxs-lookup"><span data-stu-id="7561d-153">A successful game experience features the right mix of challenge and reward.</span></span> <span data-ttu-id="7561d-154">Пользователь должен иметь возможность выбирать уровень сложности, с помощью самый легкий режим просто пользователю нужно было успешно land в пользовательской области на поверхности просмотрены HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7561d-154">The user should be able to choose a level of difficulty, with the easiest mode simply requiring the user to successfully land in a user-defined area on a surface scanned by the HoloLens.</span></span> <span data-ttu-id="7561d-155">После того как пользователь возвращает зависания игры, они могут затем ремеслу сложность по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="7561d-155">Once a user gets the hang of the game, they can then crank up the difficulty as they see fit.</span></span>

### <a name="adding-input-for-hand-gestures"></a><span data-ttu-id="7561d-156">Идет Добавление входных данных для жестами руками</span><span class="sxs-lookup"><span data-stu-id="7561d-156">Adding input for hand gestures</span></span>

<span data-ttu-id="7561d-157">Базовый HoloLens входных данных имеет только два жесты - [коснитесь Air и раскрытия](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="7561d-157">HoloLens base input has only two gestures - [Air Tap and Bloom](gestures.md).</span></span> <span data-ttu-id="7561d-158">Пользователям не нужно запоминать контекстные особенности или перечня определенных жестов чему интерфейс платформы, гибким и удобные для изучения.</span><span class="sxs-lookup"><span data-stu-id="7561d-158">Users don’t need to remember contextual nuances or a laundry list of specific gestures which makes the platform’s interface both versatile and easy to learn.</span></span> <span data-ttu-id="7561d-159">Хотя система может предоставлять только эти два жесты, HoloLens, как устройство позволяет одновременно отслеживать два руки.</span><span class="sxs-lookup"><span data-stu-id="7561d-159">While the system may only expose these two gestures, HoloLens as a device is capable of tracking two hands at once.</span></span> <span data-ttu-id="7561d-160">Является нашей оды к лунный Lander [иммерсивные приложения](app-model.md) это означает, что у нас есть возможность расширять базовый набор жестов использовать две руки и добавления собственных восхитительно tactile означает, что для модуля лунного навигации.</span><span class="sxs-lookup"><span data-stu-id="7561d-160">Our ode to Lunar Lander is an [immersive app](app-model.md) which means we have the ability to extend the base set of gestures to leverage two hands and add our own delightfully tactile means for lunar module navigation.</span></span>

<span data-ttu-id="7561d-161">Если снова посмотреть на схеме исходный элемент управления **нам требовалось решать Осевая сила и угла поворота**.</span><span class="sxs-lookup"><span data-stu-id="7561d-161">Looking back at the original control scheme, **we needed to solve for thrust and rotation**.</span></span> <span data-ttu-id="7561d-162">Проблема заключается в том, поворот в новом контексте добавляет дополнительной оси (с технической точки зрения двух, но менее важна для начальных оси Y).</span><span class="sxs-lookup"><span data-stu-id="7561d-162">The caveat is rotation in the new context adds an additional axis (technically two, but the Y axis is less important for landing).</span></span> <span data-ttu-id="7561d-163">Два различных ship перемещений естественным образом приспособлены для сопоставления с каждой стороны:</span><span class="sxs-lookup"><span data-stu-id="7561d-163">The two distinct ship movements naturally lend themselves to be mapped to each hand:</span></span>

<span data-ttu-id="7561d-164">![Коснитесь и перетащите жестов для поворота lander на всем трем осям](images/module-handdrag.gif)</span><span class="sxs-lookup"><span data-stu-id="7561d-164">![Tap and drag gesture to rotate lander on all three axes](images/module-handdrag.gif)</span></span><br>
<span data-ttu-id="7561d-165">*Коснитесь и перетащите жестов для поворота lander на всем трем осям*</span><span class="sxs-lookup"><span data-stu-id="7561d-165">*Tap and drag gesture to rotate lander on all three axes*</span></span>

<span data-ttu-id="7561d-166">**Более широкая**</span><span class="sxs-lookup"><span data-stu-id="7561d-166">**Thrust**</span></span>

<span data-ttu-id="7561d-167">Бегунка исходном компьютере аркадная сопоставлен Масштаб значений, чем выше уровень был перемещен дополнительные надежность была применена к корабля.</span><span class="sxs-lookup"><span data-stu-id="7561d-167">The lever on the original arcade machine mapped to a scale of values, the higher the lever was moved the more thrust was applied to the ship.</span></span> <span data-ttu-id="7561d-168">Важная особенность, достойная отметить здесь — пользователь может принимать их передачу управления и поддерживать нужное значение.</span><span class="sxs-lookup"><span data-stu-id="7561d-168">An important nuance to point out here is the user can take their hand off of the control and maintain a desired value.</span></span> <span data-ttu-id="7561d-169">Можно эффективно использовать коснитесь и перетащите поведение для достижения такого же результата.</span><span class="sxs-lookup"><span data-stu-id="7561d-169">We can effectively use tap-and-drag behavior to achieve the same result.</span></span> <span data-ttu-id="7561d-170">Значение Осевая сила начинается с нуля.</span><span class="sxs-lookup"><span data-stu-id="7561d-170">The thrust value starts at zero.</span></span> <span data-ttu-id="7561d-171">Пользователь нажимает и перетаскивает для увеличения значения.</span><span class="sxs-lookup"><span data-stu-id="7561d-171">The user taps and drags to increase the value.</span></span> <span data-ttu-id="7561d-172">На этом этапе может позволить переходят к его обслуживания.</span><span class="sxs-lookup"><span data-stu-id="7561d-172">At that point they could let go to maintain it.</span></span> <span data-ttu-id="7561d-173">Любое изменение значения жест касания и перетащите бы отклонение от исходного значения.</span><span class="sxs-lookup"><span data-stu-id="7561d-173">Any tap-and-drag gesture value change would be the delta from the original value.</span></span>

<span data-ttu-id="7561d-174">**Поворот**</span><span class="sxs-lookup"><span data-stu-id="7561d-174">**Rotation**</span></span>

<span data-ttu-id="7561d-175">Это немного более сложным.</span><span class="sxs-lookup"><span data-stu-id="7561d-175">This is a little more tricky.</span></span> <span data-ttu-id="7561d-176">HAVING, holographic кнопки «поворот» коснитесь делает ужасно взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="7561d-176">Having holographic “rotate” buttons to tap makes for a terrible experience.</span></span> <span data-ttu-id="7561d-177">Нет физического элемента управления, чтобы использовать, поэтому поведение должны поступать из обработка объект, представляющий lander, или с lander, сам.</span><span class="sxs-lookup"><span data-stu-id="7561d-177">There isn’t a physical control to leverage, so the behavior must come from manipulation of an object representing the lander, or with the lander itself.</span></span> <span data-ttu-id="7561d-178">У нас получилось метода с помощью коснитесь и перетащите которого позволяет эффективно «по запросу и принудительную» его в направлении он нуждается в них для лицевой стороной.</span><span class="sxs-lookup"><span data-stu-id="7561d-178">We came up with a method using tap-and-drag which enables a user to effectively “push and pull” it in the direction they want it to face.</span></span> <span data-ttu-id="7561d-179">Любое время, пользователь касается и содержит точку в место, где была инициирована жест становится точку отсчета для поворота.</span><span class="sxs-lookup"><span data-stu-id="7561d-179">Any time a user taps and holds, the point in space where the gesture was initiated becomes the origin for rotation.</span></span> <span data-ttu-id="7561d-180">Перетаскивание из источника преобразует к разностным изменениям между перевода Рука (X, Y, Z) и применяет их к дельта lander значений поворота.</span><span class="sxs-lookup"><span data-stu-id="7561d-180">Dragging from the origin converts the delta of the hand's translation (X,Y,Z) and applies it to the delta of the lander's rotation values.</span></span> <span data-ttu-id="7561d-181">Проще говоря *перетаскивать слева <> – вправо, вверх <> – вниз», «вперед <> – обратно в пробелы поворачивает корабль соответствующим образом*.</span><span class="sxs-lookup"><span data-stu-id="7561d-181">Or more simply, *dragging left <-> right, up <-> down, forward <-> back in spaces rotates the ship accordingly*.</span></span>

<span data-ttu-id="7561d-182">Поскольку HoloLens можно отслеживать две руки, поворот можно назначить в правом нижнем, а Осевая сила управляется слева.</span><span class="sxs-lookup"><span data-stu-id="7561d-182">Since the HoloLens can track two hands, rotation can be assigned to the right hand while thrust is controlled by the left.</span></span> <span data-ttu-id="7561d-183">Умелого является решающим фактором для успеха в этой игре.</span><span class="sxs-lookup"><span data-stu-id="7561d-183">Finesse is the driving factor for success in this game.</span></span> <span data-ttu-id="7561d-184">*Чувствовать* этих взаимодействий является абсолютным наивысший приоритет.</span><span class="sxs-lookup"><span data-stu-id="7561d-184">The *feel* of these interactions is the absolute highest priority.</span></span> <span data-ttu-id="7561d-185">Особенно в контексте tactile погружения.</span><span class="sxs-lookup"><span data-stu-id="7561d-185">Especially in context of tactile immersion.</span></span> <span data-ttu-id="7561d-186">Поставки, которая слишком быстро реагирует бы излишне сложным испытывал некоторые колебания, хотя один слишком медленно требуют от пользователя «Push-уведомлений и получения по запросу» относительно корабля awkwardly long количество времени.</span><span class="sxs-lookup"><span data-stu-id="7561d-186">A ship that reacts too quickly would be unnecessarily difficult to steer, while one too slow would require the user to “push and pull” on the ship for an awkwardly long amount of time.</span></span>

### <a name="adding-input-for-game-controllers"></a><span data-ttu-id="7561d-187">Идет Добавление входных данных, игровые устройства управления</span><span class="sxs-lookup"><span data-stu-id="7561d-187">Adding input for game controllers</span></span>

<span data-ttu-id="7561d-188">Хотя жестами руками на HoloLens обеспечивают возможность novel точное управление, по-прежнему отсутствия 'true' tactile отзыв, полученный от аналогового элементов управления.</span><span class="sxs-lookup"><span data-stu-id="7561d-188">While hand gestures on the HoloLens provide a novel method of fine-grain control, there is still a certain lack of 'true' tactile feedback that you get from analog controls.</span></span> <span data-ttu-id="7561d-189">Подключение контроллеру игр Xbox позволяет вернуть чувство физической природы задействуя устройства управления для сохранения точное управление.</span><span class="sxs-lookup"><span data-stu-id="7561d-189">Connecting an Xbox game controller allows to bring back this sense of physicality while leveraging the control sticks to retain fine-grain control.</span></span>

<span data-ttu-id="7561d-190">Существует несколько способов для применения схемы управления сравнительно просто — контроллер Xbox.</span><span class="sxs-lookup"><span data-stu-id="7561d-190">There are multiple ways to apply the relatively straight-forward control scheme to the Xbox controller.</span></span> <span data-ttu-id="7561d-191">Так как мы пытаемся оставаться как можно ближе к исходной arcade настроить максимально **более широкая** сопоставляется лучшие "активировать".</span><span class="sxs-lookup"><span data-stu-id="7561d-191">Since we're trying to stay as close to the original arcade set up as possible, **Thrust** maps best to the trigger button.</span></span> <span data-ttu-id="7561d-192">Эти кнопки это аналогового элементы управления, то есть они имеют более простой *включения и отключения* состояния, они фактически реагировать на них степень давления, применяемыми к ним.</span><span class="sxs-lookup"><span data-stu-id="7561d-192">These buttons are analog controls, meaning they have more than simple *on and off* states, they actually respond to the degree of pressure put on them.</span></span> <span data-ttu-id="7561d-193">Это дает нам аналогичные конструкцию как **бегунка Осевая сила**.</span><span class="sxs-lookup"><span data-stu-id="7561d-193">This gives us a similar construct as the **thrust lever**.</span></span> <span data-ttu-id="7561d-194">В отличие от оригинальную игру и наличии жест этот элемент управления будет обрезана Осевая сила корабля, когда пользователь останавливает усилия по триггеру.</span><span class="sxs-lookup"><span data-stu-id="7561d-194">Unlike the original game and the hand gesture, this control will cut the ship's thrust once a user stops putting pressure on the trigger.</span></span> <span data-ttu-id="7561d-195">Его по-прежнему предоставляет пользователю такую же степень умелого как исходное аркадные игры.</span><span class="sxs-lookup"><span data-stu-id="7561d-195">It still gives the user the same degree of finesse as the original arcade game did.</span></span>

<span data-ttu-id="7561d-196">![Левый джойстик сопоставляется поворот и отменять изменения, правом джойстик сопоставляется выдачи и отменять изменения](images/thumbsticksidebyside.gif)</span><span class="sxs-lookup"><span data-stu-id="7561d-196">![Left thumbstick is mapped to Yaw and Roll, Right thumbstick is mapped to Pitch and Roll](images/thumbsticksidebyside.gif)</span></span><br>
<span data-ttu-id="7561d-197">*Левый джойстик сопоставляется поворот и отменять изменения; правом джойстик сопоставляется выдачи и отменять изменения*</span><span class="sxs-lookup"><span data-stu-id="7561d-197">*Left thumbstick is mapped to yaw and roll; right thumbstick is mapped to pitch and roll*</span></span>

<span data-ttu-id="7561d-198">Двойной thumbsticks естественным образом приспособлены для управления ship поворота.</span><span class="sxs-lookup"><span data-stu-id="7561d-198">The dual thumbsticks naturally lend themselves to controlling ship rotation.</span></span> <span data-ttu-id="7561d-199">К сожалению, существуют 3 оси на который можно поворачивать корабль и два thumbsticks оба способа поддерживает две оси.</span><span class="sxs-lookup"><span data-stu-id="7561d-199">Unfortunately, there are 3 axes on which the ship can rotate and two thumbsticks which both support two axes.</span></span> <span data-ttu-id="7561d-200">Это несоответствие означает либо один джойстик элементов управления одной оси; или перекрытие осей для thumbsticks.</span><span class="sxs-lookup"><span data-stu-id="7561d-200">This mismatch means either one thumbstick controls one axis; or there is overlap of axes for the thumbsticks.</span></span> <span data-ttu-id="7561d-201">Первое решение в итоге кажется «неисправный», так как thumbsticks по своей природе blend их локальные значения X и Y.</span><span class="sxs-lookup"><span data-stu-id="7561d-201">The former solution ended up feeling "broken" since thumbsticks inherently blend their local X and Y values.</span></span> <span data-ttu-id="7561d-202">Второму решению требуется некоторое тестирование для определения, какие избыточное осях чувствовать самым естественным выбором.</span><span class="sxs-lookup"><span data-stu-id="7561d-202">The latter solution required some testing to find which redundant axes feel the most natural.</span></span> <span data-ttu-id="7561d-203">Последний пример использует *Поворот* и *наката* (осей X и Y) для левый джойстик и *шаг* и *наката* (оси Z и X) для правого джойстик.</span><span class="sxs-lookup"><span data-stu-id="7561d-203">The final sample uses *yaw* and *roll* (Y and X axes) for the left thumbstick, and *pitch* and *roll* (Z and X axes) for the right thumbstick.</span></span> <span data-ttu-id="7561d-204">Это показалось, самым естественным выбором как *наката* кажется независимо друг от друга хорошо сочетаются с *Поворот* и *pitch*.</span><span class="sxs-lookup"><span data-stu-id="7561d-204">This felt the most natural as *roll* seems to independently pair well with *yaw* and *pitch*.</span></span> <span data-ttu-id="7561d-205">Заметим, с помощью обоих thumbsticks для *наката* удвоенное значение поворота; также происходит довольно приятно иметь lander do-циклы.</span><span class="sxs-lookup"><span data-stu-id="7561d-205">As a side note, using both thumbsticks for *roll* also happens to double the rotation value; it's pretty fun to have the lander do loops.</span></span>

<span data-ttu-id="7561d-206">Этот пример приложения демонстрирует пространственных распознавания и tactile погружения значительно можно изменить стиль работы благодаря Windows Mixed Reality расширяемый входной модальностей.</span><span class="sxs-lookup"><span data-stu-id="7561d-206">This sample app demonstrates how spatial recognition and tactile immersion can significantly change an experience thanks to Windows Mixed Reality's extensible input modalities.</span></span> <span data-ttu-id="7561d-207">Хотя лунный Lander может произойти 40 лет в век, основные понятия доступны с что мало восьмиугольник с конечностей будет располагаться до бесконечности.</span><span class="sxs-lookup"><span data-stu-id="7561d-207">While Lunar Lander may be nearing 40 years in age, the concepts exposed with that little octagon-with-legs will live on forever.</span></span> <span data-ttu-id="7561d-208">Если представить себе в будущем, почему бы не рассмотрим раньше?</span><span class="sxs-lookup"><span data-stu-id="7561d-208">When imagining the future, why not look at the past?</span></span>

## <a name="technical-details"></a><span data-ttu-id="7561d-209">Технические подробности</span><span class="sxs-lookup"><span data-stu-id="7561d-209">Technical details</span></span>

<span data-ttu-id="7561d-210">Можно найти сценарии и prefabs для примера приложения лунного модуля на [смешанной реальности разработки Labs на сайте GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).</span><span class="sxs-lookup"><span data-stu-id="7561d-210">You can find scripts and prefabs for the Lunar Module sample app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).</span></span>

## <a name="about-the-author"></a><span data-ttu-id="7561d-211">Об авторе</span><span class="sxs-lookup"><span data-stu-id="7561d-211">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="7561d-212"><b>Addison Linville</b></span><span class="sxs-lookup"><span data-stu-id="7561d-212"><b>Addison Linville</b></span></span><br><span data-ttu-id="7561d-213">Конструктор UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="7561d-213">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="7561d-214">См. также</span><span class="sxs-lookup"><span data-stu-id="7561d-214">See also</span></span>
* [<span data-ttu-id="7561d-215">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="7561d-215">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="7561d-216">Жесты</span><span class="sxs-lookup"><span data-stu-id="7561d-216">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="7561d-217">Типы приложений, смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="7561d-217">Types of mixed reality apps</span></span>](types-of-mixed-reality-apps.md)