---
title: Тома отрисовки
description: Объемные образы содержат ценные сведения с прозрачность и цвет на протяжении всего тома, не могут быть легко выражены как поверхности. Узнайте, как эффективно визуализировать объемные изображения в Windows Mixed Reality.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: объемные изображения, подготовки к просмотру тома, производительности, смешанной реальности
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604096"
---
# <a name="volume-rendering"></a><span data-ttu-id="14d59-105">Тома отрисовки</span><span class="sxs-lookup"><span data-stu-id="14d59-105">Volume rendering</span></span>

<span data-ttu-id="14d59-106">Медицинские MRI или проектирование тома, см. в разделе [тома, Подготовка к просмотру в Википедии](https://en.wikipedia.org/wiki/Volume_rendering).</span><span class="sxs-lookup"><span data-stu-id="14d59-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="14d59-107">Эти объемные образы содержат ценные сведения с прозрачность и цвет на протяжении всего тома, который не может быть выражен легко как поверхности такие как [кусочно-линейной сеток](https://en.wikipedia.org/wiki/Polygon_mesh).</span><span class="sxs-lookup"><span data-stu-id="14d59-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="14d59-108">Ключевые решения для повышения производительности</span><span class="sxs-lookup"><span data-stu-id="14d59-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="14d59-109">НЕПРАВИЛЬНЫЙ: Наивный подход: Показать всего тома, обычно работает слишком медленно</span><span class="sxs-lookup"><span data-stu-id="14d59-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="14d59-110">ХОРОШИЙ: На переднем плоскости: Показать только один срез тома</span><span class="sxs-lookup"><span data-stu-id="14d59-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="14d59-111">ХОРОШИЙ: На переднем вложенных том: Отображение только несколько слоев тома</span><span class="sxs-lookup"><span data-stu-id="14d59-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="14d59-112">ХОРОШИЙ: Уменьшите разрешение отображения тома (см. в разделе «Отрисовка сцен смешанной разрешение»)</span><span class="sxs-lookup"><span data-stu-id="14d59-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="14d59-113">Есть только определенный объем информации, которая может передаваться из приложения на экране в любой определенный кадр, это пропускная способность общего объема памяти.</span><span class="sxs-lookup"><span data-stu-id="14d59-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="14d59-114">Также любой обработки (или «заливка»), необходимых для преобразования этих данных для представления также требует времени.</span><span class="sxs-lookup"><span data-stu-id="14d59-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="14d59-115">Таким образом являются основными факторами при выполнении отрисовки тома:</span><span class="sxs-lookup"><span data-stu-id="14d59-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="14d59-116">Ширина экрана \* Высота экрана \* экрана Count \* тома слои на что пиксель = всего Volume образцы кадров</span><span class="sxs-lookup"><span data-stu-id="14d59-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="14d59-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (полный res тома: слишком много выборок в режиме)</span><span class="sxs-lookup"><span data-stu-id="14d59-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="14d59-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% полного) (тонкая срез: 1. пример на пиксель, прошел)</span><span class="sxs-lookup"><span data-stu-id="14d59-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="14d59-119">1028 \* 720 \* 2 \* 10 = 14803200 (% 3.9 полного) (срез вложенных тома: 10 примеров на пиксель, довольно прошел, ищет 3d)</span><span class="sxs-lookup"><span data-stu-id="14d59-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="14d59-120">200 \* 200 \* 2 \* 256 = 20480000 (5% от полной) (понизить res тома: меньшее количество пикселей, всего тома, ищет 3d, но немного blury)</span><span class="sxs-lookup"><span data-stu-id="14d59-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="14d59-121">Представляющий 3D-текстуры</span><span class="sxs-lookup"><span data-stu-id="14d59-121">Representing 3D Textures</span></span>

<span data-ttu-id="14d59-122">ЦП:</span><span class="sxs-lookup"><span data-stu-id="14d59-122">On the CPU:</span></span>

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

<span data-ttu-id="14d59-123">В графическом Процессоре:</span><span class="sxs-lookup"><span data-stu-id="14d59-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="14d59-124">Заливки и градиенты</span><span class="sxs-lookup"><span data-stu-id="14d59-124">Shading and Gradients</span></span>

<span data-ttu-id="14d59-125">Как затенение томе, например MRI, для наглядное представление.</span><span class="sxs-lookup"><span data-stu-id="14d59-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="14d59-126">Основной метод – заставить «интенсивность window» (min и max) необходимость интенсивности в см. в разделе и легко масштабировать в это пространство для просмотра черно-белый интенсивность.</span><span class="sxs-lookup"><span data-stu-id="14d59-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="14d59-127">«Шкалы цветов» можно затем применяется к значениям в пределах диапазона и хранить как текстуру, таким образом, разные части спектра интенсивность затененную различных цветов:</span><span class="sxs-lookup"><span data-stu-id="14d59-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="14d59-128">Во многих наших приложений, мы сохраняем в наши корпоративные значение необработанные интенсивность и «сегментации индекса» (для сегментирования различных частей, такие как обложки и кости, эти сегменты обычно создаются специалистами в выделенные инструменты).</span><span class="sxs-lookup"><span data-stu-id="14d59-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="14d59-129">Можно объединить с подходом, выше, чтобы поместить свой цвет или шкалы даже в разных цветов для каждого сегмента индекса:</span><span class="sxs-lookup"><span data-stu-id="14d59-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="14d59-130">Создание срезов в шейдере тома</span><span class="sxs-lookup"><span data-stu-id="14d59-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="14d59-131">Это отличный первый шаг — создать «среза плоскость», можно перемещаться тома «Фрагментирование», и как проверки значений в каждой точке.</span><span class="sxs-lookup"><span data-stu-id="14d59-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="14d59-132">Это предполагает, что имеется куб «VolumeSpace», которое представляет, когда том в абсолютном пространстве, который может использоваться в качестве ссылки для размещения точки:</span><span class="sxs-lookup"><span data-stu-id="14d59-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="14d59-133">Трассировка тома в шейдеров</span><span class="sxs-lookup"><span data-stu-id="14d59-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="14d59-134">Как использовать графический Процессор для выполнения трассировки вложенных тома (проходит несколько voxels глубоких затем слоев данных из резервной копии на передний план):</span><span class="sxs-lookup"><span data-stu-id="14d59-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="14d59-135">Всего тома отрисовки</span><span class="sxs-lookup"><span data-stu-id="14d59-135">Whole Volume Rendering</span></span>

<span data-ttu-id="14d59-136">Изменение в приведенном выше коде вложенных тома мы получаем:</span><span class="sxs-lookup"><span data-stu-id="14d59-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="14d59-137">Отрисовка сцен разрешение смешанных</span><span class="sxs-lookup"><span data-stu-id="14d59-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="14d59-138">Как отобразить часть сцены с низким разрешением и поместить его обратно в месте:</span><span class="sxs-lookup"><span data-stu-id="14d59-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="14d59-139">Настройка двух вне экрана камеры, один для выполнения каждого глаза, который обновления каждого кадра</span><span class="sxs-lookup"><span data-stu-id="14d59-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="14d59-140">С низким разрешением два целевых объектов отрисовки (предположим, что 200 x 200 каждый), что отображают камеры</span><span class="sxs-lookup"><span data-stu-id="14d59-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="14d59-141">Настройка квадрант, которое перемещает глазах у пользователя</span><span class="sxs-lookup"><span data-stu-id="14d59-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="14d59-142">Каждый кадр:</span><span class="sxs-lookup"><span data-stu-id="14d59-142">Each Frame:</span></span>
1. <span data-ttu-id="14d59-143">Рисование целевых объектов отрисовки для каждого глаза с низким разрешением (тома данных, ресурсоемкие шейдеры т. д.)</span><span class="sxs-lookup"><span data-stu-id="14d59-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="14d59-144">Рисования сцены обычно как полным разрешением (сетки, пользовательского интерфейса и т. д.)</span><span class="sxs-lookup"><span data-stu-id="14d59-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="14d59-145">Отображение quad глазах у пользователя поверх сцены и проецировать, низкое разрешение подготавливает к просмотру.</span><span class="sxs-lookup"><span data-stu-id="14d59-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="14d59-146">Результат: visual сочетание элементов высокого разрешения с помощью данных на томе с низким разрешением, но с высокой плотностью.</span><span class="sxs-lookup"><span data-stu-id="14d59-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>
