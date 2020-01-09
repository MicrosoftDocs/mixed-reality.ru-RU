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
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="d7d37-104">Камера размещаемые в Unity</span><span class="sxs-lookup"><span data-stu-id="d7d37-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="d7d37-105">Включение возможности для видеокамеры</span><span class="sxs-lookup"><span data-stu-id="d7d37-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="d7d37-106">Для использования [камеры](locatable-camera.md)приложение должно быть объявлено как "веб-камера".</span><span class="sxs-lookup"><span data-stu-id="d7d37-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="d7d37-107">В редакторе Unity перейдите к параметрам проигрывателя, перейдя на страницу "Изменение > параметров проекта > Player".</span><span class="sxs-lookup"><span data-stu-id="d7d37-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="d7d37-108">Перейдите на вкладку "Магазин Windows".</span><span class="sxs-lookup"><span data-stu-id="d7d37-108">Click the "Windows Store" tab</span></span>
3. <span data-ttu-id="d7d37-109">В разделе "Параметры публикации > возможности" Проверьте возможности веб- **камеры** и **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="d7d37-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="d7d37-110">Только одна операция может выполняться с камерой за раз.</span><span class="sxs-lookup"><span data-stu-id="d7d37-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="d7d37-111">Чтобы определить, в каком режиме в настоящее время используется камера (Фото, видео или нет), можно проверить UnityEngine. XR. WSA. Camera. Mode.</span><span class="sxs-lookup"><span data-stu-id="d7d37-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="d7d37-112">Запись фотографий</span><span class="sxs-lookup"><span data-stu-id="d7d37-112">Photo Capture</span></span>

<span data-ttu-id="d7d37-113">**Пространство имен:** *UnityEngine. XR. WSA. веб-камера*</span><span class="sxs-lookup"><span data-stu-id="d7d37-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="d7d37-114">**Тип:** *фотозапись*</span><span class="sxs-lookup"><span data-stu-id="d7d37-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="d7d37-115">Тип *фотосъемки* позволяет вам по-прежнему иметь фотографии фотокамеры.</span><span class="sxs-lookup"><span data-stu-id="d7d37-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="d7d37-116">Общий шаблон использования *фотосъемки* для получения фотографий выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d7d37-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="d7d37-117">Создание объекта *Фотозаписи*</span><span class="sxs-lookup"><span data-stu-id="d7d37-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="d7d37-118">Создание объекта *камерапараметерс* с нужными параметрами</span><span class="sxs-lookup"><span data-stu-id="d7d37-118">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="d7d37-119">Запуск фоторежима через *стартфотомодеасинк*</span><span class="sxs-lookup"><span data-stu-id="d7d37-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="d7d37-120">Взять нужную фотографию</span><span class="sxs-lookup"><span data-stu-id="d7d37-120">Take the desired photo</span></span>
    * <span data-ttu-id="d7d37-121">используемых Взаимодействие с этим изображением</span><span class="sxs-lookup"><span data-stu-id="d7d37-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="d7d37-122">Отключение режима фото и очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="d7d37-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="d7d37-123">Стандартная настройка для фотозахвата</span><span class="sxs-lookup"><span data-stu-id="d7d37-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="d7d37-124">Для всех трех вариантов использования Начните с тех же самых первых 3 шагов.</span><span class="sxs-lookup"><span data-stu-id="d7d37-124">For all three uses, start with the same first 3 steps above</span></span>

<span data-ttu-id="d7d37-125">Начните с создания объекта *фотосъемки*</span><span class="sxs-lookup"><span data-stu-id="d7d37-125">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="d7d37-126">Затем сохраните объект, задайте параметры и запустите режим фото.</span><span class="sxs-lookup"><span data-stu-id="d7d37-126">Next, store your object, set your parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="d7d37-127">В итоге вы также будете использовать тот же код очистки, представленный здесь.</span><span class="sxs-lookup"><span data-stu-id="d7d37-127">In the end, you will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="d7d37-128">После выполнения этих действий можно выбрать тип фотографии для записи.</span><span class="sxs-lookup"><span data-stu-id="d7d37-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="d7d37-129">Запись фотографии в файл</span><span class="sxs-lookup"><span data-stu-id="d7d37-129">Capture a Photo to a File</span></span>

<span data-ttu-id="d7d37-130">Самой простой операцией является запись фотографии непосредственно в файл.</span><span class="sxs-lookup"><span data-stu-id="d7d37-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="d7d37-131">Фотографию можно сохранить в формате JPG или PNG.</span><span class="sxs-lookup"><span data-stu-id="d7d37-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="d7d37-132">Если вы успешно начали фото-режим, возьмите фотографию и сохраните ее на диске.</span><span class="sxs-lookup"><span data-stu-id="d7d37-132">If you successfully started photo mode, take a photo and store it on disk</span></span>

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

<span data-ttu-id="d7d37-133">После записи фотографии на диск выйдите из режима Photo, а затем очистите объекты</span><span class="sxs-lookup"><span data-stu-id="d7d37-133">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="d7d37-134">Запись фотографии в Texture2D</span><span class="sxs-lookup"><span data-stu-id="d7d37-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="d7d37-135">При записи данных в Texture2D процесс очень похож на запись на диск.</span><span class="sxs-lookup"><span data-stu-id="d7d37-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="d7d37-136">Выполните описанный выше процесс настройки.</span><span class="sxs-lookup"><span data-stu-id="d7d37-136">Follow the set up process above.</span></span>

<span data-ttu-id="d7d37-137">В *онфотомодестартед*запишите кадр в память.</span><span class="sxs-lookup"><span data-stu-id="d7d37-137">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

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

<span data-ttu-id="d7d37-138">Затем вы примените результат к текстуре и используйте общий код очистки, приведенный выше.</span><span class="sxs-lookup"><span data-stu-id="d7d37-138">You will then apply your result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="d7d37-139">Запись фотографии и взаимодействие с необработанными байтами</span><span class="sxs-lookup"><span data-stu-id="d7d37-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="d7d37-140">Чтобы взаимодействовать с необработанными байтами в кадре памяти, выполните те же действия по настройке, что и в предыдущем разделе, и *онфотомодестартед* , как при записи фотографии в Texture2D.</span><span class="sxs-lookup"><span data-stu-id="d7d37-140">To interact with the raw bytes of an in memory frame, follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="d7d37-141">Разница заключается в *онкаптуредфототомемори* , где можно получить необработанные байты и взаимодействовать с ними.</span><span class="sxs-lookup"><span data-stu-id="d7d37-141">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="d7d37-142">В этом примере вы создадите *список<Color>* который можно обработать или применить к текстуре с помощью *сетпикселс ()* .</span><span class="sxs-lookup"><span data-stu-id="d7d37-142">In this example, you will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="d7d37-143">Видеозапись</span><span class="sxs-lookup"><span data-stu-id="d7d37-143">Video Capture</span></span>

<span data-ttu-id="d7d37-144">**Пространство имен:** *UnityEngine. XR. WSA. веб-камера*</span><span class="sxs-lookup"><span data-stu-id="d7d37-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="d7d37-145">**Тип:** *видеокаптуре*</span><span class="sxs-lookup"><span data-stu-id="d7d37-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="d7d37-146">Функция *видеокаптуре* очень похожа на функцию *фотозахвата*.</span><span class="sxs-lookup"><span data-stu-id="d7d37-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="d7d37-147">Единственное отличие заключается в том, что необходимо указать значение кадров в секунду, которое можно сохранить непосредственно на диск в виде MP4-файла.</span><span class="sxs-lookup"><span data-stu-id="d7d37-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="d7d37-148">Ниже приведены действия по использованию *видеокаптуре* .</span><span class="sxs-lookup"><span data-stu-id="d7d37-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="d7d37-149">Создание объекта *видеокаптуре*</span><span class="sxs-lookup"><span data-stu-id="d7d37-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="d7d37-150">Создание объекта *камерапараметерс* с нужными параметрами</span><span class="sxs-lookup"><span data-stu-id="d7d37-150">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="d7d37-151">Запуск видеорежима через *стартвидеомодеасинк*</span><span class="sxs-lookup"><span data-stu-id="d7d37-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="d7d37-152">Начать запись видео</span><span class="sxs-lookup"><span data-stu-id="d7d37-152">Start recording video</span></span>
5. <span data-ttu-id="d7d37-153">Закончить запись видео</span><span class="sxs-lookup"><span data-stu-id="d7d37-153">Stop recording video</span></span>
6. <span data-ttu-id="d7d37-154">Воспроизведение видеорежима и очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="d7d37-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="d7d37-155">Начните с создания нашего объекта видеокаптуре *видеокаптуре m_VideoCapture = NULL;*</span><span class="sxs-lookup"><span data-stu-id="d7d37-155">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="d7d37-156">Затем настройте необходимые параметры для записи и запуска.</span><span class="sxs-lookup"><span data-stu-id="d7d37-156">Next, set up the parameters you will want for the recording and start.</span></span>

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

<span data-ttu-id="d7d37-157">После запуска Запустите запись.</span><span class="sxs-lookup"><span data-stu-id="d7d37-157">Once started, begin the recording</span></span>

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

<span data-ttu-id="d7d37-158">После начала записи можно обновить пользовательский интерфейс или поведение, чтобы включить остановку.</span><span class="sxs-lookup"><span data-stu-id="d7d37-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="d7d37-159">Здесь вы только зарегистрируетесь.</span><span class="sxs-lookup"><span data-stu-id="d7d37-159">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="d7d37-160">Позже вы захотите отключить запись.</span><span class="sxs-lookup"><span data-stu-id="d7d37-160">At a later point, you will want to stop the recording.</span></span> <span data-ttu-id="d7d37-161">Например, это может произойти из таймера или ввода пользователя.</span><span class="sxs-lookup"><span data-stu-id="d7d37-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="d7d37-162">После остановки записи остановите видеорежим и очистите ресурсы.</span><span class="sxs-lookup"><span data-stu-id="d7d37-162">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="d7d37-163">"Устранение неполадок"</span><span class="sxs-lookup"><span data-stu-id="d7d37-163">Troubleshooting</span></span>
* <span data-ttu-id="d7d37-164">Нет доступных разрешений</span><span class="sxs-lookup"><span data-stu-id="d7d37-164">No resolutions are available</span></span>
    * <span data-ttu-id="d7d37-165">Убедитесь, что в проекте указана возможность использования **веб-камеры** .</span><span class="sxs-lookup"><span data-stu-id="d7d37-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7d37-166">См. также</span><span class="sxs-lookup"><span data-stu-id="d7d37-166">See Also</span></span>
* [<span data-ttu-id="d7d37-167">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="d7d37-167">Locatable camera</span></span>](locatable-camera.md)
