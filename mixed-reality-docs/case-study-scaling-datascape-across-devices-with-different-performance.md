---
title: Пример использования. масштабирование Датаскапе на разных устройствах с различной производительностью
description: В этом практическом примере представлено представление о том, как разработчики Майкрософт оптимизируют приложение Датаскапе, чтобы обеспечить привлекательную работу на устройствах с различными возможностями повышения производительности.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: иммерсивное головной телефон, оптимизация производительности, VR, пример использования
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523392"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="f8c4c-104">Пример использования. масштабирование Датаскапе на разных устройствах с различной производительностью</span><span class="sxs-lookup"><span data-stu-id="f8c4c-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="f8c4c-105">Датаскапе — это приложение Windows Mixed Reality, разработанное внутри корпорации Майкрософт, где мы сосредоточены на отображении данных о погоде на основе данных ландшафта.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="f8c4c-106">Приложение исследует уникальную информацию, которую получают пользователи при обнаружении данных в смешанной реальности, отключив пользователя к визуализации данных с помощью Holographic.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="f8c4c-107">Для Датаскапе мы хотели ориентироваться на различные платформы с различными аппаратными возможностями, от Microsoft HoloLens до впечатляющих головных телефонов Windows Mixed Reality, а также от компьютеров с более низким потреблением до самых современных ПК с высокопроизводительным графическим процессором.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="f8c4c-108">Основная задача — это визуализация сцены в визуально привлекательном масштабе на устройствах с различными графическими возможностями при выполнении с высокой частотой кадров.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="f8c4c-109">В этом практическом примере рассматривается процесс и методы, используемые для создания некоторых дополнительных систем с большим числом GPU, описание возникших проблем и способ их преодолел все испытания.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="f8c4c-110">Прозрачность и перерисовка</span><span class="sxs-lookup"><span data-stu-id="f8c4c-110">Transparency and overdraw</span></span>

<span data-ttu-id="f8c4c-111">В нашей основной визуализации возникают проблемы с прозрачностью, так как прозрачность может быть дорогостоящей на GPU.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="f8c4c-112">Сплошная геометрия может быть подготовлена к просмотру спереди на задний план во время записи в буфер глубины, при этом все будущие Пиксели, расположенные за этой точкой, удаляются.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="f8c4c-113">Это предотвращает выполнение построителя текстуры скрытыми пикселями, что значительно ускоряет процесс.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="f8c4c-114">Если геометрия упорядочена оптимально, каждый пиксель на экране будет нарисован только один раз.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="f8c4c-115">Прозрачная геометрия должна быть отсортирована на передний план и полагается на смешение выходных данных шейдера пикселей к текущему пикселю на экране.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="f8c4c-116">Это может привести к тому, что каждый пиксель на экране рисуется на несколько раз в кадре, что называется перерисовкой.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="f8c4c-117">Для HoloLens и основных ПК Этот экран можно заполнять лишь несколько раз, что делает прозрачную визуализацию проблематичной.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="f8c4c-118">Общие сведения о компонентах сцены Датаскапе</span><span class="sxs-lookup"><span data-stu-id="f8c4c-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="f8c4c-119">Мы имели три основных компонента для нашей сцены. **Пользовательский интерфейс, схема**и **Погода**.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="f8c4c-120">Мы знали, что наши эффекты погоды потребовали бы всего времени GPU, поэтому мы намеренно разработали пользовательский интерфейс и ландшафта таким образом, чтобы сократить все перерисовки.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="f8c4c-121">Мы несколько раз переработали пользовательский интерфейс, чтобы максимально сокращать объем перерисовок.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="f8c4c-122">Мы выдвигают на стороне более сложной геометрии, а не наложение прозрачной картинки поверх других для таких компонентов, как светящиеся кнопки и обзоры карт.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="f8c4c-123">Для Map мы использовали пользовательский шейдер, который бы мог выделять стандартные функции Unity, такие как тени и сложное освещение, заменяя их простой моделью освещения Sun и пользовательским вычислением тумана.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="f8c4c-124">Это создавало простой шейдер пикселей и освобождать циклы GPU.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="f8c4c-125">Мы управляем, чтобы получить пользовательский интерфейс и карту для отрисовки в бюджете, где в зависимости от оборудования не требуется вносить изменения. Однако визуализация погоды, в частности, в облачной отрисовке, выстала более сложной задачей.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="f8c4c-126">Общие сведения о облачных данных</span><span class="sxs-lookup"><span data-stu-id="f8c4c-126">Background on cloud data</span></span>

<span data-ttu-id="f8c4c-127">Наши облачные данные были скачаны с серверов http://nomads.ncep.noaa.gov/) NOAA (и поступили в нас на трех разных 2D-слоях, каждый с верхней и нижней высотой облака, а также с плотностью облака для каждой ячейки сетки.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="f8c4c-128">Данные обрабатывались в текстуру облачных сведений, где каждый компонент хранился в красном, зеленом и синем компоненте текстуры для удобного доступа к GPU.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="f8c4c-129">Геометрические облака</span><span class="sxs-lookup"><span data-stu-id="f8c4c-129">Geometry clouds</span></span>

<span data-ttu-id="f8c4c-130">Чтобы убедиться, что наши компьютеры могут визуализировать наши облака, мы решили начать с подхода, который будет использовать сплошную геометрию для уменьшения перерисовки.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="f8c4c-131">Сначала мы попытались создавать облака, создавая сплошную хеигхтмапную сетку для каждого слоя, используя радиус текстуры облачной информации на вершину для создания фигуры.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="f8c4c-132">Мы использовали шейдер Geometry для создания вершин как в верхней, так и в нижней части облака, создающей сплошные облачные фигуры.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="f8c4c-133">Мы использовали значение плотности от текстуры, чтобы окрасить облако с более темными цветами для более сжатых облаков.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="f8c4c-134">**Шейдер для создания вершин:**</span><span class="sxs-lookup"><span data-stu-id="f8c4c-134">**Shader for creating the vertices:**</span></span>

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

<span data-ttu-id="f8c4c-135">Мы предоставили небольшой шаблон шума для получения более подробных сведений о реальных данных.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="f8c4c-136">Чтобы создать скругленные края облака, мы обрезаем пикселов в шейдере пикселей, когда значение радиуса интерполяции достигает порогового значения, чтобы отбросить почти нулевые значения.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Геометрические облака](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="f8c4c-138">Так как облака являются сплошной геометрией, они могут быть отображены до того, как ландшафта скрывает все дорогостоящие Пиксели карт под для дальнейшего улучшения частоты кадров.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="f8c4c-139">Это решение хорошо работает на всех графических картах от min-Spec до высокопроизводительных графических карт, а также на HoloLens, из-за подхода к отрисовке геометрического объекта Geometry.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="f8c4c-140">Сплошные облака частиц</span><span class="sxs-lookup"><span data-stu-id="f8c4c-140">Solid particle clouds</span></span>

<span data-ttu-id="f8c4c-141">Теперь у нас есть решение для резервного копирования, которое создало личное представление наших облачных данных, но было немного лакклустер в отношении "WOW" и не передавало объемные, что требовалось для наших высокопроизводительных компьютеров.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="f8c4c-142">Следующий шаг — создание облаков, представляющих их приблизительно 100 000 частиц для создания более согласованного и объемныеного вида.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="f8c4c-143">Если частицы остаются сплошными и сортируются от начала до конца, мы по-прежнему можем получить преимущество от использования отбора в буфере глубины пикселов за ранее визуализированными частицами, уменьшая перерисовку.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="f8c4c-144">Кроме того, с помощью решения на основе примитивов можно изменить объем частиц, используемый для другого оборудования.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="f8c4c-145">Тем не менее все пикселы по-прежнему нуждаются в тщательном тестировании, что приводит к дополнительным издержкам.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="f8c4c-146">Во первых, мы создали положение примитивов вокруг центральной точки опыта при запуске.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="f8c4c-147">Мы намерены выровнять частицы по центру и уменьшить это расстояние.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="f8c4c-148">Мы заранее отсортировани все частицы от центра к обратной стороне, чтобы сначала отображались ближайшие частицы.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="f8c4c-149">При использовании шейдера вычислений в качестве текстуры облачной информации будет размещаться правильная высота и цвет на основе плотности.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="f8c4c-150">Мы использовали *дравпроцедурал* , чтобы визуализировать четыре отдельных примитива, что позволяет постоянно оставаться на GPU.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="f8c4c-151">Каждая часть содержит как высоту, так и радиус.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="f8c4c-152">Высота была основана на облачных данных, выборке из текстуры облачной информации, а радиус был основан на первоначальном распределении, где будет рассчитываться горизонтальное расстояние до ближайшего соседнего.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="f8c4c-153">Эти данные будут использоваться для ориентации самого себя на высоту, так что когда пользователи просматривает их по горизонтали, отображается высота, и когда пользователи рассмотрели его сверху вниз, будет охвачена область между соседними сторонами.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![Фигурная часть](images/particle-shape-700px.png)

<span data-ttu-id="f8c4c-155">**Код шейдера, иллюстрирующий распределение:**</span><span class="sxs-lookup"><span data-stu-id="f8c4c-155">**Shader code showing the distribution:**</span></span>

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

<span data-ttu-id="f8c4c-156">Так как мы сортирует частицы спереди на задний план и по-прежнему использовали сплошной шейдер стиля для обрезки (не Blend) прозрачных пикселов, этот метод обрабатывает неудивительное количество частиц, избегая дорогостоящего нарисовать даже на компьютерах с более низким энергопотреблением.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="f8c4c-157">Прозрачные облака частиц</span><span class="sxs-lookup"><span data-stu-id="f8c4c-157">Transparent particle clouds</span></span>

<span data-ttu-id="f8c4c-158">Твердая частица предоставляла представление об облаках, но по-прежнему требовалось что-нибудь для продажи флуффинесс облаков.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="f8c4c-159">Мы решили испытать пользовательское решение для высококачественных графических плат, в которых можно реализовать прозрачность.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="f8c4c-160">Для этого мы просто переключили первоначальный порядок сортировки частиц и изменили шейдер для использования альфа-текстуры.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Облака Пушок](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="f8c4c-162">Он выглядит замечательно, но оказался слишком большим для даже самых требовательных компьютеров, так как это приведет к отрисовке каждого пикселя на экране сотни раз!</span><span class="sxs-lookup"><span data-stu-id="f8c4c-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="f8c4c-163">Отображение за пределами экрана с низким разрешением</span><span class="sxs-lookup"><span data-stu-id="f8c4c-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="f8c4c-164">Чтобы уменьшить количество пикселей, отображаемых облаками, мы начали отображать их в буфере разрешения квартала (по сравнению с экраном) и растягивать конечный результат на экран после отрисовки всех частиц.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="f8c4c-165">Это позволило нам примерно 4X, но в комплекте с несколькими предостережениями.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="f8c4c-166">**Код для отображения на экране:**</span><span class="sxs-lookup"><span data-stu-id="f8c4c-166">**Code for rendering off-screen:**</span></span>

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

<span data-ttu-id="f8c4c-167">Во-первых, при отрисовке в буфер вне экрана мы потеряли всю информацию о глубине из нашей основной сцены, что привело к горы отрисовки поверх Mountain.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="f8c4c-168">Во вторых, при растяжении буфера также появились артефакты на краях наших облаков, где изменение разрешения было заметным.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="f8c4c-169">В следующих двух разделах рассказывается о том, как мы разрешили эти проблемы.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="f8c4c-170">Буфер глубины частицы</span><span class="sxs-lookup"><span data-stu-id="f8c4c-170">Particle depth buffer</span></span>

<span data-ttu-id="f8c4c-171">Чтобы сделать частицу сосуществование с мировой геометрией, где Mountain или объект может охватить частицы за ним, мы заполнили буфер экрана с буфером глубины, содержащим геометрию основной сцены.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="f8c4c-172">Чтобы создать такой буфер глубины, мы создали вторую камеру, выполняя визуализацию только сплошной геометрии и глубины сцены.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="f8c4c-173">Затем мы использовали новую текстуру в шейдере пикселей для облаков, чтобы окклуде Пиксели.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="f8c4c-174">Мы использовали ту же текстуру, чтобы вычислить расстояние до геометрического пикселя в облаке.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="f8c4c-175">Используя это расстояние и применяя его к альфа-каналу пикселя, мы приходили уменьшить воздействие облаков по мере того, как они близки к ландшафта, устраняя при этом все жесткие вырезаниеи, где частицы и ландшафта встречаются.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![Облака, накладываемые на ландшафта](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="f8c4c-177">Увеличение резкости краев</span><span class="sxs-lookup"><span data-stu-id="f8c4c-177">Sharpening the edges</span></span>

<span data-ttu-id="f8c4c-178">Растянутые облачные облака были почти идентичны облакам нормального размера в центре частиц или в том месте, где они перекрываются, но показали некоторые артефакты на краях облака.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="f8c4c-179">В противном случае четкие края будут выглядеть размытыми, а при перемещении камеры были введены эффекты псевдонима.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="f8c4c-180">Мы разрешили это, выполнив простой шейдер в буфере экрана, чтобы определить, где произошло большое изменение (1).</span><span class="sxs-lookup"><span data-stu-id="f8c4c-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="f8c4c-181">Мы помещаем пикселы с большими изменениями в новый буфер шаблона (2).</span><span class="sxs-lookup"><span data-stu-id="f8c4c-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="f8c4c-182">Затем мы использовали буфер трафарета для маскирования этих областей с высокой контрастностью при применении обратного буфера к экрану, что приводит к пропускам в и вокруг облаков (3).</span><span class="sxs-lookup"><span data-stu-id="f8c4c-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="f8c4c-183">Затем все части снова визуализируются в полноэкранном режиме, но в этот раз использовался буфер шаблона, чтобы маскировать все, кроме краев, что приводит к минимальному набору затронутых пикселей (4).</span><span class="sxs-lookup"><span data-stu-id="f8c4c-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="f8c4c-184">Так как буфер команд уже был создан для частиц, нам просто пришлось снова отобразить его на новой камере.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![Ход отрисовки ребер облака](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="f8c4c-186">Конечный результат — это резкие края с дешевыми разделами облаков.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="f8c4c-187">Хотя это было гораздо быстрее, чем визуализация всех частиц в полноэкранном режиме, по-прежнему взимается плата, связанная с тестированием пикселов на соответствие с буфером трафарета, поэтому при большом объеме перерисовки по-прежнему взимается стоимость.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="f8c4c-188">Частицы для отбора</span><span class="sxs-lookup"><span data-stu-id="f8c4c-188">Culling particles</span></span>

<span data-ttu-id="f8c4c-189">Для нашего обратного света мы создали длинные ленты треугольников в шейдере вычислений, создавая множество беспроводных протоколов "Ветер" в мире.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="f8c4c-190">В то время как воздействие на обмотку не слишком велико, так как фактамные ленты созданы, то было создано множество сотен тысяч вершин, что привело к высокой нагрузке для шейдера вершин.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="f8c4c-191">Мы представили Добавление буферов в шейдер вычислений для передачи подмножества полос обмотки для рисования.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="f8c4c-192">Используя простую логику фрустум представлений в шейдере вычислений, можно определить, находится ли полоска вне представления камеры и не допустить ее добавления в буфер push-уведомлений.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="f8c4c-193">Это значительно сокращает количество полос, освобождая некоторые необходимые циклы на GPU.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="f8c4c-194">**Код, демонстрирующий буфер добавления:**</span><span class="sxs-lookup"><span data-stu-id="f8c4c-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="f8c4c-195">*Вычисление шейдера:*</span><span class="sxs-lookup"><span data-stu-id="f8c4c-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="f8c4c-196">*C#приведен*</span><span class="sxs-lookup"><span data-stu-id="f8c4c-196">*C# code:*</span></span>

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

<span data-ttu-id="f8c4c-197">Мы попытались использовать ту же методику в частях облака, где мы бы выдавали их в шейдере вычислений и относимся к визуализации только видимым частицам.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="f8c4c-198">Эта методика на самом деле не позволила нам значительно сэкономить GPU, так как крупнейший узким местом был объем отображаемых на экране пикселей, а не затраты на вычисление вершин.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="f8c4c-199">Другая проблема с этим методом заключается в том, что буфер добавления заполнен в случайном порядке из-за его параллелизации в результате вычисления частиц, что приводит к снижению количества элементов облака.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="f8c4c-200">Существуют методы сортировки буфера push-уведомлений, но ограниченный объем выростов производительности, который мы получаем за исключением частиц, скорее всего, будет смещен с дополнительной сортировкой, поэтому мы решили не выполнять эту оптимизацию.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="f8c4c-201">Адаптивная визуализация</span><span class="sxs-lookup"><span data-stu-id="f8c4c-201">Adaptive rendering</span></span>

<span data-ttu-id="f8c4c-202">Для обеспечения постоянной частоты кадров в приложении с различными условиями отрисовки, такими как облако и четкое представление, мы предоставили адаптивную визуализацию для нашего приложения.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="f8c4c-203">Первым шагом адаптивной визуализации является измерение GPU.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="f8c4c-204">Мы сделали это, вставив пользовательский код в буфер команд GPU в начале и в конец визуализированного кадра, записывая как левое, так и правильное время на экране глаз.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="f8c4c-205">Измеряя время, затраченное на визуализацию и сравнивая его с требуемой частотой обновления, мы получили представление о том, как близко мы будем удалять кадры.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="f8c4c-206">Когда вы закроете, чтобы удалить кадры, мы адаптировани к отрисовке, чтобы ускорить их выполнение.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="f8c4c-207">Одним из простых способов адаптации является изменение размера окна просмотра экрана, требующего отображения меньшего количества пикселей.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="f8c4c-208">С помощью *UnityEngine. XR. ксрсеттингс. рендервиевпортскале* система сжимает целевое окно просмотра и автоматически растягивает результат до размера экрана.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="f8c4c-209">Небольшое изменение масштаба очень заметно для мирового геометрического объекта, а коэффициент масштабирования 0,7 требует половину объема отображаемых пикселей.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% Scale, половина пикселей](images/datascape-scaling-700px.jpg)

<span data-ttu-id="f8c4c-211">Когда мы определим, что мы будем сбрасывать кадры, мы меньшим масштабом по фиксированному числу, а затем вернемся к этому, когда мы снова выполняем достаточно быстро.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="f8c4c-212">Хотя мы решили, какой облачный метод использовать в зависимости от возможностей графического оборудования при запуске, можно создать его на основе данных из измерения GPU, чтобы система не поддерживала низкое разрешение в течение длительного времени, но это не так давно.  для просмотра в Датаскапе.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="f8c4c-213">Заключительные идеи</span><span class="sxs-lookup"><span data-stu-id="f8c4c-213">Final thoughts</span></span>

<span data-ttu-id="f8c4c-214">Нацеливание на различные аппаратные средства является сложной задачей и требует определенного планирования.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="f8c4c-215">Рекомендуется начать работу с конечными компьютерами, чтобы ознакомиться с проблемным пространством и разработать решение для резервного копирования, которое будет выполняться на всех компьютерах.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="f8c4c-216">Разработайте свое решение с учетом скорости заполнения, поскольку пиксели будут самыми ценными.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="f8c4c-217">Целевая геометрическая геометрия по прозрачности.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="f8c4c-218">С помощью решения для резервного копирования можно приступить к расширению уровня сложности для высокопроизводительных компьютеров или просто улучшить разрешение резервного копирования.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="f8c4c-219">Разработка для наихудших сценариев и, возможно, рассмотрите возможность адаптивной отрисовки для больших ситуаций.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="f8c4c-220">Об авторах</span><span class="sxs-lookup"><span data-stu-id="f8c4c-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="f8c4c-221"><b>Роберт Ферресе</b></span><span class="sxs-lookup"><span data-stu-id="f8c4c-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="f8c4c-222">Инженер по программному обеспечению@Microsoft</span><span class="sxs-lookup"><span data-stu-id="f8c4c-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="f8c4c-223"><b>Андерссон "+ +"</b></span><span class="sxs-lookup"><span data-stu-id="f8c4c-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="f8c4c-224">Инженер по программному обеспечению@Microsoft</span><span class="sxs-lookup"><span data-stu-id="f8c4c-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="f8c4c-225">См. также</span><span class="sxs-lookup"><span data-stu-id="f8c4c-225">See also</span></span>
* [<span data-ttu-id="f8c4c-226">Основные сведения о производительности смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="f8c4c-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="f8c4c-227">Рекомендации по повышению производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="f8c4c-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
