---
title: Камера размещаемые в Unity
description: Использование камеры HoloLens размещаемые в Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Фото, видео, hololens, Камера, Unity, размещаемые
ms.openlocfilehash: b4a1a7e11a7606dab76b954c8d58a335d6bae0ab
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597617"
---
# <a name="locatable-camera-in-unity"></a>Камера размещаемые в Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Включение возможности для видеокамеры

Для использования [камеры](locatable-camera.md)приложение должно быть объявлено как "веб-камера".
1. В редакторе Unity перейдите к параметрам проигрывателя, перейдя на страницу "Изменение > параметров проекта > Player".
2. Перейдите на вкладку "Магазин Windows".
3. В разделе "Параметры публикации > возможности" Проверьте возможности веб- **камеры** и **микрофона** .

Только одна операция может выполняться с камерой за раз. Чтобы определить, в каком режиме в настоящее время используется камера (Фото, видео или нет), можно проверить UnityEngine. XR. WSA. Camera. Mode.

## <a name="photo-capture"></a>Запись фотографий

**Пространство имен:** *UnityEngine. XR. WSA. веб-камера*<br>
**Тип:** *фотозапись*

Тип *фотосъемки* позволяет вам по-прежнему иметь фотографии фотокамеры. Общий шаблон использования *фотосъемки* для получения фотографий выглядит следующим образом:
1. Создание объекта *Фотозаписи*
2. Создание объекта *камерапараметерс* с нужными параметрами
3. Запуск фоторежима через *стартфотомодеасинк*
4. Взять нужную фотографию
    * используемых Взаимодействие с этим изображением
5. Отключение режима фото и очистка ресурсов

### <a name="common-set-up-for-photocapture"></a>Стандартная настройка для фотозахвата

Для всех трех вариантов использования Начните с тех же самых первых 3 шагов.

Начните с создания объекта *фотосъемки*

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

Затем сохраните объект, задайте параметры и запустите режим фото.

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

В итоге вы также будете использовать тот же код очистки, представленный здесь.

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

После выполнения этих действий можно выбрать тип фотографии для записи.

### <a name="capture-a-photo-to-a-file"></a>Запись фотографии в файл

Самой простой операцией является запись фотографии непосредственно в файл. Фотографию можно сохранить в формате JPG или PNG.

Если вы успешно начали фото-режим, возьмите фотографию и сохраните ее на диске.

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

После записи фотографии на диск выйдите из режима Photo, а затем очистите объекты

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

### <a name="capture-a-photo-to-a-texture2d"></a>Запись фотографии в Texture2D

При записи данных в Texture2D процесс очень похож на запись на диск.

Выполните описанный выше процесс настройки.

В *онфотомодестартед*запишите кадр в память.

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

Затем вы примените результат к текстуре и используйте общий код очистки, приведенный выше.

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Запись фотографии и взаимодействие с необработанными байтами

Чтобы взаимодействовать с необработанными байтами в кадре памяти, выполните те же действия по настройке, что и в предыдущем разделе, и *онфотомодестартед* , как при записи фотографии в Texture2D. Разница заключается в *онкаптуредфототомемори* , где можно получить необработанные байты и взаимодействовать с ними.

В этом примере вы создадите *список<Color>* который можно обработать или применить к текстуре с помощью *сетпикселс ()* .

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

## <a name="video-capture"></a>Видеозапись

**Пространство имен:** *UnityEngine. XR. WSA. веб-камера*<br>
**Тип:** *видеокаптуре*

Функция *видеокаптуре* очень похожа на функцию *фотозахвата*. Единственное отличие заключается в том, что необходимо указать значение кадров в секунду, которое можно сохранить непосредственно на диск в виде MP4-файла. Ниже приведены действия по использованию *видеокаптуре* .
1. Создание объекта *видеокаптуре*
2. Создание объекта *камерапараметерс* с нужными параметрами
3. Запуск видеорежима через *стартвидеомодеасинк*
4. Начать запись видео
5. Закончить запись видео
6. Воспроизведение видеорежима и очистка ресурсов

Начните с создания нашего объекта видеокаптуре *видеокаптуре m_VideoCapture = NULL;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

Затем настройте необходимые параметры для записи и запуска.

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

После запуска Запустите запись.

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

После начала записи можно обновить пользовательский интерфейс или поведение, чтобы включить остановку. Здесь вы только зарегистрируетесь.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

Позже вы захотите отключить запись. Например, это может произойти из таймера или ввода пользователя.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

После остановки записи остановите видеорежим и очистите ресурсы.

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

## <a name="troubleshooting"></a>"Устранение неполадок"
* Нет доступных разрешений
    * Убедитесь, что в проекте указана возможность использования **веб-камеры** .

## <a name="see-also"></a>См. также
* [Камера с определяемым местоположением](locatable-camera.md)
