---
title: Пример использования - просматривая отверстия в реальности
description: В этом практическом объясняется, как реализовать «магический окно» воздействие на HoloLens, позволяя пользователю см. в статье за стены, в разделе ближайшее снизу целое, а также в виртуальной отверстия в своей среде фактическое.
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, magic окна, фокусировки
ms.openlocfilehash: 945a09614fbc77400825b524f4e0b591bf7b1f6b
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873928"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="33bc6-104">Пример использования - просматривая отверстия в реальности</span><span class="sxs-lookup"><span data-stu-id="33bc6-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="33bc6-105">При рассмотрении вопроса о смешанной реальности и их возможности с Microsoft HoloLens, они обычно придерживаться вопросы, такие как «Какие объекты, можно ли добавить в Мои места»?</span><span class="sxs-lookup"><span data-stu-id="33bc6-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="33bc6-106">или «Что можно я слоя на основе моей сферы?»</span><span class="sxs-lookup"><span data-stu-id="33bc6-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="33bc6-107">Хотелось бы выделить еще одна область, можно рассмотреть — по существу ухищрения — с помощью той же технологии для поиска в или с помощью физического объектов вокруг вас.</span><span class="sxs-lookup"><span data-stu-id="33bc6-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="33bc6-108">Технический</span><span class="sxs-lookup"><span data-stu-id="33bc6-108">The tech</span></span>

<span data-ttu-id="33bc6-109">Если мучились пришельцы, как они существенно повышает стен в  **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, разблокировать стены в безопасном  **[фрагментов](case-study-creating-an-immersive-experience-in-fragments.md)**, или были найдется Чтобы увидеть hangar UNSC бесконечности в  **[Halo 5 опыт в E3 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, то вам уже знакома, о чем я говорю.</span><span class="sxs-lookup"><span data-stu-id="33bc6-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="33bc6-110">В зависимости от свое воображение этот прием visual можно поместить временные отверстия в вашей внутренних или скрыть миров под свободные floorboard.</span><span class="sxs-lookup"><span data-stu-id="33bc6-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![RoboRaid добавляет трехмерного каналы и другие структуры стен отображается только с помощью бреши в системе, как решать вредоносных программ.](images/roboraid-640px.png)

<span data-ttu-id="33bc6-112">RoboRaid добавляет трехмерного каналы и другие структуры стен отображается только с помощью бреши в системе, как решать вредоносных программ.</span><span class="sxs-lookup"><span data-stu-id="33bc6-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="33bc6-113">С помощью одного из этих уникальных голограммы на HoloLens, приложение может создать иллюзию содержимого за стен или через ваш floor таким же образом, реальность проявляет себя через окна.</span><span class="sxs-lookup"><span data-stu-id="33bc6-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="33bc6-114">Переместить самостоятельно слева, и вы увидите, все, что находится справа от оператора.</span><span class="sxs-lookup"><span data-stu-id="33bc6-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="33bc6-115">Ближе, и вы увидите чуть подробнее всего содержимого.</span><span class="sxs-lookup"><span data-stu-id="33bc6-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="33bc6-116">Основное отличие — это что реальные отверстия позволяют, то время как вашей floor параллельных не позволяют переходить через этого магического holographic содержимого.</span><span class="sxs-lookup"><span data-stu-id="33bc6-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="33bc6-117">(Я добавлю задачу в невыполненную работу.)</span><span class="sxs-lookup"><span data-stu-id="33bc6-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="33bc6-118">Как это делается</span><span class="sxs-lookup"><span data-stu-id="33bc6-118">Behind the scenes</span></span>

<span data-ttu-id="33bc6-119">Этот прием состоит из двух результатов.</span><span class="sxs-lookup"><span data-stu-id="33bc6-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="33bc6-120">Во-первых, holographic содержимое закрепляется на мира с помощью «пространственных привязки».</span><span class="sxs-lookup"><span data-stu-id="33bc6-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="33bc6-121">Использование привязки для того, что содержимое «world заблокирован» означает, что вы просматриваете не переместятся визуально от физических объектов, рядом с ней, даже при перемещении или базовой системы пространственное сопоставление обновляет его трехмерной модели комнате.</span><span class="sxs-lookup"><span data-stu-id="33bc6-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="33bc6-122">Во-вторых это holographic содержимое ограничено визуально очень определенное пространство, видела только через отверстия в реальности.</span><span class="sxs-lookup"><span data-stu-id="33bc6-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="33bc6-123">Что перекрытия нерационально требовать просматривая логических брешь в системе, окно или двери, которая занимается продажей фокус.</span><span class="sxs-lookup"><span data-stu-id="33bc6-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="33bc6-124">Без чего-либо блокировки большую часть представления взломан в пространстве с измерением секретный древнейшие может просто выглядеть плохо помещено динозавров.</span><span class="sxs-lookup"><span data-stu-id="33bc6-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![Это не фактический снимок экрана, но иллюстрация того, как выглядит секретный underworld из 101 основы MR на HoloLens.](images/origamiholecomposited-640px.png)

<span data-ttu-id="33bc6-128">Это не фактический снимок экрана, а также показано, как секретный underworld из [101 основы MR](holograms-101.md) выглядит на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="33bc6-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="33bc6-129">Черный корпус не отображается, но вы увидите содержимое через виртуальный отверстия.</span><span class="sxs-lookup"><span data-stu-id="33bc6-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="33bc6-130">(При просмотре на настоящем устройстве, округление вниз предположительно исчезают еще более, так как глаза сосредоточиться на дальнейшие расстоянии, как, если их там еще нет.)</span><span class="sxs-lookup"><span data-stu-id="33bc6-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="33bc6-131">Блокировка World holographic содержимого</span><span class="sxs-lookup"><span data-stu-id="33bc6-131">World-locking holographic content</span></span>

<span data-ttu-id="33bc6-132">В Unity вызывая holographic содержимое, чтобы оставаться в мире заблокирован так же просто, как добавление WorldAnchor компонента:</span><span class="sxs-lookup"><span data-stu-id="33bc6-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="33bc6-133">Компонент WorldAnchor постоянно настроит положения и поворота элемента его GameObject (и таким образом все остальное в этот объект в иерархии) для поддержания стабильной относительно ближайших физические объекты.</span><span class="sxs-lookup"><span data-stu-id="33bc6-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="33bc6-134">При создании содержимого, создайте его таким образом, что корневой вращения объекта центрируется в этот виртуальный брешь в системе.</span><span class="sxs-lookup"><span data-stu-id="33bc6-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="33bc6-135">(Если pivot объекта глубоко в стену, его незначительные изменения в положения и поворота будут гораздо более наглядными и отверстия может выглядеть очень редко.)</span><span class="sxs-lookup"><span data-stu-id="33bc6-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="33bc6-136">Все, кроме виртуального отверстия occluding</span><span class="sxs-lookup"><span data-stu-id="33bc6-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="33bc6-137">Существует ряд способов для выборочного блокирования представлении, чтобы новые скрыт в стенах.</span><span class="sxs-lookup"><span data-stu-id="33bc6-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="33bc6-138">Самый простой вариант использует преимущества тот факт, что HoloLens использует изображении аддитивны, это означает, что полностью черным объекты невидимым.</span><span class="sxs-lookup"><span data-stu-id="33bc6-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="33bc6-139">Это можно сделать в Unity не выполняя все специальные шейдера или материала рекомендации — просто создайте черный материала и назначьте его на объект, в содержимое.</span><span class="sxs-lookup"><span data-stu-id="33bc6-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="33bc6-140">Если вам не очень хочется выполнив 3D-моделирования, просто использовать небольшое число объектов квадрант по умолчанию и перекрывающиеся немного.</span><span class="sxs-lookup"><span data-stu-id="33bc6-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="33bc6-141">Есть ряд недостатков этого подхода, но он является самым быстрым способом, то или иное действие работа начало низкой четкости проверки концепции работы отлично подходит, даже если вы подозреваете, что вы можете выполнить его рефакторинг.</span><span class="sxs-lookup"><span data-stu-id="33bc6-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="33bc6-142">Недостатком выше подхода «черного ящика» — что он не нельзя было сфотографировать хорошо.</span><span class="sxs-lookup"><span data-stu-id="33bc6-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="33bc6-143">Хотя эффект может выглядеть идеальное через отображение HoloLens, все снимки экрана, которые можно предпринять покажет большого объекта черный вместо останется по часам или floor.</span><span class="sxs-lookup"><span data-stu-id="33bc6-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="33bc6-144">Причиной этого является то, что физического оборудования и снимки экрана составного голограммы и реальность по-разному.</span><span class="sxs-lookup"><span data-stu-id="33bc6-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="33bc6-145">Давайте использования на некоторое время, в некоторые фиктивные расчеты...</span><span class="sxs-lookup"><span data-stu-id="33bc6-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="33bc6-146">*Предупреждение фальшивые math! Эти номера и формул предназначены для демонстрации точки, не следует каких-либо точные метрики!*</span><span class="sxs-lookup"><span data-stu-id="33bc6-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="33bc6-147">Отображаемые через HoloLens:</span><span class="sxs-lookup"><span data-stu-id="33bc6-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="33bc6-148">Как видно снимки экрана и видео:</span><span class="sxs-lookup"><span data-stu-id="33bc6-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="33bc6-149">На английском языке: Вы видите через HoloLens представляет собой простой сочетание затемненном реальности (например, через очков)) и любым голограммы приложение хочет отобразить.</span><span class="sxs-lookup"><span data-stu-id="33bc6-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="33bc6-150">Но когда вы делаете снимок экрана, изображение камеры смешивается с голограммы приложения в соответствии с значением прозрачности каждого пикселя.</span><span class="sxs-lookup"><span data-stu-id="33bc6-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="33bc6-151">Один из способов обойти это является изменение материал «черного ящика», только запись в буфер глубины и сортировать все непрозрачный материалы.</span><span class="sxs-lookup"><span data-stu-id="33bc6-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="33bc6-152">Пример этого см. [файл WindowOcclusion.shader в MixedRealityToolkit на GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span><span class="sxs-lookup"><span data-stu-id="33bc6-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="33bc6-153">Соответствующие строки копируются здесь:</span><span class="sxs-lookup"><span data-stu-id="33bc6-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="33bc6-154">(Обратите внимание, «Offset 50, 100» строки – разобраться со несвязанных проблем, поэтому, возможно, смысл убрать,.)</span><span class="sxs-lookup"><span data-stu-id="33bc6-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="33bc6-155">Подобное реализации невидимым перекрытия материал позволит рисования поля, которое выглядит правильно, в отображении и смешанной реальности на снимках экрана приложения.</span><span class="sxs-lookup"><span data-stu-id="33bc6-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="33bc6-156">Для получения премиальных баллов вы можете попытаться улучшить производительность этого ящика еще дальше, clever делаем для рисования еще меньшее количество пикселей невидимым, но, действительно можно получить в weeds и обычно не является необходимым.</span><span class="sxs-lookup"><span data-stu-id="33bc6-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![Вот секретный underworld из 101 основы MR Unity рисует его, за исключением внешней части occluding поле.](images/underworld-occluded-640px.png)

<span data-ttu-id="33bc6-159">Вот секретное underworld из [101 основы MR](holograms-101.md) как Unity рисует его, за исключением внешней части occluding поле.</span><span class="sxs-lookup"><span data-stu-id="33bc6-159">Here is the secret underworld from [MR Basics 101](holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="33bc6-160">Обратите внимание, что вращения для underworld в центре окна, что помогает поддерживать отверстия максимально относительно вашего фактическое floor стабильным.</span><span class="sxs-lookup"><span data-stu-id="33bc6-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="33bc6-161">Сделать это самостоятельно</span><span class="sxs-lookup"><span data-stu-id="33bc6-161">Do it yourself</span></span>

<span data-ttu-id="33bc6-162">Есть HoloLens и хотите попробовать эффект самостоятельно?</span><span class="sxs-lookup"><span data-stu-id="33bc6-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="33bc6-163">Проще всего, можно сделать (не требует дополнительного программирования) — установите бесплатное приложение средства просмотра 3D, а затем загрузить [the.fbx файл загрузки, я предоставил на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) просматривать модель pot цветка в комнате.</span><span class="sxs-lookup"><span data-stu-id="33bc6-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="33bc6-164">Загрузить ее на HoloLens, и вы увидите иллюзию на работе.</span><span class="sxs-lookup"><span data-stu-id="33bc6-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="33bc6-165">Когда вы будете перед модели, будут отображаться только в небольших брешь в системе — все остальное остается невидимым.</span><span class="sxs-lookup"><span data-stu-id="33bc6-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="33bc6-166">Посмотрите на модели из любой другой стороне, и он полностью исчезнет.</span><span class="sxs-lookup"><span data-stu-id="33bc6-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="33bc6-167">Используйте перемещения, поворота и масштабирования элементов управления средства просмотра трехмерной для размещения виртуального брешь в системе с любой вертикальной поверхности, которые можно представить для создания некоторыми идеями!</span><span class="sxs-lookup"><span data-stu-id="33bc6-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![Просмотр этой модели в редакторе Unity покажет большой черный прямоугольник вокруг flowerpot.](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="33bc6-170">Просмотр этой модели в редакторе Unity покажет большой черный прямоугольник вокруг flowerpot.</span><span class="sxs-lookup"><span data-stu-id="33bc6-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="33bc6-171">На HoloLens поле не отображается, возможности эффекта magic окно.</span><span class="sxs-lookup"><span data-stu-id="33bc6-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="33bc6-172">Если вы хотите создать приложение, которое использует эту методику, см. статью [руководстве 101 основы MR](holograms-101.md) в [учебники смешанной реальности](tutorials.md).</span><span class="sxs-lookup"><span data-stu-id="33bc6-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](holograms-101.md) in the [Mixed Reality tutorials](tutorials.md).</span></span> <span data-ttu-id="33bc6-173">Глава 7 заканчивается развертывания в вашей floor, отображающую скрытые underworld (как показано на рисунке выше).</span><span class="sxs-lookup"><span data-stu-id="33bc6-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="33bc6-174">Кто сказал, что должны были быть нудным руководства?</span><span class="sxs-lookup"><span data-stu-id="33bc6-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="33bc6-175">Ниже приведены некоторые идеи из где вы можете расширить эту идею далее:</span><span class="sxs-lookup"><span data-stu-id="33bc6-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="33bc6-176">Решить, как сделать интерактивный содержимое внутри виртуальной брешь в системе.</span><span class="sxs-lookup"><span data-stu-id="33bc6-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="33bc6-177">Пользователей может несколько снизить за их пределами может действительно повысить смысле бы поинтересоваться, которую может предоставить этот прием.</span><span class="sxs-lookup"><span data-stu-id="33bc6-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="33bc6-178">Решить, как см. в разделе через объекты к известной области.</span><span class="sxs-lookup"><span data-stu-id="33bc6-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="33bc6-179">Например как вы поместите holographic отверстия в таблице кофе и см. в разделе вашей floor под ним?</span><span class="sxs-lookup"><span data-stu-id="33bc6-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="33bc6-180">Об авторе</span><span class="sxs-lookup"><span data-stu-id="33bc6-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="33bc6-181"><b>Эрик Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="33bc6-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="33bc6-182">Старший инженер @Microsoft</span><span class="sxs-lookup"><span data-stu-id="33bc6-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="33bc6-183">См. также</span><span class="sxs-lookup"><span data-stu-id="33bc6-183">See also</span></span>
* [<span data-ttu-id="33bc6-184">101. Основы смешанной реальности: полный проект с использованием устройства</span><span class="sxs-lookup"><span data-stu-id="33bc6-184">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="33bc6-185">Системы координат</span><span class="sxs-lookup"><span data-stu-id="33bc6-185">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="33bc6-186">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="33bc6-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="33bc6-187">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="33bc6-187">Spatial mapping</span></span>](spatial-mapping.md)