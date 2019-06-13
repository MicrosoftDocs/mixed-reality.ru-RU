---
title: Может быть найдена камеры
description: Общие сведения о переднюю камеру HoloLens, как это работает и профили и способы их устранения, доступных разработчикам.
author: wguyman
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: камеры, hololens, цвет камеры, обращенные, hololens 2, cv, компьютерного зрения, fiducial, маркеры, QR-код, qr, фото, видео
ms.openlocfilehash: cadcd0762b8adf1001896c614451d2e1c9776c65
ms.sourcegitcommit: 79398a6b5b7037babcb05d86a5bcc336fd089ea0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028610"
---
# <a name="locatable-camera"></a>Может быть найдена камеры

HoloLens включает world камера на передней части устройства, которая позволяет приложениям увидеть, что пользователь видит. Разработчики имеют доступ к и элемент управления камеры, так же, как и для камер цвет телефонах, портативные компьютеры и рабочие столы. Же универсальной платформы windows [записи мультимедиа](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) и API-интерфейсы, которые работают на мобильные и Классические приложения windows media foundation, работать на HoloLens. Unity [произошел эти API-интерфейсы windows](locatable-camera-in-unity.md) для абстрагирования простое использование камеры на HoloLens для задач, таких как создание регулярных фотографии и видео (с или без голограммы) и размещение положение камеры в и перспективы на сцены.

## <a name="device-camera-information"></a>Сведения об устройстве камеры

### <a name="hololens-first-generation"></a>HoloLens (первого)

* Камера фото и видео (PV) основных фокус с автоматически белый баланс, автоматически раскрытия и конвейер обработки полный образ.
* С выходом мира Светодиод конфиденциальности Технический горит всякий раз, когда активен камеры
* Камера поддерживает следующие режимы (все режимы являются соотношение сторон 16:9) на 30, 24, 20, 15 и 5 кадров/с:

  |  Видео  |  Предварительный просмотр  |  По-прежнему  |  Горизонтальное поле of обзора H- |  Предлагается использовать | 
  |----------|----------|----------|----------|----------|
  |  1280 x 720 |  1280 x 720 |  1280 x 720 |  45deg  |  (режим по умолчанию с помощью стабилизации видео) | 
  |  Н/Д |  Н/Д |  2048 x 1152 |  67deg |  По-прежнему изображение высоким разрешением | 
  |  1408 x 792 |  1408 x 792 |  1408 x 792 |  48deg |  Разрешение нерабочей области (заполнение) перед стабилизации видео | 
  |  1344 x 756 |  1344 x 756 |  1344 x 756 |  67deg |  Большие FOV видеорежима с нерабочей области | 
  |  896 x 504 |  896 x 504 |  896 x 504 |  48deg |  Низкие требования к мощности / задачами обработки в режиме с низким разрешением для образа | 

### <a name="hololens-2"></a>HoloLens 2

* Камера фото и видео (PV) автоматически фокус с автоматически белый баланс, автоматически раскрытия и конвейер обработки полный образ.
* Светодиод конфиденциальности белый с выходом мира горит всякий раз, когда активен камеры.
* HoloLens 2 поддерживает профили разных камеры. Узнайте, как [обнаружения и выбора возможностей камеры](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles).
* Камера поддерживает следующие профили и способы их устранения (все видео режимы являются соотношение сторон 16:9):
  
  | Профиль                                         | Видео     | Предварительный просмотр   | По-прежнему     | Частота кадров | Горизонтальное поле of обзора H- | Предлагается использовать                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Для прежних версий, 0 BalancedVideoAndPhoto, 100             | 2272 x 1278 | 2272 x 1278 |           | 15,30       | 64.69                            | Запись видео высокого качества                |
  | Для прежних версий, 0 BalancedVideoAndPhoto, 100             |           |           | 3904 x 2196 |             | 64.69                            | Высокое качество фотосъемки                  |
  | BalancedVideoAndPhoto, 120                       | 1952 x 1100 | 1952 x 1100 | 1952 x 1100 | 15,30       | 64.69                            | Долгая длительность сценариев                     |
  | BalancedVideoAndPhoto, 120                       | 1504 x 846  | 1504 x 846  |           | 15,30       | 64.69                            | Долгая длительность сценариев                     |
  | Видеоконференций, 100                           | 1952 x 1100 | 1952 x 1100 | 1952 x 1100 | 15,30,60    | 64.69                            | Видеоконференции, длительные сценариев |
  | Видеоконференций, 100                           | 1504 x 846  | 1504 x 846  |           | 5,15,30,60  | 64.69                            | Видеоконференции, длительные сценариев |
  | Устанавливаемая 100 BalancedVideoAndPhoto 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | Видеоконференции, длительные сценариев |
  | Устанавливаемая 100 BalancedVideoAndPhoto 120 | 1280 x 720  | 1280 x 720  | 1280 x 720  | 15,30       | 64.69                            | Видеоконференции, длительные сценариев |
  | Устанавливаемая 100 BalancedVideoAndPhoto 120 | 1128 x 635  |           |           | 15,30       | 64.69                            | Видеоконференции, длительные сценариев |
  | Устанавливаемая 100 BalancedVideoAndPhoto 120 | 960x540   |           |           | 15,30       | 64.69                            | Видеоконференции, длительные сценариев |
  | Устанавливаемая 100 BalancedVideoAndPhoto 120 | 760 x 428   |           |           | 15,30       | 64.69                            | Видеоконференции, длительные сценариев |
  | Устанавливаемая 100 BalancedVideoAndPhoto 120 | 640 x 360   |           |           | 15,30       | 64.69                            | Видеоконференции, длительные сценариев |
  | Устанавливаемая 100 BalancedVideoAndPhoto 120 | 500 x 282   |           |           | 15,30       | 64.69                            | Видеоконференции, длительные сценариев |
  | Устанавливаемая 100 BalancedVideoAndPhoto 120 | 424 x 240 пикселей   |           |           | 15,30       | 64.69                            | Видеоконференции, длительные сценариев |

>[!NOTE]
>Клиенты могут использовать [смешанный захвата реальности](mixed-reality-capture.md) видео или фотографии вашего приложения, которые включают голограммы и стабилизации видео.
>
>Как разработчик существуют рекомендации, которые следует учитывать при создании приложения, если будет выглядеть как можно лучше, когда клиент получает содержимое. Можно также включить (и настройка) записи смешанной реальности из непосредственно в приложении. Подробнее см. на [смешанный реальности записи для разработчиков](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Поиск камеры устройства в мире

Когда HoloLens длится фотографии и видео, записанные кадры включать местоположение камеры в мире, а также перспективной проекции камеры. Это позволяет приложениям делать выводы о позиции камеры в реальном мире расширенные сценарии работы с образами. Разработчики творчески можно выполнить откат собственные сценарии, с использованием их обработка избранные изображений или библиотеки компьютерного зрения пользовательского компьютера.

«Камера» в документации по HoloLens может относиться к «виртуальный игр камеры» (пирамиды обзора приложения выполняет визуализацию). Если не обозначается в противном случае, «камера» на этой странице относится к реальных камеры цвета RGB.

Сведения об этом титульной страницы [Media Foundation атрибуты](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx), однако существует также API-интерфейсы для извлечения с помощью встроенных функций камеры [API-интерфейсы WinRT](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics).  

### <a name="images-with-coordinate-systems"></a>Образы с помощью системы координат

Каждого кадра изображения (ли фото или видео) включает в себя в системе координат, а также две важные преобразования. «view» преобразование схемы из предоставленного системы координат к камере и карт «проекция» от камеры в пиксели на рисунке. Вместе эти преобразования определяют для каждого пикселя луча в трехмерном пространстве, представляющий путь, по photons, которые вызвали пикселя. Эти лучи могут быть связаны с другого содержимого в приложении, получая преобразование из системы координат рамки для некоторых других системы координат (например, из [стационарной системой отсчета координат](coordinate-systems.md#stationary-frame-of-reference)). Таким образом, каждый кадр образа предоставляет следующие возможности.
* Данные о пикселях (в формате RGB и NV12/JPEG и т.д.)
* 3 части метаданных (хранятся в виде [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)), позволяющие каждого кадра «может быть найдена»:

|  Имя атрибута  |  Тип  |  Код GUID  |  Описание | 
|----------|----------|----------|----------|
|  MFSampleExtension_Spatial_CameraCoordinateSystem  |  IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))  |  {9D13C82F-2199-4E67-91CD-D1A4181F2534}  |  Магазины [системы координат](coordinate-systems-in-directx.md) из захваченного кадра | 
|  MFSampleExtension_Spatial_CameraViewTransform  |  BLOB-объектов ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {4E251FA4-830F-4770-859A-4B8D99AA809B}  |  Сохраняет преобразование внешние камеры в системе координат | 
|  MFSampleExtension_Spatial_CameraProjectionTransform  |  BLOB-объектов ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {47F9FCB5-2A02-4F26-A477-792FDF95886A}  |  Сохраняет преобразование проекции камеры | 

Преобразование проекции представляет внутренние свойства (фокусное, центр проекции, наклон) из группы связанных элементов, на изображении, начиная от -1 до + 1 по оси X и Y.

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

Различные приложения будет иметь разные системы координат. Ниже приведен обзор потока для поиска точки камеры для одного приложения:

![Преобразований, применяемых к камере систем координат](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a>Камера, определяемый приложением систему координат

Чтобы перейти из «CameraView» и «CameraCoordinateSystem» вашего приложения/мировая система координат, вам потребуется следующее:

[Может быть найдена камеры в Unity](locatable-camera-in-unity.md): CameraToWorldMatrix автоматически предоставляется классом PhotoCaptureFrame (поэтому не нужно беспокоиться о преобразованиях CameraCoordinateSystem).

[Может быть найдена камеры в DirectX](locatable-camera-in-directx.md): Показывает довольно простой способ запроса для преобразования между системой координат камеры и coordinate system(s) собственные приложения.

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a>Определяемый приложением системы координат в координаты в пикселях

Предположим, что вы хотите найти или рисования в определенном месте 3d на образе камеры:

Преобразования представления и проекции, во время матрицы 4 x 4, должны использоваться немного по-разному. А именно, после выполнения проекции, один будет «нормализации, w», это дополнительное действие в проекции имитирует нескольких разных местах 3d может оказаться как двумерный место на экране (т. е. ничего вдоль луча определенных будут отображаться на одной точки). Поэтому ключевые моменты (в коде шейдера):

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a>Пикселя, определяемый приложением систему координат

Переход от точки в мировых координатах несколько сложнее:

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

Мы определим UnProject как:

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

Чтобы найти расположение фактического world точки, необходим, один из следующих: два world лучи и найти их пересечения или известный размер точки.

### <a name="distortion-error"></a>Ошибка искажений

На HoloLens, видео и по-прежнему потоки образа, неискаженных в конвейере обработки образ системы перед выполнением кадров, доступными для приложения (поток предварительного просмотра содержит исходное искаженные кадров). Поскольку предоставляется только матрица проекции, должны предполагать, что представляют собой изображение кадры идеальной pinhole камеры, тем undistortion работают в обработчике изображений может по-прежнему ошибку до 10 точек при использовании матрица проекции в метаданные кадра. Во многих вариантов использования, эта ошибка будет не имеет значения, но если выравнивание голограммы плакаты реальном мире/маркеры, например, и вы Обратите внимание, что < 10px смещения (примерно 11 мм для голограммы расположен сейчас 2 м) этот искажение ошибки может стать причиной.

## <a name="locatable-camera-usage-scenarios"></a>Сценарии использования может быть найдена камеры

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Показать фотографии или видео в мире, где оно было записано

Кадры камеры устройства поставляются с преобразования «Камеры для World», который может использоваться для отображения, где устройство конкретно при было получено изображение. Для примера небольшой значок holographic можно разместить в этом расположении (CameraToWorld.MultiplyPoint(Vector3.zero)) и даже draw небольшой стрелки в направлении, что камера была с выходом (CameraToWorld.MultiplyVector(Vector3.forward)).

### <a name="painting-the-world-using-a-camera-shader"></a>Рисование мира с помощью камеры шейдера

В этом разделе мы создадим материал «шейдера», цвета, всему миру зависимости от того, где оно отобразилось в представлении камеры устройства. Фактически мы сделаем заключается в каждой вершины найдет его расположение относительно камеры, а затем каждый пиксел будет использовать «матрица проекции» рис out, который изображения текселя, она будет связана с. Наконец и при необходимости мы будем Исчезание углы изображение, чтобы оно выглядело больше памяти по принципу мечты:

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

### <a name="tag--pattern--poster--object-tracking"></a>Тег / Pattern / плакат / отслеживание объектов

Во многих приложениях смешанной реальности использовать распознаваемый изображение или шаблон visual для создания точки отслеживается в пространстве. Затем используется для отрисовки объектов относительно их, выберите или создайте известном расположении. Некоторые варианты применения HoloLens: поиск объекта реального мира, помечены fiducials (например монитор TV с QR-кода), помещая голограммы на fiducials и визуально выполнить связывание с устройств не HoloLens, таких как планшеты, которые были установки для взаимодействия с HoloLens через Wi-Fi.

Для распознавания шаблон visual, а затем поместите этого объекта в абсолютном пространстве приложения, вам потребуется следующее:
1. Образ шаблона распознавания набор средств, например QR-код, AR тегов, поиска лиц, средства отслеживания круг, распознавание текста и т.д.
2. Собирать изображений на кадрах во время выполнения и передавать их на уровне распознавания
3. Unproject их расположение образа обратно в мире позиций или лучи скорее всего мира. Скрипт, который поможет полностью удалить все из конфигурации дисковых пространств, см. в разделе
4. Поместите виртуальный моделей на эти расположения world

Некоторые важные образа обработки ссылки:
* [OpenCV](http://opencv.org/)
* [QR-теги](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Сохранение интерактивное приложение частоты кадров важно, особенно при работе с алгоритмы распознавания изображений выполняющейся длительное время. По этой причине мы обычно используем следующий шаблон:
1. Основной поток: управляет объектом камеры
2. Основной поток: запрашивает новый кадров (асинхронный)
3. Основной поток: передайте новые кадры для отслеживания потока
4. Поток отслеживания: обрабатывает изображения для сбора ключевые моменты
5. Основной поток: Перемещает виртуальная модель в соответствии с найден ключевые моменты
6. Основной поток: повторите шаг 2

В некоторых системах маркера изображения только указать расположение один пиксель (другие предоставляют полный преобразование в этом случае не будут нужны в этом разделе), которое соответствует луча возможных расположений. Чтобы получить в одном месте 3d мы затем можно использовать несколько лучи и найти конечный результат, их приблизительное пересечение. Для этого вам потребуется:
1. Получить цикл начинается сбор нескольких изображений с камеры
2. Найти [связанных функциональных точек](#pixel-to-application-specified-coordinate-system)и их мир лучами
3. При наличии словарь функций, каждая из которых несколько лучи world, можно использовать следующий код для решения на пересечении этих лучи:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

Учитывая два или несколько отслеживаемых тег расположения, можно расположить modelled сцены в соответствии со сценарием текущего пользователей. Если нельзя рассчитывать на гравитации, затем нужно будет три тега места. Во многих случаях мы используем простой цветовой схемы, где белый сферы представляют в реальном времени отслеживаются тег расположения и синий сферы представляют смоделировать тег расположения, позволяет пользователю визуально оценить качество выравнивания. Во всех приложениях предполагается следующее:
* Два или несколько расположений смоделировать тега
* Один «калибровки место», который является родительским для объекта теги в сцене
* Идентификатор функции камеры
* Поведение, которое перемещает пространство калибровки для выравнивания modelled теги с тегами в режиме реального времени (мы осторожность, чтобы переместить пространство для родительского, не modelled маркеров, так как другие connect положения относительно их).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="render-holograms-from-the-cameras-position"></a>Визуализации голограммы начиная с позиции камеры

Примечание. Если вы пытаетесь создать свой собственный [смешанный захвата реальности (MRC)](mixed-reality-capture.md), который объединяет голограммы с потоком камеры, можно использовать [эффекты MRC](mixed-reality-capture-for-developers.md) или включить свойство showHolograms в [ Может быть найдена камеры в Unity](locatable-camera-in-unity.md).

Если вы хотите сделать специальные рендеринга непосредственно в потоке RGB камеры, существует возможность отображения голограммы в место, начиная с позиции камеры в соответствии с веб-канал видео чтобы предоставить возможность просмотра и динамические записи пользовательских голограмма.

В Скайп это делается для отображения удаленного клиента, что видит пользователь HoloLens и позволяют им взаимодействовать с тем же голограммы. Перед отправкой по каждого кадра через службу Скайп, мы получаем данные соответствующего камеры каждого кадра. Мы затем камеры внешних и внутренних метаданных видеокадра и затем отправить его через службу Скайп.

На принимающей стороне с помощью Unity, мы уже синхронизированы все голограммы в пространстве пользователя HoloLens, с помощью той же системе координат. Это позволяет нам используйте камеры внешних метаданных для размещения Unity камеры в шифрованию в мире (по отношению к остальной части голограммы), пользователь HoloLens репутацию, при этом видео кадра и использовать встроенные данные камеры для Убедитесь, что представление одинаков.

После правильной установки камеры, мы соберем какие голограммы камеры видит на рамки, которую мы получили от Скайп, создание представления, HoloLens пользователь видит при использовании Graphics.Blit смешанной реальности.

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Отслеживание или определить тегами стационарным или перемещения реальных объектов/лица с помощью светодиодных индикаторов или другие библиотеки распознаватель

Примеры
* Промышленный роботов с помощью светодиодных индикаторов (или QR-коды для медленнее перемещение объектов)
* Определение и распознавание объектов в комнате
* Определение и распознавание людей в комнате (например место holographic карточек контактов через лиц)

## <a name="see-also"></a>См. также
* [Камера с определяемым местоположением в DirectX](locatable-camera-in-directx.md)
* [Камера с определяемым местоположением в Unity](locatable-camera-in-unity.md)
* [Съемка смешанной реальности](mixed-reality-capture.md)
* [Съемка смешанной реальности для разработчиков](mixed-reality-capture-for-developers.md)
* [Общие сведения о записи мультимедиа](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
