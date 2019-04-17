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
# <a name="volume-rendering"></a>Тома отрисовки

Медицинские MRI или проектирование тома, см. в разделе [тома, Подготовка к просмотру в Википедии](https://en.wikipedia.org/wiki/Volume_rendering). Эти объемные образы содержат ценные сведения с прозрачность и цвет на протяжении всего тома, который не может быть выражен легко как поверхности такие как [кусочно-линейной сеток](https://en.wikipedia.org/wiki/Polygon_mesh).

Ключевые решения для повышения производительности
1. НЕПРАВИЛЬНЫЙ: Наивный подход: Показать всего тома, обычно работает слишком медленно
2. ХОРОШИЙ: На переднем плоскости: Показать только один срез тома
3. ХОРОШИЙ: На переднем вложенных том: Отображение только несколько слоев тома
4. ХОРОШИЙ: Уменьшите разрешение отображения тома (см. в разделе «Отрисовка сцен смешанной разрешение»)

Есть только определенный объем информации, которая может передаваться из приложения на экране в любой определенный кадр, это пропускная способность общего объема памяти. Также любой обработки (или «заливка»), необходимых для преобразования этих данных для представления также требует времени. Таким образом являются основными факторами при выполнении отрисовки тома:
* Ширина экрана * Высота экрана * экрана Count * тома слои на что пиксель = всего Volume образцы кадров
* 1028 * 720 * 2 * 256 = 378961920 (100%) (полный res тома: слишком много выборок в режиме)
* 1028 * 720 * 2 * 1 = 1480320 (0.3% полного) (тонкая срез: 1. пример на пиксель, прошел)
* 1028 * 720 * 2 * 10 = 14803200 (% 3.9 полного) (срез вложенных тома: 10 примеров на пиксель, довольно прошел, ищет 3d)
* 200 * 200 * 2 * 256 = 20480000 (5% от полной) (понизить res тома: меньшее количество пикселей, всего тома, ищет 3d, но немного blury)

## <a name="representing-3d-textures"></a>Представляющий 3D-текстуры

ЦП:

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

В графическом Процессоре:

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

## <a name="shading-and-gradients"></a>Заливки и градиенты

Как затенение томе, например MRI, для наглядное представление. Основной метод – заставить «интенсивность window» (min и max) необходимость интенсивности в см. в разделе и легко масштабировать в это пространство для просмотра черно-белый интенсивность. «Шкалы цветов» можно затем применяется к значениям в пределах диапазона и хранить как текстуру, таким образом, разные части спектра интенсивность затененную различных цветов:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

Во многих наших приложений, мы сохраняем в наши корпоративные значение необработанные интенсивность и «сегментации индекса» (для сегментирования различных частей, такие как обложки и кости, эти сегменты обычно создаются специалистами в выделенные инструменты). Можно объединить с подходом, выше, чтобы поместить свой цвет или шкалы даже в разных цветов для каждого сегмента индекса:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Создание срезов в шейдере тома

Это отличный первый шаг — создать «среза плоскость», можно перемещаться тома «Фрагментирование», и как проверки значений в каждой точке. Это предполагает, что имеется куб «VolumeSpace», которое представляет, когда том в абсолютном пространстве, который может использоваться в качестве ссылки для размещения точки:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Трассировка тома в шейдеров

Как использовать графический Процессор для выполнения трассировки вложенных тома (проходит несколько voxels глубоких затем слоев данных из резервной копии на передний план):

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

## <a name="whole-volume-rendering"></a>Всего тома отрисовки

Изменение в приведенном выше коде вложенных тома мы получаем:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Отрисовка сцен разрешение смешанных

Как отобразить часть сцены с низким разрешением и поместить его обратно в месте:
1. Настройка двух вне экрана камеры, один для выполнения каждого глаза, который обновления каждого кадра
2. С низким разрешением два целевых объектов отрисовки (предположим, что 200 x 200 каждый), что отображают камеры
3. Настройка квадрант, которое перемещает глазах у пользователя

Каждый кадр:
1. Рисование целевых объектов отрисовки для каждого глаза с низким разрешением (тома данных, ресурсоемкие шейдеры т. д.)
2. Рисования сцены обычно как полным разрешением (сетки, пользовательского интерфейса и т. д.)
3. Отображение quad глазах у пользователя поверх сцены и проецировать, низкое разрешение подготавливает к просмотру.
4. Результат: visual сочетание элементов высокого разрешения с помощью данных на томе с низким разрешением, но с высокой плотностью.
