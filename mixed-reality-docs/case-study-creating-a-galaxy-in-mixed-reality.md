---
title: Практический пример — создание одной далекой в смешанной реальности
description: Перед доставкой Microsoft HoloLens, мы попросили наше сообщество разработчиков, на какие приложения они хотели бы видеть опытной группой внутреннего построения нового устройства. Более 5000 идеи были общими, и после опроса Twitter 24-часовом, победителя было идею, называется «Galaxy Explorer».
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, Windows Mixed Reality, поделиться идеей, пример внедрения
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604833"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="b5c73-105">Практический пример — создание одной далекой в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="b5c73-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="b5c73-106">Перед доставкой Microsoft HoloLens, мы попросили наше сообщество разработчиков, на какие приложения они хотели бы видеть опытной группой внутреннего построения нового устройства.</span><span class="sxs-lookup"><span data-stu-id="b5c73-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="b5c73-107">Более 5000 идеи были общими, и после опроса Twitter 24-часовом, победителя было идею вызывается [Galaxy Explorer](galaxy-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="b5c73-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="b5c73-108">Энди Zibits, art интереса к проекту и Karim Luccin, инженер по вопросам графики команды, поговорим о совместной работе между картинок и инженеров приводило к созданию точных и интерактивные представления galaxy Млечного в обозревателе Galaxy.</span><span class="sxs-lookup"><span data-stu-id="b5c73-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="b5c73-109">Технический</span><span class="sxs-lookup"><span data-stu-id="b5c73-109">The Tech</span></span>

<span data-ttu-id="b5c73-110">[Наша группа](galaxy-explorer.md#meet-the-team) - делать копии двумя конструкторами, три разработчика, четыре исполнители, производитель и одного тестер — бы шесть недель для создания полностью функциональное приложение, которое позволит пользователям получать дополнительные сведения о vastness и прелесть нашей галактики Млечного.</span><span class="sxs-lookup"><span data-stu-id="b5c73-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="b5c73-111">Мы хотели воспользоваться всеми преимуществами возможность отобразить трехмерные объекты непосредственно в своей сфере жизни, поэтому мы решили, что необходимо для создания реалистичного выглядящие галактики где люди смогут увеличить масштаб close и увидеть отдельные звезд, каждый на собственные траекторий HoloLens .</span><span class="sxs-lookup"><span data-stu-id="b5c73-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="b5c73-112">В первую неделю разработки мы выпустили несколько целей для наших представление космоса Млечного: Ей нужно иметь глубину, перемещения и вид объемные — full звезд, которые помогают создать форму космоса.</span><span class="sxs-lookup"><span data-stu-id="b5c73-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="b5c73-113">При создании анимированных галактики, оказывали миллиардов звезд проблема, что большое число отдельных элементов, которые необходимо обновить будет слишком большой размер каждого кадра для HoloLens для анимации с использованием ЦП.</span><span class="sxs-lookup"><span data-stu-id="b5c73-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="b5c73-114">Наше решение участвует сложных сочетание искусством.</span><span class="sxs-lookup"><span data-stu-id="b5c73-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="b5c73-115">Как это делается</span><span class="sxs-lookup"><span data-stu-id="b5c73-115">Behind the scenes</span></span>

<span data-ttu-id="b5c73-116">Чтобы разрешить пользователям просматривать отдельные звезд, что нашим первым этапом было выяснить, сколько примитивы, просмотром мог за один раз.</span><span class="sxs-lookup"><span data-stu-id="b5c73-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="b5c73-117">Подготовка к просмотру примитивы</span><span class="sxs-lookup"><span data-stu-id="b5c73-117">Rendering particles</span></span>

<span data-ttu-id="b5c73-118">Текущий ЦП удобны для обработки последовательные задачи и до нескольких параллельных задач за один раз (в зависимости от того, сколько ядер у), но графических процессоров намного больше подходит для обработки тысяч операций параллельного.</span><span class="sxs-lookup"><span data-stu-id="b5c73-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="b5c73-119">Тем не менее так как обычно они не используют ту же память, как ЦП, обмена данными между ЦП <> GPU может быстро стать узким местом.</span><span class="sxs-lookup"><span data-stu-id="b5c73-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="b5c73-120">Наше решение должно было осуществлять галактики на GPU, и его пришлось полностью live в GPU.</span><span class="sxs-lookup"><span data-stu-id="b5c73-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="b5c73-121">Мы начали нагрузочные тесты с тысячами частиц точки в различных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="b5c73-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="b5c73-122">Это позволило нам получить космоса на HoloLens, чтобы увидеть, что выполнено, а что нет.</span><span class="sxs-lookup"><span data-stu-id="b5c73-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="b5c73-123">Создание положение звезды</span><span class="sxs-lookup"><span data-stu-id="b5c73-123">Creating the position of the stars</span></span>

<span data-ttu-id="b5c73-124">Один из наших участников команды уже создала C# код, который создал бы звезды в их начальное положение.</span><span class="sxs-lookup"><span data-stu-id="b5c73-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="b5c73-125">Звезды находятся на эллипс и их положения могут быть описаны свойством (**curveOffset**, **ellipseSize**, **повышение прав**) где **curveOffset**— это угол звезды вдоль эллипса, **ellipseSize** — это измерение эллипса вдоль X и Z и повышение правильное высоту данного типа "звезда" в пределах космоса.</span><span class="sxs-lookup"><span data-stu-id="b5c73-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="b5c73-126">Таким образом, мы можем создать буфер ([Unity ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)), может инициализироваться значением каждый атрибут типа "звезда" и отправить его в GPU, где бы live для остальной части интерфейса.</span><span class="sxs-lookup"><span data-stu-id="b5c73-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="b5c73-127">Чтобы нарисовать этот буфер, мы используем [Unity DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) разрешающее под управлением шейдера (кода на GPU) на произвольный набор точек без необходимости фактическое сетки, который представляет космоса:</span><span class="sxs-lookup"><span data-stu-id="b5c73-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="b5c73-128">**ЦП:**</span><span class="sxs-lookup"><span data-stu-id="b5c73-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="b5c73-129">**GPU:**</span><span class="sxs-lookup"><span data-stu-id="b5c73-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="b5c73-130">Мы начали с необработанных циклическая шаблоны с тысячами примитивы.</span><span class="sxs-lookup"><span data-stu-id="b5c73-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="b5c73-131">Это давало доказательства, что нам нужно, мы может управлять многих частицы и запустите его со скоростью высокой производительностью, что мы не были удовлетворительными в общей форме космоса.</span><span class="sxs-lookup"><span data-stu-id="b5c73-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="b5c73-132">Чтобы улучшить фигуры, попытка различные шаблоны и системы частиц с поворотом.</span><span class="sxs-lookup"><span data-stu-id="b5c73-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="b5c73-133">Это были перспективных, так как число эффектов и производительности лет обеспечивает согласованность, но фигуры разбил рядом с центром и звезды были выпуска внешне чего нельзя было реалистичные.</span><span class="sxs-lookup"><span data-stu-id="b5c73-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="b5c73-134">Нам требовалось вывод, что позволило бы нам управлять времени и переместить в действительности частицы циклов когда-нибудь ближе к центру космоса.</span><span class="sxs-lookup"><span data-stu-id="b5c73-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Предпринята различные шаблоны и системы частиц, которые вращать, подобные этим.](images/galaxy-patterns-500px.png)

<span data-ttu-id="b5c73-136">Предпринята различные шаблоны и системы частиц, которые вращать, подобные этим.</span><span class="sxs-lookup"><span data-stu-id="b5c73-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="b5c73-137">Наша команда была исследование, о функции галактики способом, и мы внесли системе частиц пользовательских специально для galaxy таким образом, нам удалось переместить частицы на кнопку с многоточием на основе "[теории wave плотность](https://en.wikipedia.org/wiki/Density_wave_theory),» которого theorizes, вооружений из galaxy описаны области, более высокой плотности, но постоянным корректировкам, например передряги трафика.</span><span class="sxs-lookup"><span data-stu-id="b5c73-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="b5c73-138">Похоже, стабильной и сплошной, но звездочек действительно движутся входящий и исходящий руки при переходе по их соответствующих многоточие.</span><span class="sxs-lookup"><span data-stu-id="b5c73-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="b5c73-139">В нашей системе частицы никогда не существует на ЦП — мы создания карточек и расположить их на GPU, поэтому вся система является просто начальное состояние + время.</span><span class="sxs-lookup"><span data-stu-id="b5c73-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="b5c73-140">Она выполнялась следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b5c73-140">It progressed like this:</span></span>

![Эволюция система частиц с помощью графического процессора](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="b5c73-142">Эволюция система частиц с помощью графического процессора</span><span class="sxs-lookup"><span data-stu-id="b5c73-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="b5c73-143">После достаточно многоточие добавляются и устанавливаются для поворота, галактики приступила к форме «оружию», где сходятся перемещение звезды.</span><span class="sxs-lookup"><span data-stu-id="b5c73-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="b5c73-144">Интервал звездочек вдоль каждого контуру передан часть случайности, и каждого типа "звезда" получил немного позиционные случайности добавлен.</span><span class="sxs-lookup"><span data-stu-id="b5c73-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="b5c73-145">Она создана гораздо более естественной выглядящие распределение звезда перемещения и arm.</span><span class="sxs-lookup"><span data-stu-id="b5c73-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="b5c73-146">И, наконец мы добавили возможность диска цветов в зависимости от расстояния от центра.</span><span class="sxs-lookup"><span data-stu-id="b5c73-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="b5c73-147">Создание движения звезд</span><span class="sxs-lookup"><span data-stu-id="b5c73-147">Creating the motion of the stars</span></span>

<span data-ttu-id="b5c73-148">Для анимации общие движение типа "звезда", необходимо добавить постоянное угол для каждого кадра и получить звезд, перемещающиеся их эллипсы с постоянной скоростью Радиальный.</span><span class="sxs-lookup"><span data-stu-id="b5c73-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="b5c73-149">Это основная причина использования **curveOffset**.</span><span class="sxs-lookup"><span data-stu-id="b5c73-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="b5c73-150">Это неверно с технической точки зрения как звезды будет двигаться быстрее на длинный сторонах кнопку с многоточием, но общие движение посчитали хорошо.</span><span class="sxs-lookup"><span data-stu-id="b5c73-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![Звезды быстродействие на длинный дуги, медленнее по краям.](images/ellipse-movement.jpg)

<span data-ttu-id="b5c73-152">Звезды быстродействие на длинный дуги, медленнее по краям.</span><span class="sxs-lookup"><span data-stu-id="b5c73-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="b5c73-153">Таким образом, каждого типа "звезда" полностью описывается (**curveOffset**, **ellipseSize**, **повышение прав**, **возраст**) где **возраст** представляет собой совокупность объектов общее время, истекшее с момента загрузки сцены.</span><span class="sxs-lookup"><span data-stu-id="b5c73-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




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

<span data-ttu-id="b5c73-154">Это позволило нам для создания десятков тысяч звезд один раз при запуске приложения, а затем мы анимированы одним набор звезд вдоль изгибов установленным.</span><span class="sxs-lookup"><span data-stu-id="b5c73-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="b5c73-155">Поскольку все, что в GPU, система можно анимировать все звезды в параллельном режиме без затрат на ЦП.</span><span class="sxs-lookup"><span data-stu-id="b5c73-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![Вот, как он выглядит когда рисование белого четырехугольники.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="b5c73-157">Вот, как он выглядит когда рисование белого четырехугольники.</span><span class="sxs-lookup"><span data-stu-id="b5c73-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="b5c73-158">Чтобы сделать каждой грани четырьмя камеры, мы использовали шейдер геометрии для преобразования каждого типа "звезда" положение двумерной прямоугольник на экране, который будет содержать наших типа "звезда" текстуры.</span><span class="sxs-lookup"><span data-stu-id="b5c73-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Ромбы вместо четырехугольники.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="b5c73-160">Ромбы вместо четырехугольники.</span><span class="sxs-lookup"><span data-stu-id="b5c73-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="b5c73-161">Так как мы хотели бы ограничить перекрытий (количество раз, будут обрабатываться пиксель) настолько, насколько возможно, мы (повернутый) нашей четырехугольники таким образом, чтобы они бы меньше перекрытие.</span><span class="sxs-lookup"><span data-stu-id="b5c73-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="b5c73-162">Добавление облака</span><span class="sxs-lookup"><span data-stu-id="b5c73-162">Adding clouds</span></span>

<span data-ttu-id="b5c73-163">Существует много способов, чтобы почувствовать объемные частицами — из Рэй marching внутри тома для рисования столько частицы можно имитировать в облаке.</span><span class="sxs-lookup"><span data-stu-id="b5c73-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="b5c73-164">В режиме реального времени Рэй marching будет не слишком дорого стоят их трудно автора, поэтому мы впервые опробовал создании фальшивый системы с помощью метода для лесов отрисовки в играх — с большим количеством двумерные изображения деревьев, с которыми сталкиваются камеры.</span><span class="sxs-lookup"><span data-stu-id="b5c73-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="b5c73-165">При этом в игре, мы имеют текстуры деревьев, подготовке к просмотру с камеры, который вращается вокруг, сохранять эти изображения и во время выполнения для каждой карточки элемент с объявлением, выберите образ, который соответствует направление представления.</span><span class="sxs-lookup"><span data-stu-id="b5c73-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="b5c73-166">Это не работает также с голограммы используются образы.</span><span class="sxs-lookup"><span data-stu-id="b5c73-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="b5c73-167">Разница между глаза левой и правой глаза сделать так, что мы должны более высокое разрешение, в противном случае она просто выглядит плоской, псевдонимы, или повторяющихся.</span><span class="sxs-lookup"><span data-stu-id="b5c73-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="b5c73-168">Наши второй попытки мы пробовали, наличие столько частицы максимально.</span><span class="sxs-lookup"><span data-stu-id="b5c73-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="b5c73-169">Лучшие визуальные элементы движущееся изображение достигалось при аддитивно нарисованную частицы и размыть их перед их добавлением в сцене.</span><span class="sxs-lookup"><span data-stu-id="b5c73-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="b5c73-170">Типичных проблем, возникающих при таком подходе были связаны с сколько примитивы, мы изобразить за один раз и какой объем области, они рассматриваются, сохраняя при этом 60 кадров/с экрана.</span><span class="sxs-lookup"><span data-stu-id="b5c73-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="b5c73-171">Размытие полученный образ для получения этого облака испытываешь, как правило, было очень дорогостоящей операцией.</span><span class="sxs-lookup"><span data-stu-id="b5c73-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Без текстуры это, как будет выглядеть облака с прозрачностью 2%.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="b5c73-173">Без текстуры это, как будет выглядеть облака с прозрачностью 2%.</span><span class="sxs-lookup"><span data-stu-id="b5c73-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="b5c73-174">Добавочные и необходимости много означает, что бы нам несколько четырехугольники друг над другом, многократно заливки та же точка.</span><span class="sxs-lookup"><span data-stu-id="b5c73-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="b5c73-175">В центре космоса та же точка имеет сотни четырехугольники друг над другом, и это имело место огромные затраты при, выполняемая во весь экран.</span><span class="sxs-lookup"><span data-stu-id="b5c73-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="b5c73-176">Выполнив облаков во весь экран и попытке размытия их было бы это плохая идея, поэтому вместо этого мы решили позволяют сделать работу за нас оборудования.</span><span class="sxs-lookup"><span data-stu-id="b5c73-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="b5c73-177">Бит объект контекста, сначала</span><span class="sxs-lookup"><span data-stu-id="b5c73-177">A bit of context first</span></span>

<span data-ttu-id="b5c73-178">При использовании текстуры в игре размера текстуры редко будет соответствовать мы будем использовать его в область, но можно использовать различные виды текстуры, фильтрацию, чтобы получить видеокарта для интерполяции цветов, мы хотим из пикселей текстуры ([Фильтрациятекстур<C3/настроек).](https://msdn.microsoft.com/library/dn642451.aspx)</span><span class="sxs-lookup"><span data-stu-id="b5c73-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="b5c73-179">Фильтрация интересующей нас [билинейная фильтрация](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) которого будет вычислять значение любой точки, используя 4 ближайших.</span><span class="sxs-lookup"><span data-stu-id="b5c73-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Оригинал, прежде чем применять фильтрацию](images/texture-1.png)

![Результат после фильтрации](images/texture-2.png)

<span data-ttu-id="b5c73-182">С помощью этого свойства, мы видим, что каждый раз, когда мы пытаемся нарисуйте текстуру в области дважды в качестве большое, оно размывает результат.</span><span class="sxs-lookup"><span data-stu-id="b5c73-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="b5c73-183">Вместо передачи в полноэкранный режим и потери эти ценные миллисекунд, мы может уйти на что-то еще, мы визуализируем tiny версии экрана.</span><span class="sxs-lookup"><span data-stu-id="b5c73-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="b5c73-184">Затем путем копирования этой текстуры и растягивания его с коэффициентом 2 несколько раз, мы получаем в полноэкранный режим во время Размытие содержимого в процессе.</span><span class="sxs-lookup"><span data-stu-id="b5c73-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![X3 увеличить обратно в полном разрешении.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="b5c73-186">X3 увеличить обратно в полном разрешении.</span><span class="sxs-lookup"><span data-stu-id="b5c73-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="b5c73-187">Это позволило нам получить часть облака с только небольшую часть исходной стоимости.</span><span class="sxs-lookup"><span data-stu-id="b5c73-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="b5c73-188">Вместо добавления облаков на полным разрешением, мы только paint 1/был кратен 64 пикселов и просто растянуть текстуры обратно в полном разрешении.</span><span class="sxs-lookup"><span data-stu-id="b5c73-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Слева с upscale от 1/8 к полным разрешением; и, с 3 увеличить с помощью степенью числа 2.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="b5c73-190">Слева с upscale от 1/8 к полным разрешением; и, с 3 увеличить с помощью степенью числа 2.</span><span class="sxs-lookup"><span data-stu-id="b5c73-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="b5c73-191">Обратите внимание, что пытается перейти от 1/был кратен 64 размера для полный размер за одно действие будет полностью меняет внешний вид, как графическая плата по-прежнему использовать менее 4 пикселей в нашей программе установки для затенения больше области и артефакты начать отображение.</span><span class="sxs-lookup"><span data-stu-id="b5c73-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="b5c73-192">Затем Если добавить полным разрешением звезд с уменьшить размер карточек, мы получаем полный galaxy:</span><span class="sxs-lookup"><span data-stu-id="b5c73-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![Рядом с окончательный результат galaxy рендеринге полным разрешением звезд](images/full-galaxy-500px.png)

<span data-ttu-id="b5c73-194">Как только мы находились на правильном пути с фигурой, мы добавили слой облаков, будут выгружены временных точек на другие мы рисования в Photoshop и добавлены некоторые дополнительные цвета.</span><span class="sxs-lookup"><span data-stu-id="b5c73-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="b5c73-195">Это приводило к галактики Млечного наших картинок и инженеры обоих посчитали хороший о и оно соответствовало наших целей и получать глубины, тома и движения — все это без налог ЦП.</span><span class="sxs-lookup"><span data-stu-id="b5c73-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![Наши окончательный Galaxy Млечного в трехмерном пространстве.](images/final-galaxy-500px.jpg)

<span data-ttu-id="b5c73-197">Наши окончательный Galaxy Млечного в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="b5c73-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="b5c73-198">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="b5c73-198">More to explore</span></span>

<span data-ttu-id="b5c73-199">Мы с открытым код приложения Galaxy обозревателя и делает ее доступной на [GitHub](https://github.com/Microsoft/GalaxyExplorer) для разработчикам.</span><span class="sxs-lookup"><span data-stu-id="b5c73-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="b5c73-200">Хотите узнать подробнее о процессе разработки для Galaxy Explorer?</span><span class="sxs-lookup"><span data-stu-id="b5c73-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="b5c73-201">Извлечь все наши последние обновления проекта на [канал YouTube Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span><span class="sxs-lookup"><span data-stu-id="b5c73-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="b5c73-202">Об авторах</span><span class="sxs-lookup"><span data-stu-id="b5c73-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="b5c73-203"><b>Karim Luccin</b> — разработчик программного обеспечения и энтузиаст необычные визуальные элементы.</span><span class="sxs-lookup"><span data-stu-id="b5c73-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="b5c73-204">Он был инженером графики для Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="b5c73-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="b5c73-205"><b>Энди Zibits</b> является энтузиаст интереса картинок и места, в который управляемых team трехмерного моделирования для Galaxy Explorer и мучились для частицы еще больше.</span><span class="sxs-lookup"><span data-stu-id="b5c73-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="b5c73-206">См. также</span><span class="sxs-lookup"><span data-stu-id="b5c73-206">See also</span></span>
* [<span data-ttu-id="b5c73-207">Galaxy Explorer на сайте GitHub</span><span class="sxs-lookup"><span data-stu-id="b5c73-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="b5c73-208">Galaxy Explorer проект обновления на сайте YouTube</span><span class="sxs-lookup"><span data-stu-id="b5c73-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
