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
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="523a3-104">Может быть найдена камеры в Unity</span><span class="sxs-lookup"><span data-stu-id="523a3-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="523a3-105">Включение возможности для видеокамера фото</span><span class="sxs-lookup"><span data-stu-id="523a3-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="523a3-106">Функция «Веб-камера» должен быть объявлен для приложения для использования [камеры](locatable-camera.md).</span><span class="sxs-lookup"><span data-stu-id="523a3-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="523a3-107">В редакторе Unity, перейдите к параметрам проигрывателя, перейдя на страницу «Изменить > проекта Параметры > Player»</span><span class="sxs-lookup"><span data-stu-id="523a3-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="523a3-108">Перейдите на вкладку «Windows Store»</span><span class="sxs-lookup"><span data-stu-id="523a3-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="523a3-109">В разделе «Возможности публикации > Параметры» установите флажок **веб-камера** и **"микрофон"** возможности</span><span class="sxs-lookup"><span data-stu-id="523a3-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="523a3-110">Одновременно с камеры могут возникнуть только одну операцию.</span><span class="sxs-lookup"><span data-stu-id="523a3-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="523a3-111">Чтобы определить, какой режим (фото, видео или none) камеры в данный момент, можно проверить UnityEngine.XR.WSA.WebCam.Mode.</span><span class="sxs-lookup"><span data-stu-id="523a3-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="523a3-112">Фотосъемки</span><span class="sxs-lookup"><span data-stu-id="523a3-112">Photo Capture</span></span>

<span data-ttu-id="523a3-113">**Пространство имен:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="523a3-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="523a3-114">**Тип:** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="523a3-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="523a3-115">*PhotoCapture* типа позволяет по-прежнему воспользоваться фотографии с видеокамеры фотографии.</span><span class="sxs-lookup"><span data-stu-id="523a3-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="523a3-116">Общий шаблон с помощью *PhotoCapture* чтобы сделать фотографию выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="523a3-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="523a3-117">Создание *PhotoCapture* объекта</span><span class="sxs-lookup"><span data-stu-id="523a3-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="523a3-118">Создание *CameraParameters* с параметрами, мы хотим</span><span class="sxs-lookup"><span data-stu-id="523a3-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="523a3-119">Перейти в режим фотографий с помощью *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="523a3-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="523a3-120">Сделать нужные фото</span><span class="sxs-lookup"><span data-stu-id="523a3-120">Take the desired photo</span></span>
    * <span data-ttu-id="523a3-121">(необязательно) Взаимодействовать с изображения</span><span class="sxs-lookup"><span data-stu-id="523a3-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="523a3-122">Выход из режима фотографии и очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="523a3-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="523a3-123">Общие настройки для PhotoCapture</span><span class="sxs-lookup"><span data-stu-id="523a3-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="523a3-124">Для всех трех целей мы начнем с тем же сначала 3 описанные выше действия</span><span class="sxs-lookup"><span data-stu-id="523a3-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="523a3-125">Мы начнем с создания *PhotoCapture* объекта</span><span class="sxs-lookup"><span data-stu-id="523a3-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="523a3-126">Далее мы хранения нашего объекта, значение списка параметров и Photo режим запуска</span><span class="sxs-lookup"><span data-stu-id="523a3-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="523a3-127">В конце концов мы также применяются те же очистки здесь код</span><span class="sxs-lookup"><span data-stu-id="523a3-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="523a3-128">После выполнения этих шагов можно выбрать тип фотографии для записи.</span><span class="sxs-lookup"><span data-stu-id="523a3-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="523a3-129">Захват фото в файл</span><span class="sxs-lookup"><span data-stu-id="523a3-129">Capture a Photo to a File</span></span>

<span data-ttu-id="523a3-130">Самый простой операции — извлечение фотографии непосредственно в файл.</span><span class="sxs-lookup"><span data-stu-id="523a3-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="523a3-131">Фотографии могут сохраняться как JPG или PNG.</span><span class="sxs-lookup"><span data-stu-id="523a3-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="523a3-132">Если мы успешно запущен режим фотографий, мы теперь будет сделать фотографию и сохранять их на диске</span><span class="sxs-lookup"><span data-stu-id="523a3-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

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

<span data-ttu-id="523a3-133">После сохранения фотографий на диск, мы выйти из режима фотографии и затем выполнить очистку объектов</span><span class="sxs-lookup"><span data-stu-id="523a3-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="523a3-134">Записать фотографию, чтобы Texture2D</span><span class="sxs-lookup"><span data-stu-id="523a3-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="523a3-135">При записи данных Texture2D, процесс аналогичен чрезвычайно записи на диск.</span><span class="sxs-lookup"><span data-stu-id="523a3-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="523a3-136">Мы будем следовать выше процесс установки.</span><span class="sxs-lookup"><span data-stu-id="523a3-136">We will follow the set up process above.</span></span>

<span data-ttu-id="523a3-137">В *OnPhotoModeStarted*, мы будет захвата кадра в память.</span><span class="sxs-lookup"><span data-stu-id="523a3-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

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

<span data-ttu-id="523a3-138">Затем мы наш результат применения к текстуре и использоваться общие очистки приведенный выше код.</span><span class="sxs-lookup"><span data-stu-id="523a3-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="523a3-139">Захват фото и взаимодействие с необработанными байтами</span><span class="sxs-lookup"><span data-stu-id="523a3-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="523a3-140">Для взаимодействия с необработанные байты обработки в памяти кадра, мы будем следовать те же самые действия, что и выше и *OnPhotoModeStarted* как захват фотографию, чтобы Texture2D.</span><span class="sxs-lookup"><span data-stu-id="523a3-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="523a3-141">Различие заключается в *OnCapturedPhotoToMemory* где мы можем получать необработанные байты и взаимодействовать с ними.</span><span class="sxs-lookup"><span data-stu-id="523a3-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="523a3-142">В этом примере мы создадим *списка<Color>*  которого может быть дополнительно обработаны или применить к текстуры с помощью *SetPixels()*</span><span class="sxs-lookup"><span data-stu-id="523a3-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="523a3-143">Видеозаписи</span><span class="sxs-lookup"><span data-stu-id="523a3-143">Video Capture</span></span>

<span data-ttu-id="523a3-144">**Пространство имен:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="523a3-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="523a3-145">**Тип:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="523a3-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="523a3-146">*VideoCapture* функции, подобные очень *PhotoCapture*.</span><span class="sxs-lookup"><span data-stu-id="523a3-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="523a3-147">Только два различия, что необходимо указать значение кадры на второй (кадров/с), и можно сохранить только непосредственно на диск как MP4-файл.</span><span class="sxs-lookup"><span data-stu-id="523a3-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="523a3-148">Указания по использованию *VideoCapture* таковы:</span><span class="sxs-lookup"><span data-stu-id="523a3-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="523a3-149">Создание *VideoCapture* объекта</span><span class="sxs-lookup"><span data-stu-id="523a3-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="523a3-150">Создание *CameraParameters* с параметрами, мы хотим</span><span class="sxs-lookup"><span data-stu-id="523a3-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="523a3-151">Запуск видеорежима через *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="523a3-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="523a3-152">Начать запись видео</span><span class="sxs-lookup"><span data-stu-id="523a3-152">Start recording video</span></span>
5. <span data-ttu-id="523a3-153">Остановить запись видео</span><span class="sxs-lookup"><span data-stu-id="523a3-153">Stop recording video</span></span>
6. <span data-ttu-id="523a3-154">Выход из режима видео и очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="523a3-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="523a3-155">Мы начнем с создания нашей *VideoCapture* объект *VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="523a3-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="523a3-156">Мы затем настроим параметры, которые нам потребуются средства для записи и запуска.</span><span class="sxs-lookup"><span data-stu-id="523a3-156">We then will set up the parameters we will want for the recording and start.</span></span>

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

<span data-ttu-id="523a3-157">После запуска, мы начнем с записи</span><span class="sxs-lookup"><span data-stu-id="523a3-157">Once started, we will begin the recording</span></span>

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

<span data-ttu-id="523a3-158">После запуска записи удалось обновить пользовательский Интерфейс или поведения, чтобы включить остановки.</span><span class="sxs-lookup"><span data-stu-id="523a3-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="523a3-159">Здесь мы просто в журнал</span><span class="sxs-lookup"><span data-stu-id="523a3-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="523a3-160">В дальнейшем необходимо остановить запись.</span><span class="sxs-lookup"><span data-stu-id="523a3-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="523a3-161">Это может произойти с таймером или пользовательского ввода, для экземпляра.</span><span class="sxs-lookup"><span data-stu-id="523a3-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="523a3-162">После остановки записи нужно будет остановить видеорежима и очистить наши ресурсы.</span><span class="sxs-lookup"><span data-stu-id="523a3-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="523a3-163">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="523a3-163">Troubleshooting</span></span>
* <span data-ttu-id="523a3-164">Никаких действий не доступны.</span><span class="sxs-lookup"><span data-stu-id="523a3-164">No resolutions are available</span></span>
    * <span data-ttu-id="523a3-165">Убедитесь, **веб-камера** возможности, указанные в проекте.</span><span class="sxs-lookup"><span data-stu-id="523a3-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="523a3-166">См. также</span><span class="sxs-lookup"><span data-stu-id="523a3-166">See Also</span></span>
* [<span data-ttu-id="523a3-167">Может быть найдена камеры</span><span class="sxs-lookup"><span data-stu-id="523a3-167">Locatable camera</span></span>](locatable-camera.md)
