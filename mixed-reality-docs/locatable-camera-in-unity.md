---
title: Может быть найдена камеры в Unity
description: Использование может быть найдена камеры HoloLens в Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: фото, видео, hololens, камеры, unity, может быть найдена
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601769"
---
# <a name="locatable-camera-in-unity"></a>Может быть найдена камеры в Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Включение возможности для видеокамера фото

Функция «Веб-камера» должен быть объявлен для приложения для использования [камеры](locatable-camera.md).
1. В редакторе Unity, перейдите к параметрам проигрывателя, перейдя на страницу «Изменить > проекта Параметры > Player»
2. Перейдите на вкладку «Windows Store»
3. В разделе «Возможности публикации > Параметры» установите флажок **веб-камера** и **"микрофон"** возможности

Одновременно с камеры могут возникнуть только одну операцию. Чтобы определить, какой режим (фото, видео или none) камеры в данный момент, можно проверить UnityEngine.XR.WSA.WebCam.Mode.

## <a name="photo-capture"></a>Фотосъемки

**Пространство имен:** *UnityEngine.XR.WSA.WebCam*<br>
**Тип:** *PhotoCapture*

*PhotoCapture* типа позволяет по-прежнему воспользоваться фотографии с видеокамеры фотографии. Общий шаблон с помощью *PhotoCapture* чтобы сделать фотографию выглядит следующим образом:
1. Создание *PhotoCapture* объекта
2. Создание *CameraParameters* с параметрами, мы хотим
3. Перейти в режим фотографий с помощью *StartPhotoModeAsync*
4. Сделать нужные фото
    * (необязательно) Взаимодействовать с изображения
5. Выход из режима фотографии и очистка ресурсов

### <a name="common-set-up-for-photocapture"></a>Общие настройки для PhotoCapture

Для всех трех целей мы начнем с тем же сначала 3 описанные выше действия

Мы начнем с создания *PhotoCapture* объекта

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

Далее мы хранения нашего объекта, значение списка параметров и Photo режим запуска

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

В конце концов мы также применяются те же очистки здесь код

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

После выполнения этих шагов можно выбрать тип фотографии для записи.

### <a name="capture-a-photo-to-a-file"></a>Захват фото в файл

Самый простой операции — извлечение фотографии непосредственно в файл. Фотографии могут сохраняться как JPG или PNG.

Если мы успешно запущен режим фотографий, мы теперь будет сделать фотографию и сохранять их на диске

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

После сохранения фотографий на диск, мы выйти из режима фотографии и затем выполнить очистку объектов

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a>Записать фотографию, чтобы Texture2D

При записи данных Texture2D, процесс аналогичен чрезвычайно записи на диск.

Мы будем следовать выше процесс установки.

В *OnPhotoModeStarted*, мы будет захвата кадра в память.

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

Затем мы наш результат применения к текстуре и использоваться общие очистки приведенный выше код.

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Захват фото и взаимодействие с необработанными байтами

Для взаимодействия с необработанные байты обработки в памяти кадра, мы будем следовать те же самые действия, что и выше и *OnPhotoModeStarted* как захват фотографию, чтобы Texture2D. Различие заключается в *OnCapturedPhotoToMemory* где мы можем получать необработанные байты и взаимодействовать с ними.

В этом примере мы создадим *списка<Color>*  которого может быть дополнительно обработаны или применить к текстуры с помощью *SetPixels()*

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a>Видеозаписи

**Пространство имен:** *UnityEngine.XR.WSA.WebCam*<br>
**Тип:** *VideoCapture*

*VideoCapture* функции, подобные очень *PhotoCapture*. Только два различия, что необходимо указать значение кадры на второй (кадров/с), и можно сохранить только непосредственно на диск как MP4-файл. Указания по использованию *VideoCapture* таковы:
1. Создание *VideoCapture* объекта
2. Создание *CameraParameters* с параметрами, мы хотим
3. Запуск видеорежима через *StartVideoModeAsync*
4. Начать запись видео
5. Остановить запись видео
6. Выход из режима видео и очистка ресурсов

Мы начнем с создания нашей *VideoCapture* объект *VideoCapture m_VideoCapture = null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

Мы затем настроим параметры, которые нам потребуются средства для записи и запуска.

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

После запуска, мы начнем с записи

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

После запуска записи удалось обновить пользовательский Интерфейс или поведения, чтобы включить остановки. Здесь мы просто в журнал

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

В дальнейшем необходимо остановить запись. Это может произойти с таймером или пользовательского ввода, для экземпляра.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

После остановки записи нужно будет остановить видеорежима и очистить наши ресурсы.

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a>Устранение неполадок
* Никаких действий не доступны.
    * Убедитесь, **веб-камера** возможности, указанные в проекте.

## <a name="see-also"></a>См. также
* [Может быть найдена камеры](locatable-camera.md)
