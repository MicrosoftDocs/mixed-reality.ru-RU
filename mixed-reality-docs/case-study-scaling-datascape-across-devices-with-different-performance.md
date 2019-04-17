---
title: 'Учебный пример: масштабирование Datascape на устройствах, которые имеют различный уровень производительности'
description: В этом практическом представлены подробные сведения о как разработчики Microsoft оптимизировать приложение Datascape для разработки удобную среду для устройств с помощью широкий набор возможностей производительности.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: насыщенные гарнитуры, пример виртуальной Реальности, для оптимизации производительности
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604873"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="69e07-104">Учебный пример: масштабирование Datascape на устройствах, которые имеют различный уровень производительности</span><span class="sxs-lookup"><span data-stu-id="69e07-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="69e07-105">Datascape представляет собой приложение Windows Mixed Reality, внутренней разработки в корпорации Майкрософт где мы ознакомились с отображением данных о погоде на основе данных ландшафта.</span><span class="sxs-lookup"><span data-stu-id="69e07-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="69e07-106">Приложение описывается уникальных ценных сведений, которые пользователи получают из обнаружение данных в смешанной реальности, заключив пользователя с помощью визуализации данных holographic.</span><span class="sxs-lookup"><span data-stu-id="69e07-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="69e07-107">Для Datascape мы хотели предназначены для различных платформ с различных аппаратных возможностей, начиная от Microsoft HoloLens в Windows Mixed Reality иммерсивную и от малой ПК до самой последней ПК с высоким быстродействием GPU.</span><span class="sxs-lookup"><span data-stu-id="69e07-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="69e07-108">Основная проблема была Подготовка к просмотру наших сцены в визуально привлекательные вопрос на устройствах с совершенно другое графические возможности во время выполнения при высокой частоте кадров.</span><span class="sxs-lookup"><span data-stu-id="69e07-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="69e07-109">В этом практическом проведет через процесс и методики, используемые для создания, некоторые из наших дополнительные систем интенсивно использующих графический Процессор с описанием проблемы, с которыми мы столкнулись, и как мы позволяют обойти их.</span><span class="sxs-lookup"><span data-stu-id="69e07-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="69e07-110">Прозрачность и может быть нарисован поверх</span><span class="sxs-lookup"><span data-stu-id="69e07-110">Transparency and overdraw</span></span>

<span data-ttu-id="69e07-111">Наши основные отрисовки трудностей обработаны прозрачности, поскольку прозрачности, могут потреблять на графическом Процессоре.</span><span class="sxs-lookup"><span data-stu-id="69e07-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="69e07-112">Сплошная линия геометрического объекта может визуализироваться сверху вниз при записи в буфер глубины, остановка любой будущих пикселей, расположенных за точки из уничтожается.</span><span class="sxs-lookup"><span data-stu-id="69e07-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="69e07-113">Это предотвращает выполнение построителя текстуры, значительно ускоряет процесс скрытые пикселей.</span><span class="sxs-lookup"><span data-stu-id="69e07-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="69e07-114">Если geometry оптимально отсортировано, каждый пиксель на экране будет отображен только один раз.</span><span class="sxs-lookup"><span data-stu-id="69e07-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="69e07-115">Прозрачный geometry сортироваться обратно на передний план и зависит от того, наложения выходные данные шейдера пикселей для текущего пикселя на экране.</span><span class="sxs-lookup"><span data-stu-id="69e07-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="69e07-116">Это может привести каждого пикселя на экране, отрисовывается в несколько раз на кадр, называются перерисовывать.</span><span class="sxs-lookup"><span data-stu-id="69e07-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="69e07-117">Для HoloLens и массовым ПК, экрана может быть заполнен только небольшое число раз, прозрачность, Подготовка к просмотру проблематичным.</span><span class="sxs-lookup"><span data-stu-id="69e07-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="69e07-118">Введение в компоненты Datascape сцены</span><span class="sxs-lookup"><span data-stu-id="69e07-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="69e07-119">Нам необходимо было три основных компонента наших сцены; **пользовательского интерфейса, карты**, и **погоды**.</span><span class="sxs-lookup"><span data-stu-id="69e07-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="69e07-120">На раннем этапе мы знали, что наши эффекты погоды потребует время GPU, он может получить, поэтому мы разработали специально пользовательского интерфейса и ландшафта, способом, который сведет любой перекрытий.</span><span class="sxs-lookup"><span data-stu-id="69e07-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="69e07-121">Мы переработали пользовательский Интерфейс несколько раз свести к минимуму объем перерисовывать он создается.</span><span class="sxs-lookup"><span data-stu-id="69e07-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="69e07-122">Мы сделали ошибку боковой части более сложной геометрии, а не прозрачного art наложение друг над другом для компонентов, таких как свечение обзоры кнопки и карты.</span><span class="sxs-lookup"><span data-stu-id="69e07-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="69e07-123">Карты мы использовали пользовательский шейдер, который бы убрать стандартные возможности Unity, такие как сложные освещения и появлении теней их замены с моделью освещения простой единый sun и вычисление пользовательских туман.</span><span class="sxs-lookup"><span data-stu-id="69e07-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="69e07-124">Это созданный простой построитель текстуры и освободите циклов GPU.</span><span class="sxs-lookup"><span data-stu-id="69e07-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="69e07-125">Нам удалось получить пользовательский Интерфейс и карту для подготовки к просмотру в бюджет где нам не нужно любые изменения их в зависимости от оборудования; Тем не менее погоды визуализации, в частности облачная отрисовка, оказалось действительно сложная!</span><span class="sxs-lookup"><span data-stu-id="69e07-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="69e07-126">Сведения о данных в облаке</span><span class="sxs-lookup"><span data-stu-id="69e07-126">Background on cloud data</span></span>

<span data-ttu-id="69e07-127">Наших облачных данных был загружен с серверов NOAA (http://nomads.ncep.noaa.gov/) и перешла к нам в три различных 2D слоев, каждый из которых высоту верхней и нижней частях облака, а также плотность облака для каждой ячейки сетки.</span><span class="sxs-lookup"><span data-stu-id="69e07-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="69e07-128">В текстуры info cloud хранения каждого компонента в компоненте красного, зеленого и синего текстуры для быстрого доступа в GPU, получили обрабатывать данные.</span><span class="sxs-lookup"><span data-stu-id="69e07-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="69e07-129">Geometry облака</span><span class="sxs-lookup"><span data-stu-id="69e07-129">Geometry clouds</span></span>

<span data-ttu-id="69e07-130">Чтобы убедиться в том, что наши компьютеры малой могут сделать наши облака, которые мы решили начать с перерисовывать подход, который лучше использовать сплошной свести к минимуму.</span><span class="sxs-lookup"><span data-stu-id="69e07-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="69e07-131">Во-первых, мы попытались создания облаков, создавая карты высоты сплошная сетки для каждого слоя, создание фигуры с помощью radius текстуры info cloud на вершину.</span><span class="sxs-lookup"><span data-stu-id="69e07-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="69e07-132">Шейдер геометрии мы использовали для создания вершины в верхней и нижней частью облака, создание сплошной cloud фигур.</span><span class="sxs-lookup"><span data-stu-id="69e07-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="69e07-133">Мы использовали значение плотности из текстуры для цвета в облако с более темные цвета для более плотных облаков.</span><span class="sxs-lookup"><span data-stu-id="69e07-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="69e07-134">**Шейдер по созданию вершин:**</span><span class="sxs-lookup"><span data-stu-id="69e07-134">**Shader for creating the vertices:**</span></span>

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

<span data-ttu-id="69e07-135">Мы представили небольшой шум, чтобы получить более подробные сведения на основе реальных данных.</span><span class="sxs-lookup"><span data-stu-id="69e07-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="69e07-136">Для создания краев round облака, мы обрезается пиксели в шейдер пикселей, помеченным radius интерполированное значение пороговое значение, чтобы отменить практически без значений.</span><span class="sxs-lookup"><span data-stu-id="69e07-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Geometry облака](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="69e07-138">Так как облака geometry сплошная линия, они могут быть представлены перед ландшафта, чтобы скрыть точки дорогостоящие карты под для дальнейшего повышения частоты кадров.</span><span class="sxs-lookup"><span data-stu-id="69e07-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="69e07-139">Это решение выполнялись на всех графических плат из спецификации min видеокарт, а также на HoloLens, из-за подход отрисовки geometry сплошная линия.</span><span class="sxs-lookup"><span data-stu-id="69e07-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="69e07-140">Сплошной частиц облака</span><span class="sxs-lookup"><span data-stu-id="69e07-140">Solid particle clouds</span></span>

<span data-ttu-id="69e07-141">Теперь у нас было резервного копирования, который неплохую представлением наших облачных данных, но был немного lackluster фактора «Да» и был передает объемные считают, что нам требовалось для наших высокопроизводительных машинах.</span><span class="sxs-lookup"><span data-stu-id="69e07-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="69e07-142">Следующим этапом создании облака, представляя их с 100 000 примитивы, для создания более естественному и объемные вид.</span><span class="sxs-lookup"><span data-stu-id="69e07-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="69e07-143">Сортировать от передних к задним частицы оставаться сплошной, мы может принести пользу глубина буфера, визуализируемых пикселей за ранее готовый для просмотра частицы уменьшение перекрытий.</span><span class="sxs-lookup"><span data-stu-id="69e07-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="69e07-144">Кроме того с помощью решения на основе частиц, мы можем изменить объем примитивы, используемые на другое оборудование целевого.</span><span class="sxs-lookup"><span data-stu-id="69e07-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="69e07-145">Тем не менее все пиксели по-прежнему должны быть протестированы глубины, что приведет к появлению некоторыми дополнительными издержками.</span><span class="sxs-lookup"><span data-stu-id="69e07-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="69e07-146">Во-первых мы создали частиц позиций относительно центральной точки работы во время запуска.</span><span class="sxs-lookup"><span data-stu-id="69e07-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="69e07-147">Мы распределенных частицы более плотно вокруг центра и менее сложным в расстояние.</span><span class="sxs-lookup"><span data-stu-id="69e07-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="69e07-148">Таким образом, чтобы сначала визуализируются ближайший частицы мы предварительно отсортированы все примитивы в центре на задний план.</span><span class="sxs-lookup"><span data-stu-id="69e07-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="69e07-149">Вычислительного шейдера бы образец текстуры info облако для размещения каждой частиц в правильный высоту и цвет, который оно зависит от плотности.</span><span class="sxs-lookup"><span data-stu-id="69e07-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="69e07-150">Мы использовали *DrawProcedural* для подготовки к просмотру квадрант на примитив, позволяя частиц данные оставались на GPU, все время.</span><span class="sxs-lookup"><span data-stu-id="69e07-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="69e07-151">Каждую частицу содержится высоту и radius.</span><span class="sxs-lookup"><span data-stu-id="69e07-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="69e07-152">Высота был основан на облачные данные, взятых из текстуры info облака и радиус был основан на первоначального распространения, где он будет вычисляться для хранения расстояние по горизонтали для ближайшего соседа.</span><span class="sxs-lookup"><span data-stu-id="69e07-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="69e07-153">Четырехугольники будет использовать эти данные, чтобы сориентировать себя под углом по высоте, когда пользователи рассматривать по горизонтали, появлялась высота, и когда пользователи рассмотрели его сверху вниз, будет рассматриваться область между своим соседям.</span><span class="sxs-lookup"><span data-stu-id="69e07-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![Примитив фигуры](images/particle-shape-700px.png)

<span data-ttu-id="69e07-155">**Код шейдера, показывающий распределение:**</span><span class="sxs-lookup"><span data-stu-id="69e07-155">**Shader code showing the distribution:**</span></span>

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

<span data-ttu-id="69e07-156">Так как мы сортировки частицы начала к концу, и мы по-прежнему использовать сплошной стиль шейдера пикселей прозрачный клипов (не blend), этот метод обрабатывает возрасти примитивы, как избежать дорогостоящей чрезмерное draw даже на компьютерах, маломощное.</span><span class="sxs-lookup"><span data-stu-id="69e07-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="69e07-157">Прозрачный частиц облака</span><span class="sxs-lookup"><span data-stu-id="69e07-157">Transparent particle clouds</span></span>

<span data-ttu-id="69e07-158">Сплошной частицы приведен органических понимание к фигуре облаков, но по-прежнему требуется что-то продать fluffiness облаков.</span><span class="sxs-lookup"><span data-stu-id="69e07-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="69e07-159">Мы решили попробовать пользовательское решение для видеокарт, где мы можем быстрее выводить прозрачности.</span><span class="sxs-lookup"><span data-stu-id="69e07-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="69e07-160">Для этого мы просто переключить исходный порядок сортировки частицы и изменить шейдер, который нужно использовать альфа-канал текстуры.</span><span class="sxs-lookup"><span data-stu-id="69e07-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Компания облака](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="69e07-162">Он отлично выглядели но оказался слишком большими для даже самые сложные компьютеров, так как это приведет к визуализации каждого пикселя на экране сотни раз!</span><span class="sxs-lookup"><span data-stu-id="69e07-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="69e07-163">Визуализации вне экрана с низким разрешением</span><span class="sxs-lookup"><span data-stu-id="69e07-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="69e07-164">Чтобы уменьшить количество пикселей, преобразовываемый для облака, мы начали, обработав их в буфере квартала разрешения (по сравнению с экрана) и растяжение в результате резервного копирования на экран после рисования всех частей.</span><span class="sxs-lookup"><span data-stu-id="69e07-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="69e07-165">Это дает примерно 4 x ускорение, но прилагается несколько предостережений.</span><span class="sxs-lookup"><span data-stu-id="69e07-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="69e07-166">**Код для подготовки к просмотру вне экрана:**</span><span class="sxs-lookup"><span data-stu-id="69e07-166">**Code for rendering off-screen:**</span></span>

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

<span data-ttu-id="69e07-167">Во-первых при подготовке к просмотру в во буфере вне экрана, вдруг всех сведениях из наших основных сцены, в результате чего частицы за горы подготовки к просмотру на основе mountain.</span><span class="sxs-lookup"><span data-stu-id="69e07-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="69e07-168">Во-вторых также растягивания буфера появился артефактов на краях наших облаков, где был заметно изменяет разрешение.</span><span class="sxs-lookup"><span data-stu-id="69e07-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="69e07-169">Следующих двух разделах поговорим о том, как мы устранения этих проблем.</span><span class="sxs-lookup"><span data-stu-id="69e07-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="69e07-170">Буфер глубины частиц</span><span class="sxs-lookup"><span data-stu-id="69e07-170">Particle depth buffer</span></span>

<span data-ttu-id="69e07-171">Чтобы сделать частицы совместно работать с трехмерной геометрии, где mountain или объект стоит осветить частицы за ней, заполненное буфере вне экрана с буфер глубины, содержащий геометрии сцены основной.</span><span class="sxs-lookup"><span data-stu-id="69e07-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="69e07-172">Для создания такого буфера глубины, мы создали второй камеры, Подготовка к просмотру только сплошная геометрии и глубина сцены.</span><span class="sxs-lookup"><span data-stu-id="69e07-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="69e07-173">Затем мы использовали создать текстуру в шейдер пикселей облаков для скрывать пикселей.</span><span class="sxs-lookup"><span data-stu-id="69e07-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="69e07-174">Мы использовали той же текстуры для вычисления расстояния к данной геометрии за точки облака.</span><span class="sxs-lookup"><span data-stu-id="69e07-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="69e07-175">Используя расстояние между ними и применять его в качестве альфа пикселя, у нас теперь было эффект облаков исчезновение, как можно ближе к ландшафта, удаление любого жесткого порезов, когда удовлетворяют примитивов и ландшафта.</span><span class="sxs-lookup"><span data-stu-id="69e07-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![Смешением в ландшафта облака](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="69e07-177">Увеличение резкости краев</span><span class="sxs-lookup"><span data-stu-id="69e07-177">Sharpening the edges</span></span>

<span data-ttu-id="69e07-178">Облака растягивается вверх выглядело почти идентичен нормального размера облака в центре частицы или там, где они overlapped, но показал некоторые артефакты на краях облака.</span><span class="sxs-lookup"><span data-stu-id="69e07-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="69e07-179">В противном случае четкие границы выглядит нечетким и эффекты псевдоним были введены при перемещении камеры.</span><span class="sxs-lookup"><span data-stu-id="69e07-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="69e07-180">Мы решили эту проблему, выполнив простой шейдер в буфере вне экрана, чтобы определить, где много важных изменений в отличие от этого (1).</span><span class="sxs-lookup"><span data-stu-id="69e07-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="69e07-181">Мы опубликовали пиксели с большими изменениями в новый буфер шаблона (2).</span><span class="sxs-lookup"><span data-stu-id="69e07-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="69e07-182">Затем мы использовали буфер шаблона маске этих областей Высокая контрастность при применении буфере вне экрана, на экран, приводит к уязвимости в и вокруг облака (3).</span><span class="sxs-lookup"><span data-stu-id="69e07-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="69e07-183">Мы затем подготавливается к просмотру всех частей снова в полноэкранном режиме, но сейчас используется буфер шаблона, чтобы маскировать все, но края, приводит к минимальный набор пикселей пользовался (4).</span><span class="sxs-lookup"><span data-stu-id="69e07-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="69e07-184">Поскольку буфер команд уже был создан для частицы, нам просто пришлось визуализировать его снова в новую камеру.</span><span class="sxs-lookup"><span data-stu-id="69e07-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![Ход отрисовки границ облака](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="69e07-186">В результате был четкие границы с разделами требует больших затрат центра облаков.</span><span class="sxs-lookup"><span data-stu-id="69e07-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="69e07-187">Хотя это было намного быстрее, чем подготовки к просмотру все примитивы в полноэкранный режим, по-прежнему затраты, связанные с тестированием пикселей от буфер шаблона, чтобы по-прежнему перерисовывать большие объемы прилагается затраты.</span><span class="sxs-lookup"><span data-stu-id="69e07-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="69e07-188">Исключения примитивов</span><span class="sxs-lookup"><span data-stu-id="69e07-188">Culling particles</span></span>

<span data-ttu-id="69e07-189">Для наших эффекта ветра созданного нами долго лент треугольника в вычислительном шейдере, создание многие поставщики из ветра в мире.</span><span class="sxs-lookup"><span data-stu-id="69e07-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="69e07-190">Эффект ветра была не создает большой нагрузки на коэффициент заполнения, из-за тонким полосы создан, но он преобразовывался многие сотни тысяч вершины, что в результате в условиях большой нагрузки для шейдера вершин.</span><span class="sxs-lookup"><span data-stu-id="69e07-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="69e07-191">Мы представили append буферы на вычислительного шейдера для веб-канала подмножество ветра полосковых линий для отрисовки.</span><span class="sxs-lookup"><span data-stu-id="69e07-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="69e07-192">Простое представление пирамиды обзора установлена логики в вычислительного шейдера мы могли бы определить, было ли полоса за пределами представления камеры и предотвратить добавление буфер Push-уведомлений.</span><span class="sxs-lookup"><span data-stu-id="69e07-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="69e07-193">Это количество лент значительно сократить, освободить некоторые необходимые циклов в GPU.</span><span class="sxs-lookup"><span data-stu-id="69e07-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="69e07-194">**Кода, демонстрирующий используется буфер append:**</span><span class="sxs-lookup"><span data-stu-id="69e07-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="69e07-195">*Вычислить шейдер:*</span><span class="sxs-lookup"><span data-stu-id="69e07-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="69e07-196">*C#код:*</span><span class="sxs-lookup"><span data-stu-id="69e07-196">*C# code:*</span></span>

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

<span data-ttu-id="69e07-197">Мы пробовали, используя ту же методику на частицы облака, где мы исключать их на вычислительного шейдера и только передача видимым частицы к просмотру.</span><span class="sxs-lookup"><span data-stu-id="69e07-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="69e07-198">Этот метод фактически не сохраняли нам большую в GPU момента пиксели сумма отображается на экране и не включает стоимость вычисления вершины крупнейших узким местом.</span><span class="sxs-lookup"><span data-stu-id="69e07-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="69e07-199">Другая проблема с помощью этого способа был, что добавление буфер заполнен в случайном порядке из-за своей природе распараллеленного частицы, вызывая отсортированный частицы быть без отсортированными, приводит к мелькания частицы облачных вычислений.</span><span class="sxs-lookup"><span data-stu-id="69e07-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="69e07-200">Существуют способы сортировки буфере Push-уведомлений, но ограниченный объем рост производительности, который мы получили из визуализируемых частицы бы смещение с дополнительную сортировку, скорее всего, мы решили не реализации этой оптимизации.</span><span class="sxs-lookup"><span data-stu-id="69e07-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="69e07-201">Адаптивная отрисовка</span><span class="sxs-lookup"><span data-stu-id="69e07-201">Adaptive rendering</span></span>

<span data-ttu-id="69e07-202">Для обеспечения постоянной частоты кадров на приложения с различными Подготовка к просмотру условия, такие как облачно vs в четкое мы представили адаптивной отрисовки на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="69e07-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="69e07-203">Адаптивная отрисовка первым делом для измерения GPU.</span><span class="sxs-lookup"><span data-stu-id="69e07-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="69e07-204">Мы сделали это, вставив пользовательский код в буфер команд GPU в начале и конце Отрисованный кадр, обе записи слева и справа глаз времени экрана.</span><span class="sxs-lookup"><span data-stu-id="69e07-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="69e07-205">Измеряя время, затраченное визуализации и ее сравнение с нашей требуемой-частота обновления Наша текущая понять, насколько близко, нам пришлось пропуск кадров.</span><span class="sxs-lookup"><span data-stu-id="69e07-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="69e07-206">Если рядом с удалением кадров, мы адаптировать наших отрисовки для ускорения.</span><span class="sxs-lookup"><span data-stu-id="69e07-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="69e07-207">Один из простых способов адаптации изменяют размер окна просмотра экрана, требуя визуализирован меньше точек.</span><span class="sxs-lookup"><span data-stu-id="69e07-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="69e07-208">С помощью *UnityEngine.XR.XRSettings.renderViewportScale* система сжимает целевого окна просмотра и автоматически растягивает результат резервного копирования по размеру экрана.</span><span class="sxs-lookup"><span data-stu-id="69e07-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="69e07-209">Небольшое изменение в шкале выходит на трехмерной геометрии и масштабный коэффициент 0,7 требует половина объема пикселей для отображения.</span><span class="sxs-lookup"><span data-stu-id="69e07-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![Масштаб 70%, половина пикселей](images/datascape-scaling-700px.jpg)

<span data-ttu-id="69e07-211">При обнаружении, то, что не будет удалено кадров нам уменьшить масштаб с фиксированным числом и повысить его обратно, когда мы запускаем достаточно быстро еще раз.</span><span class="sxs-lookup"><span data-stu-id="69e07-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="69e07-212">Хотя мы решили, какой способ облака для использования на основе графических возможностей оборудования во время запуска, возможно, основываться на данных из измерения GPU, чтобы запретить системе staying с низким разрешением, в течение длительного времени, но это что-то мы не было времени  Чтобы изучить данные в Datascape.</span><span class="sxs-lookup"><span data-stu-id="69e07-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="69e07-213">Заключительные замечания</span><span class="sxs-lookup"><span data-stu-id="69e07-213">Final thoughts</span></span>

<span data-ttu-id="69e07-214">Предназначенные для различных аппаратных средств является довольно сложной и требует определенного планирования.</span><span class="sxs-lookup"><span data-stu-id="69e07-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="69e07-215">Мы рекомендуем начать предназначенных для малой машин, чтобы ознакомиться с пространство проблемы и разрабатывать решения архивации, которое будет выполняться на всех компьютерах.</span><span class="sxs-lookup"><span data-stu-id="69e07-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="69e07-216">При разработке решения с коэффициент заполнения в виду, так как будут самый ценный ресурс.</span><span class="sxs-lookup"><span data-stu-id="69e07-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="69e07-217">Целевой объект geometry сплошная линия по прозрачности.</span><span class="sxs-lookup"><span data-stu-id="69e07-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="69e07-218">С решением архивации можно запустите слоев в дополнительные сложности для машин верхний предел или может быть просто повысить разрешения из решения для архивации.</span><span class="sxs-lookup"><span data-stu-id="69e07-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="69e07-219">Проектирование для худшего варианта развития и может быть рассмотрите возможность использования адаптивной отрисовки для случаев большой.</span><span class="sxs-lookup"><span data-stu-id="69e07-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="69e07-220">Об авторах</span><span class="sxs-lookup"><span data-stu-id="69e07-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="69e07-221"><b>Роберт Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="69e07-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="69e07-222">Разработчик программного обеспечения @Microsoft</span><span class="sxs-lookup"><span data-stu-id="69e07-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="69e07-223"><b>Дэн Andersson</b></span><span class="sxs-lookup"><span data-stu-id="69e07-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="69e07-224">Разработчик программного обеспечения @Microsoft</span><span class="sxs-lookup"><span data-stu-id="69e07-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="69e07-225">См. также</span><span class="sxs-lookup"><span data-stu-id="69e07-225">See also</span></span>
* [<span data-ttu-id="69e07-226">Основные сведения о производительности для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="69e07-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="69e07-227">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="69e07-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
