---
title: Пример использования. Создание Galaxy в смешанной реальности
description: Прежде чем приступить к работе с Microsoft HoloLens, мы спросили наше сообщество разработчиков, какого рода приложение хотели бы видеть для нового устройства опытную внутреннюю сборку. Было предоставлено более 5000 идей, и после опроса Twitter в течение 24 часов победителя была идея «Galaxy Explorer».
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, Windows Mixed Reality, поделиться своей идеей, пример внедрения
ms.openlocfilehash: f13395250c8a73718408c051ab95d2ec4bf62014
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278182"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="97ffd-105">Пример использования. Создание Galaxy в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="97ffd-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="97ffd-106">Прежде чем приступить к работе с Microsoft HoloLens, мы спросили наше сообщество разработчиков, какого рода приложение хотели бы видеть для нового устройства опытную внутреннюю сборку.</span><span class="sxs-lookup"><span data-stu-id="97ffd-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="97ffd-107">Было предоставлено более 5000 идей, и после опроса Twitter за 24 часа победителем является идея [Galaxy Explorer](galaxy-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="97ffd-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="97ffd-108">Энди Зибитс, ведущий сотрудник по проекту и Карим ЛукЦин, графический инженер команды, расскажу о совместной работе между искусством и проектированием, которые привели к созданию точного интерактивного представления Млечный путь Galaxy в Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="97ffd-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="97ffd-109">Технический</span><span class="sxs-lookup"><span data-stu-id="97ffd-109">The Tech</span></span>

<span data-ttu-id="97ffd-110">[Наша группа](galaxy-explorer.md#meet-the-team) состоит из двух конструкторов, трех разработчиков, четырех исполнителей, производителя и одного инженера-тестировщика, для создания полнофункционального приложения, которое позволило бы людям изучать и исследовать огромное и привлекательность нашего Млечный путьного Galaxy.</span><span class="sxs-lookup"><span data-stu-id="97ffd-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="97ffd-111">Мы хотели воспользоваться всеми преимуществами использования HoloLens для отрисовки трехмерных объектов непосредственно в своем собственном пространстве, поэтому мы решили создать реалистичный взгляд на Galaxy, где люди смогут увеличить и увидеть отдельные звезды, каждый на их собственном траекторий.</span><span class="sxs-lookup"><span data-stu-id="97ffd-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="97ffd-112">В течение первой недели разработки мы получили несколько целей для нашего представления Млечный путьного способа Galaxy: он нуждается в глубине, перемещении и объемные — заполнении звезд, которые помогут создать форму Galaxy.</span><span class="sxs-lookup"><span data-stu-id="97ffd-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="97ffd-113">Проблема с созданием анимированного Galaxy, которому были выделены миллиарды звезд, заключается в том, что количество отдельных элементов, нуждающихся в обновлении, будет слишком большим для каждого кадра, чтобы объект HoloLens мог анимировать с помощью ЦП.</span><span class="sxs-lookup"><span data-stu-id="97ffd-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="97ffd-114">Наше решение потребовало сложного сочетания искусства и науки.</span><span class="sxs-lookup"><span data-stu-id="97ffd-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="97ffd-115">Как это делается</span><span class="sxs-lookup"><span data-stu-id="97ffd-115">Behind the scenes</span></span>

<span data-ttu-id="97ffd-116">Чтобы позволить людям исследовать отдельные звезды, наш первый шаг — выяснить, сколько частиц можно было визуализировать одновременно.</span><span class="sxs-lookup"><span data-stu-id="97ffd-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="97ffd-117">Отрисовка частиц</span><span class="sxs-lookup"><span data-stu-id="97ffd-117">Rendering particles</span></span>

<span data-ttu-id="97ffd-118">Текущие ЦП отлично подходят для обработки последовательных задач и до нескольких параллельных задач одновременно (в зависимости от количества ядер), но графические процессоры гораздо более эффективны при обработке тысяч операций параллельно.</span><span class="sxs-lookup"><span data-stu-id="97ffd-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="97ffd-119">Однако, так как они обычно не используют общую память для ЦП, Обмен данными между ЦП < > GPU может быстро стать узким местом.</span><span class="sxs-lookup"><span data-stu-id="97ffd-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="97ffd-120">Наше решение состояло в том, чтобы сделать Galaxy на GPU, и он должен полностью прожить на GPU.</span><span class="sxs-lookup"><span data-stu-id="97ffd-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="97ffd-121">Мы начали стрессовые тесты с тысячами точек в различных шаблонах.</span><span class="sxs-lookup"><span data-stu-id="97ffd-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="97ffd-122">Это позволило нам получить Galaxy на HoloLens, чтобы узнать, что вы работали и чего не сделали.</span><span class="sxs-lookup"><span data-stu-id="97ffd-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="97ffd-123">Создание расположения звезд</span><span class="sxs-lookup"><span data-stu-id="97ffd-123">Creating the position of the stars</span></span>

<span data-ttu-id="97ffd-124">Один из наших участников команды уже написал C# код, который мог бы создать звезды на их начальной позиции.</span><span class="sxs-lookup"><span data-stu-id="97ffd-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="97ffd-125">Звезды располагаются на эллипсе, и их положения могут быть описаны (**курвеоффсет**, **еллипсесизе**, **повышение прав**), где **курвеоффсет** — угол звезды на эллипсе, **Еллипсесизе** — это измерение эллипса вдоль X и Z, а также повышенная высота звездочки в Galaxy.</span><span class="sxs-lookup"><span data-stu-id="97ffd-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="97ffd-126">Таким образом, можно создать буфер ([Компутебуффер Unity](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)), который будет инициализирован с каждым атрибутом звезды, и отправить его на GPU, где он будет использоваться для оставшейся работы.</span><span class="sxs-lookup"><span data-stu-id="97ffd-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="97ffd-127">Чтобы нарисовать этот буфер, мы используем [Дравпроцедурал Unity](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) , который позволяет запускать шейдер (код на GPU) в произвольном наборе точек без фактической сетки, представляющей Galaxy:</span><span class="sxs-lookup"><span data-stu-id="97ffd-127">To draw this buffer, we use [Unity’s DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="97ffd-128">**ЗАГРУЗКИ**</span><span class="sxs-lookup"><span data-stu-id="97ffd-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="97ffd-129">**СОВМЕЩЕН**</span><span class="sxs-lookup"><span data-stu-id="97ffd-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="97ffd-130">Мы начали с необработанными циклическими шаблонами с тысячами частиц.</span><span class="sxs-lookup"><span data-stu-id="97ffd-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="97ffd-131">Это позволило нам проверить, что нам нужно было бы управлять многими частицами и запускать их с помощью производительных скоростей, но мы не удовлетворены общей формой Galaxy.</span><span class="sxs-lookup"><span data-stu-id="97ffd-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="97ffd-132">Чтобы улучшить форму, мы попытались попытаться выполнить различные закономерности и системы частиц с поворотом.</span><span class="sxs-lookup"><span data-stu-id="97ffd-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="97ffd-133">Это было первоначальное расчетное обусловлено тем, что число частиц и неизменности производительности согласовывается, но фигура раскрывается в центре, а звезды выводятся в направлении, что не было реалистичным.</span><span class="sxs-lookup"><span data-stu-id="97ffd-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="97ffd-134">Мы потребовали эмиссию, которая позволила бы нам управлять временем, а частицы — реалистично передвигаться ближе к центру Galaxy.</span><span class="sxs-lookup"><span data-stu-id="97ffd-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Мы попытались поворачивать различные закономерности и системы частей, которые поворачиваются, подобно этим.](images/galaxy-patterns-500px.png)

<span data-ttu-id="97ffd-136">Мы попытались поворачивать различные закономерности и системы частей, которые поворачиваются, подобно этим.</span><span class="sxs-lookup"><span data-stu-id="97ffd-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="97ffd-137">Наша группа выполнила некоторые исследования о способе ГАЛАКСИЕС функции и предоставила пользовательскую систему частиц, специально предназначенную для Galaxy, чтобы мы могли перемещать частицы на эллипсы на основе «[теории» плотности](https://en.wikipedia.org/wiki/Density_wave_theory), которые сеоризес, что руки Galaxy являются областями с более высокой плотностью, но в постоянный Flux, как Застревание трафика.</span><span class="sxs-lookup"><span data-stu-id="97ffd-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="97ffd-138">Он выглядит стабильным и сплошным, но звезды фактически перемещаются и выходят с руки по мере их перемещения по соответствующим эллипсам.</span><span class="sxs-lookup"><span data-stu-id="97ffd-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="97ffd-139">В нашей системе частицы никогда не существовали на ЦП — мы создаем карты и расходим их всем на GPU, так что вся система – это просто начальное состояние и время.</span><span class="sxs-lookup"><span data-stu-id="97ffd-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="97ffd-140">Он выполняется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="97ffd-140">It progressed like this:</span></span>

![Ход выполнения системы частиц с отрисовкой GPU](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="97ffd-142">Ход выполнения системы частиц с отрисовкой GPU</span><span class="sxs-lookup"><span data-stu-id="97ffd-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="97ffd-143">Когда добавляются достаточное многоточия и для них устанавливается значение повернуть, ГАЛАКСИЕС начался в виде «подлокотников», где сходится движение звезд.</span><span class="sxs-lookup"><span data-stu-id="97ffd-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="97ffd-144">Для расстояния звезд на каждом эллиптическом пути было определено случайное значение, и каждая звездочка получит немного места.</span><span class="sxs-lookup"><span data-stu-id="97ffd-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="97ffd-145">Это создало гораздо более естественное распределение «перемещения звезд» и «фигура ARM».</span><span class="sxs-lookup"><span data-stu-id="97ffd-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="97ffd-146">Наконец, мы добавили возможность делать цвета на основе расстояния от центра.</span><span class="sxs-lookup"><span data-stu-id="97ffd-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="97ffd-147">Создание движения звезд</span><span class="sxs-lookup"><span data-stu-id="97ffd-147">Creating the motion of the stars</span></span>

<span data-ttu-id="97ffd-148">Чтобы анимировать общее движение звезды, нам требовалось добавить постоянный угол для каждого кадра и получить звезды, перемещающиеся вдоль эллипсов, на постоянной скорости радиального круга.</span><span class="sxs-lookup"><span data-stu-id="97ffd-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="97ffd-149">Это основная причина использования **курвеоффсет**.</span><span class="sxs-lookup"><span data-stu-id="97ffd-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="97ffd-150">Это не так хорошо, как звезды будут быстро перемещаться по длинным сторонам эллипса, но в целом это далеко не так.</span><span class="sxs-lookup"><span data-stu-id="97ffd-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![Звезды перемещаются быстрее на длинную дугу, медленнее по краям.](images/ellipse-movement.jpg)

<span data-ttu-id="97ffd-152">Звезды перемещаются быстрее на длинную дугу, медленнее по краям.</span><span class="sxs-lookup"><span data-stu-id="97ffd-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="97ffd-153">При этом каждая звезда полностью описывается (**курвеоффсет**, **еллипсесизе**, **повышение прав**, **возраст**), где **Age** — это совокупность общего времени, которое прошло с момента загрузки сцены.</span><span class="sxs-lookup"><span data-stu-id="97ffd-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

<span data-ttu-id="97ffd-154">Это позволило нам создавать десятки тысяч звезд один раз в начале приложения, а затем анимировать один набор звезд вдоль установленных кривых.</span><span class="sxs-lookup"><span data-stu-id="97ffd-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="97ffd-155">Так как все работает на GPU, система может анимировать все звезды в параллельном режиме, не изменяя ЦП.</span><span class="sxs-lookup"><span data-stu-id="97ffd-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![Вот как это выглядит при рисовании белых чисел.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="97ffd-157">Вот как это выглядит при рисовании белых чисел.</span><span class="sxs-lookup"><span data-stu-id="97ffd-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="97ffd-158">Чтобы сделать каждую двухмерную камеру, мы использовали шейдер Geometry для преобразования каждой из позиций звезды в плоский прямоугольник на экране, который будет содержать нашу текстуру звезды.</span><span class="sxs-lookup"><span data-stu-id="97ffd-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Ромбы вместо четырех.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="97ffd-160">Ромбы вместо четырех.</span><span class="sxs-lookup"><span data-stu-id="97ffd-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="97ffd-161">Так как мы хотели ограничить перерисовку (количество попыток обработки пикселя), мы поменяли наши четыре, чтобы они были менее перекрываться.</span><span class="sxs-lookup"><span data-stu-id="97ffd-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="97ffd-162">Добавление облаков</span><span class="sxs-lookup"><span data-stu-id="97ffd-162">Adding clouds</span></span>

<span data-ttu-id="97ffd-163">Существует множество способов получить объемныеное чувство с частицами — от луча марта в рамках тома до отрисовки максимально возможного количества частиц для имитации облака.</span><span class="sxs-lookup"><span data-stu-id="97ffd-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="97ffd-164">В режиме реального времени луч в марте был бы слишком дорогостоящим и трудным для создания, поэтому мы сначала попытались создать фальшивый систему с помощью метода для визуализации лесов в играх — с большим количеством двумерных изображений с деревьями, направленными на камеру.</span><span class="sxs-lookup"><span data-stu-id="97ffd-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="97ffd-165">Когда мы делаем это в игре, можно получить текстуры деревьев, отображаемых с камеры, которая поворачивает, сохранить все эти изображения и во время выполнения для каждой карточки объявления выбрать изображение, соответствующее направлению представления.</span><span class="sxs-lookup"><span data-stu-id="97ffd-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="97ffd-166">Это не подходит, если изображения являются голограммами.</span><span class="sxs-lookup"><span data-stu-id="97ffd-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="97ffd-167">Различие между левым глазом и верным глазом делает его таким образом, чтобы нам было необходимо более высокое разрешение, или же оно просто выглядит плоским, псевдонимом или повторяющимся.</span><span class="sxs-lookup"><span data-stu-id="97ffd-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="97ffd-168">При второй попытке мы попытались иметь как можно больше частиц.</span><span class="sxs-lookup"><span data-stu-id="97ffd-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="97ffd-169">Лучшие визуальные элементы были достигнуты, когда мы добавили частицы и размытые, прежде чем добавлять их в сцену.</span><span class="sxs-lookup"><span data-stu-id="97ffd-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="97ffd-170">Типичные проблемы, связанные с этим подходом, связаны с тем, сколько частиц можно было рисовать в одно время, а также о том, какая область экрана она охватывает, сохраняя 60fps.</span><span class="sxs-lookup"><span data-stu-id="97ffd-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="97ffd-171">Размытие полученного изображения для получения этого облака обычно является очень дорогостоящей операцией.</span><span class="sxs-lookup"><span data-stu-id="97ffd-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Без текстуры это будут выглядеть облака с непрозрачностью 2%.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="97ffd-173">Без текстуры это будут выглядеть облака с непрозрачностью 2%.</span><span class="sxs-lookup"><span data-stu-id="97ffd-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="97ffd-174">Аддитивное и наличие большого количества таких элементов означает, что у нас будет несколько четырех поверх друг друга, которые будут многократно закрасить один и тот же пиксель.</span><span class="sxs-lookup"><span data-stu-id="97ffd-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="97ffd-175">В центре Galaxy один и тот же пиксель имеет сотни тысяч поверх друг друга, и это имело огромное значение при заполнении во весь экран.</span><span class="sxs-lookup"><span data-stu-id="97ffd-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="97ffd-176">При выполнении полноэкранных облаков и попытке размытия они были бы плохой идеей, поэтому мы решили позволить оборудованию выполнять работу за нас.</span><span class="sxs-lookup"><span data-stu-id="97ffd-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="97ffd-177">Первый контекст</span><span class="sxs-lookup"><span data-stu-id="97ffd-177">A bit of context first</span></span>

<span data-ttu-id="97ffd-178">При использовании текстур в игре размер текстуры редко будет совпадать с областью, в которой мы хотим использовать ее, но можно использовать различные виды фильтрации текстур, чтобы получить графическую карту для интерполяции нужного цвета от пикселя текстуры ([Фильтрация текстур](https://msdn.microsoft.com/library/dn642451.aspx)).</span><span class="sxs-lookup"><span data-stu-id="97ffd-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="97ffd-179">Фильтрация, интересующая нас, — это [билинейнойная фильтрация](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) , которая вычислит значение любого пикселя с помощью четырех ближайших соседей.</span><span class="sxs-lookup"><span data-stu-id="97ffd-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Оригинал перед фильтрацией](images/texture-1.png)

![Результат после фильтрации](images/texture-2.png)

<span data-ttu-id="97ffd-182">Используя это свойство, мы видим, что каждый раз, когда мы пытаемся рисовать текстуру в области дважды, она размыта в результате.</span><span class="sxs-lookup"><span data-stu-id="97ffd-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="97ffd-183">Вместо подготовки к просмотру в полноэкранном режиме и потери ценных миллисекунд мы можем поработать с другими, выполняя визуализацию в маленькую версию экрана.</span><span class="sxs-lookup"><span data-stu-id="97ffd-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="97ffd-184">Затем, скопировав эту текстуру и растягивая ее на 2 раза несколько раз, мы вернемся к полноэкранному экрану при размытии содержимого в процессе.</span><span class="sxs-lookup"><span data-stu-id="97ffd-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![X3 воспроизводится до полного разрешения.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="97ffd-186">X3 воспроизводится до полного разрешения.</span><span class="sxs-lookup"><span data-stu-id="97ffd-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="97ffd-187">Это позволило нам получить облачную часть только с долей первоначальных затрат.</span><span class="sxs-lookup"><span data-stu-id="97ffd-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="97ffd-188">Вместо того чтобы добавлять облака при полном разрешении, мы рисуем только 1/64th пикселя и просто растяните текстуру до полного разрешения.</span><span class="sxs-lookup"><span data-stu-id="97ffd-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Left, с масштабированием от 1 до 8 до полного разрешения; и Right, с 3 возможностями масштабирования с использованием степени 2.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="97ffd-190">Left, с масштабированием от 1 до 8 до полного разрешения; и Right, с 3 возможностями масштабирования с использованием степени 2.</span><span class="sxs-lookup"><span data-stu-id="97ffd-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="97ffd-191">Обратите внимание, что попытка перейти от 1/64th размера к полному размеру в одном пути будет выглядеть совершенно иначе, так как графическая карта по-прежнему будет использовать 4 пикселя в нашей программе установки для затенения большего размера области и артефактов.</span><span class="sxs-lookup"><span data-stu-id="97ffd-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="97ffd-192">Затем, если мы добавим звезду с полным разрешением с меньшими картами, мы получаем полное Galaxy:</span><span class="sxs-lookup"><span data-stu-id="97ffd-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![Ближайший окончательный результат отрисовки Galaxy с использованием полного числа звезд](images/full-galaxy-500px.png)

<span data-ttu-id="97ffd-194">После того, как мы находились в правильном расположении с фигурой, мы добавили слой облаков, расвлеки временные точки с теми, которые были окрашены в Photoshop, и добавили дополнительный цвет.</span><span class="sxs-lookup"><span data-stu-id="97ffd-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="97ffd-195">Результат был Млечный путьным способом Galaxy наших художественных и инженерных команд, и он отвечает нашим целям, которые имеют глубину, громкость и движение — все это без массового потребления ресурсов ЦП.</span><span class="sxs-lookup"><span data-stu-id="97ffd-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![Наш окончательный Млечный путь способ Galaxy трехмерный.](images/final-galaxy-500px.jpg)

<span data-ttu-id="97ffd-197">Наш окончательный Млечный путь способ Galaxy трехмерный.</span><span class="sxs-lookup"><span data-stu-id="97ffd-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="97ffd-198">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="97ffd-198">More to explore</span></span>

<span data-ttu-id="97ffd-199">Мы открыли код для приложения Galaxy Explorer и сделали его доступным на сайте [GitHub](https://github.com/Microsoft/GalaxyExplorer) для разработки.</span><span class="sxs-lookup"><span data-stu-id="97ffd-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="97ffd-200">Хотите узнать больше о процессе разработки для Galaxy Explorer?</span><span class="sxs-lookup"><span data-stu-id="97ffd-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="97ffd-201">Ознакомьтесь со всеми прошлыми обновлениями проекта в [канале Microsoft HoloLens YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span><span class="sxs-lookup"><span data-stu-id="97ffd-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="97ffd-202">Об авторах</span><span class="sxs-lookup"><span data-stu-id="97ffd-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="97ffd-203"><b>Карим лукЦин</b> — это инженер по программному обеспечению и визуальные визуализации.</span><span class="sxs-lookup"><span data-stu-id="97ffd-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="97ffd-204">Он был инженером графики для Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="97ffd-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="97ffd-205"><b>Энди зибитс</b> является ведущим руководителем и сферой, которая управляет группой трехмерного моделирования для Galaxy Explorer и фаугхт для еще большего числа частиц.</span><span class="sxs-lookup"><span data-stu-id="97ffd-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="97ffd-206">См. также:</span><span class="sxs-lookup"><span data-stu-id="97ffd-206">See also</span></span>
* [<span data-ttu-id="97ffd-207">Обозреватель Galaxy на GitHub</span><span class="sxs-lookup"><span data-stu-id="97ffd-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="97ffd-208">Обновления проектов обозревателя Galaxy на YouTube</span><span class="sxs-lookup"><span data-stu-id="97ffd-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
