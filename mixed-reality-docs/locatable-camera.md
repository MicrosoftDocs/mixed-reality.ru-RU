---
title: Камера с определяемым местоположением
description: Общие сведения о передней камере HoloLens, принципах ее работы, а также о профилях и разрешениях, доступных разработчикам.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: Камера, hololens, цветовая камера, лицевая сторона, hololens 2, ОПС, компьютерное зрение, фидуЦиал, маркеры, QR-код, QR-, Фото, видео
ms.openlocfilehash: e158eb2e708164cbd68620f3f46d3039c2eaa730
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216225"
---
# <a name="locatable-camera"></a>Камера с определяемым местоположением

HoloLens включает в себя камеру, подключенную к передней части устройства, что позволяет приложениям видеть, что видит пользователь. У разработчиков есть доступ к камере и управление ей, точно так же, как и для цветных камер на смартфонах, портативных компьютерах или настольных ПК. Те же универсальные функции [захвата мультимедиа Windows Media](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) и Windows Media Foundation, которые работают с мобильными и рабочим столами в HoloLens. Unity [также упаковывает эти API Windows](locatable-camera-in-unity.md) в абстрактное простое использование камеры в HoloLens для таких задач, как обычные фотографии и видеоролики (с голограммами или без них), а также нахождение расположения камеры в и перспективы на сцене.

## <a name="device-camera-information"></a>Сведения о камере устройства

### <a name="hololens-first-generation"></a>HoloLens (первое поколение)

* Фиксированная камера с фокусировкой или видео (ПС) с автобалансом белого, автоматической экспозицией и полным конвейером обработки изображений.
* Белый индикатор конфиденциальности, направленный на мир, будет загораться каждый раз, когда камера активна
* Камера поддерживает следующие режимы (все режимы — 16:9 пропорций) в 30, 24, 20, 15 и 5 кадров/с.

  |  Видео  |  Предварительный просмотр  |  Могут  |  Горизонтальное поле представления (H-фов) |  Предлагаемое использование | 
  |----------|----------|----------|----------|----------|
  |  1280 x 720 |  1280 x 720 |  1280 x 720 |  45deg  |  (режим по умолчанию с видео стабилизации) | 
  |  Недоступно |  Недоступно |  2048x1152 |  67deg |  Изображение с наивысшим разрешением по-прежнему | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  Разрешение перепроверки (заполнения) перед видео стабилизации | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  Крупный фов видеорежим с пересканированием | 
  |  896x504 |  896x504 |  896x504 |  48deg |  Режим низкого разрешения/отключения для задач обработки изображений | 

### <a name="hololens-2"></a>HoloLens 2

* Автоматическое фокусирование фотографии и Видеокамеры (ПС) с автобалансом белого, автоматической экспозицией и полным конвейером обработки изображений.
* Белый индикатор конфиденциальности, направленный на мир, будет освещен всякий раз, когда камера активна.
* HoloLens 2 поддерживает различные профили камеры. Узнайте, как [обнаруживать и выбирать возможности камеры](https://docs.microsoft.com//windows/uwp/audio-video-camera/camera-profiles).
* Камера поддерживает следующие профили и разрешения (все видеорежимы имеют соотношение пропорций 16:9):
  
  | Профиль                                         | Видео     | Предварительный просмотр   | Могут     | Частота кадров | Горизонтальное поле представления (H-фов) | Предлагаемое использование                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Прежние, 0 Баланцедвидеоандфото, 100             | 2272x1278 | 2272x1278 |           | 15, 30       | 64,69                            | Высококачественная запись видео                |
  | Прежние, 0 Баланцедвидеоандфото, 100             | 896x504   | 896x504   |           | 15, 30       | 64,69                            | Предварительный просмотр потока для записи фотографий высокого качества |
  | Прежние, 0 Баланцедвидеоандфото, 100             |           |           | 3904x2196 |             | 64,69                            | Высокое качество записи фотографий                  |
  | Баланцедвидеоандфото, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30       | 64,69                            | Сценарии длительной длительности                     |
  | Баланцедвидеоандфото, 120                       | 1504x846  | 1504x846  |           | 15, 30       | 64,69                            | Сценарии длительной длительности                     |
  | Видеоконференции, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30, 60    | 64,69                            | Видеоконференции, сценарии длительной длительности |
  | Видеоконференции, 100                           | 1504x846  | 1504x846  |           | 5, 15, 30, 60  | 64,69                            | Видеоконференции, сценарии длительной длительности |
  | Видеоконференции, 100 Баланцедвидеоандфото, 120 | 1920 x 1080 | 1920 x 1080 | 1920 x 1080 | 15, 30       | 64,69                            | Видеоконференции, сценарии длительной длительности |
  | Видеоконференции, 100 Баланцедвидеоандфото, 120 | 1280 x 720  | 1280 x 720  | 1280 x 720  | 15, 30       | 64,69                            | Видеоконференции, сценарии длительной длительности |
  | Видеоконференции, 100 Баланцедвидеоандфото, 120 | 1128x636  |           |           | 15, 30       | 64,69                            | Видеоконференции, сценарии длительной длительности |
  | Видеоконференции, 100 Баланцедвидеоандфото, 120 | 960x540   |           |           | 15, 30       | 64,69                            | Видеоконференции, сценарии длительной длительности |
  | Видеоконференции, 100 Баланцедвидеоандфото, 120 | 760x428   |           |           | 15, 30       | 64,69                            | Видеоконференции, сценарии длительной длительности |
  | Видеоконференции, 100 Баланцедвидеоандфото, 120 | 640 x 360   |           |           | 15, 30       | 64,69                            | Видеоконференции, сценарии длительной длительности |
  | Видеоконференции, 100 Баланцедвидеоандфото, 120 | 500x282   |           |           | 15, 30       | 64,69                            | Видеоконференции, сценарии длительной длительности |
  | Видеоконференции, 100 Баланцедвидеоандфото, 120 | 424x240   |           |           | 15, 30       | 64,69                            | Видеоконференции, сценарии длительной длительности |

>[!NOTE]
>Клиенты могут использовать [запись смешанной реальности](mixed-reality-capture.md) , чтобы принимать видео или фотографии приложения, включая голограммы и видео стабилизации.
>
>В качестве разработчика необходимо учитывать вопросы, которые следует учитывать при создании приложения, если вы хотите, чтобы он был как можно более хорошим, когда клиент захватывает содержимое. Вы также можете включить (и настроить) запись смешанной реальности непосредственно в приложении. Узнайте больше о [записи смешанной реальности для разработчиков](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Поиск камеры устройства в мире

Когда HoloLens принимает фотографии и видео, захваченные кадры включают расположение камеры в мире, а также модель линзы камеры. Это позволяет приложениям полагаться на расположение камеры в реальном мире для сценариев дополненных изображений. Разработчики могут творческо разбросить свои сценарии, используя избранные изображения или пользовательские библиотеки компьютерных концепций.

"Камера" в любой части документации по HoloLens может ссылаться на "виртуальная игровая Камера" (фрустум приложение готовится к просмотру). Если не указано иное, "Камера" на этой странице относится к реальной цветовой камере RGB.

### <a name="using-unity"></a>Использование Unity

Чтобы перейти от "Камераинтринсикс" и "Камеракурдинатесистем" к своей системе координат приложения или мира, следуйте инструкциям в статье о [камере размещаемые в Unity](locatable-camera-in-unity.md) .  Камератоворлдматрикс автоматически предоставляется классом Фотокаптурефраме, поэтому вам не нужно беспокоиться о преобразованиях Камеракурдинатесистем, описанных ниже.

### <a name="using-mediaframereference"></a>Использование Медиафрамереференце

Эти инструкции применяются, если вы используете класс [медиафрамереференце](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference) для чтения кадров изображения с камеры.

Каждый кадр изображения (фото или видео) включает в себя [спатиалкурдинатесистем](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) с корнем на камере во время записи, доступ к которому можно получить с помощью свойства [курдинатесистем](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) [медиафрамереференце](https://docs.microsoft.com//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Кроме того, каждый кадр содержит описание модели линзы, которое можно найти в свойстве [камераинтринсикс](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) . Вместе эти преобразования определяются для каждого пикселя в трехмерном пространстве, представляющем путь, взятый фотоны, который создал пиксель. Эти лучи могут быть связаны с другим содержимым в приложении путем получения преобразования из системы координат кадра в другую систему координат (например, из [стационарной рамки ссылки](coordinate-systems.md#stationary-frame-of-reference)). В итоге каждый кадр изображения предоставляет следующие сведения:
* Пиксельные данные (в формате RGB/NV12/JPEG/т. д.)
* [Спатиалкурдинатесистем](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) из расположения записи
* Класс [камераинтринсикс](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) , содержащий режим линзы камеры

[Образец холографикфацетраккинг](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) показывает довольно простой способ запроса преобразования между системой координат камеры и собственными системами координат приложения.

### <a name="using-media-foundation"></a>Использование Media Foundation

Если вы используете Media Foundation непосредственно для чтения кадров изображения с камеры, можно использовать [атрибуты MFSampleExtension_CameraExtrinsics](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-cameraextrinsics) и [MFSampleExtension_PinholeCameraIntrinsics](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) для каждого кадра, чтобы нахождение кадров камеры относительно других систем координат вашего приложения, как показано в следующем примере кода:

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>Ошибка искажения

В HoloLens поток видео и все еще не искажается в конвейере обработки образа системы до того, как фреймы становятся доступными для приложения (в предварительной версии потока содержатся исходные искаженные кадры). Поскольку доступны только Камераинтринсикс, приложения должны предположить, что кадры изображения представляют собой идеальную пинхоле камеру.

В HoloLens (первое поколение) функция undistortия в обработчике изображений может оставить ошибку размером до 10 пикселей при использовании Камераинтринсикс в метаданных кадра. Во многих случаях эта ошибка не имеет значения, но если вы выводите голограммы на реальные плакаты и маркеры, а также заметили <10px смещение (примерно 11mm для голограмм, расположенных на расстоянии 2 метров), эта ошибка может быть вызвана ошибкой искажения. 

## <a name="locatable-camera-usage-scenarios"></a>Сценарии использования камеры размещаемые

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Показывать фотографию или видео в мире, где они были собраны

Кадры камеры устройства поставляются с преобразованием «Камера — мир», которое можно использовать для отображения точного расположения устройства при создании образа. Например, можно разместить небольшой holographic-значок в этом месте (Камератоворлд. Мултиплипоинт (Vector3. Zero)) и даже нарисовать маленькую стрелку в направлении, в котором была направлена камера (Камератоворлд. Мултипливектор (Vector3. Forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Тег/шаблон/Афиша/Отслеживание объектов

Многие приложения смешанной реальности используют распознаваемый образ или визуальный шаблон для создания отслеживающей точки в пространстве. Затем он используется для отрисовки объектов относительно этого момента или для создания известного расположения. Некоторые способы использования HoloLens включают поиск объекта в реальном мире с тегами фидуЦиалс (например, ТВ-монитор с QR-кодом), размещение голограмм на фидуЦиалс и визуальное связывание с устройствами, не являющимися HoloLens, такими как планшеты, настроенные для обмена данными с HoloLens через Wi-Fi.

Чтобы распознать визуальный шаблон, а затем поместить этот объект в мировое пространство приложений, потребуется выполнить несколько действий:
1. Набор средств для распознавания шаблона изображения, например QR-код, Теги AR, поиск лиц, круговые инспекторы, распознавание текста и т. д.
2. Собирать кадры изображения во время выполнения и передавать их на уровень распознавания
3. Отменяйте свои расположения образов обратно в мировые положения или, вероятнее всего, в разных регионах. 
4. Размещение виртуальных моделей в этих местах мира

Некоторые важные ссылки для обработки изображений:
* [OpenCV](https://opencv.org/)
* [Теги QR](https://en.wikipedia.org/wiki/QR_code)
* [фацесдк](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Поддержание интерактивной частоты кадров приложений очень важна, особенно при работе с долгосрочными алгоритмами распознавания изображений. По этой причине мы обычно используем следующий шаблон:
1. Основной поток: управляет объектом Camera
2. Основной поток: запрашивает новые кадры (асинхронно)
3. Основной поток: передача новых кадров в отслеживаемый поток
4. Поток отслеживания: обрабатывает изображение для сбора ключевых точек
5. Основной поток: перемещение виртуальной модели в соответствие найденных ключевых точек
6. Основной поток: повторение из шага 2

Некоторые системы меток изображений обеспечивают только одно место в пикселях (другие предоставляют полное преобразование, в котором этот раздел не потребуется), что соответствует лучау возможных расположений. Чтобы получить одно трехмерное расположение, можно использовать несколько лучей и найти окончательный результат по их приблизительному пересечением. Вот как это сделать.
1. Получение цикла, который собирает несколько изображений с камеры
2. Найдите связанные точки компонентов и их лучи мира
3. Если у вас есть словарь функций, каждый из которых имеет несколько мировых индексов, можно использовать следующий код для решения пересечения этих лучей:

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

Учитывая два или более расположений отслеживаний тегов, можно разместить смоделированную сцену в соответствии с текущим сценарием пользователя. Если вы не можете предположить сила притяжения, вам потребуется три расположения тегов. Во многих случаях мы используем простую цветовую схему, где белый шарик представляет расположение тегов, отслеживающихся в реальном времени, а синий шарик — расположение тегов в модели. Это позволяет пользователю визуально оценить качество выравнивания. Мы предполагаем, что во всех наших приложениях выполняется следующая настройка:
* Два или более расположений тегов в модели
* Одна область калибровки, которая в сцене является родителем тегов
* Идентификатор компонента камеры
* Поведение, которое перемещает пространство калибровки для согласования тегов, заключенных в модели, с тегами в реальном времени (мы осторожно перейдем к родительскому пространству, а не к самим маркерам, так как другие соединения являются позициями, связанными с ними).

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

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Отслеживать или выявлять стационарные или переносить реальные объекты и лица с помощью индикаторов или других библиотек распознавателей;

Примеры
* Промышленные роботы с индикаторами (или QR-коды для более медленных движущихся объектов)
* Определение и распознавание объектов в комнате
* Определение и распознавание людей в комнате (например, помещайте с помощью карточек контактных лиц)

## <a name="see-also"></a>См. также
* [Пример камеры размещаемые](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Камера с определяемым местоположением в Unity](locatable-camera-in-unity.md)
* [Запись смешанной реальности](mixed-reality-capture.md)
* [Съемка смешанной реальности для разработчиков](mixed-reality-capture-for-developers.md)
* [Введение в запись носителя](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Пример отслеживания с "holographic лиц"](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
