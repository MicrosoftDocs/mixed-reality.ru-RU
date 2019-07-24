---
title: Подготовка тома
description: Изображения объемные содержат обширную информацию с непрозрачностью и цветом в рамках всего тома, которые не могут быть легко выражены в качестве поверхностей. Узнайте, как эффективно визуализировать объемные образы в Windows Mixed Reality.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: образ объемные, подготовка тома, производительность, Смешанная реальность
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548634"
---
# <a name="volume-rendering"></a><span data-ttu-id="24a07-105">Подготовка тома</span><span class="sxs-lookup"><span data-stu-id="24a07-105">Volume rendering</span></span>

<span data-ttu-id="24a07-106">Сведения о медицинских MRI или технологических томах см. [в статье Подготовка тома в Википедии](https://en.wikipedia.org/wiki/Volume_rendering).</span><span class="sxs-lookup"><span data-stu-id="24a07-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="24a07-107">Эти "объемные изображения" содержат обширные сведения с непрозрачностью и цветом в рамках всего тома, которые не могут быть легко выражены в виде таких поверхностей, как многоугольные [сетки](https://en.wikipedia.org/wiki/Polygon_mesh).</span><span class="sxs-lookup"><span data-stu-id="24a07-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="24a07-108">Основные решения для повышения производительности</span><span class="sxs-lookup"><span data-stu-id="24a07-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="24a07-109">ПРАВИЛЬНЫМ Упрощенный подход: Отображение всего тома, обычно выполняется слишком медленно</span><span class="sxs-lookup"><span data-stu-id="24a07-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="24a07-110">РЕКОМЕНДУЕТСЯ Вырезание плоскости: Отображение только одного среза тома</span><span class="sxs-lookup"><span data-stu-id="24a07-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="24a07-111">РЕКОМЕНДУЕТСЯ Вырезание подразделов: Показывать только несколько слоев тома</span><span class="sxs-lookup"><span data-stu-id="24a07-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="24a07-112">РЕКОМЕНДУЕТСЯ Уменьшение разрешения отрисовки тома (см. раздел "Визуализация в режиме смешанного разрешения")</span><span class="sxs-lookup"><span data-stu-id="24a07-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="24a07-113">Существует только определенный объем информации, которую можно передать из приложения на экран в каком-либо конкретном кадре. это общая пропускная способность памяти.</span><span class="sxs-lookup"><span data-stu-id="24a07-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="24a07-114">Кроме того, для преобразования данных для представления также требуется время обработки (или заливки).</span><span class="sxs-lookup"><span data-stu-id="24a07-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="24a07-115">Ниже приведены основные моменты, которые следует учитывать при выполнении подготовки тома.</span><span class="sxs-lookup"><span data-stu-id="24a07-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="24a07-116">Ширина экрана \* высота экрана \* — количество \* том-слои-вкл.-пиксель = всего-Volume-Samples-on-Frame</span><span class="sxs-lookup"><span data-stu-id="24a07-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="24a07-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (полный объем ресурсов: слишком много выборок)</span><span class="sxs-lookup"><span data-stu-id="24a07-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="24a07-118">1028 \* 720 \* 2 \* 1 = 1480320 (0,3% от полной) (тонкий срез: 1 выборка на пиксель, выполняется без проблем.)</span><span class="sxs-lookup"><span data-stu-id="24a07-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="24a07-119">1028 \* 720 \* 2 \* 10 = 14803200 (3,9% от полной) (срез вспомогательного тома: 10 выборок на пиксель, выполняется довольно гладко, выглядит трехмерная)</span><span class="sxs-lookup"><span data-stu-id="24a07-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="24a07-120">200 \* 200 \* 2 \* 256 = 20480000 (5% от полной) (более низкий объем ресурсов: меньше пикселей, полный том, объемный, но немного размытие)</span><span class="sxs-lookup"><span data-stu-id="24a07-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="24a07-121">Представление трехмерных текстур</span><span class="sxs-lookup"><span data-stu-id="24a07-121">Representing 3D Textures</span></span>

<span data-ttu-id="24a07-122">На ЦП:</span><span class="sxs-lookup"><span data-stu-id="24a07-122">On the CPU:</span></span>

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

<span data-ttu-id="24a07-123">На GPU:</span><span class="sxs-lookup"><span data-stu-id="24a07-123">On the GPU:</span></span>

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a><span data-ttu-id="24a07-124">Заливка и градиенты</span><span class="sxs-lookup"><span data-stu-id="24a07-124">Shading and Gradients</span></span>

<span data-ttu-id="24a07-125">Как затенить том, например MRI, для полезной визуализации.</span><span class="sxs-lookup"><span data-stu-id="24a07-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="24a07-126">Основным методом является «окно интенсивности» (минимальное и максимальное), интенситиес в рамках, и просто масштабируется в это пространство, чтобы увидеть интенсивность черной и белой шкалы.</span><span class="sxs-lookup"><span data-stu-id="24a07-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="24a07-127">Цветовая шкала может быть применена к значениям в пределах этого диапазона и сохранена в виде текстуры, чтобы различные части спектра интенсивности можно было затенить разными цветами:</span><span class="sxs-lookup"><span data-stu-id="24a07-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="24a07-128">Во многих наших приложениях мы сохраняем на нашем томе значение интенсивности необработанных данных и "индекс сегментации" (для сегментирования различных частей, таких как Обложка и кость, эти сегменты обычно создаются экспертами в выделенных инструментах).</span><span class="sxs-lookup"><span data-stu-id="24a07-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="24a07-129">Это можно сочетать с описанным выше способом, чтобы задать другой цвет или даже разную цветовую шкалу для каждого индекса сегмента:</span><span class="sxs-lookup"><span data-stu-id="24a07-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="24a07-130">Срез томов в шейдере</span><span class="sxs-lookup"><span data-stu-id="24a07-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="24a07-131">Отличным первым шагом является создание "плоскости среза", которая может перемещаться по тому, "размещая ее" и проверять значения в каждой точке.</span><span class="sxs-lookup"><span data-stu-id="24a07-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="24a07-132">Предполагается, что существует куб «Волумеспаце», который представляет место, где находится том в мировом пространстве, который можно использовать в качестве ссылки для размещения точек:</span><span class="sxs-lookup"><span data-stu-id="24a07-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="24a07-133">Трассировка тома в шейдере</span><span class="sxs-lookup"><span data-stu-id="24a07-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="24a07-134">Как использовать графический процессор для трассировки вложенного тома (проходит несколько вокселс глубоких слоев данных с обратно на передний план):</span><span class="sxs-lookup"><span data-stu-id="24a07-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a><span data-ttu-id="24a07-135">Отрисовка всего тома</span><span class="sxs-lookup"><span data-stu-id="24a07-135">Whole Volume Rendering</span></span>

<span data-ttu-id="24a07-136">При изменении приведенного выше кода подраздела мы получаем:</span><span class="sxs-lookup"><span data-stu-id="24a07-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="24a07-137">Отображение сцены смешанного разрешения</span><span class="sxs-lookup"><span data-stu-id="24a07-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="24a07-138">Как отобразить часть сцены с низким разрешением и вернуть ее на месте:</span><span class="sxs-lookup"><span data-stu-id="24a07-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="24a07-139">Установка двух экранных камер: один для отслеживания каждого глаза, который обновляет каждый кадр</span><span class="sxs-lookup"><span data-stu-id="24a07-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="24a07-140">Настройте два целевого объекта отрисовки с низким разрешением (скажем, 200x200 каждый), что камеры визуализируются в</span><span class="sxs-lookup"><span data-stu-id="24a07-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="24a07-141">Настроили четыре, которые переходят перед пользователем</span><span class="sxs-lookup"><span data-stu-id="24a07-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="24a07-142">Каждый кадр:</span><span class="sxs-lookup"><span data-stu-id="24a07-142">Each Frame:</span></span>
1. <span data-ttu-id="24a07-143">Нарисуйте цели рендеринга для каждого взгляда с низким разрешением (данные тома, дорогостоящие шейдеры и т. д.).</span><span class="sxs-lookup"><span data-stu-id="24a07-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="24a07-144">Отрисовка сцены в обычном режиме с полным разрешением (сетки, Пользовательский интерфейс и т. д.)</span><span class="sxs-lookup"><span data-stu-id="24a07-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="24a07-145">Нарисуйте «четыре» перед пользователем, поверх сцены и проецирование низкого уровня просмотра на него.</span><span class="sxs-lookup"><span data-stu-id="24a07-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="24a07-146">Результат: визуальное сочетание элементов с полным разрешением с низким уровнем разрешения, но с данными о томах с высокой плотностью.</span><span class="sxs-lookup"><span data-stu-id="24a07-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>
