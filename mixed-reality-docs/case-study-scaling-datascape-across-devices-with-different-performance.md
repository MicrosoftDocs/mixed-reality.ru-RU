---
title: Пример использования. масштабирование Датаскапе на разных устройствах с различной производительностью
description: В этом практическом примере представлено представление о том, как разработчики Майкрософт оптимизируют приложение Датаскапе, чтобы обеспечить привлекательную работу на устройствах с различными возможностями повышения производительности.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: иммерсивное головной телефон, оптимизация производительности, VR, пример использования
ms.openlocfilehash: 05f97188c81d85685540be998111ecfc47d9ef9c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436503"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Пример использования. масштабирование Датаскапе на разных устройствах с различной производительностью

Датаскапе — это приложение Windows Mixed Reality, разработанное внутри корпорации Майкрософт, где мы сосредоточены на отображении данных о погоде на основе данных ландшафта. Приложение исследует уникальную информацию, которую получают пользователи при обнаружении данных в смешанной реальности, отключив пользователя к визуализации данных с помощью Holographic.

Для Датаскапе мы хотели ориентироваться на различные платформы с различными аппаратными возможностями, от Microsoft HoloLens до впечатляющих головных телефонов Windows Mixed Reality, а также от компьютеров с более низким потреблением до самых современных ПК с высокопроизводительным графическим процессором. Основная задача — это визуализация сцены в визуально привлекательном масштабе на устройствах с различными графическими возможностями при выполнении с высокой частотой кадров.

В этом практическом примере рассматривается процесс и методы, используемые для создания некоторых дополнительных систем с большим числом GPU, описание возникших проблем и способ их преодолел все испытания.

## <a name="transparency-and-overdraw"></a>Прозрачность и перерисовка

В нашей основной визуализации возникают проблемы с прозрачностью, так как прозрачность может быть дорогостоящей на GPU.

Сплошная геометрия может быть подготовлена к просмотру спереди на задний план во время записи в буфер глубины, при этом все будущие Пиксели, расположенные за этой точкой, удаляются. Это предотвращает выполнение построителя текстуры скрытыми пикселями, что значительно ускоряет процесс. Если геометрия упорядочена оптимально, каждый пиксель на экране будет нарисован только один раз.

Прозрачная геометрия должна быть отсортирована на передний план и полагается на смешение выходных данных шейдера пикселей к текущему пикселю на экране. Это может привести к тому, что каждый пиксель на экране рисуется на несколько раз в кадре, что называется перерисовкой.

Для HoloLens и основных ПК Этот экран можно заполнять лишь несколько раз, что делает прозрачную визуализацию проблематичной.

## <a name="introduction-to-datascape-scene-components"></a>Общие сведения о компонентах сцены Датаскапе

Мы имели три основных компонента для нашей сцены. **Пользовательский интерфейс, схема**и **Погода**. Мы знали, что наши эффекты погоды потребовали бы всего времени GPU, поэтому мы намеренно разработали пользовательский интерфейс и ландшафта таким образом, чтобы сократить все перерисовки.

Мы несколько раз переработали пользовательский интерфейс, чтобы максимально сокращать объем перерисовок. Мы выдвигают на стороне более сложной геометрии, а не наложение прозрачной картинки поверх других для таких компонентов, как светящиеся кнопки и обзоры карт.

Для Map мы использовали пользовательский шейдер, который бы мог выделять стандартные функции Unity, такие как тени и сложное освещение, заменяя их простой моделью освещения Sun и пользовательским вычислением тумана. Это создавало простой шейдер пикселей и освобождать циклы GPU.

Мы управляем, чтобы получить пользовательский интерфейс и карту для отрисовки в бюджете, где в зависимости от оборудования не требуется вносить изменения. Однако визуализация погоды, в частности, в облачной отрисовке, выстала более сложной задачей.

## <a name="background-on-cloud-data"></a>Общие сведения о облачных данных

Наши облачные данные были скачаны с серверов NOAA (https://nomads.ncep.noaa.gov/) и пришли в нас на трех разных 2D-слоях, каждая из которых имеет верхнюю и нижнюю высоту облака, а также плотность облака для каждой ячейки сетки. Данные обрабатывались в текстуру облачных сведений, где каждый компонент хранился в красном, зеленом и синем компоненте текстуры для удобного доступа к GPU.

## <a name="geometry-clouds"></a>Геометрические облака

Чтобы убедиться, что наши компьютеры могут визуализировать наши облака, мы решили начать с подхода, который будет использовать сплошную геометрию для уменьшения перерисовки.

Сначала мы попытались создавать облака, создавая сплошную хеигхтмапную сетку для каждого слоя, используя радиус текстуры облачной информации на вершину для создания фигуры. Мы использовали шейдер Geometry для создания вершин как в верхней, так и в нижней части облака, создающей сплошные облачные фигуры. Мы использовали значение плотности от текстуры, чтобы окрасить облако с более темными цветами для более сжатых облаков.

**Шейдер для создания вершин:**

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

Мы предоставили небольшой шаблон шума для получения более подробных сведений о реальных данных. Чтобы создать скругленные края облака, мы обрезаем пикселов в шейдере пикселей, когда значение радиуса интерполяции достигает порогового значения, чтобы отбросить почти нулевые значения.

![Геометрические облака](images/datascape-geometry-clouds-700px.jpg)

Так как облака являются сплошной геометрией, они могут быть отображены до того, как ландшафта скрывает все дорогостоящие Пиксели карт под для дальнейшего улучшения частоты кадров. Это решение хорошо работает на всех графических картах от min-Spec до высокопроизводительных графических карт, а также на HoloLens, из-за подхода к отрисовке геометрического объекта Geometry.

## <a name="solid-particle-clouds"></a>Сплошные облака частиц

Теперь у нас есть решение для резервного копирования, которое создало личное представление наших облачных данных, но было немного лакклустер в отношении "WOW" и не передавало объемные, что требовалось для наших высокопроизводительных компьютеров.

Следующий шаг — создание облаков, представляющих их приблизительно 100 000 частиц для создания более согласованного и объемныеного вида.

Если частицы остаются сплошными и сортируются от начала до конца, мы по-прежнему можем получить преимущество от использования отбора в буфере глубины пикселов за ранее визуализированными частицами, уменьшая перерисовку. Кроме того, с помощью решения на основе примитивов можно изменить объем частиц, используемый для другого оборудования. Тем не менее все пикселы по-прежнему нуждаются в тщательном тестировании, что приводит к дополнительным издержкам.

Во первых, мы создали положение примитивов вокруг центральной точки опыта при запуске. Мы намерены выровнять частицы по центру и уменьшить это расстояние. Мы заранее отсортировани все частицы от центра к обратной стороне, чтобы сначала отображались ближайшие частицы.

При использовании шейдера вычислений в качестве текстуры облачной информации будет размещаться правильная высота и цвет на основе плотности.

Мы использовали *дравпроцедурал* , чтобы визуализировать четыре отдельных примитива, что позволяет постоянно оставаться на GPU.

Каждая часть содержит как высоту, так и радиус. Высота была основана на облачных данных, выборке из текстуры облачной информации, а радиус был основан на первоначальном распределении, где будет рассчитываться горизонтальное расстояние до ближайшего соседнего. Эти данные будут использоваться для ориентации самого себя на высоту, так что когда пользователи просматривает их по горизонтали, отображается высота, и когда пользователи рассмотрели его сверху вниз, будет охвачена область между соседними сторонами.

![Фигурная часть](images/particle-shape-700px.png)

**Код шейдера, иллюстрирующий распределение:**

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

Так как мы сортирует частицы спереди на задний план и по-прежнему использовали сплошной шейдер стиля для обрезки (не Blend) прозрачных пикселов, этот метод обрабатывает неудивительное количество частиц, избегая дорогостоящего нарисовать даже на компьютерах с более низким энергопотреблением.

## <a name="transparent-particle-clouds"></a>Прозрачные облака частиц

Твердая частица предоставляла представление об облаках, но по-прежнему требовалось что-нибудь для продажи флуффинесс облаков. Мы решили испытать пользовательское решение для высококачественных графических плат, в которых можно реализовать прозрачность.

Для этого мы просто переключили первоначальный порядок сортировки частиц и изменили шейдер для использования альфа-текстуры.

![Облака Пушок](images/fluffy-clouds-700px.jpg)

Он выглядит замечательно, но оказался слишком большим для даже самых требовательных компьютеров, так как это приведет к отрисовке каждого пикселя на экране сотни раз!

## <a name="render-off-screen-with-lower-resolution"></a>Отображение за пределами экрана с низким разрешением

Чтобы уменьшить количество пикселей, отображаемых облаками, мы начали отображать их в буфере разрешения квартала (по сравнению с экраном) и растягивать конечный результат на экран после отрисовки всех частиц. Это позволило нам примерно 4X, но в комплекте с несколькими предостережениями.

**Код для отображения на экране:**

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

Во-первых, при отрисовке в буфер вне экрана мы потеряли всю информацию о глубине из нашей основной сцены, что привело к горы отрисовки поверх Mountain.

Во вторых, при растяжении буфера также появились артефакты на краях наших облаков, где изменение разрешения было заметным. В следующих двух разделах рассказывается о том, как мы разрешили эти проблемы.

## <a name="particle-depth-buffer"></a>Буфер глубины частицы

Чтобы сделать частицу сосуществование с мировой геометрией, где Mountain или объект может охватить частицы за ним, мы заполнили буфер экрана с буфером глубины, содержащим геометрию основной сцены. Чтобы создать такой буфер глубины, мы создали вторую камеру, выполняя визуализацию только сплошной геометрии и глубины сцены.

Затем мы использовали новую текстуру в шейдере пикселей для облаков, чтобы окклуде Пиксели. Мы использовали ту же текстуру, чтобы вычислить расстояние до геометрического пикселя в облаке. Используя это расстояние и применяя его к альфа-каналу пикселя, мы приходили уменьшить воздействие облаков по мере того, как они близки к ландшафта, устраняя при этом все жесткие вырезаниеи, где частицы и ландшафта встречаются.

![Облака, накладываемые на ландшафта](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Увеличение резкости краев

Растянутые облачные облака были почти идентичны облакам нормального размера в центре частиц или в том месте, где они перекрываются, но показали некоторые артефакты на краях облака. В противном случае четкие края будут выглядеть размытыми, а при перемещении камеры были введены эффекты псевдонима.

Мы разрешили это, выполнив простой шейдер в буфере экрана, чтобы определить, где произошло большое изменение (1). Мы помещаем пикселы с большими изменениями в новый буфер шаблона (2). Затем мы использовали буфер трафарета для маскирования этих областей с высокой контрастностью при применении обратного буфера к экрану, что приводит к пропускам в и вокруг облаков (3).

Затем все части снова визуализируются в полноэкранном режиме, но в этот раз использовался буфер шаблона, чтобы маскировать все, кроме краев, что приводит к минимальному набору затронутых пикселей (4). Так как буфер команд уже был создан для частиц, нам просто пришлось снова отобразить его на новой камере.

![Ход отрисовки ребер облака](images/cloud-steps-1-4-700px.jpg)

Конечный результат — это резкие края с дешевыми разделами облаков.

Хотя это было гораздо быстрее, чем визуализация всех частиц в полноэкранном режиме, по-прежнему взимается плата, связанная с тестированием пикселов на соответствие с буфером трафарета, поэтому при большом объеме перерисовки по-прежнему взимается стоимость.

## <a name="culling-particles"></a>Частицы для отбора

Для нашего обратного света мы создали длинные ленты треугольников в шейдере вычислений, создавая множество беспроводных протоколов "Ветер" в мире. В то время как воздействие на обмотку не слишком велико, так как фактамные ленты созданы, то было создано множество сотен тысяч вершин, что привело к высокой нагрузке для шейдера вершин.

Мы представили Добавление буферов в шейдер вычислений для передачи подмножества полос обмотки для рисования. Используя простую логику фрустум представлений в шейдере вычислений, можно определить, находится ли полоска вне представления камеры и не допустить ее добавления в буфер push-уведомлений. Это значительно сокращает количество полос, освобождая некоторые необходимые циклы на GPU.

**Код, демонстрирующий буфер добавления:**

*Вычисление шейдера:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#приведен*

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

Мы попытались использовать ту же методику в частях облака, где мы бы выдавали их в шейдере вычислений и относимся к визуализации только видимым частицам. Эта методика на самом деле не позволила нам значительно сэкономить GPU, так как крупнейший узким местом был объем отображаемых на экране пикселей, а не затраты на вычисление вершин.

Другая проблема с этим методом заключается в том, что буфер добавления заполнен в случайном порядке из-за его параллелизации в результате вычисления частиц, что приводит к снижению количества элементов облака.

Существуют методы сортировки буфера push-уведомлений, но ограниченный объем выростов производительности, который мы получаем за исключением частиц, скорее всего, будет смещен с дополнительной сортировкой, поэтому мы решили не выполнять эту оптимизацию.

## <a name="adaptive-rendering"></a>Адаптивная визуализация

Для обеспечения постоянной частоты кадров в приложении с различными условиями отрисовки, такими как облако и четкое представление, мы предоставили адаптивную визуализацию для нашего приложения.

Первым шагом адаптивной визуализации является измерение GPU. Мы сделали это, вставив пользовательский код в буфер команд GPU в начале и в конец визуализированного кадра, записывая как левое, так и правильное время на экране глаз.

Измеряя время, затраченное на визуализацию и сравнивая его с требуемой частотой обновления, мы получили представление о том, как близко мы будем удалять кадры.

Когда вы закроете, чтобы удалить кадры, мы адаптировани к отрисовке, чтобы ускорить их выполнение. Одним из простых способов адаптации является изменение размера окна просмотра экрана, требующего отображения меньшего количества пикселей.

С помощью *UnityEngine. XR. ксрсеттингс. рендервиевпортскале* система сжимает целевое окно просмотра и автоматически растягивает результат до размера экрана. Небольшое изменение масштаба очень заметно для мирового геометрического объекта, а коэффициент масштабирования 0,7 требует половину объема отображаемых пикселей.

![70% Scale, половина пикселей](images/datascape-scaling-700px.jpg)

Когда мы определим, что мы будем сбрасывать кадры, мы меньшим масштабом по фиксированному числу, а затем вернемся к этому, когда мы снова выполняем достаточно быстро.

Хотя мы решили, какой облачный метод использовать в зависимости от возможностей графического оборудования при запуске, можно создать его на основе данных из измерения GPU, чтобы система не поддерживала низкое разрешение в течение длительного времени, но это не так давно.  для просмотра в Датаскапе.

## <a name="final-thoughts"></a>Заключительные идеи

Нацеливание на различные аппаратные средства является сложной задачей и требует определенного планирования.

Рекомендуется начать работу с конечными компьютерами, чтобы ознакомиться с проблемным пространством и разработать решение для резервного копирования, которое будет выполняться на всех компьютерах. Разработайте свое решение с учетом скорости заполнения, поскольку пиксели будут самыми ценными. Целевая геометрическая геометрия по прозрачности.

С помощью решения для резервного копирования можно приступить к расширению уровня сложности для высокопроизводительных компьютеров или просто улучшить разрешение резервного копирования.

Разработка для наихудших сценариев и, возможно, рассмотрите возможность адаптивной отрисовки для больших ситуаций.

## <a name="about-the-authors"></a>Об авторах

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Роберт Ферресе</b><br>@Microsoft инженера программного обеспечения</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Андерссон "+ +"</b><br>@Microsoft инженера программного обеспечения</td>
</tr>
</table>


## <a name="see-also"></a>См. также
* [Основные сведения о производительности смешанной реальности](understanding-performance-for-mixed-reality.md)
* [Рекомендации по повышению производительности для Unity](performance-recommendations-for-unity.md)

 
